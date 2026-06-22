# Medusa

> **Medusa Skill Framework (MSF)** — 超高速 Claude Code Skill 掃描與排序引擎，以 Rust 編寫。

## 概覽

Medusa 掃描 `.claude/skills/` 目錄下的所有 Skill YAML 文件，分析複雜度與價值，產生審計報告並推薦最佳 Skill 組合。

核心功能：
- **審計排序系統**：60/30/10 加權（價值/複雜度/使用頻率）
- **9 層等級系統**：從 Novice 到 Legendary 自動分級
- **上下文構建**：分析 Skill 之間的依賴關係與融合機會
- **自動晉升**：使用頻率達到門檻後自動升級

## 啟動

```bash
# 掃描當前目錄下的 skills
cargo run

# 或使用編譯後的執行檔
./target/release/medusa

# 開發模式
cargo run -- --path /path/to/skills

# 建置
cargo build --release
```

## 技術棧

- **語言：** Rust (Edition 2021)
- **並行處理：** Rayon
- **YAML 解析：** Serde + TOML
- **檔案遍歷：** WalkDir
- **雜湊：** FxHash（高速）

## 輸出格式

```json
{
  "skill": "skill-name",
  "level": "Expert",
  "confidence": 0.87,
  "experience": 142.5,
  "metrics": {
    "complexity_score": 0.72,
    "value_score": 0.91
  },
  "context": {
    "dependencies": [...],
    "fusion_opportunities": [...]
  }
}
```

## 版本

當前版本：`0.11.0`

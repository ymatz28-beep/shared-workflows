# shared-workflows

Reusable GitHub Actions workflows for ymatz28-beep projects.

## Available Workflows

### claude-issue-handler.yml

Issue-driven Claude Code automation. Creates a standard pipeline:
Issue (with `update` label) -> Claude CLI -> commit -> comment -> close

**Inputs:**
- `checkout_ref` — Branch to checkout (default: `main`)
- `claude_prompt` — Domain-specific instructions for Claude
- `success_comment` — Comment on success (default: `反映完了 ✅`)
- `no_changes_comment` — Comment when nothing changed
- `timeout_minutes` — Job timeout (default: `10`)

**Required Secrets:**
- `ANTHROPIC_API_KEY`

**Usage:**
```yaml
jobs:
  update:
    uses: ymatz28-beep/shared-workflows/.github/workflows/claude-issue-handler.yml@main
    with:
      claude_prompt: "あなたは..."
      success_comment: "反映完了 ✅\nhttps://example.github.io/my-project/"
    secrets:
      ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
```

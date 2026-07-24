# JC Skill

Public, reusable Codex workflows by Jiajun Chen.

This repository contains exactly one Codex plugin, `jcskill`. The plugin can hold multiple skills over time. Its first skill is `rename-codex-session`.

## Included skill

### `rename-codex-session`

Renames the current Codex task or optimizes up to 30 recent Codex task titles from their latest substantive work.

Safety boundaries:

- Reads only Codex tasks, not ChatGPT chats.
- Prepares all candidate titles before making changes.
- Changes task titles only.
- Never sends messages, forks, pins, archives, or deletes tasks.
- Skips ambiguous tasks instead of guessing.

## Install from skills.sh

```bash
npx skills add thejiajun/jcskill \
  --skill rename-codex-session \
  --agent codex \
  --global
```

## Install as a Codex plugin

```bash
codex plugin marketplace add thejiajun/jcskill
codex plugin add jcskill@jcskill
```

Start a new Codex task after installation so Codex loads the skill.

## Usage

```text
$rename-codex-session Rename this task from its latest substantive work.
```

```text
$rename-codex-session Optimize the titles of my 30 most recent Codex tasks.
```

## Compatibility

This skill requires Codex task-management tools compatible with:

- `list_threads`
- `read_thread`
- `set_thread_title`

If those tools are unavailable, the skill can propose a title but cannot apply it.

The hourly automation is not included. Each user must create their own recurring automation if desired.

## Repository structure

```text
.agents/plugins/marketplace.json
plugins/jcskill/
├── .codex-plugin/plugin.json
└── skills/
    └── rename-codex-session/
        ├── SKILL.md
        └── agents/openai.yaml
```

## License

MIT

# hermes-agent-themes

A personal collection of [Hermes Agent](https://github.com/NousResearch/hermes-agent) skins.
Each skin is a single YAML file that themes the CLI, the TUI, and the desktop GUI from
one palette — drop it in `~/.hermes/skins/` and Hermes repaints every surface live.

## Themes

### Gruvbox

All six are faithful ports of the official [Gruvbox](https://github.com/morhetz/gruvbox)
palette (dark mode uses the *bright* accents, light mode uses the *neutral* ones,
exactly like the upstream Vim theme).

| Skin | Background | Foreground | Accent |
|---|---|---|---|
| [`gruvbox-dark`](skins/gruvbox-dark.yaml) | `#282828` | `#ebdbb2` | `#fabd2f` |
| [`gruvbox-dark-hard`](skins/gruvbox-dark-hard.yaml) | `#1d2021` | `#ebdbb2` | `#fabd2f` |
| [`gruvbox-dark-soft`](skins/gruvbox-dark-soft.yaml) | `#32302f` | `#ebdbb2` | `#fabd2f` |
| [`gruvbox-light`](skins/gruvbox-light.yaml) | `#fbf1c7` | `#3c3836` | `#af3a03` |
| [`gruvbox-light-hard`](skins/gruvbox-light-hard.yaml) | `#f9f5d7` | `#3c3836` | `#af3a03` |
| [`gruvbox-light-soft`](skins/gruvbox-light-soft.yaml) | `#f2e5bc` | `#3c3836` | `#af3a03` |

*Hard* = deeper dark / brighter cream, *soft* = lighter dark / warmer tan — the standard
Gruvbox contrast ladder (`dark0_hard · dark0 · dark0_soft`, `light0_hard · light0 · light0_soft`).

### Horizon

Ports of [base16-horizon-scheme](https://git.michaelball.name/base16-horizon-scheme/tree/)
by Michaël Ball — the Base16 rendering of Jonathan Olaleye's
[Horizon VSCode theme](https://github.com/jolaleye/horizon-theme-vscode). The base16
roles map straight onto Hermes' semantic keys: `base00` background, `base01` status/menu
surfaces, `base02` borders & selection, `base03` muted text, `base05/07` text hierarchy,
coral `base09` accent. In the two light skins, pastel tints that fall below ~2.5:1 on
blush (`#FDF0ED`) are replaced by the darker Horizon-family equivalents of the same hue,
so status colors stay green/amber/red instead of vanishing.

| Skin | Background | Foreground | Accent |
|---|---|---|---|
| [`horizon-dark`](skins/horizon-dark.yaml) | `#1C1E26` | `#CBCED0` | `#E58D7D` |
| [`horizon-light`](skins/horizon-light.yaml) | `#FDF0ED` | `#403C3D` | `#DA103F` |
| [`horizon-terminal-dark`](skins/horizon-terminal-dark.yaml) | `#1C1E26` | `#CBCED0` | `#FAB795` |
| [`horizon-terminal-light`](skins/horizon-terminal-light.yaml) | `#FDF0ED` | `#403C3D` | `#E95678` |

The two *terminal* variants follow the terminal scheme files (signature mint `#29D398`
strings, aqua `#26BBD9`, pink `#EE64AC`); the plain dark/light variants follow the
VSCode-derived schemes (warm peaches, violet `#B072D1` keywords, raspberry `#DA103F`).

## Install

```bash
cp skins/*.yaml ~/.hermes/skins/
```

Activate one — every open surface (CLI, TUI, desktop) repaints within ~a second:

```bash
hermes config set display.skin gruvbox-dark
```

Switch between installed skins with `hermes skin list` / `hermes skin use <name>`,
or the desktop Appearance settings and `⌘K`. Revert with:

```bash
hermes config set display.skin default
```

## Tuning a skin you like

Don't fork a file for a one-color tweak — edit the **active** skin in place so the
rest of the palette (background included) survives:

```bash
hermes skin set ui_tool "#8ec07c"   # e.g. gruvbox-aqua tool markers
```

## Palette mapping

The skins set the full semantic key list (`background`, `ui_accent`, `ui_tool`,
`ui_thinking`, `banner_*`, `status_bar_*`, `completion_menu_*`, `diff_*`,
`syntax_*`, …). Gruvbox role choices follow gruvbox.vim itself: keywords → red,
numbers/constants → purple, strings → green, comments → `gray_245`, borders →
`dark2`/`light2`, status bar → `dark1`/`light1`. Light-mode accents use the darker
*faded* orange so interactive text clears WCAG AA on cream. Horizon skins follow the
base16 slot conventions instead (see the Horizon section above).

## Credits

- Gruvbox color palette by [Pavel "morhetz" Pertsev](https://github.com/morhetz/gruvbox), MIT license.
- Horizon palette via [Michaël Ball's base16-horizon-scheme](https://git.michaelball.name/base16-horizon-scheme/),
  based on the Horizon VSCode theme by [Jonathan Olaleye](https://github.com/jolaleye/horizon-theme-vscode), MIT license.
- Hermes skin schema: [`hermes_cli/skin_engine.py`](https://github.com/NousResearch/hermes-agent) and `apps/shared/src/skin.ts`.

MIT © Alexi Rahman

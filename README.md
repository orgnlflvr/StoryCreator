# Story Creator

Write your own stories for **!Ω Factorial Omega: My Dystopian Robot Girlfriend** by Incontinent Cell, and play them in the game's own dialogue box, with the real portraits, faces, outfits, backgrounds, music and the game's timing minigames.

> [!IMPORTANT]
> This is a **fan-made mod**. It is not made, checked or supported by Incontinent Cell.
> It does not unlock or touch any paid or patron content.
> Use it on a **copy** of your game folder.

## Version notice

| | Version |
| --- | --- |
| Story Creator | 1.0.0 |
| Game | 0.97.12 |
| MelonLoader | **0.7.3** (stable) |
| OS | Windows |

> [!WARNING]
> Use MelonLoader **0.7.3**. Do **not** enable "nightly builds" in the MelonLoader installer.

## Features

- **Story editor.** Write scenes at `http://127.0.0.1:8766/stories`, with a checker that points out mistakes, then play them in game with F3.
- **The real cast.** Jun, Annalie, Melissa, Shanice, Big Daddy and more, with their own faces, gestures and outfits.
- **Places and music.** The game's backgrounds and soundtrack, plus your own pictures if you want.
- **Choices and endings.** Branch your story with choice buttons and as many endings as you like.
- **Minigames in stories.** Use the game's own timing bar: bowling matches, repairs, rescues. Scores can decide the ending.
- **Stage page.** Place characters with the mouse and copy the lines into your story.
- **Story packs.** Share stories as one `.storypack` file.

No AI server is needed. Stories can be played once your save is past the prologue.

## Installation

1. Make a copy of your game folder. Work only in the copy.
2. Run the [MelonLoader](https://github.com/LavaGang/MelonLoader) installer, pick the game's `.exe` from the copy, choose **0.7.3**, and install.
3. Start the game once and let MelonLoader finish setting up. Close it at the menu.
4. Download `StoryCreator_1.0.0.zip` from [Releases](../../releases) and copy its `Mods` and `UserData` folders into the game folder.
5. Start the game, load a save and press **F3**.

> [!NOTE]
> **Coming from Jun Link 1.0 or MDRG Panel?** Update Jun Link to 1.1 (or remove it) and delete `Mods\MdrgPanelML.dll`. Story Creator stays off while an older all-in-one version is in `Mods`, and the log says why. On the first start, your stories and backgrounds are copied over.

### Keys and pages

| Key / page | What it does |
| --- | --- |
| F3 | Play a story (press again to stop) |
| F9 | Open the settings page |
| `http://127.0.0.1:8766/stories` | Story editor |
| `http://127.0.0.1:8766/stage` | Stage: place characters with the mouse |
| `http://127.0.0.1:8766/packs` | Install and make story packs |

## Included example stories

| Story | What it shows |
| --- | --- |
| **Example: One Bowling Throw** | The smallest minigame story: one throw of the game's timing bar, three outcomes |
| **Strike Night: The Gauntlet** | Full bowling matches: `@score reset`, several throws, `@total` for win / tie / lose, rematches |
| **Not Today, Melissa** | A minigame as story tension: three holds decide how her what-if night ends |

## Writing your own stories

Stories are plain `.story` text files in `UserData\StoryCreator\jun_stories`. A tiny one:

```
title: Hello
# start
@background room
{bot} [happy]: You wrote a story. I am proud of you.
? Thanks -> end
? Again! -> start
```

A bowling throw with the game's timing bar:

```
@score reset
@minigame skillcheck 1
{bot} [lecture]: {pins} pins. Total: {total}.
@total win>=8 lose
```

Every command and every character's faces are in the editor's help panel.

## Backgrounds for stories

Some example stories use the game's own places (bowling alley, night cafe). Without them, a drawn stand-in or the street is used. The game's pictures are **not** in this repo or the release (the `jun_backgrounds` folder here only holds the drawn bowling stand-in). Make them from your own copy of the game, from the game folder:

```
pip install UnityPy
python "UserData\StoryCreator\tools\export_backgrounds.py"
```

> [!CAUTION]
> The exported pictures belong to the game. Keep them on your PC. Never upload them, put them in a story pack, or open a pull request with them.

## Want to talk to Jun too?

[Jun Link](https://github.com/orgnlflvr/JunLink) is a separate, optional mod: chat with Jun through an AI model running on your own PC. Both run side by side.

## Building from source

Story Creator and Jun Link are built from the same source. Requirements: the [.NET 6 SDK](https://dotnet.microsoft.com/download/dotnet/6.0), and a game folder with MelonLoader 0.7.3 that has been started once.

1. Copy `Local.props.example` to `Local.props` and put your game folder in it.
2. In `src\Melon`, run `build_story.bat`. The DLL lands in `src\Melon\out\story\StoryCreator.dll`.

Or by hand: `dotnet build -c Release -p:Mod=Story -p:GameDir="C:\path\to\game"`.

## Configuration

Everything is on the settings page (F9 or `http://127.0.0.1:8766/settings`) and saved in `UserData\StoryCreator.cfg`: story key, music, choice buttons, character size and spread, background fade, and the web port.

## Reporting problems

Open an [issue](../../issues) and attach `MelonLoader\Latest.log`. Say your game version and what you did right before it went wrong.

## Credits

- Made by **Original Flavour** ([@orgnlflvr](https://github.com/orgnlflvr)).
- **!Ω Factorial Omega: My Dystopian Robot Girlfriend** and all its characters, art and music belong to Incontinent Cell. This mod is unofficial.
- [MelonLoader](https://github.com/LavaGang/MelonLoader) by LavaGang.
- [Montserrat](https://github.com/JulietaUla/Montserrat) font (SIL Open Font License), built into the web pages.
- Thanks to Ikari and the MDRG modding community.

## License

The mod's own code and story files are under the [MIT License](LICENSE.txt).
This does not cover the game or anything from it.

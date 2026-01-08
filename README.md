# FNF-Window-Control-Events-PC-V-SLICE-
a events of where the charters make their own mods, using this makes a someone's life better.

Window Control Events — Technical Documentation
Window Control Events is a lightweight extension for Friday Night Funkin’ (V‑Slice) that exposes three OS‑level window actions to the Chart Editor: changing the window title, changing the window icon, and teleporting the window to preset screen positions.
Each feature is implemented using a dedicated ScriptedModule and a matching ScriptedSongEvent, making the system fully modular and easy to extend.

Features
• Change Window Title
Allows charts to dynamically update the game window’s title bar text.
Useful for meta storytelling, glitch effects, or giving characters a way to “speak” through the window itself.

• Change Window Icon
Replaces the window’s icon at runtime using PNG files stored in the mod folder.
Great for horror mods, character‑themed transitions, or desktop‑level visual cues.

• Window Teleport Event
Instantly snaps the game window to preset screen positions using real display resolution detection.
Supports:

top-left

top-right

bottom-left

bottom-right

center

Perfect for Rewrite‑style cinematics, multi‑monitor jumps, or desktop interaction sequences.

Architecture
Modules (/scripts/)
Each system is implemented as a full Haxe class extending ScriptedModule.
Modules expose callable functions such as:

setWindowTitle(title:String)

setWindowIcon(path:String)

teleportWindow(position:String)

These functions interact directly with Lime’s window API.

Events (/events/)
Each module has a matching ScriptedSongEvent that:

Defines a unique event ID

Provides a Chart Editor schema

Passes parameters to the module via scriptCall()

This keeps chart logic clean and engine‑safe.

Chart Editor Integration
Each event appears automatically in the Chart Editor with its own parameter field:

Window Title Event
json
{
  "title": "string"
}
Window Icon Event
json
{
  "path": "string"
}
Window Teleport Event
json
{
  "position": "string"
}
Events can be placed at any timestamp and will execute instantly during gameplay.

Error Handling
Missing icons fail silently without crashing

Invalid teleport positions fall back to center

Null window references are safely ignored

All operations are sandbox‑safe and cross‑platform compatible

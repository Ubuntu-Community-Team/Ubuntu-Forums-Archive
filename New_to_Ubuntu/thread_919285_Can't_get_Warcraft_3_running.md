---
title: "Can't get Warcraft 3 running"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Solais on 2008-09-13
I installed it normally, have wine, i hit play wc3 and it blinks and stays in black screen have to restart pc manually? do i need anything else?:(

---

### Post by dioltas on 2008-09-13
I copied this directly from the [[COLOR="Blue"]wine app database[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1177").

> Running Warcraft 3 under Wine

by Jesse Allen; the3dfxdude at gmail com*

small updates by Jasmine Iwanek

Last updated 2008-07-11

Before you get started

This HOWTO only lists information specific to this app. Please keep comments and test reports brief. Please don't post copies of wine logs here! If you have trouble, see other ways of getting help.

Wine+Warcraft 3 Status as of Wine 1.0.0/1.1.1

Known Problems

    * D3D8: Direct 3D mode is slow on anything but the lowest settings.
    * FreeBSD: could work on version 6.2 or later, but problematic
    * quartz: Divx movies have poor playback performance.
    * opengl: Resolution bugs, window management bugs. Losing focus will crash the game.

Minimum Requirements

    * Video card and driver that supports hardware based acceleration with OpenGL.
    * Correct device node permissions to your audio, video, and cdrom.
    * winecfg: A drive letter for your cdrom, and running as Win2k, XP or later.
    * A REAL COPY OF THE GAME -- The game probably won't work right if you don't have a real copy.
    * Linux kernel 2.6 with NTPL or FreeBSD kernel 6.2 (preferably 7) or later.

Recommended Requirements

    * Warcraft 3 1.21b or later
    * Wine 0.9.18 - 0.9.45. If using later wine, you must patch it--see below.
    * Linux kernel 2.6.17+ or FreeBSD kernel 6.2+

**Bad Versions**
Even with patch 1.21b, it's recommended to not use these versions of software because they break the SecuRom copy protection (ie "Please insert disc"):

    * Linux vanilla x86-64 kernel: 2.6.9-2.6.15, and versions less than 2.6
    * Wine compiled with GCC 4.0.0-4.0.2
    * Native msvcrt.dll
    * Nvidia video driver compiled against mismatched X11 header files
    * Fedora Core 6 kernel package less than 2.6.18-1.2784.fc6, and kernel package "kernel.x86_64 2.6.20-1.2933.fc6".
    * FreeBSD

Additionally, FreeBSD kernels less than 6.2 might not work with current versions of Wine at all.

Installing the Game

To default the game to use OpenGL, see the registry import below. This creates HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III with new DWORD value called "Gfx OpenGL" with the value set to 1. So you may create a file using the text, or use regedit to do the same.

When the game's installed, everything should run as expected.

After installing the game, its highly recommended that you browse to your Warcraft III folder and rename the movies folder. Many people crash from the movies because of buggy sound drivers, or simply hang, so you should do this in case you are one of them. You can still play the movies under mplayer (or xine if you so choose)! TutorialIn.mpq is the very first cinematic of the game, and for the rest; *Op.mpq is the cinematic at the start of the campaign and *Ed.mpq is the cinematic and the end. If you wanted to follow the story, it's not hard at all to play the ones corresponding where you are at.

Running the Game

Use the shortcuts created by the game found in your launcher menus.

Multiplayer Setup

Make sure you have the correct ports open. Open outbound and inbound, TCP and UDP, port 6112, or whatever you set in the game configuration. More Network Ports

If you try to play using the Local Area Network option, and do not see a game hosted from your machine on another or vice versa, and you are in the same subnet, this is likely caused by not having a default gateway. The game relies on sending UDP packets to the broadcast address and Linux will not send them unless there is a default gateway or another rule to handle them. To fix it, there are two methods:

Add a default gateway.
- OR -
Route 255. 255. 255. 255 to your local network.

See Wine Traffic #62 for another description of the issue. This is not considered a bug.

Mouse Automatic Edge Scrolling

When running windowed, if you move the cursor out of the screen and back again, sometimes it stays as the scrolling cursor and not the pointer cursor. Hover the mouse over a unit or building to fix the cursor. This is an oversight in the game itself and not a bug in Wine. Use mouse grab or full screen mode to bypass this problem. You may also disable automatic scrolling and use the middle mouse button or the directional keys (non-keypad) for manual scrolling.

Hope it helps. I've never played Warcraft myself, so no experience of it. The [[COLOR="Blue"]wine app database[/COLOR]]("http://appdb.winehq.org/") is always a good place to look if you are having trouble getting a windows application running. The comments usually have good guides/tips. Look for gold / platinum ratings.

---

### Post by Valok on 2008-09-15
Open up your C: directory you made under WINE, then rename the movies folder to something else.  Apparently WINE doesn't like the movies and renaming this folder fixes the problem.

---


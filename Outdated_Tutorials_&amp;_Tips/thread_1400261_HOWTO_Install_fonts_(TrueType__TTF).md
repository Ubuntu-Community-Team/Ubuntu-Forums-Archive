---
title: "HOWTO: Install fonts (TrueType / TTF)"
date: 2010-02-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2010-02-06
[FONT=Arial][SIZE=1]**Issue description: **You want to use fonts such as *Arial Narrow* but they aren't available in the font menu. Or you want to read a .doc or .docx file that comes from other people who uses this font but when you open the file the fonts are replaced.[/SIZE][/FONT]
[FONT=Arial][SIZE=1]
[/SIZE][/FONT][FONT=Arial][SIZE=1]*Note: If you consider yourself an advanced user find below option 2.*[/SIZE][/FONT]

[FONT=Arial][SIZE=1]**Option 1 for beginners.**[/SIZE][/FONT]
 [FONT=Arial][SIZE=1]**STEPS**[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Arial][SIZE=1]Close all OpenOffice windows.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]Navigate to the following Ubuntu menus.
[/SIZE][/FONT][FONT=Arial][SIZE=1]***Application > Add/Remove...***[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]Install [/SIZE][/FONT][FONT=Arial][SIZE=1]***Fonty Python. ***[/SIZE][/FONT][FONT=Arial][SIZE=1]This is a font manager for Ubuntu. It's similar to [/SIZE][/FONT][FONT=Arial][SIZE=1]*Adobe Type Manager*. Find below attached screenshot[/SIZE][/FONT][FONT=Arial][SIZE=1]. [/SIZE][/FONT]
[*] [FONT=Arial][SIZE=1]Open *Fonty Python.*[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]Navigate to the following [/SIZE][/FONT][FONT=Arial][SIZE=1]*Fonty Python's *[/SIZE][/FONT][FONT=Arial][SIZE=1]menu ***Help > Help F1.***[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]The help window will open. Follow instructions on this page.[/SIZE][/FONT]
[*] [FONT=Arial][SIZE=1]Open OpenOffice. Find the font under the font menu.[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=1]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=1][B]Option 2 for advanced users.
STEPS[/B][/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Arial][SIZE=1]Close all OpenOffice windows.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]Download the font you want from the following site. For example [/SIZE][/FONT][FONT=Arial][SIZE=1]*Arial Narrow*[/SIZE][/FONT][FONT=Arial][SIZE=1]. Find below attached screenshot to clarify [/SIZE][/FONT][FONT=Arial][SIZE=1]download link [/SIZE][/FONT][FONT=Arial][SIZE=1]location.
[http://www.free-fonts-ttf.org/true-type-fonts/lexicon-17-high-quality-collections.htm?page=32](http://www.free-fonts-ttf.org/true-type-fonts/lexicon-17-high-quality-collections.htm?page=32)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]Copy the fonts to your *fonts* directory. This directory is located under. This is optional but you can create sub-folders inside this directory.
[/SIZE][/FONT][FONT=Arial][SIZE=1]***/usr/share/fonts/truetype***[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]If you do not have access to copy the fonts the the above folder then type in the following command in TERMINAL. 
[/SIZE][/FONT]```
[FONT=Arial][SIZE=1]***gksudo nautilus***[/SIZE][/FONT]
```
[*][FONT=Arial][SIZE=1]Nautilus file browser will open.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]Use Nautilus to copy the fonts to your .fonts directory.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=1]To rebuild your fonts list. Type in the following command in TERMINAL
[/SIZE][/FONT]```
[FONT=Arial][SIZE=1]***sudo fc-cache -vf***[/SIZE][/FONT]
```
[*][FONT=Arial][SIZE=1]Open OpenOffice. Find the font under the font menu.[/SIZE][/FONT]
[*] [FONT=Arial][SIZE=1]That's it. Now you can read *.doc* or *.docx* that comes from other people who uses this font.[/SIZE][/FONT]
[/LIST]
  [FONT=Arial][SIZE=1]Enjoy,
[/SIZE][/FONT]  [FONT=Arial][SIZE=1]
[/SIZE][/FONT]

---


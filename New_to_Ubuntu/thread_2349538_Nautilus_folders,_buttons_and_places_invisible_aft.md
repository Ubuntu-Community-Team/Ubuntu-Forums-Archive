---
title: "Nautilus folders, buttons and places invisible after making changes to theme"
date: 2017-01-15
forum: New to Ubuntu
---

### Post by pawan148 on 2017-01-15
[COLOR=#111111][FONT=Ubuntu]I'm using Ceti-2 theme on Ubuntu 16.04 Unity edition, and I wanted to change the theme's default blue selection/highlight color to green.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So following instructions in the theme's Readme file, I first changed the color codes in the corresponding SCSS files using a text editor, and then ran parse-sass.sh.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After that I edited the assets.svg file using Inkscape and replaced the blue color with green in all the objects. I then deleted everything inside the theme's "assets" and "borders" sub-folders and ran render-assets.sh and render-border.sh to regenerate the PNG images.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However, after setting this custome theme as my GTK theme, I'm experiencing an issue with Nautilus.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Whenever I open Nautilus, the sidebar shows nothing, there are no toolbar buttons and sometimes even the contents of a folder are not shown. These things become visible only after I hover the mouse over them.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is how Nautilus currently looks on my computer:

[/FONT][/COLOR][ATTACH=CONFIG]273217[/ATTACH]

[ATTACH=CONFIG]273218[/ATTACH]

---


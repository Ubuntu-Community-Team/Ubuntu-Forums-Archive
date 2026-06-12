---
title: "Best place to put a program's resources?"
date: 2010-01-30
forum: Programming Talk
---

### Post by aeron005 on 2010-01-30
I'm looking for some clarification here,

Would it be more logical to put my resources (bitmaps, fonts, etc.)  in the executable directory and use relative paths in my code, or to hard-code a directory such as "/usr/share/games/my_game/image.bmp"? 

Relative paths would be more portable, but in a packaging situation (.deb or otherwise) designed for linux, it would be better to stick with the typical linux conventions (binaries in /usr/games/, read-only data in /usr/share/games/, read-write in /var/games/).

Unless there's some kind of environmental variable-based trickery I'm unaware of, these are the only options... how do most developers deal with this?

---

### Post by JupiterV2 on 2010-01-30
The best way to figure it out is to actually look where programs you currently use store their resources. Use Synaptic to see where packages install their files or browse your directory tree.

---

### Post by diesch on 2010-01-31
Putting data files in the executable directory is IMHO really ugly. Use paths that are hard-coded at install time. You can use environment variables to let the user override the hardcoded paths. Another way is to use a config file to define the paths and define a command line option to select a different config file than the hardcoded default.

---

### Post by aeron005 on 2010-01-31
Thanks guys, I think the config files will make it most portable and flexible... and I'll probably just use the preprocessor to set up the defaults on each platform.

One thing I hate is when I'm on Windows and a program fills up my home directory with .rc's that aren't hidden by default and all sorts of non-windows conventions. When you're using a certain OS you just have certain expectations you know :P

---


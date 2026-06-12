---
title: "Subwoofer and headphone problem Ubuntu 12.10"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by steinmeister on 2013-04-24
[COLOR=#222222][FONT=Verdana][SIZE=2]Heythere[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]I'vebeen searching for a solution for a few months now , but noresult.[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]theproblem is that i can't get the sub woofer from my notebook(HP-pavilion DV7-7050eb) working.[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]i'vetried the solution: [/SIZE][/FONT][/COLOR]snd-hda-intelmodel= ref  butwheni do that, the sub woofer works fine, but now itkeeps on playing when i plug in my earphones.


Whenis use snd-hda-intel  model= hp-dv5 it also works, but in this case iget no sound at all when i plug in the earphones.


Isthere a fix for this??


Thanksin advance

---

### Post by lidex on 2013-09-29
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---


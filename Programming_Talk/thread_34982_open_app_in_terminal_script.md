---
title: "open app in terminal script"
date: 2005-05-17
forum: Programming Talk
---

### Post by ante0 on 2005-05-17
Hi,
I'm using this script for cedega,

#!/bin/bash
gnome-sudo "cedega "$1"" &

to open .exe files through the right-click 'scripts' menu, though, how do i make it so it opens in a terminal before executing? when i run cedega in a terminal

sudo cedega file.exe 

it opens in a window, but with the script it opens in fullscreen.

---

### Post by LordHunter317 on 2005-05-17
[QUOTE=ante0]Hi,
I'm using this script for cedega,

#!/bin/bash
gnome-sudo "cedega "$1"" &

to open .exe files through the right-click 'scripts' menu, though, how do i make it so it opens in a terminal before executing? when i run cedega in a terminal

sudo cedega file.exe 

it opens in a window, but with the script it opens in fullscreen.[/QUOTE]
 Why the hell are you running video games as root in the first place?

---

### Post by jerome bettis on 2005-05-17
#!/bin/bash
gnome-terminal --comand="gnome-sudo \"cedega \"$1\"\" &"

did that work?

---

### Post by ante0 on 2005-05-24
LordHunter, my cedega wont run in any other group than root =P
if i try running with my user i get the error, /.transgaming/wineserver-c83-251-15-161 : Premission denied.

I could just change the user group of wineserver-c83-2... to my user... but i like running in root =)

Edit: Tried changing the winserver user to mine, didnt work...

And thanks jerome, but that didnt work, now it just opens a terminal... but nothink happens.

---

### Post by LordHunter317 on 2005-05-24
[QUOTE=ante0]LordHunter, my cedega wont run in any other group than root =P[/quote]Then you need to fix it.

> I could just change the user group of wineserver-c83-2... to my user... but i like running in root =)It would be better to just delete the file.  You may have to ultimately kill your user's entire transgaming configuration ~/.transgaming and have it reload it.  This may have some negative effects on games installed, though.

However, running wine as root is a dangerous idea.  I wouldn't do it.  I don't recommend you do either; you're performing the virtual equvialent of playing with fire.

---

### Post by ante0 on 2005-06-03
Well, i just wanted the script to work because im lazy. I can cd into the game dir and run the game from there... it would work too. =) Tried changing the usergroup of the wineserver dir, with no success at all. it says that only one usergroup can be assigned to it. :) But i think i'll just go with the hard way from here ;) Thanks Anyway!

---


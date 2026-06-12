---
title: "Shell script launcher help"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by chezzo on 2008-09-22
I've just downloaded the game "Frets on Fire" and it works fine when I go into the folder the game data is saved in and click on the file "FretsonFire", which is a shell script, and then click "Run" at the popup.

However, I want to make a shortcut to it in my menu, but simply giving the location of the script as the path of the shortcut doesn't work. The text of the script reads

> #!/bin/sh
export LD_LIBRARY_PATH=$(dirname $0)
exec ./FretsOnFire.bin $@

Trying to run the script  in the terminal gives the message "exec: 3: ./FretsOnFire.bin: not found". The FretsOnFire.bin file exists in the same folder as the script, but obviously the script is written so that it must be opened manually in this folder. 

Without really knowing what I'm doing, I have tried various edits on the script - replacing "dirname" with the name of the directory, which didn't work, and replacing "./FretsOnFire.bin" with the full file path, which crashed my computer... What am I doing wrong?

---

### Post by chezzo on 2008-09-22
Don't worry, solved it...

I created a script which read

> cd [directory of files]
sh FretsOnFire

then made my shortcut link to that

---


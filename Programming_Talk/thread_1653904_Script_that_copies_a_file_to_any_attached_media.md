---
title: "Script that copies a file to any attached media"
date: 2010-12-27
forum: Programming Talk
---

### Post by hakermania on 2010-12-27
Ok, so, I'm one of the "teacher's boys" (:P) of my computer class, basicly because I'm a biit deep into ubuntu. So, he gave me 26 USB sticks and ordered me to put inside a file (.doc file, wishing Happy New Year etc). So, it is quite annoying to copy-paste the same file 26 times :/
So, I made this script, I thought of putting 4 USBs altogether (4 are the USB ports of my notebook) and wait a bit for the script to copy the file, then disconnect the USB sticks and put other 4 again and again. So, this is the script:
```
#!/bin/sh
while [ 1 ]; do
sleep 2; 
cp /home/alex/HappyNewYear.doc /media/*/
done
```It seems to be a good idea, but it outputs:
```
[COLOR=#c80000][FONT=Monospace]cp: omitting directory `/media/5C3F-12A0/'[/FONT][/COLOR]
```where [COLOR=#c80000][FONT=Monospace]5C3F-12A0 [/FONT][/COLOR]is the name of one USB (i mean this way it doesn't work for even one USB). I cannot understand why I take this error :) Thx in advance for any answers :)

---

### Post by odyniec on 2010-12-27
Only the final argument for the cp command is the destination where the copied file(s) should be placed. When the shell expands this line:
```
cp /home/alex/HappyNewYear.doc /media/*/
```
it becomes: 
```
cp /home/alex/HappyNewYear.doc /media/dir1/ /media/dir2/ /media/dir3/
```
This instructs the shell to copy the doc file and the two directories (in my example, dir1 and dir2) to dir3. Since cp does not copy directories (unless the -r option is used), it tells you that the directory was omitted. So what you end up with is the doc file being copied to just one directory (dir3) under /media.

---

### Post by trent.josephsen on 2010-12-27
There seems to be quite a rash of belief in the magical properties of * going around lately...

What you probably wanted to do was more along the lines of
```
for dest in /media/*; do
    cp /home/alex/HappyNewYear.doc $dest
done
```

This only works as advertised if all the items in /media are directories upon which a filesystem on a USB stick is mounted, but it should give you the idea.

Edit:  It also breaks if any files in /media have spaces in their names...  and probably a few other corner cases.  Untested, use at your own risk, etc.

---

### Post by hakermania on 2010-12-27
Ok, found it, for anybody following:
use for-in loop :)

---

### Post by hakermania on 2010-12-27
Hahaha this was really funny!
Sorry guys, i haven't seen your answers :) Thx

---

### Post by hakermania on 2010-12-27
@[trent.josephsen]("http://ubuntuforums.org/member.php?u=763491")
*_  It also breaks if any files in /media have spaces in their names._* 
It doesn't if you use "$dest" :)

---


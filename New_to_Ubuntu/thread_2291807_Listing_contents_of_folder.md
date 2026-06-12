---
title: "Listing contents of folder"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by ramsforums on 2015-08-22
I have a folder. I think it may contains millions of sub folders and files. Not sure what the folder contains. It was created by BleachBit application while WIPE.
The folder name is **[COLOR=#FF0000]T6o1L9lGg- [/COLOR]**

I ran the following command from the home directory

> 
rama@develop ~ $ ls -lh
total 1017M
drwxr-xr-x  2 rama rama  4.0K Aug 23 11:02 apps
drwxr-xr-x 21 rama rama  4.0K May  7 06:31 Copy
drwxr-xr-x  2 rama rama  4.0K Nov  7  2014 Desktop
drwxr-xr-x  2 rama rama  4.0K Nov  7  2014 Documents
drwxr-xr-x  4 rama rama  4.0K Dec 27  2014 Downloads
drwxr-xr-x  2 rama rama  4.0K Aug 23 08:08 empty
drwxr-xr-x  2 rama rama  4.0K Nov  7  2014 Music
-rw-r--r--  1 rama rama   382 Aug 23 09:41 mydel.c
drwxr-xr-x  6 rama rama  4.0K Nov  8  2014 ocd
drwxr-xr-x  2 rama rama  4.0K May  7 06:30 Pictures
drwxr-xr-x  2 rama rama  4.0K Nov  7  2014 Public
**[COLOR=#ff0000]drwxr-xr-x  2 rama rama 1017M Aug 23 08:08 T6o1L9lGg-[/COLOR]**
drwxr-xr-x  2 rama rama  4.0K Nov  7  2014 Templates
drwxr-xr-x  3 rama rama  252K Aug 23 11:41 testdir
drwxr-xr-x  2 rama rama  4.0K Nov  7  2014 Videos
drwxr-xr-x 19 root root  4.0K Nov  8  2014 xCopy




If I execute the following command

> cd ./T6o1L9lGg-/
ls -lh

The command runs for ever without any console output. How do I find the content of [B][COLOR=#FF0000]T6o1L9lGg-

[/COLOR][/B][COLOR=#000000]Thanks
[/COLOR][B][COLOR=#FF0000]

[/COLOR][/B][COLOR=#FF0000][/COLOR][COLOR=#000000][/COLOR]

---

### Post by austin42 on 2015-08-23
The easiest thing to do would probably be to send the output to a text file like so. ```
ls -lh [COLOR=#000000]*T6o1L9lGg-*[/COLOR][COLOR=#000000]* > *&#8203;list.txt[/COLOR]
``` but the long listing ( -l flag) will still cause it to take a while to go through everything since it looks to be about a gigabyte of data. If you just need to see the file and folder names I would suggest running something like this ```
ls -R [COLOR=#000000]*T6o1L9lGg-*[/COLOR][COLOR=#000000]* > *list.txt[/COLOR]
``` and that should complete much faster than and ls with the -l flag.

---

### Post by Doug S on 2015-08-23
It is a longshot, but I wonder if your file location database updated successfully. I can not recall, but I think it runs daily. Anyway, if it did you could list the contents via:```
locate T6o1L9lGg-
```and either redirect that to a file or to some other filter, such as "more". You can also force database update with```
sudo updatedb
```but obviously it is going to take a long time to complete.

Edit:

You could also try not sorting (-f) for the "ls" command. I created a million files on my computer and without sorting "ls" took 8 seconds, while with sorting it took 17 seconds.
"sudo updatedb" took 1.8 seconds.
For reference the directory file size was 45608960 bytes (or approx 1/22 the size or yours), with file names = 22 characters.
deleting the directory took 3 minutes. (the "rm -r dir_name" method)
deleting the files via "sudo find . -type f -print -delete" (as mentioned on the other thread) took 28 minutes.

Edit 2: I forgot to flush memory before measuring some of the above times, so the system had much information cached. New numbers, where they changed:
"sudo updatedb" 1 minute 50 seconds.
"ls -f" 47 seconds
"ls" 1 minute 20 seconds.

---

### Post by mc4man on 2015-08-23
I'd just delete the file & forget about it. It's not unlike bleachbit to create some nonsense or worse.

---

### Post by Doug S on 2015-08-24
> **mc4man said:**
> I'd just delete the file & forget about it. It's not unlike bleachbit to create some nonsense or worse.The OP has been trying, see [this]("http://ubuntuforums.org/showthread.php?t=2291800") thread.

---

### Post by vasa1 on 2015-08-24
[http://askubuntu.com/questions/427647/strange-folder-in-my-home-folder-after-a-failed-run-of-bleachbit](http://askubuntu.com/questions/427647/strange-folder-in-my-home-folder-after-a-failed-run-of-bleachbit)
[https://bbs.archlinux.org/viewtopic.php?id=169317](https://bbs.archlinux.org/viewtopic.php?id=169317)
[http://ubuntuforums.org/showthread.php?t=1804566](http://ubuntuforums.org/showthread.php?t=1804566)

And more by googling for "bleachbit creates large folder"

---


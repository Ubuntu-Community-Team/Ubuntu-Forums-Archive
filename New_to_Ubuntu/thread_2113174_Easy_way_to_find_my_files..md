---
title: "Easy way to find my files."
date: 2013-02-06
forum: New to Ubuntu
---

### Post by Hoaxaca on 2013-02-06
My family kind of ruined windows on my computer and to safe my computer i had to boot it with ubunto. Windows war ruined and almost all the photos of my kids and my work documents were gone. I managed to recover them with recoll, but this gave me thousends of folders with a lot of files i don't need. Is there a way to organize those files? because checking them one by one will take weeks.

---

### Post by RealmEleven on 2013-02-06
Short answer: no. Not unless someone has written a file-system recovery tool for Linux...?
.
If Windows has encrypted the file system, then I'll bet you an espresso that it's gone - forever; unless you can recover the Windows operating system and change the setting which encrypts the file system. Sometimes this is a matter of going into the F8 or F5 screen on boot (I forget which) and initiating a roll-back. Do this, if you can, one roll-back at a time, until you can get Windows to boot - and then change your settings or back up your files and make sure another computer can read your backup drive when you plug it in. Otherwise...
.
I vaguely recall once using a search function in Ubuntu's file manager - when I misplaced a file. As a chronic point-and-click user, I instinctively jab my fingers at CTRL-F whenever I imagine the remote possibility that I might have misplaced something :) . If you were to do a search for files with the right extensions (e.g. *.jpg, *.svg, *.png, *.doc, *.docx, *.odt, etc...), assuming you're not down to *.chk file system fragments, you might be able to isolate groups of your files from your system's files.
.
There is nothing easy or quick about this hence the (short answer)=(no) comment. That's, possibly, why some of us engage in the seemingly paranoid/obsessive-compulsive behaviour of making regular i.e. (daily/weekly/monthly/quarterly) multiple backups - with at least one backup schedule assigned to a separate hard disc, one backup schedule assigned to a DVD and one to a thumb-drive. It saves so much grief when a hard disk turns out to be a dud and seizes - or when junior deletes the main partition "file" to make extra space - never mind the file system horrors which ensue when the defragmenter confuses a dicky data connection with bad sector reads and then tries to fix it by flagging 85% of the disk as bad sectors.
.
 However, if there is some super file-system recovery tool on Linux, I'd love to hear about it too...

---

### Post by elgordodude on 2013-02-06
foremost works rather well for recovering filesystems. But that's assuming you still have the original filesystem, and it hasn't become additionally corrupted since recovery began. If all you have are thousands of folders now, than humpty dumpty would be a fair analogy... sorry, but at least it's there in some form, I know people that would envy that problem.

---

### Post by 3rdalbum on 2013-02-06
> **Hoaxaca said:**
> My family kind of ruined windows on my computer and to safe my computer i had to boot it with ubunto. Windows war ruined and almost all the photos of my kids and my work documents were gone. I managed to recover them with recoll, but this gave me thousends of folders with a lot of files i don't need. Is there a way to organize those files? because checking them one by one will take weeks.

I don't know if there is anything that already exists to categorize files. However with a bit of Bash scripting you could roll your own. Linux has a command called "file" that identifies the filetype of a file you specify. You could write a script to check that and move each file to a folder depending on what sort of file it is.

Sorry I can't help more, but that's how I would do it if there isn't already a program that can do it.

---


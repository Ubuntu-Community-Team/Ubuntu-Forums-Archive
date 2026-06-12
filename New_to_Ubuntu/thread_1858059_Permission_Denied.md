---
title: "Permission Denied"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by Dallan Taco on 2011-10-11
I had a openSUSE OS crash on me.  I tried to use the ubuntu live CD to get my files off that hard drive and onto an external backup drive.  I was told that i don't have permission to move, copy or do anything to those files. I plan on installing ubuntu once i get all my files off that drive.  Any help, please?

---

### Post by wolfen69 on 2011-10-11
The Puppy Linux Live CD should work fine for that.

---

### Post by zhogan85 on 2011-10-11
Or perhaps try 

```
sudo chmod 777 -R /path/to/directory
```

The -R makes it recursive, changing the read/write/executable of all sub-directories/files.

Then you should be able to copy your files.

---

### Post by ajgreeny on 2011-10-11
Just open the file manager as root with ```
gksudo nautilus
``` in the ubuntu live CD and you will be able to move the files where you want.

I would suggest you keep the file permissions as they are and not change them to 777 as suggested by zhogan85.

---

### Post by Dallan Taco on 2011-10-11
[QUOTE=ajgreeny;11331661]```
gksudo nautilus
``` What exactly does this do?  I would like to learn the power behind the command.

---

### Post by smurphy_it on 2011-10-11
nautilus is your "file Manager", and the gksudo command is used to launch nautilus as root.  Typically in a graphical environment you use gksudo, and if you aren't running a graphical environment you use sudo instead.

Clear as mud ?

---

### Post by smurphy_it on 2011-10-11
PS.  Anytime you don't know what a command does, you can check to see what it is in the man page(s).

example:

```
man gksudo
man nautilus
```

---

### Post by Dallan Taco on 2011-10-11
OK. Now my next question is: How can I use command promt to move the directories from the hard drive to external drive? I am a complete newbie to using command lines.  I have spent my life until now using windows.

---

### Post by Little Blue on 2011-10-11
I think the move command [FONT="Courier New"]mv[/FONT] should work fine for moving files and directories. In the case described above I guess it would be something along the lines of 

```
sudo mv /path/to/what/you/want/to/move /path/to/destination
```

The destination will be [FONT="Courier New"]/media/SOME_LABEL/where_you_want_to_stick it[/FONT]

If you're using the live disk the I'm going to guess (I haven't used a livedisk for a while so I may be wrong here) the stuff you want to move will also be stashed in one of the mounted areas within [FONT="Courier New"]/media[/FONT]

If you're that new, you might want to look up some other basics, such as [FONT="Courier New"]cd[/FONT] and [FONT="Courier New"]ls[/FONT] (change directory, list directory contents) for navigating within the commandline and finding out what's where and [FONT="Courier New"]cp[/FONT], [FONT="Courier New"]mkdir[/FONT] and [FONT="Courier New"]rm[/FONT] (copy, make a directory and delete a file [there is no recycle bin for the rm command, so be sure you want to rm a file before using it]) which are useful for file manipulation.

Hope that's all correct and helps!

---

### Post by noodles19 on 2011-10-28
Thank you, this thread helped me move what I thought to be lost data when my 11.04 crashed \\:D/

---


---
title: "Help writing and running a script"
date: 2008-11-02
forum: Programming Talk
---

### Post by b3n0 on 2008-11-02
Hey all,
I use GRip to rip all my MP3's using lame. However I that by default spaces are replaced with underscores. Theres one folder with about 15 sub folders and a heap of MP3's. Is there anyway to change all underscores to spaces in my music folder all in one hit?
Thanks,

---

### Post by ad_267 on 2008-11-02
Try this:

```
find Music -name "*_*" -exec rename "s/_/ /g" "{}" \;
```

---

### Post by b3n0 on 2008-11-02
Neat,
So I just put that into a new file and save as a .desktop file? Then how do I run it?
Also will this change the names of the folders which have also been named this way.
Thanks for the fast reply.

---

### Post by ad_267 on 2008-11-03
You can just go to Applications - Accessories - Terminal and run it. Yes it will work for directories. If you only want to change files you can do this:

find Music -name "*_*" -type f -exec rename "s/_/ /g" "{}" \;

In the terminal you can run "man find" to read about all the options for the find command, there are a lot of them.

There can be problems running this and renaming directories, because the directory will be renamed and find will no longer be able to search inside that directory, so you might have to run it twice to make sure it gets everything.

If you want to save this as a script that you can run from a launcher then you save this as a file:
```
#!/bin/bash
find Music -name "*_*" -exec rename "s/_/ /g" "{}" \;
find Music -name "*_*" -exec rename "s/_/ /g" "{}" \;
```

You could save this in a hidden directory like .scripts for example. Then you can create a new launcher and set the command to be "/home/YOUR_USERNAME/.scripts/SCRIPT_NAME". You will have to make the file executable by right clicking on it and selecting properties and changing its permissions.

---

### Post by b3n0 on 2008-11-03
Do I need to specify the directory? I don’t want to change any system files.

---

### Post by ad_267 on 2008-11-03
Yes the directory is specified. It is the "Music" part of the line. You could change that to be "/home/your_username/Music" so that you don't have to be in your home directory to run it.

---

### Post by b3n0 on 2008-11-03
Thanks I be home in 2 hours, Ill give it a shot then.

---

### Post by ad_267 on 2008-11-03
You might want to test what files it will rename to make sure you don't rename anything important. This will just output the names of the files it will rename so that you can scroll through them and then use "q" to quit.

```
find Music -name "*_*" -exec echo "{}" \; | less

```

---

### Post by b3n0 on 2008-11-03
THANK YOU!!! That worked perfectly. I ended up just using the folling command in the terminal.
```
find \home\concorde\ogg -name "*_*" -exec rename "s/_/ /g" "{}" \;
```
Thanks again.
:D

---

### Post by b3n0 on 2008-12-21
Hey guys, sorry to haul this one out from the dead. I have a new problem now and I thought it matched this thread I started a while back.
I'm looking to change the tag of some media files on my desktop. 

They are in folders and sub folders like so.
*Nathan's Healing
>27Nov
5 .mod files and 3 .mpg files
>28Nov
8 .mod files and 5 .mpg files
>29Nov
8 .mod files

The .mod files work in Cinelerra providing the tag is renamed to .mpg. As I'm going to be constantly adding .mod files to the archive from my camera, I was wondering if there was a shortcut to bulk edit them. Maybe a command in terminal or a script.
Thanks for you help

---


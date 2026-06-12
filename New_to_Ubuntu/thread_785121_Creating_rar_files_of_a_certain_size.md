---
title: "Creating rar files of a certain size"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by echris1 on 2008-05-07
When you right click on a file you want to archive and click on Create Archive, you can select rar, but is there any way to get more specific?  I'd like to get a rar thats 100MB and uses only minimal compression, because there it's only video, and thats compressed enough anyway.  I know the command line to do this is:

```

rar a -v100000 filname.rar filename.avi

```

or at least thats how to divide it up, I'm not sure how to specify compression.

Is there a way to make a script or something that I can put in the menu next to create archive?   Or at least a way to have those options in the gui?

Thanks,
echris1

---

### Post by Xiong Chiamiov on 2008-05-07
For Dolphin and Konqueror, I know you can create service menus, but I know nothing about GNOME.  That said, why again do you not want to compress it fully?  I don't think it's quite possible to do what you're asking except possibly by having a script that compresses using several different levels and finds the one closest using a binary search or something, but that's completely inefficient for whatever it is you're trying to do.

---

### Post by echris1 on 2008-05-07
It's not that I don't want to compress it fully, I just want to store it, break it up into 100MB sized rar files. The compression doesn't matter at all.  I guess I'm really just wondering how to add things to the right click menu.

---

### Post by vanadium on 2008-05-07
You might need a proprietary version of rar to create multi-volume archives of a preset size. Even then, no version for Linux might be available.

I would stick with free software. Because video is highly compressed, I would not attempt to compress furhter (will hardly work) but directly split the file in 100 Mb chunks using the "split" tool, which is by default present on your system. See "man split" for how it works.

---

### Post by subzero316 on 2008-05-07
```
rar a -v10000k archive.rar <files>
```

thats about 100 mb files

---

### Post by echris1 on 2008-05-07
Thanks subzero, I left out the k, but I was wondering if it's possible to add that command to the right click menu, so if I were to right click on a video file or something, I would see an option to compress into 100MB chunks.  Is there a way to put something in that menu to launch a console and execute that command?

---

### Post by Monicker on 2008-05-07
> **echris1 said:**
> Thanks subzero, I left out the k, but I was wondering if it's possible to add that command to the right click menu, so if I were to right click on a video file or something, I would see an option to compress into 100MB chunks.  Is there a way to put something in that menu to launch a console and execute that command?

Install the nautilus-actions package.  After it is installed:

System -> Preferences -> Nautilus Actions Configuration -> Add

Label - SplitRarFile
Tooltip - Create split rar archive from file
Icon - just pick one you like

Take the following and save it in your home dir as splitrar.sh

```
#!/bin/bash

for file in "$*"
do

rar a -v10000k archive.rar $file

done
```

Right click saved file -> Properties -> Permissions -> Allow Executing File as program

Use path to file in Nautilus configuration

Path - /home/username/splitrar.sh
Parameter - %m

Save the action.  ALT + F2, killall nautilus. After that when you right click on a file you should have a menu item called SplitRarFile.  Selecting that action will now run the script and create the split rar files in the directory.

---

### Post by echris1 on 2008-05-07
I have it all setup, and the menu item shows up, but when I select it nothing happens.  No extra processes start running and no terminals pop up.  Is there something I'm missing somewhere?

---

### Post by Monicker on 2008-05-07
Did you make sure the splitrar.sh file is executable?  You might go over all the settings again.  It worked fine when I tested it on my computer.

---

### Post by echris1 on 2008-05-07
It is set to be executable, still nothing happening.  The nautilus action setup looks like this:

[IMG]http://content.imagesocket.com/images/splitrarfilecba.jpg[/IMG]

and the splitrar.sh looks like this:

```

#!/bin/bash

for file in "$*"
do

rar a -v10000k archive.rar $file

done

```

I was wondering if it is also possible to change archive.rar to $file.rar?

---

### Post by Monicker on 2008-05-07
You can change it to $file.rar if you like.


I just tested on my system again, and I think I found the problem.  I bet the file you were trying to rar had spaces or other characters in it.  I tend to forget about that.  :P

Use this for the script:

```
#!/bin/bash

for file in "$*"
do

rar a -v10000k "$file.rar" "$file"

done
```

---

### Post by glennric on 2008-05-07
Change the script to be

```
#!/bin/bash

IFS="
"

for file in "$*"
do

rar a -v10000k "$file.rar" "$file"

done
```
and then the spaces in file names won't be a problem anymore.

---

### Post by echris1 on 2008-05-07
Tried both of those scripts, still nothing happening when I try to do it.  Does it matter at all if it's on an NTFS drive?  I mean, the regular command works fine when I just type it in.  Do I need to set permissions or something other than the run as executable?

---

### Post by Monicker on 2008-05-07
I wouldn't think ntfs would matter,especially if you can do it manually, but I suppose its possible.  I don't have any ntfs partitions to test that out though.

---

### Post by kakao on 2008-08-10
> **glennric said:**
> Change the script to be

```
#!/bin/bash

IFS="
"

for file in "$*"
do

rar a -v10000k "$file.rar" "$file"

done
```

Haven't tried it, just thinking about it, but shouldn't it rather be something like

```

#!/bin/bash

IFS="
"
rar a -v10000k "archive.rar" "$*"

```

This way I'd expect to get **one** file containing all selected files/folders rather that one file each for every selection I made in nautilus...

Cheers.

---


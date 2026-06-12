---
title: "formatting external hard drive"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by Flynn87 on 2012-04-09
i want to install games and other software on a my external hard drive using ubuntu because my pc hard drive is too small and i was just wondering what is the best file system to format my external hard drive to.

---

### Post by super mushroom on 2012-04-09
ext4 if your just using ubuntu, else for windows and pc use NTFS. Also if your new like I am, try using the Disk Utility in Ubuntu.

Further info in the 8'th reply of this thread: [URL="http://ubuntuforums.org/showthread.php?p=11831407&posted=1#post11831407"]
http://ubuntuforums.org/showthread.php?p=11831407&posted=1#post11831407[/URL]

---

### Post by Cpierce on 2012-04-09
Fat 32 is compatible with almost all OS's. Just plug it in and when it shows up on your desktop, just right click on the icon and select format.

---

### Post by Cheesemill on 2012-04-09
Formatting the drive is the easy part.

Unfortunately installing programs to anywhere except the main partition where the OS is installed isn't possible.


[COLOR=Gray]
[/COLOR][SIZE=1][COLOR=Gray](Before anyone tells me it is, I do know this but it isn't something a beginner should ever attempt - it usually means compiling software from source which I am not going to recommend)[/COLOR][/SIZE]

---

### Post by lukeiamyourfather on 2012-04-09
The "best" option is subjective. It depends on what you plan to do with the drive. If it will be used only with Linux systems format it as ext4 or another Linux native filesystem (like btrfs). If you do format it as FAT32 for compatibility reasons note that the maximum file size will be 4GB. In this day and age that causes issues for many users. NTFS overcomes the 4GB file size limit but still has many caveats and is not a Linux native filesystem. Long story short by using a non-Linux native filesystem you're trading robustness and features for compatibility with other operating systems.

---

### Post by lukeiamyourfather on 2012-04-09
> **Cheesemill said:**
> Formatting the drive is the easy part.

Unfortunately installing programs to anywhere except the main partition where the OS is installed isn't possible.


[COLOR=Gray]
[/COLOR][SIZE=1][COLOR=Gray](Before anyone tells me it is, I do know this but it isn't something a beginner should ever attempt - it usually means compiling software from source which I am not going to recommend)[/COLOR][/SIZE]

Sure it is. Symbolic links can be used to stuff things anywhere you want, even on remote shares if you so please.

---

### Post by 3Miro on 2012-04-09
Linux programs are not designed the same way as Windows. All Linux programs are sub-divided into components and then programs share those components. The result is that Linux programs use less space in both HDD and RAM, however, the side-effect is that programs cannot be isolated from each other. There is no way to selectively install Linux programs on several partitions (well, you can technically use multiple partitions on different HDDs, but in the end you will need all partitions to be present at all times for the system to work).

However, you can use an external HDD to install Windows programs under wine or any other "stand-alone" software (like MATLAB for Linux).

---

### Post by Cheesemill on 2012-04-09
> **lukeiamyourfather said:**
> Sure it is. Symbolic links can be used to stuff things anywhere you want, even on remote shares if you so please.
Did you read the last part of my post in grey?
Also I would never recommend symlinking important parts of the filesystem to a removable drive, that's just asking for trouble :)

---

### Post by Flynn87 on 2012-04-09
> **Cheesemill said:**
> Formatting the drive is the easy part.
 
Unfortunately installing programs to anywhere except the main partition where the OS is installed isn't possible.
 
 
 
[SIZE=1][COLOR=gray](Before anyone tells me it is, I do know this but it isn't something a beginner should ever attempt - it usually means compiling software from source or symlinking parts of the filesystem which I am not going to recommend)[/COLOR][/SIZE]
 
I think i'll format to ext4 seing though i won't be using any other OS, just Ubuntu. as far as not being able to install programs to anywhere except the main partition i'm determined to find a way to solve that issue even though it is a bit strange seeing though when you install a program, software game etc it gives you option to change the install directory but thats for windows 7  not sure about Ubuntu.

---

### Post by Cheesemill on 2012-04-09
> **Flynn87 said:**
>  as far as not being able to install programs to anywhere except the main partition i'm determined to find a way to solve that issue even though it is a bit strange seeing though when you install a program, software game etc it gives you option to change the install directory but thats for windows 7  not sure about Ubuntu.

When you install software in Windows it asks you where you want to install it, this is possible because the entire program and all of its files are installed in one directory (usually C:\Program Files\<program>).

Using Linux, however, a program isn't installed in just one location. Instead it is spread out over several different locations all over the hard drive depending on the purpose of each of its files. For example the main program binary is stored in /usr/bin, the manual pages are in /usr/share/docs, its menu entry is in /usr/share/applications, global configuration settings are stored in /etc, user configuration settings are stored in /home/$USER as well as other files stored in locations all over the filesystem.

Because of this it is very difficult to tell the system to just install a program to a different location. It can be done but it means either compiling the software from source and passing custom configuration options (which means you have to manually update it and take care of any dependencies), or by symlinking or mounting various system directories to your external drive (which is a sure fire way to break your system unless you know exactly what you're doing).

Again, I would not recommend any of this to someone who needs to ask how to format a disk.

---

### Post by 3Miro on 2012-04-09
> **Flynn87 said:**
> I think i'll format to ext4 seing though i won't be using any other OS, just Ubuntu. as far as not being able to install programs to anywhere except the main partition i'm determined to find a way to solve that issue even though it is a bit strange seeing though when you install a program, software game etc it gives you option to change the install directory but thats for windows 7  not sure about Ubuntu.

You can do that for Windows games under wine. You cannot do that for Linux games. See my earlier post about programs, components and sharing.

If you have no other OS, then I don't see a problem. Linux can live very comfortably on 20GB HDD space (which includes games like like OpenArena and StarControl II with the sound) and unless you have a very old machine, you should have at least that much.

---

### Post by Flynn87 on 2012-04-09
> **Cheesemill said:**
> When you install software in Windows it asks you where you want to install it, this is possible because the entire program and all of its files are installed in one directory (usually C:\Program Files\<program>).
 
Using Linux, however, a program isn't installed in just one location. Instead it is spread out over several different locations all over the hard drive depending on the purpose of each of its files. For example the main program binary is stored in /usr/bin, the manual pages are in /usr/share/docs, its menu entry is in /usr/share/applications, global configuration settings are stored in /etc, user configuration settings are stored in /home/$USER as well as other files stored in locations all over the filesystem.
 
Because of this it is very difficult to tell the system to just install a program to a different location. It can be done but it means either compiling the software from source and passing custom configuration options (which means you have to manually update it and take care of any dependencies), or by symlinking or mounting various system directories to your external drive (which is a sure fire way to break your system unless you know exactly what you're doing).
 
Again, I would not recommend any of this to someone who needs to ask how to format a disk.
 
wow that last sentence geez lol actually i didn't ask how to format a disk, i know how to do that on any operating system, i was just wondering what the best file system was for my external hard drive for installing software or games seeing though thats not possible with my level of skill as you have made clear thanks for your time.

---

### Post by Flynn87 on 2012-04-09
> **3Miro said:**
> You can do that for Windows games under wine. You cannot do that for Linux games. See my earlier post about programs, components and sharing.
 
If you have no other OS, then I don't see a problem. Linux can live very comfortably on 20GB HDD space (which includes games like like OpenArena and StarControl II with the sound) and unless you have a very old machine, you should have at least that much.
 
I have Ubuntu installed on my pc and nothing else the external hard drive is only going to be used to install Windows programs and games with a program like wine, as far as linux games and programs i'll install them on my main drive where Ubuntu is located, to get this straight installing just windows programs and games with wine on my external drive works. :) please say yes lol :P

---

### Post by 3Miro on 2012-04-09
> **Flynn87 said:**
> I have Ubuntu installed on my pc and nothing else the external hard drive is only going to be used to install Windows programs and games with a program like wine, as far as linux games and programs i'll install them on my main drive where Ubuntu is located, to get this straight installing just windows programs and games with wine on my external drive works. :) please say yes lol :P

That's just fine, it will work. I would recommend to use Linux native ext4, then give the HDD a label when you format it. With a label it will always be mounted under /media/whatever_label. Then you have to install the games from the terminal using some commands. Suppose you are installing Starcraft II:

```
WINEPREFIX="/media/whatever_label/StarctaftII" winecfg
```
Make sure the sound is working and the CD-ROM is set under drives.
```
WINEPREFIX="/media/whatever_label/StarctaftII" wine /path/to/CD-ROM/setup.exe
```
Wine should automatically add a start menu shortcut, but if it doesn't do that, then use:
```
WINEPREFIX="/media/whatever_label/StarctaftII" wine /path/to/StarctaftII.exe
```

Note, I have 64-bit Linux and I need to use
```
WINEARCH=win32 WINEPREFIX="/media/whatever_label/StarctaftII" wine whatever_command
```

I like to make my own shortcuts so I can just go to a folder and run the game with one click (not from the main menu). Here is what I use for Starctaft II.
```
#!/bin/bash
cd /media/Const/Wine/StarcraftII/drive_c/Program\ Files/StarCraft\ II/
WINEARCH=win32 WINEPREFIX="/media/Const/Wine/StarcraftII" wine StarCraft\ II.exe

```

In my case, /media/Const is a second internal HDD, but it will work with an external one just fine. The only possible issue is that external HDD's are slower and it may take longer for the game to load. It shouldn't be a problem if you have enough RAM, Linux is pretty good at caching HDD data into the RAM.

(note that wine itself will be installed on the main partition and if you install games with the default settings, they will be installed on /home/your_user_name/.wine, which is again on the main HDD)

---

### Post by Flynn87 on 2012-04-09
3Miro your a legend :D works a treat, thanks.

---

### Post by 3Miro on 2012-04-10
Glad to help. It took me some time to figure out how to do this, but once you have it set, things work great.

---


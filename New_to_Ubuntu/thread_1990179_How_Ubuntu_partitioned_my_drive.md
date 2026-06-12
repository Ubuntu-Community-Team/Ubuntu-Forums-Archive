---
title: "How Ubuntu partitioned my drive"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by PoeticJustice on 2012-05-29
Hello, I am new to Linux/Ubuntu, and I have a question regarding how Ubuntu organized my harddrive... 

So I decided to install Ubuntu alongside windows on my laptop (500 GB HD) and I ended up giving Ubuntu 100 GB, leaving windows with the remaining 400. I assumed that Linux and windows would be completely separate, but it looks like I can access or at least see all my windows files/folders from Ubuntu. However, when I click on the C drive and look at the properties, (in Ubuntu) it only shows the 400 GB. I want to know- what happened to the 100 GB that I gave Ubuntu?? I can't seem to find it anywhere. Also, where are all the Ubuntu files and programs located? When I go to windows It only shows 400 GB as well, but I expected that because the other 100 GB was reformatted.

---

### Post by jerome1232 on 2012-05-29
On Ubuntu what's the output of these commands, they will tell us how your disk is partitioned. To open a terminal press ctrl+alt+t, copy and paste these commands into it (ctrl+v to paste into terminal) then copy the output into a reply, (ctrl+c to copy out of a terminal). Be sure to go into advanced mode and highlight the output, then press the # symbol on your toolbar.

```
df -h
sudo fdisk -l
```

---

### Post by Megaptera on 2012-05-29
Windows can't 'see' Ubuntu (ext4 file type) files but Ubuntu can 'see' Windows (ntfs file type) files.

At boot can you choose between Windows and Ubuntu? Do both work OK?

To get a visual picture of your hard drive in addition to the text version described by jerome1232, install Gparted in Ubuntu and it'll give you a clear view of what's where.

More info & how to ... [http://ubuntuguide.net/install-graphical-partition-editor-gpartedin-ubuntu-linux/](http://ubuntuguide.net/install-graphical-partition-editor-gpartedin-ubuntu-linux/)

---

### Post by anonymous5 on 2012-05-29
> **PoeticJustice said:**
> Hello, I am new to Linux/Ubuntu, and I have a question regarding how Ubuntu organized my harddrive... 

So I decided to install Ubuntu alongside windows on my laptop (500 GB HD) and I ended up giving Ubuntu 100 GB, leaving windows with the remaining 400. I assumed that Linux and windows would be completely separate, but it looks like I can access or at least see all my windows files/folders from Ubuntu. However, when I click on the C drive and look at the properties, (in Ubuntu) it only shows the 400 GB. I want to know- what happened to the 100 GB that I gave Ubuntu?? I can't seem to find it anywhere. Also, where are all the Ubuntu files and programs located? When I go to windows It only shows 400 GB as well, but I expected that because the other 100 GB was reformatted.


You have two partitions in your hdd I guess. Windows can't see partitions other than FAT/NTFS, that's why you only see the 400GB partition.

On the other hand, with Ubuntu you are able to access all available partitions. With Linux there's no such thing as the C drive... only one single rooted filesystem hierarchy. Take a look at (youtube) : watch?v=-UeuoG5sAA4

I suggest you install gparted (sudo apt-get install gparted) which is a partitioning tool to see the partition layout of your hdd. Use it with caution !

---

### Post by deadflowr on 2012-05-29
Ubuntu and Windows run on two completely different filesystems.
ubuntu uses the ext4 filesystem and windows uses the ntfs and or fat32 filesystem. the ext4 filesystem CAN read the ntfs filesystem, but ntfs CANNOT read the ext4 filesystem.
If you are opening a C drive in ubuntu, then you are not in ubuntu, as drive and partitions are labelled differently in linux. In linux ext4 filesystem, the disk drives are labelled /dev/sd(a,b,c,etc,etc) and then numbered according to partitions. So if you have a single drive with three partitions they would be /dev/sda1 /dev/sda2 /dev/sda3. If you have a second drive it would be labelled /dev/sdb and so on.
If you are using ubuntu and would like to see what your disk partitioning looks like. In the top left corner at the top of the launcher is an icon the looks like the ubuntu logo. Click it and open the dash. in the top search bar type in disk utility. Open disk utility and look at the side pane. It will list all the disks and removable media  connected to your system. you should see one that will say sata or pata and a sub section that says whatever type of disk you have(WD, seagate,etc,etc), click on that and the main window will show the contents of your drive.
From there you can see how the disk is set up.

---

### Post by Erden on 2012-05-29
In addition, Disk Utility is a nice tool to see the drives and the partitions. You don't need to install, it comes with Ubuntu.

---

### Post by PoeticJustice on 2012-05-29
Thanks for all the info guys :D 

I think what I was looking for was the "File System" category in the file manager (I take it that I'm looking at all the files in the 100 GB partition when I go here). I'm still a little unclear on where a program you installed would be located.  

-Completely unrelated: what is the fastest way to access the system monitor? I found it in the Dash Home, but is there a hotkey or a button on the desktop for it?

Also, is there an easy way to release a portion of the drive back to the windows/NTFS format if I wanted to?

---

### Post by deadflowr on 2012-05-30
Applications are typically stored in /usr directory. With dependencies and configuration files and shared libraries spread in various other directories.

you can add the system monitor to the launcher, by either dragging it from the dash to the launcher panel(the left side of screen) or simply open system monitor and then right click on the icon that has been placed at the bottom of the launcher and mark it lock to launcher. You can also set keyboard shortcuts. To do that open the system setting(the cog at the top right) click on keyboard, click on shortcuts, go down to custom shortcuts, click on the plus sign at the bottom area, give it a name, and the command for the default ubuntu system monitor is  "/usr/bin/gnome-system-monitor"(without quotes). click ok and set your shortcut(mine is it set at ctrl+atl+HOME) be aware that many keybindings have already been set for other uses, and changing them might hamper something, or other.

For the last question, I can't help. I've never thought of shrinking an ubuntu partition to give space to windows, if I thought my windows install needed more space I just as soon add a new drive or connect an external hard drive.

---

### Post by Erden on 2012-05-30
> **PoeticJustice said:**
> I'm still a little unclear on where a program you installed would be located.

It may sound weird but Linux does not put all the files of a program in a single directory. More info:
[http://www.rayslinks.com/WhereAreProgramFilesinUbuntu.html](http://www.rayslinks.com/WhereAreProgramFilesinUbuntu.html)
[http://superuser.com/questions/142111/ubuntuwhich-folder-in-ubuntu-like-windows-program-filesi-asking-that-because](http://superuser.com/questions/142111/ubuntuwhich-folder-in-ubuntu-like-windows-program-filesi-asking-that-because)

---

### Post by Paqman on 2012-05-30
> **PoeticJustice said:**
> I'm still a little unclear on where a program you installed would be located.  


As others have said, bits of it will be all over the place. The good news is that you don't need to worry about it. You don't need to know the location of any part of a program to be able to launch it. Because they have integrated package managers Linux desktops are smart enough to know how to launch a program without you needing to tell them where the executable is (obviously they can also cleanly install, remove and upgrade the app).

For example, even falling back to the command line the command to launch Firefox is still just:
```
firefox
```
You can also launch applications by hitting Alt-F2 and typing their name, as well as through the dash.

---


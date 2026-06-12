---
title: "partitioning"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by opediamond on 2013-04-06
Good day all, I am a totally new user of ubuntu, new to linux, new to programming in general, so treat my question like i dont know nothing.
 my hard disk have been partioned before i installed ubuntu, now i need help in accessing the content of the second partion of my hard disk..... i mean the partition that contains my files and does not contain the ubuntu OS. 
your quick reply will be highly appreciated.

---

### Post by arpanaut on 2013-04-06
This may be a little advanced but a good read nonetheless.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

When you open your file manager is your data partition not showing? 
Linux can read and write to ntfs so it should appear on the left pane of the file manager.

---

### Post by ibjsb4 on 2013-04-06
A partition with your files in it would be a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9"), are you sure you have one.

A graphical way to see what you have would be to use gparted.  You could even post a screenshot for us to see.  To install gparted, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install gparted
```

Then to start gparted:

```
gksudo gparted
```

---

### Post by Bresser on 2013-04-06
Go to the File Manager, if it doesn't show up, open terminal (Ctrl-Alt-T). Type the following with enter after each box. Since you know you want the second partition, that it sda2.
First Type:
```
sudo -s
``` This will put you into root, that is like administrator privileges on windows.
After that you have to have a directory to find your files:
```
mkdir /mnt/secondpartition
``` This just makes a "folder" for your files/
Now you have to mount that "Folder":
```
 mount -t ntfs /dev/sda2 /mnt/secondpartition -o "umask=022"
``` This makes all the files in your second partition available to see into the folder you made:

To access that folder go to:
/home/(yourname)/mnt/secondpartition and all your files will be there.


Thank you,

Bresser.

---

### Post by 3rdalbum on 2013-04-06
If you installed Ubuntu by booting your computer from the disc, then your other partition will appear near the bottom of the Launcher on the side of the screen.

If you installed via the Windows program, then your Windows partition will appear in /host. Go into your home folder, click "file system" on the side of the window, and double-click "host"

---


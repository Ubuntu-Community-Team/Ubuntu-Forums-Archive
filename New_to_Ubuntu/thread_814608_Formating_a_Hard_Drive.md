---
title: "Formating a Hard Drive"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Dr. Tom on 2008-05-31
My apologies for posting this twice.  I do not know how that happened and I am trying to delete the second post.  Any help to remove this post would be greatly appreciated.

Tom




I am trying ti install Ubuntu 7.10 on my hard drive.

Hard Drive:  160 GB with no partitions.

They setup I use with Windows:

C:\System --> 20 GB for Windows XP Pro and motherboard drivers
D:\Programs --> 20 GB for all programs
E:\Visual Basic --> 40 GB for all Visual Basic activities
F:\Games --> 40 GB for all games
G:\Storage --> 40 GB for all downloads, files, pictures, etc.

I want to do something similar with Ubuntu.  So far I have managed to do very little.  What I have done:

- Loaded Ubuntu into memory(?)
- Opened the Install icon
- Got to the Prepare Partitions page.  I have the following:
-----/dev/sda
      free space                  160041 MB

- Click on free space and set up the following:
-----/dev/sda
      /dev/sda1   ext3                      20003 MB unknown
      /dev/sda5   swap                      20003 MB unknown
      /dev/sda6   ext3                      60019 MB unknown
      /dev/sda7   ext3                      60015 MB unknown

- Now I edit the partitions to add the Mount Points:
-----/dev/sda
      /dev/sda1   ext3      /               20003 MB unknown
      /dev/sda5   swap                      20003 MB unknown
      /dev/sda6   ext3                      60019 MB unknown
      /dev/sda7   ext3                      60015 MB unknown

This is as far as I get because I do not understand the Mount Points.  The choices I have are:
  /
  /boot
  /home
  /tmp
  /usr
  /var
  /srv
  /opt
  /usr/local

sda1 is assigned Primary and Beginning
sda5, sda6, and sda7 are assigned Logical and Beginning

What I am looking for is an explanation of the Mounting Points.
- Can I change names?  For example can I make one /usr/local_1 and another /usr/local_2?
- Which is the partition that gets the Ubuntu system files?  Is it "/"?  Is it "/boot"?  Is it "/home"?

I have two books on Ubuntu.  Both seem to assume that this is common information.  But right now I am very lost.

Thanks for any help you can give me.

Tom

---

### Post by rraj.be on 2008-06-01
Mount points are something under which you can specify the location for your partition shortcut to be placed.

but you cant see thats a shortcut.

You can specify something like /home because it will be much efficient way to mange your partitions than keeping in /boot or /usr etc.

2

you can cant change names as /local~1 or ~2 but you can create new directories with that name and use them to mount.

3

Your system files will be stored under / and boot files under /boot

and /etc will have all your configurations /home will have your personal documents

and so on

hope it helped you.

---

### Post by housam on 2008-06-01
You can read more about partitions [[COLOR="Red"]_here_[/COLOR]]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Partition.html")

---

### Post by louieb on 2008-06-01
Think you will find it easier to use GParted to create your partitions.
It can be found on the live CD under **System>Administration>Partition Editor**.   
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

Then when you install use the the manual partitioning option to set your mount points however you want. By specifying a mount point you are saying I want this part of the file system to be put on that partition.  

The *nix file systems directory structure is quite different from windows.  The file system starts with / and expands tree like from there.  Might want to go through the [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")  

In basic I would keep it simple and not deviate from the standard until you get familiar with the file system structure.  (trying to change the name of one of the standard directories in the hierarchy).  

Good Luck.
 Its

---

### Post by ugm6hr on 2008-06-01
> C:\System --> 20 GB for Windows XP Pro and motherboard drivers
D:\Programs --> 20 GB for all programs
E:\Visual Basic --> 40 GB for all Visual Basic activities
F:\Games --> 40 GB for all games
G:\Storage --> 40 GB for all downloads, files, pictures, etc.

You won't be able to have an identical setup (at least I don't think so).

Unfortunately, the file structures for Linux and XP are just different.  The closest setup I can think of:

System = /
Programs = /usr
Storage = /home

Visual Basic - no idea
Games - don't think they can be installed separately from programs (so that would have to be bigger).

Don't forget that you also have to have a **swap** partition (which Windows doesn't have).

I would actually suggest you just go with a /, /home, and swap partition.

---

### Post by sayakb on 2008-06-01
In Linux, you can create a / partition, a /home and a swap partition as ugm6hr said.
Also, if you want to keep your data organized as you kept in Windows, you can create separate folders in your /home/Documents for Games, Music, Storage etc. You can install Linux games or copy their executables to the Games folder you've made, but make sure that you add it to your PATH variables by executing:
```
PATH=$PATH:/home/Documents/Games
```

Read [here]("http://www.troubleshooters.com/linux/prepostpath.htm") for more information.

---

### Post by k3lt01 on 2008-06-01
Tom, I have 2 PCs, check my signiture for what they are.

to give you an idea of whats what in Windows and Ubuntu.
C:\ in Windows = / in Ubuntu (/ can contain the system and program files no problem)
C:\My Documents in Windows = /home in Ubuntu.

On my systems the laptop I have it setup with 3 partitions. / is 10GB and I have 2 GB of SWAP and the rest is /home. 10 GB is plenty big enough for my laptop for all the system and programs I use on it.

The Desktop also has 3 partitions, / is the small hdd (currently 20GB the 80GB died from a brownout) and it has system and programs, 2GB of SWAP, and /home is 200 GB and is my data.

You can have separate partitions for /usr /var /tmp etc, there are many you can have but on a home or even basic work PC all you need is / and /home with a SWAP. I always go 2GB for SWAP and realistically my laptop wouldn't run very well without that much because it doesn't have much RAM.

---


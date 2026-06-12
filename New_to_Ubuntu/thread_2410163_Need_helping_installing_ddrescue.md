---
title: "Need helping installing ddrescue"
date: 2019-01-11
forum: New to Ubuntu
---

### Post by outdamnspot on 2019-01-11
I'm running Ubuntu 18,04 on a USB in order to try and recover some files from a corrupted hard drive (so far, Ubuntu lets me bypass the permissions necessary for the User folder, which I couldn't assign otherwise). However, everytime I try to transfer the files off the drive onto another external HD, it stalls and I get an input/output error; this only happens with larger files. Anyway, someone on reddit said they had success using ddrescue to make an image of the drive and then rescue files from that. 

I was told, by two separate people, to input "sudo apt install ddrescue" into the terminal but when I did, it said it couldn't locate it. I also tried "sudo add-apt-repository universe" > "sudo apt udate" > "sudo apt install gddrescue" as instructed by someone else, which didn't work.

I'm very technically inept (and also deal with a health issue that makes concentrating on/absorbing new information difficult) so if someone would be willing to tell me in simple step-by-step instructions where I went wrong and exactly what I need to do, I'd really appreciate it. 
[COLOR=#DCDDDE][FONT=Whitney]


[/FONT][/COLOR]

---

### Post by oldos2er on 2019-01-11
There is no package called ddrescue, however there is drescueview and gddrescue. I think gddrescue is the one you want.

---

### Post by outdamnspot on 2019-01-12
> **oldos2er said:**
> There is no package called ddrescue, however there is drescueview and gddrescue. I think gddrescue is the one you want.

I'm confused, so gddrescue is the package but the program is just 'ddrescue'? I tried the gddrescue command line mentioned in my first post and then searched for ddrescue but couldn't find it ..

---

### Post by yetimon_64 on 2019-01-12
> **outdamnspot said:**
> I'm confused, so gddrescue is the package but the program is just 'ddrescue'? ....

Yes, gddrescue is the package you install. ddrescue is the executable the package installs. So you search for gddrescue but run the command ddrescue after installation.

An excerpt from "apt-cache show gddrescue" in terminal here...
>  Please note that this is the GNU ddrescue version providing the ddrescue
 executable. The package is named gddrescue because the ddrescue version of
 Kurt Garloff used to have the ddrescue package name already.

This excerpt explains why the package is named "gddrescue" but the executable is called "ddrescue".

You can check for yourself in terminal, if you wish, by running the command I noted above...
```
apt-cache show gddrescue
```

Regards, yeti.

---

### Post by sudodus on 2019-01-12
The package 'gddrescue' is in the repository 'universe', which is already active in installed Ubuntu systems. But in a persistent live system, run

```

sudo add-apt-repository universe

```

Use the following command lines to get 'ddrescue' and learn how to use it,

```

sudo apt update
sudo apt install gddrescue

info ddrescue  # to learn about ddrescue

```

---

### Post by outdamnspot on 2019-01-12
> **sudodus said:**
> The package 'gddrescue' is in the repository 'universe', which is already active in installed Ubuntu systems. But in a persistent live system, run

```

sudo add-apt-repository universe

```

Use the following command lines to get 'ddrescue' and learn how to use it,

```

sudo apt update
sudo apt install gddrescue

info ddrescue  # to learn about ddrescue

```

Ok, so just to double-check, after I've run "sudo apt install gddrescue", I don't then have to run "sud apt install ddrescue"? I don't know how to quote/tag multiple people but @yetimon_64 said "[COLOR=#000000]run the command ddrescue after installation", so I wasn't sure what that meant exactly. Once I've run the gddrescue command, should ddrescue be installed?[/COLOR]

---

### Post by yancek on 2019-01-12
In your original post, you indicate that you did install gddrescue so just try typing ddrescue in a terminal and hit the enter key.  You stated that insalling it didn't work'.  What exactly does that mean?

---

### Post by outdamnspot on 2019-01-13
> **yancek said:**
> In your original post, you indicate that you did install gddrescue so just try typing ddrescue in a terminal and hit the enter key.  You stated that insalling it didn't work'.  What exactly does that mean?

Well I'm confused because the package is called gddrescue, and then the program is ddrescue. So I wasn't sure if that means I need to run the command lines to install gddrescue (i.e. [COLOR=#000000][FONT=&quot]sudo apt install gddrescue) and then run the command line to install ddrescue after that; or should the gddrescue command line give me ddrescue (if that makes sense)? Because when I searched the computer for ddrescue after the gddrescue commands, I couldn't find it; then I ran "[/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo apt install ddrescue" in the terminal and it said it couldn't locate it or something.[/FONT][/COLOR]

---

### Post by sudodus on 2019-01-13
> **outdamnspot said:**
> Ok, so just to double-check, after I've run "sudo apt install gddrescue", I don't then have to run "sud apt install ddrescue"? I don't know how to quote/tag multiple people but @yetimon_64 said "[COLOR=#000000]run the command ddrescue after installation", so I wasn't sure what that meant exactly. Once I've run the gddrescue command, should ddrescue be installed?[/COLOR]

Yes, once you've run the gddrescue command, ddrescue should be installed :-)

And you can run it according to the tutorial and examples, that you find in the **info manual** 

```
info ddrescue
```

You need to use the actual device letters, in Ubuntu usually

/dev/sda or /dev/sdb or /dev/sdc ... for drives

/dev/sda1 or /dev/sdb1 or /dev/sdc1 ... for partition #1 on each drive
/dev/sda2 or /dev/sdb2 or /dev/sdc2 ... for partition #2 on each drive
...

and you can identify the device letters and partition numbers with the following commands (use the commands that you like best)

```

sudo blkid
sudo fdisk -lu
sudo lsblk -f
sudo lsblk -m
sudo parted -ls

```

You should also use a log file alias mapfile, when running ddrescue. These things are described in a detailed way in the **info manual**. Often it is a good idea to clone from the problematic drive to a new drive with at least the same size according to example 1 in 'A small tutorial with examples'

```

Example 1: Fully automatic rescue of a whole disc with two ext2
partitions in /dev/sda to /dev/sdb.
Note: you don't need to partition /dev/sdb beforehand, but if the
partition table on /dev/sda is damaged, you'll need to recreate it
somehow on /dev/sdb.

     ddrescue -f -r3 /dev/sda /dev/sdb mapfile
     fdisk /dev/sdb
     e2fsck -v -f /dev/sdb1
     e2fsck -v -f /dev/sdb2

```

I would add that

- you should **boot from a third drive** (neither the source nor target of ddrescue)

- if there is a GUID partition table (GPT), and the target drive is not exactly the same size as the source, you must repair the backup partition table at the tail end of the drive. You can do it with **gdisk**, or  automatically with [gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix)

- **no** partitions on the source (and target drive if any) should be mounted

---


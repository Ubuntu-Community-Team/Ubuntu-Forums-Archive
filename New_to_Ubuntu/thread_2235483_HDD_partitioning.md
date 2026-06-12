---
title: "HDD partitioning?"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by Yezinki on 2014-07-21
Hi,

I plan a clean install of Ubuntu 14.04 LTS on my system with a 320 GB HDD, 2 GB of physical RAM.

My question is how do I partition it, size wise and how many partitions recall /root...........???

Thanks.

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-07-21
If I were you then I would have done something like:

Root Partition :  Partition where ubuntu will be installed with ext4 partiton type : 100GB.
Swap Partition : Partiton for swap usage : 4GB.
Other Partition : Partition for storing other data eg back-up, huge softwares, workspace back-up etc.

---

### Post by stalkingwolf on 2014-07-21
there are probably as many answers to this question as there are members on the forum.
I would partition it like this.  
sda1 2 gb swap
sda2 40 gb /
sda3 100gb home
balance stroage. a place to keep important things incase of the need to reinstall.

---

### Post by oldfred on 2014-07-21
Is this just Ubuntu? Or dual boot?

My first suggestion is /, /home and swap.
My somewhat more advanced suggestion is /, /mnt/data, swap. But you cannot create the data partition during install.
You do have to use Something Else to either create partitions or choose mount points for partitions already created. All auto install options just create / (root) and swap.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

You may not not full Ubuntu. My laptop has similar specs but 1.5GB of RAM. I find Unity so slow as to be unusable. But I do install full Ubuntu and then change to gnome-panel, or fallback/flashback which is similar to the old gnome2 top & bottom panels with menus. Other suggestions are Lubuntu or Xubuntu.

---

### Post by Yezinki on 2014-07-21
Single not dual boot.

---

### Post by oldfred on 2014-07-21
> there are probably as many answers to this question as there are members on the forum.

Should be at least more than that. As we may all suggest two or three correct options. :)

---

### Post by buzzingrobot on 2014-07-21
All you really need is a '/' partition and a swap partition.

Note that the name of the partion is '/', not '/root'.

Some folks worry and fret about swap partitions.  I don't.  They are used when a system runs out of RAM it can allocate to a program that asks the OS for more RAM. You don't have much RAM, so create a swap partition of 2-4 gigs.

A number of standard directories are created and used in Linux.  Any of them can, in effect, be mapped to one partition that has the same name. So, you might create a 'home' partition during the install, and the /home directory will be created on it.

The advantage of creating a separate 'home' partition is this: if you ever change to a new Linux distribution, you can leave the existing home partition in place, preserving the files on it.

---

### Post by david253 on 2014-07-21
Lots of helpful ideas and thoughts, thanks. Partitioning is scary for a newbie

---

### Post by buzzingrobot on 2014-07-21
> **david253 said:**
>  Partitioning is scary for a newbie

If you don't have any specific reasons to manually create and use a particular partitioning scheme, I really recommend you just select the installer's option to use the entire disk and let it take care of everything.

---

### Post by david253 on 2014-07-21
> **buzzingrobot said:**
> If you don't have any specific reasons to manually create and use a particular partitioning scheme, I really recommend you just select the installer's option to use the entire disk and let it take care of everything.

Yes good point, as I havent got the confidence yet to make sure it goes well! There seems to be so much more to "fiddle with" or "fubar" with linux than windows :)

---

### Post by oldfred on 2014-07-21
Then auto install is a good option, but do not use auto install if reinstalling. Hopefully by then you understand partitioning a bit more.

If installing Windows from scratch you also can do its defaults but then may also have issues or want something other than standard install. Its just that most have systems with Windows pre-installed.

---

### Post by oldrocker99 on 2014-07-21
During installation, you can select "Something Else" at the formatting option, and set up a / partition of 32GB (my laptop has that size, and I have installed a lot of programs, and it's 48% full), and a /home partition of almost the rest of the disk, and a /swap of roughly twice your RAM. This way, when you upgrade to a different version or a different distro entirely, you can install the system to /, formatting that partition, and mount the second partition as /home without formatting it, and you'll still have all your downloads, music, and most importantly, your settings. I have a desktop with a second drive devoted to /home.

---


---
title: "Disk Usage Analyzer?"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2016-02-29
I just re-installed to a 8GB flash drive AGAIN and got this message right at the start...

Low Disk Space
This computer has only 152.7 MB disk space remaining.
You can free up disk space by removing unused programs or files or by moving files to an external disk.

Of course it gives the option to ignore or examine which opens up the disk usage analyzer.

I received this message before I performed any updates or anything. I haven't even installed anything or created any new files.

Previous installs I tried freeing up some disk space by removing some programs and in doing so my Gnome Terminal and Software Center and other crucially needed software were no longer available.

It seems the problem I am having is that I need to learn how to recognize software dependencies using disk usage analyzer.

Does anyone know of a good tutorial for Disk Usage Analyzer?

---

### Post by v3.xx on 2016-02-29
> Does anyone know of a good tutorial for Disk Usage Analyzer? 

Nope, I don't use it :)

What will this show?

```
df -h
```

Did you empty the  ".Trash" in your flash drive?  Its a hidden file.

---

### Post by jim_deadlock on 2016-02-29
Disk Usage Analyzer has nothing to do with software dependencies, it just shows how much disk space directories/files are using - it won't be much help to you in deciding which packages are taking up space. I think most of the main Ubuntu flavours will be a tight fit on 8Gb but what I would suggest is to install Ubuntu Minimal, then install a desktop immediately (sudo apt-get install lightdm ubuntu-desktop), then you can add any other packages you want.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by grahammechanical on 2016-02-29
Did you install Ubuntu to that USB stick with persistence? How much space was set aside for the persistence file. Whatever amount it was it will reduce the amount of space left over for the OS. I think that the minimum space for a Ubuntu install is between 6 & 7 GB.

When you delete stuff remember to empty the rubbish bin to free up space.

Regards

---

### Post by wyattwhiteeagle on 2016-02-29
> **v3.xx said:**
> Nope, I don't use it :)

What will this show?

```
df -h
```

Did you empty the  ".Trash" in your flash drive?  Its a hidden file.

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       3.7G  3.5G   34M 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           363M  1.2M  362M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   80K  1.8G   1% /run/shm
none            100M   80K  100M   1% /run/user

The trash...thank you for that idea...what about all the cache and temps folders? 

But I been reading on these forums that Ubuntu does its own maintenance and upkeep...is that only a common myth?

---

### Post by sudodus on 2016-02-29
There are a few commands that you can use to remove packages (after their software is unpacked and installed).

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

But with an installed system a 4 GB pendrive is way too small except for testing. It will be full very soon. As grahammechanical said, you need more, I would say at the very least 8 GB even for an installed system of Lubuntu. I would suggest a fast 16 GB pendrive.

A persistent live drive uses the drive space more efficiently, because a large part of it is compressed (a squashfs (compressed file system)). But it needs more RAM than an installed system for the same reason. See these links and try different alternatives:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)
[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

---

### Post by Geoffrey_Arndt on 2016-02-29
Recently installed Ubuntu Wily to a v3 32 giB usb-flash-stick.   (Not Live OS . . . ).   Almost as fast as a hdd install .   

Using ext2 filesysem.  Works great, . . . . too bad UEFI standards not enforced, else this would be one heck of a way to intro Linux to the uninformed masses.

---

### Post by DuckHook on 2016-02-29
> **Geoffrey_Arndt said:**
> Recently installed Ubuntu Wily to a v3 32 giB usb-flash-stick.   (Not Live OS . . . ).   Almost as fast as a hdd install .   

Using ext2 filesysem.  Works great, . . . . too bad UEFI standards not enforced, else this would be one heck of a way to intro Linux to the uninformed masses.Geoffrey,

The problem with pure USB flash stick installs has always been that flash stick memory has a very limited number of write cycles before the memory dies and becomes unwritable. I believe that each memory circuit takes 10K or so writes (I could be wrong&#8213;my memory is no more reliable than a flash stick these days), which is easily used up when things like swap, logging, tmp files, time stamping, journaling, etc are active. This is why the convention is still to go the LiveUSB with persistent partition route. Ubuntu is designed to treat any LiveUSB as a read-only medium, so all dynamic processes go into system RAM. But at the same time, the persistent data partition is spared excessive writes because, except for stuff like databases, most other data tend to be pretty static.

Ext2 will get rid of journaling, but the other dynamic processes are still hitting the stick pretty hard. You can get rid of time stamping with "noatime" on fstab, and just don't define a swap file. Tmp files can be shoved into ram with tmpfs. This leaves logging, which I choose to leave alone because the info is worth a shortened life for the USB stick.

I've heard that modern USB sticks have more write cycles and and are very good at dynamically allocating writes over the entire stick to even out wear. But I have burned out sticks before with full dynamic installs, so I use the LiveUSB with persistence method now.

---

### Post by v3.xx on 2016-02-29
I also think you need more storage space.  Your /dev/sda1 is at 3.7G.  I have one fairly vanilla install that already shows 4.4G/55% and is on a 12G partition.

---

### Post by Geoffrey_Arndt on 2016-02-29
Hello Duckhook . . 

Thanks for your input . . . I was aware of the life cycle issue of usb flash memory in general, but I've also read the newer designs are less prone to failures.    In my use case, the usb stick doesn't replace the hdd/sdd install, but seems to do a better job of demo'ing Linux operation (user security and updates via standard repos).    So, a max of 5 to 10 sessions per month (been doing for 3-4 months so far).

I wonder what the Intel "Computer on a Stick" uses . . . maybe a mini-ssd for the system directories/files?    But, I do think the life cycle thing may be a bigger issue than I at first thought.    I'll have to look at the types of ssd's available (so, that would be a more traditional & better setup).    Lastly, I've never been too comfortable with Live OS security (no login pw's, running as root, etc.).

Back to the OP's issue, I think v3.xx is right-on regarding needing more storage . . . 8 giB just too small _(but plenty big enough for tinycore linux!)_:   [http://distrowatch.com/images/slinks/tinycore.png](http://distrowatch.com/images/slinks/tinycore.png)

---

### Post by vasa1 on 2016-02-29
> **wyattwhiteeagle said:**
> ...
But I been reading **on these forums** that Ubuntu does its own maintenance and upkeep...is that only a common myth?
That is worrisome.

Please post the links to where what you've read has been stated. It has the potential to mislead people depending on what meaning is given to "maintenance and upkeep".

---

### Post by DuckHook on 2016-03-01
> **Geoffrey_Arndt said:**
> . . . I was aware of the life cycle issue of usb flash memory in general, but I've also read the newer designs are less prone to failures.Take my experiences with a grain of salt. They are based on actions that occurred years ago. I can't even remember much, but I believe it was back in the 10.04 days.

Anyways, I burned out two USB sticks with dynamic installs before I decided that it was too risky for me. Often, I had important docs on that stick and the whole idea was to have them accessible while I was on the road, which is defeated when your OS won't boot up just when you really need it.

Important to note that I wasn't knowledgeable enough back then to turn off all disk intensive functions. So I had journaling, time-stamping, swap, temp and logging all at default settings, which is damn near maximum. Since learning how to turn that stuff off, I haven't done a dynamic install to a stick, so my info is incomplete and probably outdated.

What I've done instead is bought a small USB SSD drive. They are very cheap these days and, unlike sticks, they are designed for a far higher number of writes (faster too). In the meantime, Ubuntu itself has become less disk-intensive. When you add in the practices that I'm now using to reduce disk access, I'm finding the USB SSD to be a perfect way to tote around a mini 'buntu OS. I actually have Lubuntu installed on it to run on the largest number of systems. It's great in a hotel setting where I haven't any idea what malware is on their public terminals, or on friends' or acquaintances' computers where I don't want to touch their installs in any way, shape or form.

@OP

SSD drives (120GB) are as cheap as $40 these days. I bought a USB conversion kit to go with mine for another $20. I can swap any number of SSDs into the kit, so it's not only good for mobility and alternate OSes, but also for backing up. For the absurdly low cost of these components these days, I find that the marginally greater cost over USB sticks is more than offset by the greater performance, versatility and robustness. And at 120GB, "not enough space" warnings are a non-issue.

---

### Post by gordintoronto on 2016-03-01
If that is an 8 GB flash drive, you didn't actually install onto it, you created a "live USB" with persistence. Or perhaps you did install, but you only formatted half the flash drive. In any case, if you want to run from a flash drive, your best bet is to make a Live DVD, then install onto a larger flash drive, if possible. You can install onto an 8 GB flash drive, but you'll be fighting space issues forever -- beginning the first time you apply updates.

Why install from DVD? It means the flash drive will probably be /dev/sdb, and that's a good place for it.

As an aside, it is sometimes helpful if you say exactly what you installed, eg. "Ubuntu 14.04.3 64-bit."


> **wyattwhiteeagle said:**
> $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       3.7G  3.5G   34M 100% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           363M  1.2M  362M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.8G   80K  1.8G   1% /run/shm
none            100M   80K  100M   1% /run/user

The trash...thank you for that idea...what about all the cache and temps folders? 

But I been reading on these forums that Ubuntu does its own maintenance and upkeep...is that only a common myth?

---

### Post by jim Kane on 2016-03-02
> **Geoffrey_Arndt said:**
> Hello Duckhook . . 
Back to the OP's issue, I think v3.xx is right-on regarding needing more storage . . . 8 giB just too small _(but plenty big enough for tinycore linux!)_:   [http://distrowatch.com/images/slinks/tinycore.png](http://distrowatch.com/images/slinks/tinycore.png)

or  [http://www.porteus.org/](http://www.porteus.org/)  which is only 300Mb
you can even have a Xfce or KDE gui

---

### Post by Geoffrey_Arndt on 2016-03-02
Porteus (Slackware based) is pretty awesome from what I've seen . . fast, stable etc.

---

### Post by wyattwhiteeagle on 2016-03-15
> **vasa1 said:**
> That is worrisome.

Please post the links to where what you've read has been stated. It has the potential to mislead people depending on what meaning is given to "maintenance and upkeep".

Worrisome indeed.

I haven't replied to any such threads or posts as of yet so I would have to just search different things to find them.

But my better choice would be that when I come across one...what should I do...ie report it or chime in stating my experiences and ask questions?

What is recommended that I do when I come across those "misleading" threads and posts?

---

### Post by howefield on 2016-03-15
> **wyattwhiteeagle said:**
> Worrisome indeed.

I haven't replied to any such threads or posts as of yet so I would have to just search different things to find them.

But my better choice would be that when I come across one...what should I do...ie report it or chime in stating my experiences and ask questions?

What is recommended that I do when I come across those "misleading" threads and posts?

Any posts that are worrisome to you should be reported using the Report button that you will see find in each posting "window" with and a member of staff will take a look.

I await with bated breath...

---

### Post by Geoffrey_Arndt on 2016-03-15
WyattWhiteEagle . . . to know if a thread is misleading or not requires at least a very minimum of Linux knowledge . . . . 

The problem is simple.   You're trying to put 50 pounds of potatos into a 25 pound sack.   Not zactly Rocket-Science.

---


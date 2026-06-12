---
title: "First install"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by jimv8673 on 2013-03-09
Im as new to ubuntu as is possible.  I have thought of switching over for some time but have a few questions. my machine is a dell laptop running windows 7.  I have 8gb ram, and about a 450gb hard drive. It is a 64 bit system.

I really have no use for windows as i use my computer almost exclusively for the internet.

1.  im currently downloading ubuntu 32 to burn a cd and also downloading the .exe windows installer.

2.  what i would like to do is dump windows completely, and just run ubuntu on my machine.  I think ?? :)

how can i best and most safely do this??  does the umbuntu iso wipe out windows??  can i use that 32 bit version on my 64 bit machine??

I guess basically what im asking is based on the above info what would you do ??

---

### Post by carl4926 on 2013-03-09
> [COLOR=#000000]downloading the .exe windows installer.[/COLOR]You don't want this

You should use _64 if your machine is 64bit

Then burn the .iso to a cd and boot from the cd

It's usually wise to keep windows, especially if you are new

You can use a USB pen drive instead of a CD

You can try Ubuntu live before installing

---

### Post by sudodus on 2013-03-09
> **jimv8673 said:**
> Im as new to ubuntu as is possible.  I have thought of switching over for some time but have a few questions. my machine is a dell laptop running windows 7.  I have 8gb ram, and about a 450gb hard drive. It is a 64 bit system.

I really have no use for windows as i use my computer almost exclusively for the internet.

1.  im currently downloading ubuntu 32 to burn a cd and also downloading the .exe windows installer.

2.  what i would like to do is dump windows completely, and just run ubuntu on my machine.  I think ?? :)

how can i best and most safely do this??  does the umbuntu iso wipe out windows??  can i use that 32 bit version on my 64 bit machine??

I guess basically what im asking is based on the above info what would you do ??

Welcome to the Ubuntu Forums :-)

- If you are sure you won'&#7831; need Windows you can wipe it.

- If you have a Windows recovery partition or Windows recovery disk or Windows install disk, you can wipe it.

- But if you are not quite sure, you should keep it at least for some months, and install Ubuntu alongside Windows (***dual boot***, not wubi).

* Anyway, I suggest you backup all personal files (documents, photos, video clips etc) before wiping Windows.

- With 8 GB RAM, I recommend a 64-bit Ubuntu system.

* What are your cpu and graphics card/chip? Knowing about them it will be easier to give advice, for example if you should try some other flavour of Ubuntu with different desktop environment (Lubuntu, Xubuntu or Kubuntu).
--
It is enough to let Ubuntu re-partition and re-format the drive to get rid of Windows. But think twice and consider Windows plus Ubuntu for a while and later on you can wipe Windows and make that partition into a data partition for Ubuntu.

---

### Post by jimv8673 on 2013-03-09
I have an intel core 2 duo cpu t6600 2.20Ghz 2200Mhz 2 cores  was this your question ??

I have currently drive C  and D is a recovery, but i also have a windows7 new install CD, i have to reinstall windows a lot, i tend to goof things up so i have to do the big fix :)  i dont really care because i never have anything on this machine that i care to lose.

dumped the .exe download, and also the 32 bit version, now downloading the 64 bit :)

---

### Post by sudodus on 2013-03-09
> **jimv8673 said:**
> I have an intel core 2 duo cpu t6600 2.20Ghz 2200Mhz 2 cores  was this your question ??

I have currently drive C  and D is a recovery, but i also have a windows7 new install CD, i have to reinstall windows a lot, i tend to goof things up so i have to do the big fix :)  i dont really care because i never have anything on this machine that i care to lose.

dumped the .exe download, and also the 32 bit version, now downloading the 64 bit :)

So you are ready to go and wipe Windows :-)

I suggest that you make a fresh install of Ubuntu. The simplest way is to let the installer do it automatically, but maybe it is better to first

1. Try Ubuntu, running a live session booted from the install disk. Does it work properly? What about the graphics? Maybe you need a proprietary driver (for nvidia or amd/ati/radeon). Maybe your computer would run smoother with Xubuntu?

2. Edit the partitions on your internal drive with ***gparted*** (still booted from the Ubuntu install CD/DVD drive).

An example:
You can select to use
25 GB for root partition **/** with ext4 file system
Create an extended partition
and inside it create the other partitions
9 GB for swap partition
and the rest for your home partition **/home** with ext4 file system

and you can also have a separate multimedia partition and separate test partitions if you like. Give them easy to understand ***labels***.

The basic setup is to have only two partitions: the root partition and the swap partition.

3. Installation

If you have made partitions manually,*** then during installation***, at the partitioning screen select 'Something else' and select the partitions you have created. Also install grub to the head of the drive (/dev/sda if the first drive, not to a partitions /dev/sda1 ...)

---

### Post by carl4926 on 2013-03-09
You can just choose the option to Erase everything and install Ubuntu
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

---

### Post by pfeiffep on 2013-03-09
Whether you intend to wipe out everything or not doesn't really matter at this point, I agree that you might want to 'try out Ubuntu from the live cd prior to wiping out everything. You will be able to determine if ubuntu will work with your current hardware  - maybe you'll need to try another flavor (lubuntu, xbuntu ....) if ubuntu doesn't work correctly. I have completely wiped out my Win XP installation on my old Dell laptop and found it perfectly agreeable - however I did boot from a pendrive for about a week prior to blowing away Windows!  When you've made the final decision - you can choose to replace the Win installation - I found that the replacement partitioned my 40 Gb drive and it works GREAT!  Welcome to FREE - dom!

---

### Post by fiodev on 2013-03-09
Don't erase windows untill you have used linux for a few weeks. 
Use 64 bit system
Welcome to linux
feel free to ask me any questions I will be more than happy to help with the transition!

---

### Post by cheatos on 2013-03-09
another thing concerning swap.
If you don't want to use the hibernate function (in windows something like energy saving, dunno the english word, my win7 system runs in german) you may shrink the swap or completely omit it as 8GB of ram is more than enough for ubuntu. with just a browser (firefox) opened it will need less than 1GB of ram. Swap space is something like the paging file in windows but ubuntu just uses this file when it really needs it, so no need for swap space.
This changes if you hibernate because then your system just loads the complete content of the RAM to the swap file. (then 8GB should be enough)

I would also recommend not to remove win7 from your laptop. GRUB has a built-in dual-boot function with which you may choose which OS to boot. I personally have switched about 1 year ago and still need win7 for some stuff from time to time.
You may shrink the win7 partition during installation of ubuntu to a size fitting your stored data. If it is a new installation of windows some 20 to 30GB should be enough, if you already have some stuff on there, maybe 50GB

---


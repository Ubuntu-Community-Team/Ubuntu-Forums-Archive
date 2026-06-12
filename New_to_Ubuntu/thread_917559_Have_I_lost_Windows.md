---
title: "Have I lost Windows?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by binaryike on 2008-09-12
This is a T7700 laptop with 3GB RAM and a 120GB hard drive, which has been running fine with Vista for six months. I don't store video or music on this unit, so that HD is mostly empty. And, of course, the grass is always greener - so I decided to try Linux. To avoid mistakes, I asked a Ubuntu user for help. Last evening, my "expert" installed Ubuntu 8.04, intending to create a separate partition and dual boot.

However, upon booting this computer it appears that there is but one OS available: Ubuntu. Obviously there was an error during the installation. I didn't discover the missing OS until after two hours of setting up Ubuntu.

My work is backed up, so it's not a total disaster.

However, if there is a way to unwind this, please advise.

Thanks

---

### Post by SunnyRabbiera on 2008-09-12
well its possible that the windows partition isnt being picked up by grub your bootloader.
But to see, can you go to the "places" menu and go to "computer"?
Lets see if it picks up everything there and we can go down the list.
Do you have a vista recovery disk though?

---

### Post by crazypenguin2008 on 2008-09-12
if you dont see the other partition for windows then its gone,unless the partition is hidden. i had trouble doing a dual boot install. when you do a install of linux it whipes the drives unless you partition the drives for the other OS

---

### Post by binaryike on 2008-09-12
Under Places > Computer there's nothing Windows-like.

Tomorrow I will reinstall Windows, but with murder on my mind.

---

### Post by SunnyRabbiera on 2008-09-12
> **binaryike said:**
> Under Places > Computer there's nothing Windows-like.

Tomorrow I will reinstall Windows, but with murder on my mind.

well not just yet, I also want to see what the system monitor says.
Go to system, then to administration, then to system monitor.
In that go to the last tab and tell us if linux is using the whole drive.

---

### Post by akiratheoni on 2008-09-12
> **crazypenguin2008 said:**
> if you dont see the other partition for windows then its gone,unless the partition is hidden. i had trouble doing a dual boot install. when you do a install of linux it whipes the drives unless you partition the drives for the other OS

The default option at the partition portion of Ubuntu is the slider where you determine how much space goes to Ubuntu and how much goes to Windows (if you already have Windows on your computer) so if he kept hitting 'next' in the install then Windows should still be installed unless the 'expert' deleted Vista on purpose.

Go to Applications -> Accessories -> Terminal

and copy and paste this command:

```
sudo fdisk -l
```

Type your password when it prompts you to (nothing will appear as you type your password) and paste the output here.

---

### Post by adult swim on 2008-09-12
lets be sure
go to a terminal appliacations>accessories>terminal
and then type in ```
sudo fdisk -l
``` and hit enter
it will ask for you password, type that in and hit enter and it will spit out some information.  copy and paste that back here.
EDIT: too slow!

---

### Post by gandaran on 2008-09-12
install gparted, open the terminal/console, type **sudo apt-get install gparted**  then go to system » administration » partition editor, you'll be able to see all the disk partitions

---

### Post by kansasnoob on 2008-09-12
The ouput of:

```
 sudo fdisk -l
```

is needed to answer your question.

---

### Post by billgoldberg on 2008-09-12
> **binaryike said:**
> This is a T7700 laptop with 3GB RAM and a 120GB hard drive, which has been running fine with Vista for six months. I don't store video or music on this unit, so that HD is mostly empty. And, of course, the grass is always greener - so I decided to try Linux. To avoid mistakes, I asked a Ubuntu user for help. Last evening, my "expert" installed Ubuntu 8.04, intending to create a separate partition and dual boot.

However, upon booting this computer it appears that there is but one OS available: Ubuntu. Obviously there was an error during the installation. I didn't discover the missing OS until after two hours of setting up Ubuntu.

My work is backed up, so it's not a total disaster.

However, if there is a way to unwind this, please advise.

Thanks

It's most likely gone.

Make sure to tell your "expert" to stop installing Ubuntu other peoples computers if he doesn't know what he is doing.

---

### Post by binaryike on 2008-09-12
Ike@Ike:~$ sudo fdisk -1
[sudo] password for ike: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


And System Monitor shows one partition, 141GB.

The "expert" will suffer...

---

### Post by bumanie on 2008-09-12
It is > sudo fdisk -l (A lower case L, not the digit one)

---

### Post by binaryike on 2008-09-12
In the Terminal, I entered sudo fdisk -l

Was asked for PW, but it doesn't appear with keyboard entry or with copy/paste. With no PW, I get "Try again"...

??

---

### Post by bumanie on 2008-09-12
When you type the password, there is no visual output. But if you press enter after finishing the password, you will find the command will be processed and give an output in the terminal which you can cut and paste here.

---

### Post by binaryike on 2008-09-12
THANKS!!
------------------------------

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d77d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 8168 MB, 8168931328 bytes
39 heads, 5 sectors/track, 81820 cylinders
Units = cylinders of 195 * 512 = 99840 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              43       81821     7973376    b  W95 FAT32

---

### Post by bumanie on 2008-09-12
Unfortunately, it looks as though you have wiped windows although there seems to be a FAT 32 filesystem on a second hard drive. Unless that is where you had windows, but it looks too small to contain a full windows installation.  You can try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to try to recover it. Read the documentation on the site and also read [this]("http://www.users.bigpond.net.au/hermanzone/p21.html") Test disk will often recover lost partitions. I hope it works for you.

---

### Post by binaryike on 2008-09-12
It's time to accept the problem - this is a one-OS computer.

The "second drive" is an 8GB SanDisk Ultra SDHC card in an adapter. Ubuntu recognizes it. 

I was using Allway - a backup/sync app - to maintain a backup of important folders/work on that SDHC card. Good thing!

However, in another slot on this laptop I have an 8GB Memory Stick, which Ubuntu has not yet recognized though I've inserted it, booted with it installed, etc. 

I am definitely starting to like this OS. Most people dual-boot for a while before committing, but I'll stick with what I have for a few days before making any decisions.

Thanks for the help - and hopefully the day will come when I'm competent to help others.

My Ubuntu "expert" has promised to wax my car and mow my lawn... but he won't touch my computer again!

---

### Post by SunnyRabbiera on 2008-09-12
> **binaryike said:**
> It's time to accept the problem - this is a one-OS computer.

The "second drive" is an 8GB SanDisk Ultra SDHC card in an adapter. Ubuntu recognizes it. 

I was using Allway - a backup/sync app - to maintain a backup of important folders/work on that SDHC card. Good thing!

However, in another slot on this laptop I have an 8GB Memory Stick, which Ubuntu has not yet recognized though I've inserted it, booted with it installed, etc. 

I am definitely starting to like this OS. Most people dual-boot for a while before committing, but I'll stick with what I have for a few days before making any decisions.

Thanks for the help - and hopefully the day will come when I'm competent to help others.

My Ubuntu "expert" has promised to wax my car and mow my lawn... but he won't touch my computer again!

well what brand is the USB stick you said you were having issues with?

---

### Post by binaryike on 2008-09-12
Not USB. It's a Lexar Memory Stick Pro Duo, 8GB. 

Also, can you point me to a proper guide in setting up Bluetooth devices (mouse and keyboard)? I've done all the obvious things and am still stuck on the touchpad.

---

### Post by SunnyRabbiera on 2008-09-12
> **binaryike said:**
> Not USB. It's a Lexar Memory Stick Pro Duo, 8GB. 

Also, can you point me to a proper guide in setting up Bluetooth devices (mouse and keyboard)? I've done all the obvious things and am still stuck on the touchpad.

well bluetooth is touch and go depending on what you have.

---

### Post by waspbr on 2008-09-12
on the unlikely event that your bluetooth devices don't get connect, set them to connect/search and do 

```
sudo hidd --search
```

this is what I do with my logitech bluetooth desktop

---

### Post by binaryike on 2008-09-13
My laptop once again works on Vista - and nothing else. All data has been recovered, and after an hour or two of re-installing apps and configuring, it's fine. I've put a disk image on a spare hard disk, just in case.

But Ubuntu was very interesting, and I would like to set up dual boot. After this highly negative experience, I'll need some step-by-step instructions for a noobie.

Where is the best dual-boot tutorial?

Thanks,
Ike

---


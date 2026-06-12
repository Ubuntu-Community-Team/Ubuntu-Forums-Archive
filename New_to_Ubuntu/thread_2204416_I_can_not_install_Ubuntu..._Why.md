---
title: "I can not install Ubuntu... Why?"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by davidcleagueoflegends on 2014-02-08
Error mounting /dev/sda1 at /media/ubuntu/d7ed6c3d-7da6-4dca-bb91-c29b9675afc5: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/ubuntu/d7ed6c3d-7da6-4dca-bb91-c29b9675afc5"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
How can i solve this problem. Thank you people who have time for my problem in advance.

---

### Post by whitesmith on 2014-02-08
Welcome to the forum, davidcleagueoflegends . Experiment with the "Try Ubuntu" option.  See if that works on your hardware. If it fails, there's something about your system Ubuntu doesn't like. It's always a good idea to try before installing. BTW what version do you have? Post that if there's a problem. We have to know as much as possible to help. Regards.

---

### Post by davidcleagueoflegends on 2014-02-08
Thank you for your time, im trying to install 13.10 ubuntu and im on "try now" option... What else can i provide to you? And i formated like all my partitons becose i couldn't install win xp i came here for linux...

---

### Post by Bucky Ball on 2014-02-08
Welcome. Is 'Try Ubuntu' running fine? Are you clicking the icon on the desktop to install or rebooting from disk?

---

### Post by oldos2er on 2014-02-08
Please post your hardware specs. 

Mounting a partition is something you do after installation, not before or during. Can you explain exactly what you're trying to do with the mount command?

---

### Post by grahammechanical on 2014-02-08
Does the Try Ubuntu session work?

At the moment I can only guess that you are trying to install Ubuntu on a partition that has already been formatted with a format that is not a Linux format and you have not instructed the installer program to format the partition.

Please look through some of the other posts on the different sections of this forum. You will see the kind of information that is helpful to us. Hardware specifcation, CPU, RAM size, Graphic adapter, the number of partitions and sizes, other operating systems.

You could even be trying to install Ubuntu on a partition that is too small. You give us insufficient information about what you are doing and what is happening. 

Remember, we are only Ubuntu users who are trying to help others who are also Ubuntu users. We are not technical experts with all the answers.

Regards.

---

### Post by Bucky Ball on 2014-02-08
> **grahammechanical said:**
> 

Remember, we are only Ubuntu users who are trying to help others who are also Ubuntu users. We are not technical experts with all the answers.

Or psychic, although it would help. ;)

---

### Post by whitesmith on 2014-02-08
> **davidcleagueoflegends said:**
> And i formated like all my partitions becose i couldn't install win xp i came here for linux...I'm a bit in the dark about exactly what you did. How did you format the partitions? With what? What options did you provide to the formatting software? Normally partitions are formatted by the Ubuntu installation program. Did you bypass this in the formatting process? As another person said, the more we know . . .

---

### Post by davidcleagueoflegends on 2014-02-08
I clicked on desktop to install ubuntu. And I did run system from usb flash...

---

### Post by davidcleagueoflegends on 2014-02-08
Nothing, i just run instalation from "Try now" Ubuntu...

---

### Post by whitesmith on 2014-02-08
So you actually installed Ubuntu, formatted your hard drive with it during installation, and then rebooted . . . and that's when you got the error? Also what is the Ubuntu version? Please describe your hardware, too. We aren't asking for a novella, just enough information to base educated guesses on.

---

### Post by davidcleagueoflegends on 2014-02-08
Hardware specs:AMD A4-3300 APU with Radeon(tm) HD Graphics × 2,graphic Gallium 0.4 on AMD CAICOS,os type 64-bit, ram 3.9 GiB, disk 2.1 GB? That is when i go to"System setings" and than "System" details

---

### Post by whitesmith on 2014-02-08
> **davidcleagueoflegends said:**
> Nothing, i just run instalation from "Try now" Ubuntu...OK. You selected Try Now, got an Ubuntu desktop, and then formatted your hard drive from there. Is that right? Then you rebooted and got the error. Is that right? What version of Ubuntu is this? We aren't asking for a novella, just enough information to help you.

---

### Post by davidcleagueoflegends on 2014-02-08
Yes i think i skiped the formating with Ubuntu, i did it i think with NTSC system i think its called like that, if you ever installed win xp you seen it 100 %

---

### Post by whitesmith on 2014-02-08
You may have solved your own problem. Return to the installation procedure, but this time select Install Ubuntu and let it do the formatting. Please use thread tools, above, to mark this thread closed if this solves your problem. Thanks.

---

### Post by davidcleagueoflegends on 2014-02-08
No i didnt formated hard drive from there, version is ubuntu 13.10, i didnt got this error when i reboted it i got it when i tried to install prety much anything(tried Steam,dont remember what else) or even Ubuntu.

---

### Post by davidcleagueoflegends on 2014-02-08
Im clicking from desktop to install not from reboot

---

### Post by Vladlenin5000 on 2014-02-08
> **davidcleagueoflegends said:**
> No i didnt formated hard drive from there, version is ubuntu 13.10, i didnt got this error when i reboted it i got it when i tried to install prety much anything(tried Steam,dont remember what else) or even Ubuntu.

First of all it's NTFS (NTSC is the old North American analog TV system standard): [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS) . The *_proprietary_ file system developed by _Microsoft_* should be enough as a clue to WHY a Linux distro don't like/can't be installed in such partition.

Rule of thumb: Almost all operating systems, including those proprietary of the aforementioned company, DON'T require previous partitioning but just empty space on some (bootable) drive. The installer should always take care of that for you (it has been said in this thread several times already but unfortunately you seem not willing to understand or accept this trivial fact).

Bottom line: If you intend to install Ubuntu (or any other Linux distro) as a single OS taking over the whole HDD just say so during the installation process. The installer will create and format properly the default partitioning scheme required for the OS installation. Sure, you can install in partitions you already have provided they are what the OS needs and that means NO NTFS, never! (Ubuntu can read/write NTFS but CAN'T be installed on such partition). The sooner you understand this the sooner you'll get your system up and running.

---

### Post by ajgreeny on 2014-02-08
> **davidcleagueoflegends said:**
> Hardware specs:AMD A4-3300 APU with Radeon(tm) HD Graphics × 2,graphic Gallium 0.4 on AMD CAICOS,os type 64-bit, ram 3.9 GiB, [COLOR=#ff0000]disk 2.1 GB[/COLOR]? That is when i go to"System setings" and than "System" details

2.1GB?  Surely there is a typo there?

You can't install ubuntu to a 2.1GB disk; you need at least 5GB for the OS plus more for your own files etc etc.

---

### Post by davidcleagueoflegends on 2014-02-08
I have hard disk with 496 GB! I maked 2 partitions when i was installing win xp (Instalation failed) one is 22 gib, rest are space for my files(Games,photos,music,etc.)

---

### Post by davidcleagueoflegends on 2014-02-08
You are right, yes i said wrong name. The true is "Who is working, he can mistake sometimes", how can i format it with some file system that I can install linux on. Thank you for your time man i appricate it.

---

### Post by whitesmith on 2014-02-08
It would have so much easier if you had told us more at the outset. I can't imagine why you would try installing an OS on the filesystem created by another OS. That can't possibly work, ever. If you want a working system, just follow my previous post. Ubuntu can create the NTFS partition required by Windows. It can read it as well. What it can't **do is** install itself into a partition created with that filesystem.

---

### Post by davidcleagueoflegends on 2014-02-08
I just find out that my hard disk is damaged too much that is cause :(... Thank you all.

---

### Post by Bucky Ball on 2014-02-08
When you are in 'Try now' at the desktop, could you open a terminal and post the output of this here:

```
sudo lshw -C video
```

Thanks.

* Okay, missed your last post. Hard drive dead. Please mark the thread as solved. Thanks.

---


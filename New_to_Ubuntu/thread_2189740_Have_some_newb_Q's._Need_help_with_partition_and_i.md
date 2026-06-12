---
title: "Have some newb Q's. Need help with partition and install"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by misfitwilly on 2013-11-23
Hi,
I am new here as well as to Linux. After I lost my computer to yet another virus I have decided to try this as I have heard nothing but good.
My level is amateur although I used to be good with DOS(I forgot most of it). Anyway onto my questions.
I am getting a new 500Gb HDD to start with. My Desktop is custom built by me. It's an ASUS P5G41-M LE board with IIRC a Intel core 2Quad.
My question is how should I go about partitioning the HDD and what size should the drive be I install Ubuntu on. 
Also I run a slaved drive with all my files like music photos doc etc from the legacy operating system. Once installed will Ubuntu see that drive and can it recognize the files and open them or are they useless now ? 
Forgive me but I don't know alot so trying to figure out what I am getting myself into. I'm gonna put the HDD in a swap drawer so I can keep using the other OS until I get this one where I want it to be and feel comfortable using it.

---

### Post by ian-weisser on 2013-11-23
> **misfitwilly said:**
> how should I go about partitioning the HDD and what size should the drive be I install Ubuntu on.
There are many schools of thought on this. For your first time, I recommend simply letting the installer run with the defaults. Reliable and regular data backups are more important than your first partitioning scheme.

> **misfitwilly said:**
> Once installed will Ubuntu see that drive and can it recognize the files and open them
See the files? Yes. If Windows could see them, Ubuntu certainly can see them.
Open the files? Depends on the type of file they are saved as. Yes for most common music and video file formats.

---

### Post by Bashing-om on 2013-11-23
misfitwilly; Hi ! Welcome to the forum .

Simple questions with complex answers.
Let me begin with what my partitioning looks like, Mind you I am a somewhat advanced user and have a bit of an idea of what I am doing.
You likely will not need/want separate /var and /tmp partitions. Also not shown are my data partitions, as I mount on demand only.
```

sysop@1304mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  2.1G  2.5G  46% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  380K  396M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  1.0M  2.0G   1% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda2       9.5G  1.1G  8.0G  12% /home
/dev/sda8       4.7G  504M  4.0G  12% /var
sysop@1304mini:~$ 

```
The only partitions you should be interested in making are / and /home, the others required the system will take care of - real smart system, you will grow to appreciate how smart !
If you undertake to set up your partitions manually, I would suggest somewhat larger partitions than I use for /home and / (this symbol is "root").

Else the easy peasy way is to let the install wizard do all the heavy lifting and install ubuntu onto the entire disk... once you do know what you are doing it is a simple matter to copy of your important data, and (re-)install with the set up you have learned that you prefer.

Can ubuntu read other files system as to say " Windows'" .. yes ! not a problem. However once more depending on what you want to do and how you desire to access those data partitions - there is a slight learning curve. However, out of the box there is access !

Believe me we understand the position of not knowing a lot .. none of us were born knowing what we know, we all have to start somewhere,,, also bear in mind, on this forum there is no such thing as a "dumb question". Ask away !

[INDENT][INDENT]that is my welcoming you to ubuntu, dive in! the water feels fine
[/INDENT][/INDENT]

---

### Post by fantab on 2013-11-23
Since you've "heard nothing but good" about ubuntu, I suspect your expectations must have positively sky-rocketted. Allow me to introduce 'gravity'. 

[Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm").

Linux/Ubuntu has a learning curve. The degree of its steepness depends on your willingness to learn new and different things. 
The wise thing to do will be to DUAL-BOOT Windows and Ubuntu, so that you don't face the beginner's frustrations when they find that their favorite games and applications don't work in Linux and that sometimes there is no 'real' alternative. Sometimes your hardware (like, graphics card, usb-modems, printers etc.) might not work out of the box on Linux. The reason for hardware woes is that most of the hardware manufacturers make thier drivers only for Windows and Mac. So getting it to work on Linux can be sweating.
Dual-boot until you gradually minimize the use the other OS to zero. I still have Windows on my desktop but can't remember when I used it last. I didn't have to in a long time.

About Partitions: 

You say you have a HDD with Windows. Keep it as it is. Reinstall Windows, if you have to.
When you get a new HDD, install Ubuntu on it, and tell your BIOS to boot from it. You can set this BIOS boot priority, make the second HDD as the first boot disk. Ubuntu's boot loader, GRUB will find Windows and offer to boot it from its menu. 
Like already mentioned, Ubuntu can read and write to NTFS partitions by default. So you can actually share the data on NTFS between Windows and Ubutnu. However, Windows CANNOT from Linux partitions.
Almost all of the video, audio and image formats work in Linux. Libreoffice will take care of your Microsoft Office created documents, however, sometimes you lose formatting when you open office files in Linux. There may be some unique to Windows or any other proprietory ware files that may not work at all in Linux. 

Partitions are mostly a personal choice, because only you will know what you need. Ubuntu's installer can partition the HDD for you during install, however it does not know your needs. Its not at all wise. If I were you, with 500GB HDD to install Ubuntu on then I would create my partitions:
25GB Primary Ext4 '/' [ubuntu system files]
25GB Primary Ext4 -  [Free, in case I want to install another Linux or antoher version or flavor of Ubuntu]
25GB Primary Ext4 '   [Free as above]
425GB EXTENDED 
4GB Logical SWAP 
421GB Logical Ext4 [make this either '/home' or just a plain linux partition to store my DATA]

The advantage of keeping your DATA separate from 'system files' is quite obvious. If there is any damage to 'System files' or you need to reinstall the OS for any reason, you will only have to delete/format the '/' root partition without touching your DATA, which is safe on another partition.
Extended Partition is primary partition which acts as a container for Logical Partitions. 'msdos' partition table has a ONLY FOUR Primary Partitions limit. You cannot have more than 4 primary partitions. To overcome this limitation we have an Extended partition. Inside an Extended we can have more than 100 Logical Partitions.

Do some research before you actually install ubuntu. The following topics are IMO a must:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
[https://wiki.archlinux.org/index.php/File_Systems](https://wiki.archlinux.org/index.php/File_Systems)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
[https://help.ubuntu.com/13.04/serverguide/firewall.html](https://help.ubuntu.com/13.04/serverguide/firewall.html)
[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)

Looks like I got a bit carried away...

---

### Post by Bucky Ball on 2013-11-24
Welcome. How you partition the drive is a very personal thing! Best to sit down with beverage of choice, a piece of paper and pen and nut it out.

If you are not having a separate /home partition, the decision is easy: Install Ubuntu to one large partition and leave 2Gb at the end for a /swap partition.

If you are using a separate /home, then 20Gb is fine for the / partition (where Ubuntu lives) and use the rest for /home and a 2Gb /swap at the end.

The permutations are endless though. As for the other drive, it should see that. You can do something like installing Ubuntu to a 20Gb partition and letting it put the default /home FOLDER in there. Then, delete the folders in /home and create symlinks to the existing folders on the legacy drive, like /Videos, /Music, etc. As you already have these folders on that other drive this might be the best course of action for you to avoid any duplication and keep all personal data in the one place.

As I say, there are a lot of options so takes a bit of nutting out. Perhaps let us know what the ideal setup would be for you and we can help you put that together. ;)

PS: The way others have their partitioning set up is right for them. That doesn't mean it will be right for you. As I say, it's personal.

---

### Post by 3rdalbum on 2013-11-24
I agree completely with Ian - if you are new to Ubuntu, just let Ubuntu do its own default partitioning.

Also, yes your existing files will be available and usable, especially music, videos, photos and Microsoft Office documents.

---

### Post by sdansmith on 2013-11-24
I was able to save some old files off of a previously crashed HDD using Ubuntu. I used a live CD version of Ubuntu (easy to do) from a thumb drive and then pulled all of the files off of the Hard Drive to the thumb. I'd do that first, unless you already did what the other commenters recommended. Anyway, then, since you're new, I'd let Ubuntu decide how to partition the Hard Drive, as Ian suggested.

---


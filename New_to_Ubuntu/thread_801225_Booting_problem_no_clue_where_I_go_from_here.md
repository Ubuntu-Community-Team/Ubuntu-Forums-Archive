---
title: "Booting problem no clue where I go from here"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by radiospock on 2008-05-20
Mainly for historical reasons I have quite a complex system. I have two hard drives, the first C: contains files I want to save such as pictures and documents. The second is partitioned 
into 3 parts E:, F: and J:. E Used to be part of a dual boot Windows system, but now contains my Windows boot files and is quite small: 23 GB., F is empty 138 GB. J 135 GB. has my Windows XP operating system.I installed Ubuntu 8.04 telling it to use F: and it seemed to install OK.
On rebooting itself I got a menu to choose Windows or Ubuntu. Windows boots fine, but if I select Ubuntu I get the report;
Filesystem type is NTFS, partition type 0x7 
Kernel /boot/vmlinuz-2.6.24-16-generic root=uuid-9490BBE990BBD04A loop=/ubuntu/
disks/root.disk ro quiet splash error 15:file not found press any key to continue

When I press a key I get a menu of options, 3 for various ways of starting Ubuntu and one
for Windows, headed:

Grub4dos 84.3 2008-04-22 memory 638k/2046M CODE END :0X41228 

Whichever item I choose including the Windows option I return to the same menu and have to use
the three finger salute to reboot.

---

### Post by bumanie on 2008-05-20
Looks as though you did not format the ubuntu partition to ext3 and have installed it on an ntfs partition. You will have to reinstall ubuntu and at the partitioning stage ensure you choose for it ext3. Alternatively you can pre-format with gparted, either off the ubuntu live cd or the purpose built gparted live cd which you can download [here]("http://gparted.sourceforge.net/livecd.php"). ubuntu can read/write to ntfs, but needs to have its system files etc. on ext3.

---

### Post by radiospock on 2008-05-20
> **bumanie said:**
> Looks as though you did not format the ubuntu partition to ext3 and have installed it on an ntfs partition. You will have to reinstall ubuntu and at the partitioning stage ensure you choose for it ext3. Alternatively you can pre-format with gparted, either off the ubuntu live cd or the purpose built gparted live cd which you can download [here]("http://gparted.sourceforge.net/livecd.php"). ubuntu can read/write to ntfs, but needs to have its system files etc. on ext3.
Thanks for prompt reply.
Pre-formatted ext3 as suggested, but when I ran the Ubuntu disk from within XP it didn't seem to recognise the partition as a destination for installation. How can I get over this and still have a dual boot system ?

---

### Post by volkswagner on 2008-05-20
Boot the live cd.  Explore your hard disks for the defunct install.  Note the name hda3, sda4, whatever.  You can now reinstall using this partition but reformat to ext3.  You can also use partition manager in the live cd.

---

### Post by bumanie on 2008-05-20
You will have to go into manual at the partitioning stage and look for the partition formatted with ext3 and direct ubuntu to that partition. If your description in the original post has F:\ on the second hard drive, on the second partition, in the partitioner it should be labeled sdb2 - but **double check** it is the one you have formatted to **ext3** before going further with the installation.

---

### Post by radiospock on 2008-05-22
I tried booting from the Ubuntu disk rather than installing from Windows, but I'm afraid I got completely lost by terms I didn't understand when I tried to select drive manually. Also tried letting Ubuntu `have it's head' and install where the devil it wanted from within Windows - same failure to boot. I was under the impression that all this business of choosing partitions and re-formatting was allowed for and sorted automatically when the `install from within Windows' option was chosen in the start screen when starting from within Windows. Thanks for the help but I'm afraid I might have to give up on Ubuntu as the job of installing a dual boot system is more complex than I was led to believe,unless I can find a 1,2,3 simple guide. I'm quite competent with DOS and Windows systems, but this is a whole new language to me.

---

### Post by bumanie on 2008-05-22
Did not realise you were looking at a wubi install. With wubi, you cannot direct ubuntu to a particular partition like you were trying/hoping to do. It is some type of loopback system that that mounts a disk image inside the windows filesytem and windows sees this as normal program and the image on the drive allows files to be read and used, including complete filesystems (It's something along these lines - explaining is a bit out of my league). Once installed that way, I believe there is a way of moving the image to a dedicated partition - but I don't know how to do it as I have never used wubi.
If you want a dedicated dual boot, with ubuntu going to F:\, that should not be too hard to achieve. Where are you getting stuck?
The first thing to know is that you have to create two partitions which are mandatory for a linux install. They are / (which is where the filesystem is installed) and swap (which is a partition used for processes if you run out of ram). Many users set up a dedicated /home partition as well, this way if something goes wrong with the filesystem, your data is safe in /home and you can reinstall the filesystem without affecting your data.
I can try to direct you with how to manually partition if you are intereseted in going ahead with an installation of ubuntu.

---

### Post by kansasnoob on 2008-05-22
I've really found these two sites particularly helpful:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Note that second tutorial deals with using the alternate CD which is much "fiddlier" but it contains some great links to other sites and otherwise great info.

---

### Post by radiospock on 2008-05-23
Thanks to everyone who offered help. I tried something new and got deeper in the mire than ever ! I made a new partition on the disk I want to use and booted Ubuntu from the CD (not in Windows this time) I found some detailed instructions at
 
[url http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_fiesty[/url]
 
and followed them word for word. They even explained how to select areas on disk fo swap, etc. and sizes to use. Everything seemed to go swimmingly but on re-starting the computer I simply got the message that Windows wouldn't boot as Windows\system32\hal.dll was corrupt or missing. (on inspection from a Windows CD boot it was in fact still present !) Sheer panic ! Thankfully I managed to repair Windows XP Pro with the repair console on the original disk. I think Ubuntu is still installed as a boot manager called OSL 2000 found it OK but it wouldn't boot, although Windows still works, Is there any way of making Ubuntu boot without messing up Windows again ? :(

---


---
title: "New Install Issue - Wont boot"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by wmutschler on 2014-03-13
Hi all,  I am a complete newbie to Ubuntu.  Recently attempted a new install and am getting the following error on boot:

error: attempt to read or write outside of 'hd0'.  entering rescue mode.

I'm using the 32 bit version of 13.10  TIA, Bill

---

### Post by hebrewofyhwh on 2014-03-13
Are you installing from a USB? What other information can you offer? I too am new to this and I had many issues on my first install.  I just kept redoing it until it worked.

---

### Post by wmutschler on 2014-03-13
I was installing from a DVD.  This was the third installation attempt and the farthest I have gotten.  The first two attempts ended when the install process froze before finishing.  This install attempt was to a brand new hard drive just installed on the machine.  The machine is also running WIN XP.  However, the HDD that has XP was disabled for this install.

---

### Post by mörgæs on 2014-03-13
Hi, welcome to the fora.
Please begin with a complete hardware description.

---

### Post by wmutschler on 2014-03-13
Here is the hardware description: Older desktop with the following:
AMD Athlon II X2 240 CPU
Seagate 3TB SATA HDD (Ubuntu install on this HDD.  Brand new out of the box)
Seagate 1TB HDD (runs WIN XP.  Disabled during this install)
No Video Card

If there is any other info that would be helpful, please let me know.  Thanks.

---

### Post by mörgæs on 2014-03-13
The video card, first of all. Yes, it's there, else you wouldn't have a picture on the screen.

---

### Post by thenh813 on 2014-03-13
@[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")
Many people have no Graphics Card (think laptop or APU as example), and use the integrated chipset adaptor, so technically he is right. He should have provided the Motherboard brand and type, so the Chipset, GPU and other controllers could be identified.

     [**[COLOR=#000000]@wmutschler[/COLOR]**]("http://ubuntuforums.org/member.php?u=1910672")      
Please provide the Motherboard model# and brand, the HDD could have compatability problems with the Chipset or BIOS. I want to verify this is not the case. Sometimes large drives (2TB and more) are buggy on older hardware. How is the drive formatted? GPT or MBR? Did you put /boot, /tmp or /home on a seperate partition (reccommended)? I cannot help without additional info. The reason for /tmp on a sepearate partition is so if something floods TMP it does not render the system unbootable. The reason for /home seperate is so you can wipe the OS without deleting your data. Having /boot seperate ensures that the bootloader is not destroyed if the OS gets corrupt, allowing other OSes to be booted. You only need a 30GB Partiton for /, 500MB-1GB for  /boot, 10 GB for /tmp (8.5GB is required for burning large dual layer DVDS) and give the rest to /home. This is smy opinion, but never has someone regretted having their PC set up like this for redundancy reasons. I am assuming you formatted between installs. Also, you have to create a Logical partiton to contain /tmp, / and swap.

---

### Post by wmutschler on 2014-03-13
Alright, so no stand alone video card.  It has whatever is integrated into this old Gigabyte motherboard.  According to the Gigabyte website it is most likely ATI Radeon HD4200.

---

### Post by wmutschler on 2014-03-13
thenh813: Sorry I posted prior to seeing your follow up post.  here is what I know:

motherboard: gigabyte GA-MA785GM-US2H[FONT=Arial, Verdana, Helvetica, sans-serif][COLOR=#006ffd][/COLOR][/FONT][COLOR=#434343][FONT=Arial]AMD 785G + SB710 Chipset
The drive was formatted using WIN XP.  XP only recognized 800GB (or so).  It is not partioned oher than XP formatted it thinking it on had 800GB.  

Thanks.  Bill[/FONT][/COLOR]

---

### Post by thenh813 on 2014-03-13
That is a very nice Motherboard. It should most definitely support 3TB hard disks, Windows XP does not without a patch.
You will want to wipe the drive with GParted from the LiveCD my choosing  Device>New partition table>MS-DOS (MBR).
Windows XP probabally did not format it correctly because it was not allowed to see the whole drive.
When you wipe the drive, UNPLUG the other drive's SATA cable before booting the LiveCD just to be sure there are no mistakes.
Then try repartitioning it like this:

<Size> - - -                       - - - - - - - - -<Installer Mount Point>

1GB - - - - - - - - - - - - - - /boot
ALL FREE SPACE - - - - - -  N/A (Extended Partition)
10-30GB - - - - - - - - - - - - - / (Inside Extended)
10GB - - - - - - - - - - - - - /tmp (Inside Extended)
FILL EXTENDED - - - - - - -             /home

There will be a picture:
(I used a 50 GB VirtualBox partition for example and made / 6GB because it was so small)

---

### Post by wmutschler on 2014-03-13
OK, you have got me almost there :)  I assume the LiveCD is the one I boot from and gives me the option to install or try Ubuntu?  I created this CD by downloading the Ubuntu installer and burning it to CD.  Where do I find Gparted?  BTW, sorry for the obviously dumb questions

---

### Post by thenh813 on 2014-03-13
Yes that is the right disk, search for GParted in applications. No question is stupid, not asking one is. :) I am only here to help.

Now, if Postimage.org would upload faster LOL. My internet is slow, takes overnight to download Ubuntu haha.

In honor of the first Linux I ever installed, I will be posting screenshots made with Linux Mint 9 XFCE. It is the same with all versions of Gparted, but I have always particularally liked my first two Linuxes, Ubuntu 10.10 SuperOS nad Linux Mine 9 XFCE. Someday I will donate a few bucks to the Ubuntu team.

Folow the directions, they will help you. Like I said unplug the other HDD, you dont want accidental formatting.
Click the Images for bigger, you may want to download them to a flash drive or print them.

[[IMG]http://s13.postimg.org/o8ykz4owz/TUTORIAL_001.png[/IMG]]("http://postimg.org/image/o8ykz4owz/")

[[IMG]http://s13.postimg.org/vl8miewir/TUTORIAL_002.png[/IMG]]("http://postimg.org/image/vl8miewir/")

[[IMG]http://s13.postimg.org/ble88vkmb/TUTORIAL_003.png[/IMG]]("http://postimg.org/image/ble88vkmb/")

[[IMG]http://s13.postimg.org/bb6ppj603/TUTORIAL_004.png[/IMG]]("http://postimg.org/image/bb6ppj603/")

[[IMG]http://s13.postimg.org/u28mzp0kj/TUTORIAL_005.png[/IMG]]("http://postimg.org/image/u28mzp0kj/")

[[IMG]http://s13.postimg.org/f3q859lib/TUTORIAL_006.png[/IMG]]("http://postimg.org/image/f3q859lib/")

[[IMG]http://s13.postimg.org/vcb1shjqb/TUTORIAL_007.png[/IMG]]("http://postimg.org/image/vcb1shjqb/")

ReiserFS is used in the example because it is the most reliable and fast FS when it comes to data integrity and speed.
You can use it or pick XFS, EXT3, EXT4, BTRFS, JFS, any of those will work. I reccommend XFS or ReiserFS.
You can name the partitions anything you Like, I just named them accordingly in the example.
You know in the installer, there is the something else option, click it when asked for formatting.
The first small partition should be left as EXT2 and set as boot, because boot has to be EXT2/3.
The second partition is ROOT, and is 10-30GB, set its mount point to /.
The Third Partition is TEMP and is 10GB, set its mount point to /tmp.
The fourth should be made from ALL the space left and its mount point set to /home.

---

### Post by thenh813 on 2014-03-13
MAX 8 Images in post so these were posted in a second.

[[IMG]http://s13.postimg.org/i6vjmdpur/TUTORIAL_008.png[/IMG]]("http://postimg.org/image/i6vjmdpur/")

[[IMG]http://s13.postimg.org/5oey5ssv7/TUTORIAL_009.png[/IMG]]("http://postimg.org/image/5oey5ssv7/")

Hope this helps, I will be back tomorrow.

---

### Post by wmutschler on 2014-03-13
Thanks for the detailed help and screenshots.  I got through the install process but on reboot (at end of install process), I am stuck at the verifying DMI pool data stage of boot.  I will take another look in the morning but I cant see a reason for being stuck where I am.  Also, I could not set up a partition greater than ~2TB

---

### Post by thenh813 on 2014-03-14
> 
Verifing DMI Pool.


That is not a good sign. That ALMOST ALWAYS points to hardware configuration errors or failure.

Do you have the drive set as the first boot device in BIOS?
Windows (from the second drive) can be added to Grub's list later so dont worry about having to switch disks in BIOS all the time. If the disk is the default boot device, and Grub is correctly installed, I believe the disk may have a problem.

Try booting up the LiveCD again and opening Disk Utility. Disk utility can also be launched from terminal or run dialog (ALT+F2) by executing "palimpsest". Select the 3TB disk from the drives it lists to the left and click SMART data in the upper right corner. Select run test and then extended test. It can take a while. I just want to rule out most of the possibility of a faulty drive after seeing that message. If all is good it should say Self Tests: Completed OK in the dialog box. This does not mean that the drive is completely ok, but is most probabally ok.

Here is what Gnome Disk Utility looks like running on Ubuntu 12.04.3 [wattOS R6]:
[[IMG]http://s27.postimg.org/v0ld2n5rj/2014_03_14_143749_1280x1024_scrot.jpg[/IMG]]("http://postimg.org/image/v0ld2n5rj/")

> 
Also, I could not set up a partition greater than ~2TB


Very odd. I dont know why that should be, Ubuntu DEFINITELY supports very large drives in the current kernel.

---

### Post by wmutschler on 2014-03-15
Thanks for all the help.  Not sure exactly what happened but after calling a do-over everything was working (although it has stopped working but I will create a new post for that).  I simply re-partitioned the drive into a ~2MB and ~1MB partition and let Ubuntu run through default install procedure.  

At boot up, I still get the same error about attempt to write/read outside hd0, however, it does boot into Ubuntu.

---

### Post by thenh813 on 2014-03-15
Ok, I will check the new post and link it here.
Just incase anyone in the future has similar problems and finds this thread.
That way the know where the other is.

LINK: [http://ubuntuforums.org/showthread.php?t=2211306](http://ubuntuforums.org/showthread.php?t=2211306)

---


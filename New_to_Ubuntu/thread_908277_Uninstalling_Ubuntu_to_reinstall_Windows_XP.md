---
title: "Uninstalling Ubuntu to reinstall Windows XP"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by hasins on 2008-09-02
So, I am in a mess

My office PC was formatted using the Ubuntu CD and Ubuntu was installed. 

I have two hard drives, one with 40gb (on which Ubuntu is installed) and another of 120gb which I left empty for data.

The 120 gb is refusing to mount (cant mount volume error) and I am having trouble with accounting software that I cant use on Ubuntu.

I want to change back to XP until I can figure out a little bit more about Ubuntu. So have installed it onto my laptop within my windows vista installation.

The question is how do i go about uninstalling Ubuntu to reinstall XP

I have my XP cd ready...

Am a total toddler as far as linux/ubuntu is concerned..please help!

---

### Post by oilchangeguy on 2008-09-02
make sure the computer is set to boot from the cd drive. insert the xp cd, boot from it, and follow the prompts. also is your xp cd a true xp cd, or a factory restore cd?

---

### Post by abhishek.malhotra35 on 2008-09-02
To switch back to XP, simply boot with XP CD. If you want to delete ubuntu partitions then do so while installing or you can use softwares like partitionmagic after installing XP. If you want XP and simultaneously play around with unbuntu also, then recover your grub. Your machine will become dual boot.

---

### Post by hasins on 2008-09-02
Thanks oilchangeguy and abhishek

The problem i am having is booting with cd-rom!

Cant get it to boot from cd rom

When i press esc during start, i get to the screen which gives me three boot options, all of ubuntu :(

---

### Post by hasins on 2008-09-02
oilchangeguy: its a tru xp cd, bootable, but doesnt boot by itself on ubuntu

---

### Post by theredcross on 2008-09-02
You need to go into your BIOS and change your boot sequence so that it checks your CD-ROM first. When you first turn on your computer you should see somewhere something like "Press DEL to enter setup". Different computers have different keys, but look for that and try to get into your BIOS, which will look like a bunch of text that you can navigate around with the arrow keys.

Find boot sequence, might be under advanced options or something similar, and put your CD-ROM at the top of the list. save and exit, and that will restart your computer and it should work fine from there.

---

### Post by brentoboy on 2008-09-02
your pc is probably set to boot to hard drive instead of CD.

the boot menu you are talking about is the grub menu, which is loaded after it starts booting from the hard drive.

in order to boot to cd, you have two options, 1) most computers allow you to press F8 or F12 or some other button to have a one time "boot from CD" option, if it works, it will list all possible boot options and let you choose a temporary one. 2) you could change the BIOS to try booting from CD always. to do that, while your computer is counting memory and listing harddirves and stuff, click del, or f1, or f2, or.... ? (depends on the make / model of the pc).  There is a "boot order" somewhere in the bios settings.  Change it to prefer the CD.

---

### Post by Unanimated on 2008-09-02
Also, make sure you choose the right drive and format it with the NTFS filesystem. It's so much better than FAT.

---

### Post by crispy_420 on 2008-09-02
I second the option of most "newer" PCs let you select a boot device if BIOS is an issue (locked out?).

Also I've had some issues with reinstalling an OEM XP restore disk in the past unless I wiped the drive.

---

### Post by hasins on 2008-09-05
Okay I booted from the cd rom and tried to format the hard disk to install xp

But, the system could not find any hard disks with the fdisk command!

Upon restarting with the boot set from hard disk, it recognised the hard disk and started ubuntu like normal!

What am i doing wrong?

---

### Post by halitech on 2008-09-05
fdisk is a windows program and it cannot read ext3 (or any other linux hard drive format) so you may need to use partition magic or the gparted cd to wipe all partitions first then install XP

---

### Post by lintoon on 2008-09-05
Also, if it's not booting from the cd you may be able to press a key and bring up a boot device menu.  It's one of the function keys.  A lot of systems use F12.  Some F10. Some F8.  I can't verify what every pc uses but keep your eyes open when you first turn it on/reboot or check your motherboard manual.

I would also grab a multifunction cd.  Something like Knoppix for the extra tools it supplies.  Or even the Ultimate Boot CD.  Just as a precaution.  Or am I too paranoid!!!! Who said that!!!!!!

---

### Post by halitech on 2008-09-05
> **lintoon said:**
>   Just as a precaution.  Or am I too paranoid!!!! Who said that!!!!!!

just cause you are paranoid doesn't mean they aren't out to get you ;)

---

### Post by alzie on 2008-09-05
You might want to try something like the ultimate boot cd : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

It should help you format your drive to ntfs or fat32 so that your Windows disc can do its thing.  It is also handy if you ever need to trouble shoot hard drive issues.

I hope this helps.

---

### Post by kansasnoob on 2008-09-05
You could just boot your Ubuntu Live CD and go to System > Administration > Partition Editor (aka: Gparted) and delete all of the Linux partitions.

A common stumbling block is needing to select "swapoff" to "unlock" the swap partition so it can be deleted.

Once the entire drive, or a continuous portion of it, is totally unformatted I'll bet the Windows installer will run. Then you can choose either NTFS(preferred) or FAT32.

---

### Post by oobe-feisty on 2008-09-05
why are people helping this guys install windoze i know he has ubuntu 
installed but his aim is to get it off plus anyone who doesnt know how to do this already could easily find out on the net using somthing called google take a absolute beginner about 5 mins to do that

---

### Post by knix on 2008-09-05
> **kansasnoob said:**
> You could just boot your Ubuntu Live CD and go to System > Administration > Partition Editor (aka: Gparted) and delete all of the Linux partitions.

A common stumbling block is needing to select "swapoff" to "unlock" the swap partition so it can be deleted.

Once the entire drive, or a continuous portion of it, is totally unformatted I'll bet the Windows installer will run. Then you can choose either NTFS(preferred) or FAT32.

That's what I would do.

or, according to microsoft  [http://support.microsoft.com/kb/314458]("http://support.microsoft.com/kb/314458")

---

### Post by alienexplorers on 2008-09-05
There is a gparted CD that lets you delete and build partitions.  You could use it to delete the ext3 partitions and make them NTFS partitions.  Then just go ahead and load windows xp.

---

### Post by halitech on 2008-09-06
> **oobe-feisty said:**
> why are people helping this guys install windoze i know he has ubuntu 
installed but his aim is to get it off plus anyone who doesnt know how to do this already could easily find out on the net using somthing called google take a absolute beginner about 5 mins to do that

why? because they came here and politely asked for help on doing it. they haven't ranted about ubuntu being garbage and not being able to do anything and they want to figure it out but not right now so by helping them do what they want, they will get a better impression of Ubuntu and decide to make the effort to learn it when the time is better for them.

> The 120 gb is refusing to mount (cant mount volume error) and I am having trouble with accounting software that I cant use on Ubuntu.

I want to change back to XP until I can figure out a little bit more about Ubuntu. So have installed it onto my laptop within my windows vista installation.

---

### Post by hasins on 2008-09-27
thanks everyone

this forum has been extremely helpful in guiding my first baby steps in the linux world of ubuntu

I used the live ubuntu cd terminal and called 'sudo gparted' and then deleted the partitions before using the windows cd to install xp

---

### Post by ready4thebreak on 2008-09-27
> **knix said:**
> That's what I would do.

or, according to microsoft  [http://support.microsoft.com/kb/314458]("http://support.microsoft.com/kb/314458")


I LITERALLY LAUGHED OUT LOUD AFTER READING THAT LINK! I'm still stunned that Microsoft would even acknowledge Linux after all the attempts they make to prevent it from gaining ground(i.e. the Xbox Linux hacks and the fact that every Vista user has stumbled on Linux one way or another)

---


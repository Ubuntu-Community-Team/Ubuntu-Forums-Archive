---
title: "[SOLVED] After install of Ubuntu, Windows XP will not install"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by mike272rr on 2008-11-14
Hello,  I have been reading lots of posts here about getting a dual boot set up.  Original was PC with XP.  After install of Ubuntu no more Windows, it used the whole drive. :(  I booted with my XP install CD, ran through the install and when it reboots displays a black screen with a small white horizontal cursor.  I then tried reinstalling XP using the whole drive and formated over the Ubuntu but still the install reboots to a black screen.  Read about a MBR and using the Live CD to run some commands but that didn't work.  

Is it possible to wipe out the hard drive completely and rebuild again with Windows in a smaller partition and then install Ubuntu?  Or is it easier to install Ubuntu and then use gpart to make space and install Windows?

Thanks, Mike

---

### Post by AncientPC on 2008-11-14
You may want to use the [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php") to delete all partitions on your hdd and start over from scratch.

I find it much easier to dual boot by install Windows OS's first and then installing Ubuntu afterwards.

---

### Post by cdtech on 2008-11-14
You can use the "Live CD" open "gparted" under System > Administration > Partition Editor, select the proper drive and format to fat32.

Install XP first, Window's installer is not configurable and desires the first sector of the primary drive to install the MBR. After which you can boot into XP and create a partition (any amount you want) to install Ubuntu onto.

Good luck......

---

### Post by Skripka on 2008-11-14
> **cdtech said:**
> You can use the "Live CD" open "gparted" under System > Administration > Partition Editor, select the proper drive and format to fat32.

Install XP first, Window's installer is not configurable and desires the first sector of the primary drive to install the MBR. After which you can boot into XP and create a partition (any amount you want) to install Ubuntu onto.

Good luck......

I'd recommend doing ntfs instead.  XP wants an ntfs partition to install to.

---

### Post by starcannon on 2008-11-14
Heres a couple links for you to help you set things up.

I prefer Virtual Box unless I need the windows partition for gaming:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Be sure to read the documentation and faqs, its pretty easy if you do, getting USB going is about the only geekly aspect of it, and its not to bad; indeed if you decide to use Vbox I'd be more than happy to link or post the how to for that as well.

This one is windows installed first:
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

This one is Ubuntu installed first:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

GL and keep it fun

---

### Post by cdtech on 2008-11-14
True, although I've heard formating NTFS from gparted gives some Window's installs a hard time (reading the drive). Window's XP will give you the option to format to NTFS during the install.

---

### Post by mike272rr on 2008-11-14
HI All,  This is a great forum and thanks for the info.  Just home from work and will start this over again.  I will let you know the outcome.  THX

---

### Post by mike272rr on 2008-11-17
Oh Grapola!  First the formating to fat32 and then install winxp went great.  Even got to reboot a few times selecting first Ubuntu and then winxp.  All is good.  Then I started applying patches and such.  Now there is no grub (? forgive my ignorance) boot file and thus no option to secect either Ubuntu or winxp, xp just always starts.  I reviewed the post above to boot the live cd and created one but alas is isn't working.  Of course it is me not understanding what I really need to do.  If there is a way to cut and paste one of those bot files could you direct me to it on the newbe forum?  Many thanks, Mike

---

### Post by tomtom1982 on 2008-11-17
You have to reinstall the grub bootloader. 

For this, you can use the supergrub-disk.

[http://forjamari.linex.org/frs/last_package.php?group_id=61&package_id=143](http://forjamari.linex.org/frs/last_package.php?group_id=61&package_id=143)

Burn iso-file to a cd, boot the cd and follow the instructions. It´s really easy to use, even for beginners.

---

### Post by cdtech on 2008-11-17
You'll just need to boot into your Live CD and reinstall grub to the MBR.

---

### Post by Arcturus691 on 2008-11-17
I had to reinstall XP and because M$ does not play nice with other operating systems, I had to reinstall grub.
[LIST=1]
[*]Boot from Ubuntu CD and go to the GRUB prompt
[*]at the prompt type: find /boot/grub/stage1
[*]Type: root(*hdX,Y*) Enter the drive you found with the find command.  for example: root(hd1,2)
[*]Type: setup (*hdX*)   For example: setup (hd1) This command writes the info to the MBR
[*]Type: quit
[/LIST]

---

### Post by mike272rr on 2008-11-18
A big atta-boy to everyone for your responses.  I am now the proud owner of a system that boots into either Ubuntu or WindowsXP.  I am sure to revisit this section many times as I start to learn more about Ubuntu.  

Many Thanks! Mike

---

### Post by mike272rr on 2008-11-18
Well it may take me awhile butsooner or later I will find out how to thank everyone for their comments.

---

### Post by Arcturus691 on 2008-11-19
Your not the only one who cant figure out how to thank people.  I have tried to figure out how to do so.  There is even a thread that asks the very same question.  In the thread it mentions there should be a yellow button next to reply.  I can't seem to find it.  I posted to the thread below asking for some clarification.

Thanking people thread:
[http://ubuntuforums.org/showthread.php?t=984204&highlight=thanking+people]("http://ubuntuforums.org/showthread.php?t=984204&highlight=thanking+people")

See this thread instead:
See thread:
[http://ubuntuforums.org/showthread.php?t=685924&highlight=thanking+people]("http://ubuntuforums.org/showthread.php?t=685924&highlight=thanking+people")

---


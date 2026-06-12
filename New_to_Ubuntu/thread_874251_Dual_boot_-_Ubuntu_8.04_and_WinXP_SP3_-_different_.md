---
title: "Dual boot - Ubuntu 8.04 and WinXP SP3 - different HD's"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by khaosgott on 2008-07-29
Hey guys/girls,
first of all, good to be here :-)

Now, im gonna ask for some help.

I have two separate HD's, one is 80GB Samsung with WinXP installation (must keep it because of CheckPoint secure client) and the other one is WD 160GB which is currently empty.

Im trying to install Ub 8.04 on the empty HD and create a situation where i can boot from both OS, and so far it wasnt very successful.
If anyone here (Im sure there is someone :) ) has experience with similar configuration and can post the exact steps to configure it, it would be absolutely great.

Thanks in advance,
K.

---

### Post by anewguy on 2008-07-29
What you probably have is the master boot record on your windows drive booting only Windows, and this is probably your master drive as well.  The Ubuntu drive probably has grub loaded to it's mbr but with no menu entry for Windows.

You can "fix" the mbr by running grub from the live CD as follows:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+mbr+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+mbr+grub")

Please note, however, that I do not know if that will also update the grub boot menu to include Windows.  Just to be safe, be prepared to add your Windows installation to the grub boot menu.  There are posts and how-to's for that in this forum.

---

### Post by khaosgott on 2008-07-29
Thanks for the advice, anewguy
the WinXP is indeed installed on the "master" HD, and altough I could move the jumper, I hope to find a different solution.

so far I tried to run "guided" installation on the empty HD and then tried to make it the primary boot HD at the BIOS - no success.
Also tried to configure manually the empty HD's partitions - and reached the dreaded "error 17" in return when tried to mount that partition table.
I could try to install the Ub.8-04 on the XP HD and clear some space, but I do prefer to separate between the two if its possible.

---

### Post by anewguy on 2008-07-29
You should be able to install Ubuntu using the guided installation to your empty drive and it should see the Windows installation and add it to the grub boot menu.  After doing this, there is no need to change to booting from the Ubuntu disk (as you tried via the bios), since what actually happens is that it updates the mbr on your Windows disk (since in this case the Windows disk is the master).  Then a menu will be presented each time you boot allowing you to choose Windows or Ubuntu.

This all assumes that your Checkpoint secure client doesn't do anything to the mbr, and that both your drives where up and running when you installed Ubuntu.

Indeed, I have separate disks for Windows and Ubuntu.  I already had Windows installed on the master drive, and installed Ubuntu to the slave drive.  Didn't change jumpers, bios, anything and just rebooted after Ubuntu installation.

So, now for the silly questions:

1. Where both drives up and running when you installed Ubuntu?
2. When you installed Ubuntu using the guided method, you chose your 2nd drive and said to use it all (user and swap space).  Did you get a grub error 17 when you tried to boot then?  OR did you get a grub error 17 when you tried to boot the Ubuntu disk via the BIOS? (the 2nd choice makes sense, as there is probably no mbr on the Ubuntu drive but instead it is on the Windows drive).
3. What are the sizes of your disks?
4. Which is the master Windows drive?
5. You can still boot straight into Windows using the Windows drive after Ubuntu guided installation, or does it give you a boot menu (don't try to boot from the Ubuntu drive - just leave as is and let it boot)?

---

### Post by rated727 on 2008-07-29
One thing that the Ubuntu might not have done is to install GRUB which provides the boot menu onto your first (WinXP) hard drive boot sector.  The option is not exactly "in your face" when you install Ubuntu.  In your case it may be that GRUB is installing to the MBR of the Ubuntu (second) drive.

If your computer still boots to WinXP, the easiest and safest fix is to reinstall Ubuntu as you have already done.  [SIZE="3"]**BUT**[/SIZE] when you get to the last screen in the install routine (title "Ready to install" click on the [Advanced...] button just above the install button.

Default is that Install boot loader will be selected. make sure it is.
drop the box below the line Device for boot ... and select /dev/sda (the Samsung drive) note: not /dev/sda1
If the boot loader is installed to /dev/sdb or /dev/sdb1 ((Western Digital) it would only start GRUB if your Windows drive is removed ... and what good would that accomplish:)



Caution:  Grub or Lilo can cause your computer to show symptoms of "Multiple Personality Disorder".

---


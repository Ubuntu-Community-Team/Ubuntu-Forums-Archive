---
title: "Reassurance needed!"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by David_Slack on 2015-05-15
I have not yet installed Ubuntu on my PC. I love the concept and how Ubuntu works. My concern is if I install Ubuntu alongside MS Windows 7 (64) and ultimately find I don't like Ubuntu, how easy is it to remove Ubuntu from my PC without affecting MS Windows?

---

### Post by sudodus on 2015-05-15
Welcome to the Ubuntu Forums :-)

You can try Ubuntu without installing (or install it into a USB pendrive, and boot from there). See this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by oldfred on 2015-05-15
What! Remove Ubuntu? :(

We regularly get posts where users do not understand that system boots from MBR and only part of grub is in MBR to boot. So they delete Ubuntu partition and then have major boot issue as grub in MBR has no place to load boot menu from. 
Solution is just to use your Windows repair disk or Ubuntu to reinstall a Windows or Windows like boot loader to MBR** before** deleting Ubuntu partition(s).

How to restore the Ubuntu/XP/Vista/7 bootloader 
 [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Be sure to use Windows to shrink the NTFS partition and reboot immediately to allow it to run chkdsk and make repairs. I do prefer smaller system partitions and large data partitions. You may want to consider a NTFS data partition to share data. Better to set a shared data partition as read/write and only have Windows system partition as read only. 

Most Windows 7 systems used all 4 primary partitions with MBR(msdos) partitioning.
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
    
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Geoffrey_Arndt on 2015-05-15
[U][I][B]What the hey anyway? . . . 
[/B][/I][/U]
Removal in one way doesn't really make sense, _even if you don't like or understand how to make the most of Ubuntu_ (or any Linux distro).

Why??? . . . well, if you ever have a Malware or user caused issue in Windows 7,8,10 etc., and you still have a small Linux OS installed, it can always be booted into and used to rescue the data on your windows "C" drive.

Just give Ubuntu a mere 20-30 GiB (small by today's standards).

And, if you're using a portable PC (laptop, netbook etc.), at a public wifi place, it's MUCH preferable to run an OS that doesn't have some of Windows _baked-in security issues_ - - in other words, Ubuntu is still (according to UK systems audits), much more secure to use.

---

### Post by newb85 on 2015-05-15
There are two minor sticking points to Geoffrey's argument.

One, you would go from a system that you use for everyday use, where you would probably want more than 20-30 GiB, to a system that you use only for emergency and public Wi-fi situations, where 20-30 would be overkill.  It's possible to set the system up for such a potential size reduction, but it takes more work than a regular install.

Two, if you're only going to use it for emergencies and public wi-fi, you're probably not going to do a good job of keeping it up-to-date, which somewhat lessens the security advantage.

---


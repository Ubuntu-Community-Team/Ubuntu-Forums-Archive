---
title: "1st built computer - new to installing dual OS"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by pablorpm on 2008-06-29
I recently just built my first computer and am new to this whole thing.  I have 2 hard drives but wanted to use as my OS drive and the other as my media drive.  I am trying to install Ubuntu and Windows (XP and then Vista upgrade).

I installed Ubuntu first and then boot to the Ubuntu CD so I could run the Partition Editor.  I created the other partition and formatted to NTFS.  I did notice I could not choose anything but Primary Partition.  When I ran the Windows install, the windows installer recognized all the partitions (although it did say Unknown for the first) and I installed Windows.  Unfortunately, the windows partition was on the C: drive so now when i boot it doesn't load grub anymore but goes straight to windows.

How do I make it so Ubuntu is the primary and Windows is secondary?  Thanks in advance.

---

### Post by kestrel1 on 2008-06-29
You need to install Windows first, then install Ubuntu. Ubuntu will recognise the Windows install & add it to the Grub loader. Try re-installing Ubuntu, now that Windows is on your system.

---

### Post by wolfen69 on 2008-06-29
[see this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to recover ubuntu.

---

### Post by kansasnoob on 2008-06-29
The link provided by Wolfen69 is excellent.

One concern that I have is your saying, "I am trying to install Ubuntu and Windows (XP and then Vista upgrade)."

I assume you're going to use a Vista "Upgrade Version" Disc that you already own? I just want you to know that running the Vista upgrade, or for that matter completely removing and replacing XP w/Vista, will put you back in the situation you're in right now. 

So it would be better to complete everything you're doing with windows before "fixing GRUB" to make Ubuntu bootable.

I'm including links to two guides I found very helpful as a nOOb, one for installing XP after Linux and the other for installing Vista after Linux. They both talk about restoring GRUB after the windows install:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Now the link provided by Wolfen69 is far superior in that the apc guides make the assumption that Ubuntu is always (hd0, 0). What you need to understand is that GRUB begins with the number 0 (zero), so (hd0, 0) means (hard drive number 1, partition number 1.

More about GRUB's numbering here:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

But, following the first two sections of the guide that Wolfen69 linked to is flawless, just thought as a fellow nOOb a little more info wouldn't hurt.

---

### Post by pablorpm on 2008-06-29
All of this documentation is phenomenal for the huge nOOb that I am. :)  Thanks a lot of this, wolfen69 and kansasnoob.  Now just for general advice, am I taking the proper approach in building my computer?  Is it smart for me to do dual boots off partitions or is it better practice to put different OS-es on different physical drives?  Also, would you recommend that I restore GRUB or will this affect Windows in any way (I just hear to be wary when tweaking Microsoft settings)?  These questions definitely show how new I am to this, huh? :)

---

### Post by Xerp on 2008-06-29
Personally I like to put one OS per drive (when not using virtual installs). Its just preference :) GRUB is a great bootloder and will let you load Linux or Windows. Keep it, and keep the power :)

---


---
title: "[SOLVED] Ubuntu Installed, Can I resize partitions &amp;amp; install XP after 8.1 is installe"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-11-14
Hi,

I have Ubuntu 8.1 installed & I would like to resize my partitions & add XP.  I know typically it is easier to install XP, then install Ubuntu so the grub manager will be able to make everything bootable.

Can I do it in reverse?  Is there a guide on how to do it?  Or is it as easy as install ubuntu, resize some free space with gparted, format that free space to NTFS, then install XP onto that partition & then how do you fix or install grub?

Thanks,
Rich

---

### Post by bodhi.zazen on 2008-11-14
Yes.

Boot the Ubuntu live CD and use Gparted to resize your partitions.

[Gparted Documentation]("http://gparted.sourceforge.net/documentation.php")

If you install Ubuntu, then Windows all that needs be done it to restore GRUB.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by drs305 on 2008-11-14
Sure, you can do it that way. Windows is a bit more particular on where it is placed and I think that is why many do it the other way 'round. Plus lots of people go from windows to linux, not as many the other way around. :-)

Here is a link on how to restore grub after installing windows. It's from the ubuntu documentation folks:
[RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")
[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---


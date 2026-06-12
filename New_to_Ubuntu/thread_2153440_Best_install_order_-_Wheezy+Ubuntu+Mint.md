---
title: "Best install order - Wheezy+Ubuntu+Mint?"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by JohnyBeGood on 2013-06-11
Hi,


I have separate 1TB drive that I used to install all 3.
I've tried first in this order, Wheezy, Ubuntu & Mint but first issue was that after installing Ubuntu it did not show in Grub. I still went ahead and installed Mint, there it showed that 
Ubuntu was already there. Resized one partition and made room for mint after reboot it showed all 3 with grub from Ubuntu?


I want to start fresh, format and use Gparted live CD and partition about 330GB for 3 different partitions and then install.
Which order should I use?


TIA

---

### Post by sudodus on 2013-06-11
I think all these distros show respect to each other and include the others into their grub menus.

So you can select to use the grub menu that you think looks the best. Even after installing, you can boot into one of the distros and re-install the boot-loader to use the grub system of that particular system.

See this link [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

After upgrading the kernel in a system, you need to boot into the system that manages grub and run
```
sudo update-grub
``` in order for grub to find it. The alternative is to make custom grub entries according to [How to have a custom Grub2 menu that is maintenance free]("http://ubuntuforums.org/showthread.php?t=2076205")
[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

### Post by fantab on 2013-06-11
The order does not matter, really.
You will need only one GRUB from any one Distro. So decide which its going to be and install it last.

A suggestion on partitions:
20-25 GB for '/' is plenty

Consider NOT using a separate /home, instead have a simple ext4 formatted partition to store and save your DATA. Conflicting version of applications, especially in Wheezy and Ubuntu can cause problems if you have shared /home. If you don't create a separate /home partition then your HOME folder will be created in your '/' partition. Later you can either manually mount the DATA partition when you need it or automount it using /etc/fstab at system startup. This way your DATA will be safe and you don't have to worry too much about backups. If you need to re-install or reformat you can do so easily by just wiping out the / partition clean.

My two cents...

---

### Post by newb85 on 2013-06-11
> **fantab said:**
> Consider NOT using a separate /home, instead have a simple ext4 formatted partition to store and save your DATA. Conflicting version of applications, especially in Wheezy and Ubuntu can cause problems if you have shared /home. If you don't create a separate /home partition then your HOME folder will be created in your '/' partition. Later you can either manually mount the DATA partition when you need it or automount it using /etc/fstab at system startup. This way your DATA will be safe and you don't have to worry too much about backups. If you need to re-install or reformat you can do so easily by just wiping out the / partition clean.

Agreed.  If you really want directories like ~/Documents, ~/Desktop, etc. to be unified on the three systems, my suggestion is that you replace them on the three systems with symlinks to ones you create on the Data partition.

There are hidden files in your home directory that different systems use that will conflict if you share a /home partition.  One example, Ubuntu and Mint (and possibly Wheezy) use the same hidden file to set the default DE to boot.

---

### Post by JohnyBeGood on 2013-06-11
> **fantab said:**
> The order does not matter, really.
You will need only one GRUB from any one Distro. So decide which its going to be and install it last.

A suggestion on partitions:
20-25 GB for '/' is plenty

Consider NOT using a separate /home, instead have a simple ext4 formatted partition to store and save your DATA. Conflicting version of applications, especially in Wheezy and Ubuntu can cause problems if you have shared /home. If you don't create a separate /home partition then your HOME folder will be created in your '/' partition. Later you can either manually mount the DATA partition when you need it or automount it using /etc/fstab at system startup. This way your DATA will be safe and you don't have to worry too much about backups. If you need to re-install or reformat you can do so easily by just wiping out the / partition clean.

My two cents...
Thanks to all who replied!
I will try to make seperate partition for Data. Would you guys recommend Gpart or ubuntu? I like where I can see whole HD and slide to adjust and create new partitions.

---

### Post by sudodus on 2013-06-11
Gparted is included in many linux install iso files, for example the Ubuntu desktop iso, so boot live from it and edit your partitions :-)

---

### Post by JohnyBeGood on 2013-06-12
> **sudodus said:**
> I think all these distros show respect to each other and include the others into their grub menus.

So you can select to use the grub menu that you think looks the best. Even after installing, you can boot into one of the distros and re-install the boot-loader to use the grub system of that particular system.

See this link [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

After upgrading the kernel in a system, you need to boot into the system that manages grub and run
```
sudo update-grub
``` in order for grub to find it. The alternative is to make custom grub entries according to [How to have a custom Grub2 menu that is maintenance free]("http://ubuntuforums.org/showthread.php?t=2076205")
[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]
Ok, using Gparted I created 1 Debian, 1 Ubuntu, 1 swap and 1 Data partition.
Installed Ubuntu first then Debian. While in Ubuntu issued:
```
sudo update-grub
```
But when computer boots I still get duplicates for Ubuntu and its Debian labeled GRUB ?



[IMG]http://i.imgur.com/xTmoKky.jpg[/IMG]

---

### Post by fantab on 2013-06-12
> **JohnyBeGood said:**
> Ok, using Gparted I created 1 Debian, 1 Ubuntu, 1 swap and 1 Data partition.
**Installed Ubuntu first then Debian**. While in Ubuntu issued:
```
sudo update-grub
```
But when computer boots I still get duplicates for Ubuntu and its Debian labeled GRUB ?


Since you installed DEBIAN last, in all likelihood, your GRUB is controlled by DEBIAN and NOT Ubuntu.
So the Grub should be updated from DEBIAN.

But if you installd DEBIAN last and did NOT install GRUB then what you did is correct. However from the screenshot it does appear that Debian Grub is in control.

---

### Post by newb85 on 2013-06-12
Last time I had multiple Linux systems installed, Grub was controlled by all the systems.  That is, any time a system did an update-grub (sometimes automatically due to updates), Grub was set according to the settings in that system and that system was moved to the top of the list.  I was dealing with four variants of Ubuntu, though, and not with Debian.  And I see that Debian is still at the top of the OP's list.

---

### Post by fantab on 2013-06-12
> **newb85 said:**
> Last time I had multiple Linux systems installed, Grub was controlled by all the systems.  That is, any time a system did an update-grub (sometimes automatically due to updates), Grub was set according to the settings in that system and that system was moved to the top of the list.  I was dealing with four variants of Ubuntu, though, and not with Debian.  And I see that Debian is still at the top of the OP's list.

Yes it happens when we have all Ubuntu variants (I am not really sure why though) but not when there is another Distro in the picture.
However, its not a good idea to have more than ONE Grub. ONE Grub is all that we need.

---


---
title: "Accidently set GRUB resolution too high, can't access OS"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by greenelf on 2011-12-19
I accidentally changed my GRUB resolution to high, and now my monitor is stuck at a "Out of Range" error.

Here are the commands I did to change it:
> sudo nano /etc/default/grub
GRUB-GFXMODE=1200x800
sudo update-grub

How can I fix this? I have a Live disk to boot from (I am running 11.10).

---

### Post by seawolf167 on 2011-12-19
If you hold the [SHIFT] key during POST to get your Grub menu, is it displayed? If so, you can edit the boot time options on the Grub menu itself by hitting the 'e' key. [See here ]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")for detailed information.

---

### Post by greenelf on 2011-12-19
> **seawolf167 said:**
> If you hold the [SHIFT] key during POST to get your Grub menu, is it displayed? If so, you can edit the boot time options on the Grub menu itself by hitting the 'e' key. [See here ]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")for detailed information.

As soon as I turn on my computer I get that error. I'll try rebooting in a minute!

---

### Post by oldfred on 2011-12-19
You could chroot into your system and reverse the commands you did.

You do not have to do the grub reinstall, just examples of chroot.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

From liveCD you can edit the grub.cfg file (the one we never edit directly). That would let you reboot and then make the corrections to reverse the changes permanently.

grub.cfg is read only and should not normally be edited, adjust location/path to where you mount it from liveCD:
sudo chattr -i /boot/grub/grub.cfg
gksu gedit +28 /boot/grub/grub.cfg
sudo nano /boot/grub/grub.cfg

or :
#Normally we do not directly edit grub.cfg. Edit from liveCD.
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

---


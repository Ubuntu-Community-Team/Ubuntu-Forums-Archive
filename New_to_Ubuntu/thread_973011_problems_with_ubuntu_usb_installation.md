---
title: "problems with ubuntu usb installation"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Ahmed28 on 2008-11-06
Hi, I installed Ubuntu to my 8gb UFD, I encountered several strange problem with it

1. If I restart Ubuntu, on the next boot, the mobo won't recognize the UFD anymore, and boot the HDD
Also in windows xp, the content isn't recognized at all, it keeps say error reading, but if I pulled the UFD and reinsert it, the windows recognize it, and the mobo recognized it too, but the boot setting prority in bios revert back to HDD

So everytime I reboot Ubuntu, I must pull and reinsert the UFD, and also change back the boot configuration in the bios, very tire some, is there a way around this ?

2. Just recently Ubuntu stop reading the ntfs partitions in my HDD, everytime I tried to access nffs partition, it give an error message "cannot mount volume, details : according to mtab, /dev/sda5 already mounted at /media/disk"

3. I installed wine and keepass, the installation process went smooth, but when I tried to run keepass, nothing happens at all


Can someone help ?




Thanks

---

### Post by zwygart on 2008-11-07
1. I have multi boot on my UFD and use it on different computers. As information, the most of the time I don't change the boot order in the BIOS. It changes back the next time you boot without UFD. During boot time I press everytime F8 or ESC (some computers is TAB, F4, F9, others F keys, etc.) I have to pay attention at boot time boot it works very good. This way you see if your mobo regognize your drive. It will display a list with all the bootable drives. 

If you have ext3 as the first partition on your UFD, XP cannot read it(expected if you use drivers). Also XP can only read the fist partition on a UFD. If you want use your UFD on windows, you have to make a FAT partition at the beginning of you drive, followed by ext for ubuntu.

Check at this [https://wiki.kubuntu.org/LiveUsbPendrivePersistent](https://wiki.kubuntu.org/LiveUsbPendrivePersistent), i don't found the ubuntu page.

2. Check at /media/disk
May be you have to edit /etc/fstab and remove the line with /dev/sda5. Change the name of the folder also. Instead of disk something else (windows).

sudo gedit /etc/fstab

3. I can't help you there. I don't know what keepass is and I don't use wine a lot yet.

---


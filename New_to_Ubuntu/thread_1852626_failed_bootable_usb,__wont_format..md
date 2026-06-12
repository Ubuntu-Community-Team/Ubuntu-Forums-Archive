---
title: "failed bootable usb,  wont format."
date: 2011-09-30
forum: New to Ubuntu
---

### Post by munkefrugt on 2011-09-30
Hi Im a newb to ubuntu. 
I tried to make a usb-pen into a "boot cd"
I followed these instructions found here: 

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

it said out of space, there was 8GB on the usb, so I ignored it.
now the files are read only. Im trying to format it but no luck. 
here is a few screen shots.

in advance, thanks a lot for your help:)

---

### Post by zvacet on 2011-09-30
Was USB empty and format properly?Maybe you can try that.Second option is to give moumt point /root to your files on USB ( that is warning on your first screenshot).

---

### Post by seawolf167 on 2011-09-30
Can you try again, but this time use GParted or the Windows partition editor to format (in Fat32) the flash drive before you attempt to build a bootable USB? Then re-follow the steps as outlined in your link or from the UNetbootin [homepage]("http://unetbootin.sourceforge.net/"). Note that this will cause you to lose all data on the drive so ensure you copy anything data off it that you want to keep.

---

### Post by munkefrugt on 2011-10-01
thanks for the quick replies:) I dont think I explained it all clear. my 1. priority is to make my usb pen work again.. 

Im trying with gparted(ubuntu) I press unmount but after/before I cant select format, when I right click on the usb on the disktop, I only have the options open, open in new window, eject, safly remove.Is there a way to unmount it through the terminal? does any body have any ideas? thanks again:)

---

### Post by Rex Bouwense on 2011-10-01
You should be able to format from a right click on the desktop icon and choose format or from Gparted by choosing the flash drive and then right clicking it.  Either will get you to the menu from which you can choose format.  I hope that answers your question.
I believe Safely remove device is the same as unmount.

---

### Post by seawolf167 on 2011-10-01
> **munkefrugt said:**
> Is there a way to unmount it through the terminal? does any body have any ideas? 

Like using the [*umount*]("https://help.ubuntu.com/community/Mount") command?

```
sudo umount /dev/sda
```

---

### Post by munkefrugt on 2011-10-01
wau Now it's all working. (but by try an error)I went to gparted-> selected the drive-> information-> magage flags, and by magic I can now press format:) wau it works:) thanks to you all so much for helping me whit this "simple" thing. hope you will get it back some other way..

Im sending some good energy your way:)

---

### Post by seawolf167 on 2011-10-01
Hehe, glad you got it working :)

---


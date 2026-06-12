---
title: "[SOLVED] Two installs, how do I remove one?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by bucktron on 2008-06-05
I have two installations of Ubuntu on my hard disk. I only use one and I need the storage that the unused ubuntu is taking up. To remove the second install, can i just delete the partition it is on (then reformat it for use) and update the grub bootlist? Is it that simple?
Thanks.

---

### Post by Duck2006 on 2008-06-05
> **bucktron said:**
> I have two installations of Ubuntu on my hard disk. I only use one and I need the storage that the unused ubuntu is taking up. To remove the second install, can i just delete the partition it is on (then reformat it for use) and update the grub bootlist? Is it that simple?
Thanks.

Yes, use gparted to format the partition (make sure you get the wrigh partition). Then edit your /boot/grub/menu.lst

---

### Post by bucktron on 2008-06-05
Yeah, getting the right one is vital!
I also have two linux-swap partitions - can I delete the one used by the defunct installation to free up that little bit more space? hda5 on the screen grab.
[IMG]http://farm4.static.flickr.com/3102/2553065619_6705872280.jpg[/IMG]
Thanks!

---

### Post by freduardo on 2008-06-05
Yeah the second swap can go as well.

In fact even if you were still dualbooting, you could have still used the same swap for both installs. Just so you'd know.

---

### Post by Duck2006 on 2008-06-05
If you know witch one is your swap partition for the install that you are using, yes. Look at your fstab of the install you want to keep and note witch one it is and del the other one. In the terminal type.

cat /etc/fstab

---


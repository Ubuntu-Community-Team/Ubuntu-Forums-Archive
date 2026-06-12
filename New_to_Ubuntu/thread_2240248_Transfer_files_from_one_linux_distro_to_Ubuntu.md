---
title: "Transfer files from one linux distro to Ubuntu"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by dadeda6060 on 2014-08-18
Is it possible if i can transfer my personal files from fedora to ubuntu? i no longer want to use fedora anymore and i was hoping that if i install ubuntu alongside fedora, i could transfer the files from fedora to ubuntu without using a usb or external HDD.

---

### Post by Irihapeti on 2014-08-18
Yes, you can.

BUT things can and do go wrong, so you're best off copying the files to a separate device before you do the install.

There are too many tales of woe where people lost everything because they didn't do a backup first.

---

### Post by yancek on 2014-08-18
If you have the drive space, it would be safer to install Ubuntu to another/new partition and find out if everything works as you want and then copy your personal files from Fedora to Ubuntu.  You can then just use the former fedora partition as a data partition.  Creating a separate partition for personal data eliminates this problem.

---

### Post by Tadaen_Sylvermane on 2014-08-19
If you haven't done it yet I highly suggest a data partition for your setup. In my case I have a 25gig root and rest of ssd 93gig I think mounted @ /media/data. I replace whatever folders that are generated in /home/$USER with links to the stuff in the /media/data partition. You can re-install to your hearts content without much worry as long as you don't touch that partition in the disk setup of your installer. Manually add it to the /etc/fstab and away you go. Also beats the idea of a shared /home because it doesn't hang on to configs and such which can conflict from time to time causing issues.

---


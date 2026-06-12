---
title: "Grub Timeout Won't Change"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Timey Wimey on 2013-03-23
I recently installed Ubuntu 12.04 LTS on my computer so now it dual boots with Window 7.  I am trying to get rid of the timer so that it stays at the grub menu screen indefinitely.  I have tried this method:

```
sudo gedit /etc/default/grub
```

Then I change the```
 GRUB_TIMEOUT=-1
``` Then, I run ```
sudo update-grub
```

However, the timer still comes on and goes for 30 seconds.  I have tried change the timeout to 60 seconds and it still only runs for 30 seconds.  How could I get rid of the timer or at the very least make it last for a really long time?

---

### Post by grahammechanical on 2013-03-23
I have found that sometimes running ```
sudo update-grub
``` is not sufficient. You may also need to run ```
sudo grub-install /dev/sda
``` Assuming that sda is the hard disk that has Grub installed in its MBR.

Regards

---

### Post by Timey Wimey on 2013-03-23
I just tried that and it made no difference.  Is there maybe somewhere I could change that default setting of 30 seconds and do it that way?

---

### Post by deadflowr on 2013-03-23
deleted

Edit: Reading further, you could try uncommenting/commenting (#) the GRUB_TIMEOUT line.

try running  sudo nano /etc/default/grub, instead of sudo gedit.

You can look and see if the changes happened by looking at the grub.cfg file in boot/grub folder.
Look at the end of the first section 00_header.

---


---
title: "The Disk Drive for /Windows in not Ready - Fstab?"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by Quarkrad on 2015-06-01
Just built a clean dual boot uefi machine with win7 and Ubuntu 14.04.  All was well but suddenly I'm getting the following message  **The disk drive for /windows is not ready yet or not present. Continue to wait or press S** ..........  just before Ubuntu launches its Desktop.  I've had this sort of message before - it has always been a problem in fstab.  At the grub screen I can boot into win7 or Ubuntu without any problem and when in Ubuntu I can navigate the win7 folders/files via nautilus.  Operationally the pc is working fine - but I'm a bit perplex about the disk drive message.

---

### Post by cariboo on 2015-06-01
Have you run chkdsk in Windows?

---

### Post by leunam12 on 2015-06-02
I suggest you post the results of lsblk and also your fstab. Also try this: Boot to Windows and the press WindowsKEY+R and type ```
shutdown -r -f -t 00
``` press ENTER and the computer will restart. Choose Ubuntu and see if you get the message.

---

### Post by leunam12 on 2015-06-02
Also post the results of blkid

---

### Post by Quarkrad on 2015-06-04
Sorry for the slow response - I had to do a partial rebuild.  Yes I had done a chkdsk but my problem was an erroneous entry in fstab.  I have now sorted and thank you for the terminal commands above - there is a never ending list of very useful commands.

---


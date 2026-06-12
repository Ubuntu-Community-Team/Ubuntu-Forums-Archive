---
title: "getting ubuntu in boot menu"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by sachin0091 on 2013-02-06
Actually i had xp and ubuntu in my machine
i reinstalled xp now i cant see ubuntu in operating selection menu..
can i get back it..???
if S may i know how to get it back..

---

### Post by arpanaut on 2013-02-06
You just need to reinstall grub.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That is if by reinstalling windows you did not overwrite your entire disk then you will need to reinstall Ubuntu.
Then put your data back into your /home folder, You did back up your data before you reinstalled?

If it was a wubi install then Ubuntu is gone: again you will need to reinstall.

---

### Post by sachin0091 on 2013-02-06
'm getting a grub menu in a black screan.. jus like
GRUB >
wat i need to do now to get my ubuntu back

---

### Post by arpanaut on 2013-02-06
How did you install Ubuntu in the first place? wubi, or full install with separate partitioning?
How did you go about reinstalling WinXP?  
If you have a live CD/DVD/usb, boot that up select "Try" when you get to the desktop open a terminal and copy and paste ```
sudo fdisk -lu
```into the terminal hit enter twice then copy and paste the resulting output back here.

If you still have the ubuntu partitions on your disk use the instructions from the first link above and restore grub to your mbr, if you do not have any partitions but the windows partitions then you will need to reinstall Ubuntu.

Additional information for dealing with grub prompt:
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

### Post by srekcahrai on 2013-02-06
[Grub repair]("http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows")

---

### Post by sachin0091 on 2013-02-06
have installed it saperately

---


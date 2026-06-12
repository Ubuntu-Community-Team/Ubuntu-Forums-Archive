---
title: "Strange problems after loading"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by rayeacott on 2012-10-05
[FONT=Times New Roman][SIZE=3]Hi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I loaded version 11.10 from a CD ( I have down this many time before ) and then tried to upgrade to 12.04 via the Software Updater[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Then I downloaded 12.04.1 from the site burnt it to a CD – loaded it with updates on[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Both were Ok but when I restarted the system booted to a 'grub>' prompt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please can you help?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks[/SIZE][/FONT]

---

### Post by Bashing-om on 2012-10-05
rayeacott; Hi !

It appears grub is not installed as you wish.
These links will get you squared away:
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Not knowing your system configuration, direct advise is skimpy ! But, I expect that all that is needed is to install grub to sda.

You are not UEFI enabled are you ? (different procedure) 
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by rayeacott on 2012-10-10
Hi
 
Sorry about not coming back for several days but I am still having problems
 
My system is a Pentiun 1.5 GHz with 768 MB of memory
250 GB IDE drive
 
I opened a terminal window and entered the following:
 
sudo mount /dev/sda /mnt - reply  dev/sda already mounted or /mnt busy
 
Tried to umount (sudo umount dev/sda /mnt )
 reply   umount: dev/sda not mounted and umount: /mnt not mounted
 
Also what is UEFI
 
Regards
 
Ray

---

### Post by YannBuntu on 2012-10-10
Hello
Please indicate your Boot-Info URL. This will give us informations to help you.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---


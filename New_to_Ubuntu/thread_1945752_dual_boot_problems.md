---
title: "dual boot problems"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by boregard on 2012-03-23
hi all, just installed OO 11.10 64 bit on a gateway sx2855 desktop with win 7. when i i start computer it doesn't give me an option to choose 11.10 just goes straight to win 7. i dual booted 11.10 on a acer laptop with win vista and didn't have this problem. any suggestions how fix this problem? thanks for any help.

---

### Post by NikTh on 2012-03-23
Hello , 
i just hope that you didn't erase windows during installation . 
Open a terminal and give the output of command 
```
sudo fdisk -l
```

---

### Post by MG&amp;TL on 2012-03-23
Boot a live CD, then post a screenshot of the disk utility for your disk, and the output of:

```
sudo fdisk -l
```

---

### Post by boregard on 2012-03-23
i will try suggestions and post outcome when done .btw windows is still working. thanks

---

### Post by boregard on 2012-03-23
here is info requested below. appreciate your help.

---

### Post by NikTh on 2012-03-23
Ok. I think windows are there,So get in to Ubuntu and open a terminal ,then run
```
sudo update-grub
gedit /boot/grub/grub.cfg
``` and give the results of second command. Do not take screenshot , just copy-paste them here , but inside code tags. ( select the text and hit # )

---

### Post by oldfred on 2012-03-23
You need to install the grub2 boot loader to the MBR of sda. Your Linux partition is sda5, so that part is confirmed.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by boregard on 2012-03-23
okay, got back in win7 and browsed through programs & features and  noticed wubi installer wasn't listed. i put 11.10 disk back in and found  two windows, in included screen shots. in the win7.png the window is  asking for passWd. for new acct. not sure what enter my win passW. OR  PASSw. I chose for 11.10. btw i selected wrong prefix i am installing  ubuntu 11.10 not lubuntu. in meantime i will try the above suggestions.

---

### Post by boregard on 2012-03-23
here is output from trying to update grub```
 ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 
```

---

### Post by oldfred on 2012-03-23
You cannot just run update grub from the liveCD.
This is liveCD:
 ubuntu@ubuntu
See previous post on mount of Windows partition and install of grub2's boot loader to the MBR.

---

### Post by boregard on 2012-03-23
> **oldfred said:**
> You cannot just run update grub from the liveCD.
This is liveCD:
 ubuntu@ubuntu
See previous post on mount of Windows partition and install of grub2's boot loader to the MBR.okay, out of what is listed in this screen shot what should i mount?

---

### Post by oldfred on 2012-03-23
See post #7.:)

---

### Post by boregard on 2012-03-23
whew, finally got it fixed following instructions from this link [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  from post #7. a very grateful THANKS to everyone for all your help! i am now a happy camper. best regards

---


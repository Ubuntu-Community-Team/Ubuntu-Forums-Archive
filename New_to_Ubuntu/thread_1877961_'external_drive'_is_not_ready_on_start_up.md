---
title: "'external drive' is not ready on start up"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by juniord2016 on 2011-11-09
Dear Readers
     What my problem is when I switch on my laptop, it takes time to load. After that it says drive Freecom HDD is not ready. Freecom is my external hard drive, why does it appear to be part of the computer?? an option says press S to skip so I always did. After that I just can't install things properly. Always there's an error that says 'failed to insall or remove package. Now what in the wide world does that mean???????  I'm going to tell you a mistake before this I did; Imounted the Freecom drive on the Desktop. Please help me with this. Thank you in advance if you leave a reply

---

### Post by Mark_in_Hollywood on 2011-11-12
Before I go any further, I must ask: 

1. - Do you have your data backed up?

2. - Do you have a LiveCD with the current version of the operating system you are using on your laptop?

If "NO", please get the INSTALL/LIVECD at:

[http://cdimage.ubuntu.com/releases/11.10/release/]("http://cdimage.ubuntu.com/releases/11.10/release/")

After you have downloaded it, please check the checksum and if you have a match on those checksum numbers, come back here and let me know that. We are going to be booting to the LiveCD and using GParted to see what is what. Please do not do this, if you are unfamiliar with GParted. Come back to the forum and someone will guide you through the few steps necessary to see what your drives are doing.

Also, with the external drive powered up and plugged into the laptop, cut and pasted the output of:

sudo fdisk -l 

that -l is the letter: lowercase L.

---

### Post by juniord2016 on 2011-11-23
Thank you so much for the reply. Now my only problem is the Drive on boot. Please tell me why do you think that happened when Freecom is an extrnal hard drive. After booting, nothing happens to be wrong. The installation problem seems to be a different problem. I'm burning the CD. Oh! and could you please tell me why in gnome session, where I want to change themes with 'advance settings' , it loads a blank desktop. The desktop only has my desktop background there and a wireless notification. It of course disappears after a few seconds. In a rare chance, I see my dock(mac-like) not unity on the screen which appears w hite rectangular as if it's lagging. All I could do is press ctrl alt del to log out. I can't even open the terminal with the key short cut. Thank you again for your help instructions and I apologize for the topic change where I'm not supposed to. Thank you

     Regards
     Junior

---

### Post by juniord2016 on 2011-11-23
Sorry again for the topic change

---

### Post by juniord2016 on 2011-11-23
Hello, here it is when the Freecom is plugged in. Without it, it's different. I seem to understand the problem but not the solution.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000efda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484343807   242170880   83  Linux
/dev/sda2       484345854   488396799     2025473    5  Extended
/dev/sda5       484345856   488396799     2025472   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4a0a2af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   234436544   117218241    7  HPFS/NTFS/exFAT 
```

---

### Post by Mark Phelps on 2011-11-23
Don't know how you mounted the Freecom drive initially, but however you did it, it's now probably part of your /etc/fstab file -- which will try to remount it every time you boot.

To fix that, you need to do the following:
1) Open a terminal
2) Enter "gkduso gedit /etc/fstab
3) Look through the file for the lines that mount your Freecom drive
4) Remove those two lines
5) Save the file
6) Reboot -- should not try to mount it anymore

If you're unsure of which lines to remove, then cut and paste the contents of the /etc/fstab back here and we'll tell you which lines.

Also, for better response in the forums, don't start adding replies with different problems; instead, start a new thread for each new problem.

---

### Post by juniord2016 on 2011-11-23
Thank you so much for the solution. Now everything is OK and next time I will not post many problems in one thread. Thank you for the advise

---


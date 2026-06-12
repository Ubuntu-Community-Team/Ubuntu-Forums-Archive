---
title: "External USB 3 Disk"
date: 2019-02-16
forum: New to Ubuntu
---

### Post by joestokesf125 on 2019-02-16
I have plugged in the USB cables to both the computer and the USB drive, also plugged the drive into a mains power socket and switched. The The on Button the external drive box was pressed and the blue light came, showing that the drive had power. Problem is there appears to my now sign of the drive on my computer monitor or any where else can somebody assist in the correct method of mounting the drive. All help great fully received.

---

### Post by Holger_Gehrke on 2019-02-16
Normally a USB hard drive that gets connected to a running Ubuntu Desktop system will get recognized and mounted and a file manager would start. Since this isn't happening, you should try to see what is wrong. Connect the drive to both the computer and power but don't switch it on yet. Open a terminal and enter 'journalctl -f'. Now switch the drive on. You should get several lines of messages. If their meaning is unclear to you, post them here and we'll see what's what.

Holger

PS: journalctl will just keep on running. To stop it press 'ctrl-c'.

---

### Post by joestokesf125 on 2019-02-18
Hi Holger  thank you for your reply. I did as you instructed but am unable to paste and send the terminal output because the file is to big apparently. Would the fact I have plugged the drive into a USB 3 port explain the problem? Joe

---

### Post by nselby on 2019-02-18
I don't know if you are saying that there is stuff on that drive already that you want to keep, but if it is a new drive, let me say this: I just bought a USB3 external drive and connected it and I couldn't mount it because of the filesystem on it; since it was brand new, I used the disks function to format the new drive, and it then mounted and worked just fine.

---

### Post by joestokesf125 on 2019-02-19
Thank you nselby, I switched to the USB 2 ports and everything is OK. Do you know anything about using Wine? Thank you. Joe

---

### Post by col48 on 2019-02-20
@nselby
It may help others if you tell us what was the filesystem on the drive when you purchased it (if you could identify it).

---

### Post by joestokesf125 on 2019-02-20
The file system was NTFS. It was attached to a Windows laptop for backup before.

---

### Post by nselby on 2019-02-20
@col48 the disk was NTFS out of the box. For some reason Ubuntu hated it.

---

### Post by mastablasta on 2019-02-21
eh looks like the yhave some strange formatting lately, despite they claim otherwise.

I could not load new NTFS drive from WD on widnows XP. i then reformated it and it could still not load on WInXP. it loads just fine now on Win7, win10 and linux. before it could only load on win10.

---

### Post by oldrocker99 on 2019-02-21
Do remember that USB3 cables can go bad, even if they're stationary. I was doing a write operation on a USB3 external drive, and suddenly, the system could not mount the drive. Installing a new cable did the trick.

Why this happens is a mystery to me:confused:.

---

### Post by mastablasta on 2019-02-22
yeah in my case it just stopped working. eventhough it was kept safe in the original box. it will get a hole soon. changing the cable didn't have any effect.

---


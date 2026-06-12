---
title: "Which Hard Drive driver??"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by PegM_4 on 2008-08-18
After being unable to use LiveCD to install Ubuntu, I downloaded the Alternate version and tried with it.  I ran into a problem when it wanted me to chose a HD driver.  My HD is a Western Digital model # WD1200BB-98DWA0.  Can anyone tell me which driver I need?

Thanks
Peg

---

### Post by halitech on 2008-08-18
it shouldn't need any driver unless you are using RAID on your drive.

why were you not able to use the live cd?

---

### Post by PegM_4 on 2008-08-18
It, for some reason, wouldn't recognize my drives.  From other posts I found, I should have had the option to partition my drives, but I never had that option.  It would take me to the Prepare partitions screen, then give me no options.  I couldn't click on anything or move forward.  

I tried removing drives so there were only 2 as I had read that could be a problem.  I then used Paragon Partition Magic and formated my D: drive to Ext2/3 thinking that might fix it, but with no luck.  I finally decided to try the Alternate ISO, as some people seemed to think it would be the answer.

From the little I have done with the LiveCD, I think I might really like Ubuntu, but am getting very frustrated with nothing seeming to work in my quest to install it.:(

---

### Post by Bradtek on 2008-08-18
Try checking the if the  IDE cable is seated properly / stuffed

I had this problem recently when trying to install Xubuntu on an old PC.
Even though I could partition the drive with Parted Magic Live CD
Xubuntu alternate CD failed to see the hard drive and prompted for
a driver.

The ended up replacing the IDE cable with a better one I had lying around
and  my next attempt at installing went fine although very slow on the old Pentium 200 MMX.

---

### Post by PegM_4 on 2008-08-19
No, I checked it.  That wasn't the problem.

---

### Post by tarps87 on 2008-08-19
What happens with only one hard drive connected and set to master? Is it a IDE hard drive?

---

### Post by PegM_4 on 2008-08-19
> **tarps87 said:**
> What happens with only one hard drive connected and set to master? Is it a IDE hard drive?

I  only have 1 hard drive.  It had been partitioned into 2 partitions, but now seems to be totally deleted since I used Gparted LiveCD.  I was told that Ubuntu would then partition it and install, but that still doesn't seem happen.

And, yes, it is an IDE hard drive that is set to master.  Well, I am assuming that as it has not been changed from the factory setting.  Is that a safe assumption, or do I need to take it out and look at it?

---

### Post by OldTimeTech on 2008-08-19
many times factory setting is cable select...so yes checking might be a good option.

---

### Post by tarps87 on 2008-08-19
As long as you don't void any warranty by looking inside it won't hurt to look. It usually is only a problem if it is set as a slave, when you have only one drive.

Edit: Also try:
```

sudo fdisk -l
```

---

### Post by PegM_4 on 2008-08-19
> **tarps87 said:**
> As long as you don't void any warranty by looking inside it won't hurt to look. It usually is only a problem if it is set as a slave, when you have only one drive.

Edit: Also try:
```

sudo fdisk -l
```

No luck.  It is already set to "master" setting.  I'm not sure what to do with sudo fdisk -1.  I know a little bit about computers, but definitely not a lot.:lolflag:

Peg

---

### Post by halitech on 2008-08-19
open a terminal (Applications - accessories - terminal) and type in
```
sudo fdisk -l (lower case L, not the number 1)
```

---

### Post by PegM_4 on 2008-08-19
Would my system have anything to do with it?  It is a SONY w/ 1GB RAM, Intel Pentium 4HT, 2800 MHz, AMI BIOS Type.  I don't know of any more info that might influence it.:confused:

Peg

---


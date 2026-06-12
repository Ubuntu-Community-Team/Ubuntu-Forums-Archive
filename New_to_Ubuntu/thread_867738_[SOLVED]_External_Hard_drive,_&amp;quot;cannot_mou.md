---
title: "[SOLVED] External Hard drive, &amp;quot;cannot mount volume&amp;quot;?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by germanix on 2008-07-23
I have said goodbye to Vista and have welcomed Ubuntu into my home. Ubuntu is now my one and only OS. I would probably count as one of the most dumbest users of all time, but everything seems to run just fine. I had no clue what I was doing, just inserted the Ubuntu live cd, chose the option "use the whole hard drive", then set back and enjoyed as Ubuntu wiped Vista from my machine.
My only small problem now is that I have a external hard drive which I used to back-up my files under Vista. I would now like, if possible to extract some of my personal files (mostly word documents) from this external drive and "import it" or copy it into Ububtu. When that is done, I then wish to use the ext. hard drive for back-ups with Ubuntu. I assume it needs somehow to be formatted anew?
Ubuntu recognizes the drive but cannot gain access. It tells me "cannot mount volume".
If anyone out there in thew Ubuntu community would be so kind as to explain to this old fool how to accomplice this, you will make my day.

---

### Post by vanadium on 2008-07-23
Your external drive probably is an ntfs volume that is not "clean", i.e. not properly disconnected from a Windows system. By default, Ubuntu will not automount such a drive.

I understand you do not have Windows available anymore. Otherwise, the easiest way to cure the problem would be to connect the drive to a Windows machine, eventually have it checked there and then disconnect it properly, i.e. using the "Safely remove hardware" icon in the tray.

Alternatively, you could "force mount" it to copy the files off the drive. This would be perfectly acceptable since you plan to reformat the drive afterwards anyway.

Hand-on instructions are easiest using the command line. For that, I would need to know the device name of your ntfs drive. You may want to  post the output here of the following command (make sure the drive is connected to the sytem and powered on)

```

sudo fdisk -l

```

---

### Post by germanix on 2008-07-23
The Device name of my ntfs drive is: iomega Ultra Hard Drive. I still have a laptop with xp on. I will try using that first. If not I will force mount. Thank you.

---

### Post by germanix on 2008-07-23
I used the xp machine as you suggested. Using the "safely remove hardware" did not realy work. Windows said the drive cannot be removed at this time. So I quess the force mount option is the only one left. Please explain how I should proceed.

---

### Post by germanix on 2008-07-23
Update. I now got windows to do what I wanted. Ubuntu now recognizes the iomega drive. Does this now mean that I can bach-up to this drive without further to do? or do I still need to format this drive new for Ubuntu?

---

### Post by halitech on 2008-07-23
if you would like to keep it so you can take the drive to other places where friends may not have linux, I would keep it as NTFS or Fat32 (whichever it is currently). If you don't plan on taking it anywhere, use Gparted to format the drive

---

### Post by germanix on 2008-07-23
I thank you all for the friendly help.

---


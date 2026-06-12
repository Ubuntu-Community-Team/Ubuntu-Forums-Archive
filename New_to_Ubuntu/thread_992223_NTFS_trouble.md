---
title: "NTFS trouble"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Bauro on 2008-11-24
hello all..

Let me start out by saying that i have just installed Ubuntu 3 days ago, and i have never in my life touched linux before.. 

I have already searched the forum for my problem, but i just cant seem to find an answer.

I have an external HDD running NTFS filesystem, and i want to "mount" it on ubuntu, but it wornt allow me. From what ive read, i think i need a driver called "NTFS-3G" (correct me if im wrong).
- I have downloaded the driver but how do i install it? i just got a folder with a lot of files, and i have no clue which is the ".exe" file (if thats the file im looking for?!? >.<).

---

### Post by taurus on 2008-11-24
The last time you used your external harddrive with a windows, did you just unplug it or did you go through the safely remove hardware option (bottom right corner) before you unplugged the drive?

Otherwise, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

p.s.  Which release are you running now?

---

### Post by Bauro on 2008-11-24
wow that was fast response.. im running 8.10 Ubuntu (if you mean NTFS-3G driver then its 1.5012 - but im not sure ive even installed it)

and i just unplugged it..

---

### Post by pfdevil on 2008-11-24
Hey, what is the error your getting? I've realized that my ntfs disk, sometimes if not "safely removed" it malfunctions in Ubuntu.

The best way to install NTFS-3G is: System->Administrations->Synaptic Package Manager
Do a search for NTFS, if ntfs-3g is not installed (it should be selected) select it and click apply changes. This is the preferred way to install programs in Ubuntu.

---

### Post by Bauro on 2008-11-24
I wrote the command in the terminal, and the HDD appeared under "Places", but i still cant mount it.

The error just says "Unable to mount Simpledrive"

HDD is called Simpledrive..

---

### Post by Bauro on 2008-11-24
NTFS-3G driver is not under Package manager, only a driver called "ntfsprogs" - is it the same/just as good?

---

### Post by taurus on 2008-11-24
If you don't "safely remove" your external harddrive, you need to use the force option in Ubuntu to mount it.  So, you have two options.

1.  Boot into windows and plug in that external harddrive.  Then, click the little icon at the bottom right to safely remove hardware to unmount it first before you unplug it.

2.  Use the force option to mount your external harddrive in Ubuntu but you cannot keep using the force option because eventually, force option will not work.

So, what is the output of this command again from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by pfdevil on 2008-11-24
I'm sure that it must be there. Just search for ntfs, then scroll carefully and search for ntfs-3g.

But first safely remove your hdd from windows

---

### Post by pfdevil on 2008-11-24
I'm sure that it must be there. Just search for ntfs, then scroll carefully and search for ntfs-3g.

But first safely remove your hdd from windows.

---

### Post by Bauro on 2008-11-24
ive installed the ntfs-3g driver via the package manager, but the same error appears "Cannot mount SimpleDrive"..

I have tried to unplug it, reboot Ubuntu, replug simpledrive, and then force mount..

---

### Post by SunnyRabbiera on 2008-11-24
Hmm, is this a device you mounted in windows?
Do you still have a dual boot set up?
Do you even have a windows machine?
I am just asking as sometimes I have seen XP/Vista hold devices hostage if not mounted/ unmounted right

---

### Post by Bauro on 2008-11-24
Okay it works now..

I plugged the HDD into my windows desktop and saftly removed it, and that did the trick..

Thanks for the quick and helpfull responses everyone :)

@SunnyRabbiera - i run Ubuntu 8.10 on my notebook and windows XP on my desktop computer.

---

### Post by SunnyRabbiera on 2008-11-24
No problem.
I figured that was the issue, windows leaves a log file on your external drive until you safely remove it.

---


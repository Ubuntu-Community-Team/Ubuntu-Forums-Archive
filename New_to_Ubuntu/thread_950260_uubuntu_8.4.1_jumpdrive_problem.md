---
title: "uubuntu 8.4.1 jumpdrive problem"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by sniktawekim on 2008-10-17
i am using the 8.4.1 ubuntu, also known as the eee ubuntu.
every time i insert a jumpdrive it says it cannot mount because i am not a super user.
i went to the user groups and changed my user permissions to be able to access removable hardware, and it still gives the same message.

this type of ubuntu does not let me log into the root account, so i can only sudo

i would like to be able to always access my jumpdrive as my main account without having to open a terminal every time.

at the moment, i cannot access the jumpdrive at all

---

### Post by ezramorris on 2008-10-17
> **sniktawekim said:**
> i am using the 8.4.1 ubuntu, also known as the eee ubuntu.
every time i insert a jumpdrive it says it cannot mount because i am not a super user.
i went to the user groups and changed my user permissions to be able to access removable hardware, and it still gives the same message.

this type of ubuntu does not let me log into the root account, so i can only sudo

i would like to be able to always access my jumpdrive as my main account without having to open a terminal every time.

at the moment, i cannot access the jumpdrive at all

What file system is it? If it FAT16 or FAT32, it should work automatically.

---

### Post by sniktawekim on 2008-10-18
> **ezramorris said:**
> What file system is it? If it FAT16 or FAT32, it should work automatically.

im not sure, it "loads" automatically, but what happens is it recognizes it, and then tells me i dont have the permissions to access it. it always gives me the error, unable to mount, must be a super user

i have tried multiple jumpdrives, they all came up the same

---

### Post by ezramorris on 2008-10-18
> **sniktawekim said:**
> im not sure, it "loads" automatically, but what happens is it recognizes it, and then tells me i dont have the permissions to access it. it always gives me the error, unable to mount, must be a super user

i have tried multiple jumpdrives, they all came up the same

Can you post your output from
```
sudo blkid
```
Thanks.

---

### Post by sniktawekim on 2008-10-18
> **ezramorris said:**
> Can you post your output from
```
sudo blkid
```
Thanks.


/dev/sda1: UUID="9c60b76b-c17f-4f7b-ad99-0a0a00a1e9b8" TYPE="ext3"
/dev/sda2: TYPE="swap" UUID="242066d0-9670-4b17-9ed9-0f539de38368"
/dev/sdb1: UUID="dbaca56e-ad54-402b-b33d-50544cb0ea43" TYPE="ext3"
/dev/sdc1: LABEL="MIKEWATKINS" UUID="8C42-BF90" TYPE="vfat" SEC_TYPE="msdos"

---

### Post by GregA on 2008-10-18
IF this is a recent problem, perhaps this thread will help.  

[http://ubuntuforums.org/showthread.php?t=951256](http://ubuntuforums.org/showthread.php?t=951256)

---

### Post by sniktawekim on 2008-10-19
the difference is that his system doesnt recognize a usb when he plugs it in after it is on.
mine does, it just wont permit me to mount it.

also, the solution here seems to be boot under a different OS.
i dont like that solution, and am hoping for a different one.

---

### Post by ezramorris on 2008-10-19
> **sniktawekim said:**
> the difference is that his system doesnt recognize a usb when he plugs it in after it is on.
mine does, it just wont permit me to mount it.

also, the solution here seems to be boot under a different OS.
i dont like that solution, and am hoping for a different one.

It was a different kernel, not a different OS. When you boot up, you may (or may not) get a list of a number of items, which will look similar but with different numbers. If you get this, try 2.6.24-19-generic rather than 2.6.24-21-generic.

---

### Post by rustutzman on 2008-10-19
Try opening nautilus as root and see if you can open the drive froom there. 

gksudo nautilus 

Was the drive properly shut down before removal the last time it was used?

Russ

---

### Post by sniktawekim on 2008-10-19
> **rustutzman said:**
> Try opening nautilus as root and see if you can open the drive froom there. 

gksudo nautilus 

Was the drive properly shut down before removal the last time it was used?

Russ

it wont let me open from there;




i believe it was safely removed last time, i also have been using different jumpdrives in different slots, and none work

---

### Post by rustutzman on 2008-10-19
I know this is very MSoft like but have you tried rebooting with the USB drive in place? I know that has worked for me a couple of times to gain access to a drive that was being troublesome.

Russ

---

### Post by oskar2000 on 2008-10-21
comment out the cd-rom line in fstab:

sudo gedit /etc/fstab

put a # at the beginning of the line that conains "blah...cdrom... blah"

save

and just plug it in again.

---

### Post by ezramorris on 2008-10-21
> **oskar2000 said:**
> comment out the cd-rom line in fstab:

sudo gedit /etc/fstab

put a # at the beginning of the line that conains "blah...cdrom... blah"

save

and just plug it in again.

How is this relevant? It is nothing to do with the CD-ROM.

---

### Post by sniktawekim on 2008-10-21
> **ezramorris said:**
> How is this relevant? It is nothing to do with the CD-ROM.

believe it or not, that fixed it....

---

### Post by ezramorris on 2008-10-22
> **sniktawekim said:**
> believe it or not, that fixed it....

Please enlighten me, someone.

---

### Post by oskar2000 on 2008-10-22
Stupid device naming conventions.
With IDE drives it was no problem to just assign the drives according to their place on the connector: hda, hdb, hdc...
With plug and play stuff they just get whatever isn't in use at the moment. Since the eee pc has no cd rom drive, sdc is always available, so hal will give the sd card sdc, looks into fstab, sees that sdc should be mounted as iso9660 to /media/cdrom, fails and doesn't know what else to do with it.

I have no idea why they don't just switch to UUID entirely.

---

### Post by ezramorris on 2008-10-22
Hmm, thanks for that, interesting.

> **oskar2000 said:**
> I have no idea why they don't just switch to UUID entirely.

Would seem sensible, especially as they have all the hard disk partitions as that anyway.

---


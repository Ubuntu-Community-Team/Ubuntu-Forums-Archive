---
title: "Cant mount ANY USB!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by RealG187 on 2008-09-25
I rely heavily on USB hard drives for file storage (just installed Ubuntu on the "family PC" and need to put my files away before the next user goes back onto windows.

I cannot mount any USB Storage, not even my Kingston 1 GB USB flash drive.

it says

> 
**Cannot mount Volume**
Invalid mount option when attempting to mount the volume 'FIRELITE'.
for my Verbatim Firelite USB Hard drive (volume label "Firelite")

and 

> 
**Cannot mount Volume**
Invalid mount option when attempting to mount the volume.

for my Verbatim USB drive (not sure if it has a volume label or nor)

---

### Post by RealG187 on 2008-09-25
I forgot to mention I installed it using a "Live USB Stick" (USB stick made from a Live CD), I used [UNetbootin]("https://help.ubuntu.com/community/Installation/FromUSBStick") to make the stick I booted off to install.

So I guess the USB was mounted to /media/cdrom0

I found this out by running GPartED to view the partition and it showed the mount point. When I right-clicked and choose "Mount To" <Submenu> "/media/cdrom0" it mounted. I edited my /etc/fstab for Firelite, and still get a similar problem.

Every USB Storage says that message and I cant access it until I use GPartED to mount, now I choose "Mount To" <Submenu> "/media/firelite"

The problem is **all** my USB drives are mounted as Firelite. I have not tried using more than one USB device at a time or a different port (there is only one free)

---

### Post by RequinB4 on 2008-09-25
can you paste.ubuntu.com your fstab and post the link here>

---

### Post by RealG187 on 2008-09-26
> **RequinB4 said:**
> can you paste.ubuntu.com your fstab and post the link here>

I am confused, do you want me to add ubuntu.com to my fstab and put it here?

---

### Post by EvilDaemon on 2008-09-26
No, do this.

go into the terminal and run 'fstab' or 'sudo fstab'.

Now highlight everything, and right-click "copy".

Go to [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and paste everything into there. Then it'll bring you a new page, so copy the URL, and post it back here.

---

### Post by RealG187 on 2008-09-27
Oh, there is a "pastebin" where info can be stored. I guess that's easier than making posts with lots of text?

When I type fstab, I get nothing

> mpg@Sherpat3md:~$ fstab
bash: fstab: command not found
mpg@Sherpat3md:~$ sudo fstab
[sudo] password for mpg: 
sudo: fstab: command not found
mpg@Sherpat3md:~$ 

I think you mean my /etc/fstab? If so, then [here]("http://paste.ubuntu.com/51463/")

---

### Post by dwp0980 on 2008-09-28
Delete the line below from your /etc/fstab and it should all work fine.  I had this problem and I installed from a USB using Unetbootin.

```
/dev/sdb1       /media/FIRELITE   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by RealG187 on 2008-12-30
> **dwp0980 said:**
> Delete the line below from your /etc/fstab and it should all work fine.  I had this problem and I installed from a USB using Unetbootin.

```
/dev/sdb1       /media/FIRELITE   udf,iso9660 user,noauto,exec,utf8 0       0
```

It worked on that computer, and my new Laptop I installed Ubuntu on using Unetbootin.

Marking thread as solved and giving thanks.


NOTICE: I can't give thanks, I don't see the button

---


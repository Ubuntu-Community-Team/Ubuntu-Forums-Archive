---
title: "WUBI  sh:grub &gt; desperation"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by Avinaash on 2012-06-27
I'm using Windows7 and Ubuntu 12.04 LTS. When I choose Windows from boot loader menu, its booting and launching windows7 but when I choose Ubuntu, GNU GRUB command prompt is launched instead of GUI. I tried some of the commands from the forum posts. The results are like...

**ls**
[I](memdesk) (loop0) (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)
[/I]
all X & Y in **ls (hdX,Y)** resulted in *error: unknown file system* except **ls hd0,msdos1)**.
but **ls (hd0,msdos1)/boot** is resulting in *error: file not found* so, I don't know about vmlinuz or initrd

I then tried code from this post and the results are like...

**insmod ntfs**
-> nothing happend

**set root (hd0,msdos1)**
-> nothing happend

**loopback loop0 /ubuntu/disks/root.disk**
-> error: file not found

But I have the *folder **ubuntu*** and *file **root.disk(0KB)*** on my C drive.

Please help me out! Thanks!

---

### Post by Avinaash on 2012-06-27
I'm using Windows7 and Ubuntu 12.04 LTS. When I choose Windows from boot loader menu, its booting and launching windows7 but when I choose Ubuntu, GNU GRUB command prompt is launched instead of GUI. I tried some of the commands from the forum posts. The results are like...

**ls**
[I](memdesk) (loop0) (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)
[/I]
all X & Y in **ls (hdX,Y)** resulted in *error: unknown file system* except **ls hd0,msdos1)**.
but **ls (hd0,msdos1)/boot** is resulting in *error: file not found* so, I don't know about vmlinuz or initrd

I then tried code from this post and the results are like...

**insmod ntfs**
-> nothing happend

**set root (hd0,msdos1)**
-> nothing happend

**loopback loop0 /ubuntu/disks/root.disk**
-> error: file not found

But I have the *folder **ubuntu*** and *file **root.disk(0KB)*** on my C drive.

Please help me out! Thanks!

---

### Post by drs305 on 2012-06-27
From a LiveCD, try installing Boot Repair and select the "Recommended repair" button. If that does not work, there is an option to run the boot info script. That script provides details about your system setup which will help us troubleshoot your problem.

There is a link to Boot Repair in my signature line.

---

### Post by Avinaash on 2012-06-28
Hi drs305,

I'm preparing a LiveCD. Once it is done I'll run Boot-Repair and let you know the status. Thank you :)

---

### Post by Avinaash on 2012-06-29
Hi drs305,

I ran the boot-repair from LiveCD. My problem is still unsolved.

Boot-repair URL:
paste.ubuntu.com/1066034/

Latest version of GRUB is installed on my system.

**[SIZE="3"]GNU GRUB version 1.99-21ubuntu3[/SIZE]** This is there at the top of GRUB menu.

Thanks!

---

### Post by oldfred on 2012-06-29
Please do not start two threads on same topic. Thread closed.

See
[http://ubuntuforums.org/showthread.php?t=2010850](http://ubuntuforums.org/showthread.php?t=2010850)

---


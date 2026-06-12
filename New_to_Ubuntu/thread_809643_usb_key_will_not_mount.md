---
title: "usb key will not mount"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by trigsenior on 2008-05-27
hello, 

Il make it short and sweet , when ever i put my usb flash drive in my laptop i get " unable to mount  " . however when i put the usb in my desktop which is also running ubuntu it mounts fine.  the only reason i think i does not mount is that i was a bit lazy and did not unmount properly  .... or else it was all windows fault for some reason. anyway could anyone surgest anyways to fix this ?

forgot to mention im running ubuntu 8.04

---

### Post by EXCiD3 on 2008-05-27
What format is the drive? If it is NTFS then safely disconnecting from windows is a must. Otherwise there could be a different problem with the drive.

---

### Post by issih on 2008-05-27
By any chance did you install ubuntu on the laptop from a flash drive?, if so you'll find that the install (thinking its come from a cd) incorrectly sets the mount point of usb drives as cdrom, then gets confused about the format mismatch.

If thats the case, you need to comment out the offending line in /etc/fstab that sorted me out.

hope that's useful

---

### Post by trigsenior on 2008-05-28
thanxs for your reply sorry , i was slow replying  =/

The usb was formated to fat 32 and 16 so , it seems it is a different problem , atleast not dead usb ... few 
However i did install ubuntu on my laptop from a usb , as i have no cd rom . 
Il try quoting the lines issih said and will report back straight away ! 

and thanxs alround =)

---


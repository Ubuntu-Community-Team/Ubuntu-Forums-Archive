---
title: "Verifying livecd"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by japhyr on 2008-08-17
Hello,

I have made a backup of my system using remastersys.  I want to verify that the livedvd I created is reliable, but I'm not entirely sure how to do it.

When the iso file was created, I ran md5sum on the file, and it matched the md5sum.txt that was generated in the remastersys process.  That verifies the iso file was correct, but how do I know there were no errors in the dvd write process?  Is there a file on the livedvd I can md5sum to verify the write process did not create any errors?

Also, can I boot from the livedvd on my current computer and take a look at the disc, or will that conflict with my installed system somehow?

Thanks for any help.

---

### Post by marwansherin on 2008-08-17
Can I ask a question?
I've used remastersys tool before, md5sum was ok, but after I booted from the CD I just created, it demands a password for the "sudo" command!!
so what can I do?
any help?
thanks in advance

---

### Post by alienexplorers on 2008-08-17
The sudo command does require a password no matter what.

---

### Post by alienexplorers on 2008-08-17
> **japhyr said:**
> Hello,

I have made a backup of my system using remastersys.  I want to verify that the livedvd I created is reliable, but I'm not entirely sure how to do it.

When the iso file was created, I ran md5sum on the file, and it matched the md5sum.txt that was generated in the remastersys process.  That verifies the iso file was correct, but how do I know there were no errors in the dvd write process?  Is there a file on the livedvd I can md5sum to verify the write process did not create any errors?

Also, can I boot from the livedvd on my current computer and take a look at the disc, or will that conflict with my installed system somehow?

Thanks for any help.

In the start menu for the liveCD there is a selection to check out your disk.  You may want to run this before loading the Ubuntu program to your disk.

---

### Post by t0p on 2008-08-17
> **japhyr said:**
> 
Also, can I boot from the livedvd on my current computer and take a look at the disc, or will that conflict with my installed system somehow?


If it's a Live disk, it won't interfere with your installed filesystem.  Unless you want it to, that is!! :)

---

### Post by dhughes on 2008-08-17
FYI after the verification of the LiveCD you have to reboot, I'm not sure why.

---

### Post by japhyr on 2008-08-18
I ran the checks on the disk and it passed, then I accidentally booted from the disk and saw that it works as a livecd.  Thank you everyone, I now feel much better about ever having to reinstall my system!

---


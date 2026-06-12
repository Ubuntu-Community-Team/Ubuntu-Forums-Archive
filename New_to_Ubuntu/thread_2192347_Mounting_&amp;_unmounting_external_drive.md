---
title: "Mounting &amp; unmounting external drive"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by rachel-g41 on 2013-12-07
I am currently running lubuntu on a netbook from an SD card boot. The HD disk is fried and this gives me a way to use the machine while Im waiting to get a new HD.

I have successfully mounted an external drive but mustn't have unmounted it properly because now when I try to connect it it says it can't mount because it's already mounted. 

I've googled for help but so far haven't found anything that works. I read a page about how to use udisks but when I try to install it I get an error 'udisks has no installation candidate'.

Many thanks for any help

---

### Post by rachel-g41 on 2013-12-07
This is the error msg I get in Disks

Error mounting /dev/sdc1 at /media/lubuntu/My Passport: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdc1" "/media/lubuntu/My Passport"' exited with non-zero exit status 21: mount: according to mtab, /dev/sdc1 is already mounted on /media/lubuntu/My Passport


 (udisks-error-quark, 0)

---

### Post by rachel-g41 on 2013-12-08
I guess I posted in the wrong place? Didn't give enough info? Or my question is below even absolute beginner level?

Oh well.

---

### Post by steeldriver on 2013-12-08
Hello and welcome to the forums

Sometimes questions just slip through the cracks, we're all volunteers and all scattered in different timezones. 

It seems like the device *is* mounted, so what happens if you try to access the contents? for example in a terminal

```
ls -l /media/lubuntu/My\ Passport
```

Note that you will need to 'escape' the space in the name using a backslash - or put it in quotes e.g. "/media/lubuntu/My Passport"

---

### Post by rachel-g41 on 2013-12-08
Many thanks for replying. I know sometimes things just slip by but it had so many views and when it slipped of the first page I felt abandoned....

Anyway, something strange happened. I just connected the disk to do as you suggest and this time a box popped up asking did I want to open it in file manager - so today it's working fine. 

The immediate problem is solved, and this time I'll try to disconnect properly to avoid a repetition. 

Thanks again.

---

### Post by steeldriver on 2013-12-08
OK well post back if the problem repeats - those WD Passport drives are a bit of an odd duck, at least if the (Windows-based) encryption / password protection is enabled, iirc they try to mount a kind of virtual CD-ROM 'unlocker' which doesn't work on Linux afaik

---

### Post by rachel-g41 on 2013-12-08
Just to say thanks again - I tried the command you suggested, it lists my files, I tried the umount command then repeated and hey presto, no files.


It's all good practice for an absolute beginner.

---

### Post by amjjawad on 2013-12-08
Welcome to Ubuntu Forums and thanks for using Linux :)

If your problem is fixed and you don't have any further Q, please mark this thread as 'Solved' so that everyone knows it is solved and won't go through the posts. Beside, to help others who might run into the same issue - they can find your thread by a google search or [www.googlubuntu.com](www.googlubuntu.com)

Enjoy!

---

### Post by rachel-g41 on 2013-12-08
well, yes it's solved in the sense that I've now plugged the device in & out a few times with no further problems, though I'm not sure why the problem suddenly disappeared. 

Marked as solved in any case

---

### Post by tulisqiya on 2013-12-08
Here also solved my problem, thank you for your help

---

### Post by amjjawad on 2013-12-09
> **rachel-g41 said:**
> well, yes it's solved in the sense that I've now plugged the device in & out a few times with no further problems, though I'm not sure why the problem suddenly disappeared. 

Marked as solved in any case

Glad it disappeared ;)
Wish you all the best and hope you will get your new HDD soon!

Thank you!

---

### Post by rachel-g41 on 2013-12-15
The problem has occured again.  Using the command suggested  ls -l /media/lubuntu/My\ Passport  tells me that the file or directory does not exist. 

Any help much appreciated

---


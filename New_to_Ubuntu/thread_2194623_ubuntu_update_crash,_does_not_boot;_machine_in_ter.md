---
title: "ubuntu update crash, does not boot; machine in terminal"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by woodchimp on 2013-12-19
hi,  (I have now Solved it. See bottom of page)

I was updating my Ubuntu machine, unfortunately it crashed. Now it will not boot into Ubuntu but after huge amount of error messages it sits in the terminal; I can use command lines and tried sudo apt-get update but again it gives error messages same with upgrade and dist-upgrade.

I have used a very old ubuntu live and can access the disc and I can see my files. ( I cannot find a newer live download now?) .

It is the only operating system on the computer. 

Can anyone tell me how to get it running again, but I am a novice?

Thank you.


The system would enter the "grub" (Choice of how to boot) and one of the choices was Previous linux; I selected that and there were three older Ubuntu versions, I merely kept selecting older versions rebooting and one of them worked. Went into software update/upgrade and updated and upgraded the system.  Rebooted a few times to prove it worked.

---

### Post by UltimateCat on 2013-12-19
If you are able to post those error messages that might help us to understand what happened.

Based on your description it sounds like you have more than one version of Ubuntu in your GNU Grub Menu-

How many partitions do you have?  To find that out you can run as 'root' the command:
```
fdisk -l (small letter L) 

```

A fresh install of Ubuntu 12.04 or Ubuntu 13.04 might help as they are both supported.
After you download the iso image than you can burn it to CD/DVD or put it on a usb memory stick and install it that way.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

Hope that helps

---


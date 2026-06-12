---
title: "Duel Booting Win7 and Ubuntu (both pre existing)"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Birkinator on 2013-01-16
Good Day Gents,

This is my first time using Ubuntu and the ubuntu forum, so please bare with me. 

With windows 7 previously installed on the local/primary HDD, I have installed Ubuntu on an external HDD and have not made any changes or installations other than updates. Is there a way that i can take both pre existing OS's and duel boot them, with windows remaining as my primary, or should i go ahead and format the external and start from scratch. How to's would be very, VERY, helpful. Thank you in advance!

---

### Post by mad2-814 on 2013-01-16
First off, Welcome to Ubuntu.  I started just a year ago and it's great.  But as for the installation, are you wanting to install them both on your primary disk?

---

### Post by audiomick on 2013-01-16
Hi. I've never done this, so I am not going to try and offer exact instructions. I believe, however, that it should be possible.

Do you know if you have grub installed to the external HD? I think that would be your best option. You need a grub installed there, and then to update it such that it knows about the windows. I think it should be as easy as installing grub, then running
```
sudo update-grub
```

with the drive attached to the computer. You would have to have the bios set to boot from the external. As I understand it, if the internal is also in the boot list, it should then boot to windows when the external is not connected.

---

### Post by centaurusa on 2013-01-16
> **Birkinator said:**
> Is there a way that i can take both pre existing OS's and duel boot them, with windows remaining as my primary, or should i go ahead and format the external and start from scratch.

Is there some reason why you simply wouldn't install Linux and Windows 7 "side by side" on the hard drive?  For a permanent dual-boot installation, I don't see the point of using an external USB drive since, in order for this to be effective, it would have to remain plugged in - just like a fixed hard drive.

Dual-booting with Windows pre-installed is normally straightforward.  There are many tutorials available on the subject.  See, for example:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

A second such tutorial at:

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

also offers a link to [Dual-boot Ubuntu 12.04 and Windows 7 on a computer with 2 hard drives]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/") which may be useful (I haven't read this page) if you wish to stick with the external drive.

---

### Post by Birkinator on 2013-01-16
> **mad2-814 said:**
> First off, Welcome to Ubuntu.  I started just a year ago and it's great.  But as for the installation, are you wanting to install them both on your primary disk?
Thank you for the welcome :). The configuration i currently have is my Waindows 7 primary on the internal HDD(C:), and Ubuntu loaded on a docked USB HDD(F:). I want to duel boot so that i can use both simultaneously so that i can use windows to search forums, learning materials, ect... while i implement what i have learned on the Ubuntu portion without having to have a completely separate computer.

---

### Post by mad2-814 on 2013-01-16
If that is what you want to do then keep your installation, but install virtualbox on your windows install and then install Ubuntu inside virtualbox so that you can run both at the same time.  I don't think it is possible to run both at the same time natively, but virtualbox is what you are looking for.

---

### Post by audiomick on 2013-01-16
> **Birkinator said:**
>  I want to duel boot so that i can use both simultaneously so that i can use windows to search forums, learning materials, ect... while i implement what i have learned on the Ubuntu portion without having to have a completely separate computer.

Be aware that you can't run both systems on a dual boot simultaneously. You boot into one or the other.

And a tip: it's up to you of course, but I would never use Windows to go into the internet if I had a Linux install available.

---

### Post by Birkinator on 2013-01-16
I have installed Virtual box, How would i go about adding the Ubuntu on the external to the application? or do i have to create a Virtual Disk and re install Ubuntu?

---

### Post by mad2-814 on 2013-01-16
I would install a new copy into virtualbox.

Here's a good tutorial,

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Birkinator on 2013-01-16
Thank you very much, This works great!

---


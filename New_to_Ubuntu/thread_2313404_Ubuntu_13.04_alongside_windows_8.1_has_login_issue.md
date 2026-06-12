---
title: "Ubuntu 13.04 alongside windows 8.1 has login issue"
date: 2016-02-12
forum: New to Ubuntu
---

### Post by harsh8 on 2016-02-12
Hello Everyone,

I just installed ubuntu 13.04 (Raring Ringtail, 64bit) alongside windows 8.1 (32 bit) by clicking on wubi.exe in my PC. It asked for things like space allocated (30gb), username and password. The Installation started downloading amd64.tar.xd which completed successfully and now I select from windows 8.1 and ubuntu in boot time. All good except I am unable to login to ubuntu with the username and password I provided during installation. It lets me use ubuntu as guest. So is there any way to change/ create a new ubuntu administration account? How can I login to ubuntu as an administator.

If you need any more information ask me. I searched and surfed for relevant solutions and came across grub thing. I dont know what it is but I cannot find it during load time. During boot my pc starts windows 8.1 and then it shows two options like windows 8.1 and ubuntu in blue colored windows 8.1 screen.

 I Thank you for the replies and help in advance.

---

### Post by ian-weisser on 2016-02-12
Ubuntu 13.04 is past End Of Life, and is no longer supported. 13.04 does not receive security updates anymore, and may be vulnerable to published exploits.
WUBI is no longer maintained, is not recommended for new users, and has only limited support.

If you wish to test a functioning snapshot of Ubuntu, including software and hardware compatibility, the simplest method is to create a LiveUSB stick.

If you wish to experiment with a complete Ubuntu install, the simplest method is to install a Virtual Machine host (like Virtualbox) on your Windows 8.1 system, and install Ubuntu 14.04 or 15.10 as a VM guest. 

There are many possible ways to install and try Ubuntu. Those are merely two of the easiest.

---

### Post by alexandari on 2016-02-12
Take a look at this [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by grahammechanical on 2016-02-12
Back in the days when Ubuntu 13.04 was the latest Ubuntu release there were reports of instability and data loss due to wubi.exe being incompatible with Windows 8. And so is is not recommended that we use wubi.

This is a user forum and relies on users to share their experiences. And this comment was made about wubi about 18 months ago

> With no active development for Wubi, there are few experienced users of  Ubuntu who also use wubi on this forum, and hence few here who can give  informed support for wubi.

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

A similar situation applies to old Ubuntu releases such as 13.04. We have all moved on. Linux commands remain the same but a Graphical User Interface changes in small ways. 

Each Ubuntu release has its own store of software called a repository or a software source. And these repositories are closed when the version reaches end of life. Not only will 13.04 not receive any security updates you will not be able to install any software from the repositories.

As regards the "grub thing." Well, Grub = GRand Unified Bootloader. It is the common boot loader for Linux distributions. It has a limited role and the reason why we cannot find it during load time is that by the time Linux is loading Grub has done its job and is no longer present in system memory. Having our user name or password rejected at the login screen is not a boot loader problem.

Regards.

---

### Post by yancek on 2016-02-12
The link below explains why you should not expect a WUBI install of Ubuntu to work on windows 8.  It is not supported any longer and the Ubuntu documentation below specifically explains that it will not be and that it is not expected to work with windows 8 and newer.  Either put it on it's own partition, put it on a flash drive or use virtual software.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by harsh8 on 2016-02-13
Thank you all for the light of knowledge, greatly appreciated.

Will move on to ubuntu14.04 LTS...

---


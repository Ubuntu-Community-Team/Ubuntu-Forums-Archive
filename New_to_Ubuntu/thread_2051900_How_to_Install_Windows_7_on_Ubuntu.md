---
title: "How to Install Windows 7 on Ubuntu?"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by nachinew on 2012-09-02
HI,

I Installed UBUNTU 12 on my machine, I am a beginner of UBUNTU, but i need to work with windows 7, But i don`t how..... Please guide me how to install windows 7 on Ubuntu machine.....

---

### Post by Bodsda on 2012-09-02
Hi,

I'm not sure what you mean by installing windows 7 'on' ubuntu. Windows 7 is an operating system and needs to be installed alongside ubuntu, not as a program in ubuntu.

Assuming you have some hard drive space not committed to your ubuntu installation, you should be able to insert the Windows 7 install cd, reboot, boot from cd, and run through the normal installer.

HTH,
Bodsda

---

### Post by gandaran on 2012-09-02
[http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html](http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html)
this guide is for an older Ubuntu but should still work
or google search on how to use Virtualbox on Ubuntu.

---

### Post by nachinew on 2012-09-02
> **Bodsda said:**
> Hi,

I'm not sure what you mean by installing windows 7 'on' ubuntu. Windows 7 is an operating system and needs to be installed alongside ubuntu, not as a program in ubuntu.

Assuming you have some hard drive space not committed to your ubuntu installation, you should be able to insert the Windows 7 install cd, reboot, boot from cd, and run through the normal installer.

HTH,
Bodsda

Thanks, Yes I mean alongside of UBUNTU, But I am currently using UBUNTU....
I need use window 7 in dual Boot Method, I don`t interested in Virtual running and using wine etc. Please share the method how to install windows 7 along side with Ubuntu..... :p

---

### Post by Bodsda on 2012-09-02
> **nachinew said:**
> Yes I mean alongside of UBUNTU, But I am currently using UBUNTU....
I need use window 7 in dual Boot Method, I don`t interested in Virtual running and using wine etc. Please share the method how to install windows 7 along side with Ubuntu..... :p

See if this helps.
[https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu)

Bodsda

---

### Post by nachinew on 2012-09-02
> **gandaran said:**
> [http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html](http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html)
this guide is for an older Ubuntu but should still work
or google search on how to use Virtualbox on Ubuntu.


Thanks but i am not interested in Virtual running. I need a dual boot method.....;)

---

### Post by nachinew on 2012-09-03
Any one having or share idea??????????????

---

### Post by blade4 on 2012-09-03
Refer this page : 

[http://ubuntuforums.org/showthread.php?t=732307](http://ubuntuforums.org/showthread.php?t=732307)

Cheers

---

### Post by mcduck on 2012-09-03
Yes. Put the Win install disc in the drive, and boot the machine. Same as with any normal Windows install. :D

(although since you already have Ubuntu, you'd probably want to resize your Ubuntu partitions first, leaving some empty, unpartitioned space for Windows in the beginning of the drive. And because Windows will overwrite the bootloader with it's own, you need to reinstall Grub after you've completed the Windows install. That's pretty simple and quick thing to do as long as ou have a working Ubuntu Live-CD/USB around. Just follow the link Bodsda posted above. )

---

### Post by Paqman on 2012-09-03
Check Bodsda's link, it has the correct procedure you'll have to follow once you have installed Windows. As mentioned above, easiest thing to do is create some space for Windows (either free space or NTFS) before installing.

Back up your data on Ubuntu before starting, just in case you accidentally install over the top of it!

---

### Post by nachinew on 2012-09-03
Thanks all, I will try and get back to you if i struck anything on middle....:p

---


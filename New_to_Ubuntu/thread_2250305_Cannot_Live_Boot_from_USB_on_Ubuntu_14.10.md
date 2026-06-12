---
title: "Cannot Live Boot from USB on Ubuntu 14.10"
date: 2014-10-27
forum: New to Ubuntu
---

### Post by bro4 on 2014-10-27
I recently installed Ubuntu 14.04 on my system replacing Windows 8.1 completely and even more recently upgraded that to 14.10. 
I wanted to try some other Linux OSes through USB drives on my Ubuntu 14.10 machine, but it is not working. I have already changed boot device priority in my BIOS to prioritize my USB and also enabled Legacy USB as well as UEFI support(are they applicable?) but cannot make it work.

Also, my Ubuntu 14.10 shows a "Booting in insecure mode" message for about 2 seconds before starting to boot. I was skimming through the forum where I found that this was a known issue in Utopic machines with secure boot disabled. Could this be the problem?

Any help is much appreciated. Let me know if any additional info is required. Thanks! :)

---

### Post by oldfred on 2014-10-28
How did you make flash drive installer. 
There seems to be a syslinux version issue.

 Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by Alireza_Zamani on 2014-10-31
in ubuntu use Disk Startup Creator.

---

### Post by bro4 on 2014-11-02
Hello Everyone, 

Thanks for the reply. I am sorry, but I am still not getting it :( 
So, the live USB drive is fully functioning. It is not a problem on that side. What I am having trouble with is getting the drive to boot into a live session of the linux distribution. I looked into the links provided by @[oldfred]("http://ubuntuforums.org/member.php?u=852711") but I am still having trouble figuring out the problem and booting into my live usb drive. Could you possibly give step by step instructions? I am sorry for all the trouble.

---

### Post by bro4 on 2014-11-02
Also, I made the live USB drive through a windows machine using Linux Live USB installer. Would that make a difference? Should I make it through mkusb or any other tool within Ubuntu??

---

### Post by oldfred on 2014-11-02
See this thread & post:
 [http://ubuntuforums.org/showthread.php?t=1958073&p=13157475#post13157475](http://ubuntuforums.org/showthread.php?t=1958073&p=13157475#post13157475)

I would try unetbootin or another installer.

---


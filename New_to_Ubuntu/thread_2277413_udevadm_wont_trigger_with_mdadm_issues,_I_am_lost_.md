---
title: "udevadm wont trigger with mdadm issues, I am lost and can't boot"
date: 2015-05-08
forum: New to Ubuntu
---

### Post by evan21 on 2015-05-08
So I was impatient and hard shutdown during a lengthy update about a three weeks ago (never will happen again!!!). Now I get the option to boot to other kernals or in safe mode, neither work. When i boot the current kernal I get the following:
[IMG]http://i46.photobucket.com/albums/f148/ghhhds/20150508_155134.jpg[/IMG]So I tried to fix each issue separtely. I tried to fix the udev issue by booting the live cd, mounting my boot drive and updating the initramfs (current kernal version). It appears to work until i reboot and nothing changes.

Next i tried to fix the mdadm issue. Upon further investigation my mdadm.conf file was blank. Also in /dev there is no md0 device listed. I am running a simple mirrored RAID 1. I tried mdadm --detail --scan /etc... which didnt work because on the live cd mdadm isnt installed. I apt-get mdadm which did install mdadm along with postfix, dont know what that is. During install the local /etc created a mdadm.conf with one of the raid uuids in it. Tried copying that mdadm.conf to my boot's location and rebooted with no luck. 

I am confused what is actually causing the issue. My best guess is I didnt let the new update finish installing the kernal but trying to update the new kernal does nothing for me. I am at a loss on why that would empty my mdadm.conf file though.

Any help would be most appreciated.

Thanks.

---

### Post by sandyd on 2015-05-09
Hi, can you post the contents of /etc/mdadm/mdadm.conf on the system (not the livecd) please?

---

### Post by evan21 on 2015-05-09
Thank You for the reply.

[IMG]http://i46.photobucket.com/albums/f148/ghhhds/20150509_150307.jpg[/IMG]

My system name is server. I really hope we can figure out what is going on.

---


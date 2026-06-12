---
title: "Slow Boot time"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by jjgo1 on 2015-12-22
The computer has recently been switched from Windows XP to Ubuntu and although it is faster it isn't as fast as I had expected.

The computer has:

Ubuntu 15.10 64bit

2x1GB of 667MHZ DDR2 Ram

320GB HDD (less than 70GB used)

Nvidia GeForce 8500 GT (512MB)

Intel® Core™2 Duo CPU E8500 @ 3.16GHz × 2 

A boot chart has been attached to help.


[ATTACH]266302[/ATTACH]

---

### Post by oldfred on 2015-12-22
Never learned to read Boot chart.
If just boot issues:
       systemd-analyze blame
    
But older system with Full Ubuntu and Unity usually does not work well. On my older laptop with 1.5GB RAM & Intel Core Duo I used Ubuntu but replaced Unity with fallback. With Unity it was so slow as to be unusable.
With a dedicated graphics card it may run, but still be slower. 

I liked flashback/fallback/gnome-panel as it is the old menu system like gnome2. Others will suggest Lubuntu or Xubuntu.
       Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)

---

### Post by Geoffrey_Arndt on 2015-12-22
Agree with OldeFred re not using Ubuntu with Unity desktop if wanting speed.   On a similar system, I have Ubuntu Mate and it is quite snappy/fast.

---

### Post by jjgo1 on 2015-12-22
Here is the results of running the commands. I hope this helps.

systemd-analyze:

Startup finished in 5.835s (kernel) + 28.094s (userspace) = 33.929s

systemd-analyze blame:

         13.661s gpu-manager.service
         11.215s accounts-daemon.service
         10.749s dev-sda1.device
          8.354s plymouth-quit-wait.service
          7.239s apparmor.service
          6.863s ModemManager.service
          6.168s binfmt-support.service
          5.542s alsa-restore.service
          5.522s speech-dispatcher.service
          5.522s systemd-user-sessions.service
          5.492s systemd-logind.service
          5.449s irqbalance.service
          5.449s apport.service
          5.447s pppd-dns.service
          5.446s grub-common.service
          5.444s ondemand.service
          5.438s thermald.service
          5.437s rsyslog.service
          5.436s NetworkManager.service
          4.812s colord.service
          4.485s polkitd.service
          3.257s systemd-udevd.service
          1.873s systemd-tmpfiles-setup.service

---

### Post by Geoffrey_Arndt on 2015-12-22
So, if fast start time is the goal, best way to do that is by getting a lighter desktop (Ubuntu w/Mate > Xubuntu  w/Xfce > Lubuntu w/LXDE) AND add a SSD as the main system drive.    On a newer System76 Galago laptop, Ubuntu "with" Unity loads in about 6 seconds - and shuts down in half that time.   But that's a 16 gb ram system with an I7.    

All things considered, a Mate laptop looks pretty good and is light.   But the biggest advantage of Ubuntu (whatever desktop used) is not speed, it's stability and the transparency of the actual OS . . . i.e., not a 'Black-Box.   It's an amazing thing, you actually are an OS "owner" versus an OS renter.

---

### Post by oldfred on 2015-12-22
How long does it take to boot?
None of those entries look excessively long. But not sure with your system.

My old laptop takes about 1 minute.

---

### Post by sammiev on 2015-12-22
I have lubuntu running from a external HDD via USB 2 port.

I'm very impressed with the results.

---

### Post by philinux on 2015-12-22
I'm running 15.04 ubuntu on an Acer 1412. Boots to login in about 35 seconds then another 15 or 20 to desktop. Suits me.

---


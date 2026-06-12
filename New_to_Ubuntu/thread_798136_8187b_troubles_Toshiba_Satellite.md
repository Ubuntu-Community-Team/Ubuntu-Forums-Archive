---
title: "8187b troubles Toshiba Satellite"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by mistered39 on 2008-05-17
Running 8.04 on Toshiba A215-S7428
Used  ndiswrapper to install modified driver(8197) and hardware shows it is present:

edv@edv-laptop:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8197) present
edv@edv-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

edv@edv-laptop:~$ 


But no wireless shows to configure. Where do I go from here?

---

### Post by empthollow on 2008-05-17
I don't know much about ndiswrapper but i have had enough problems with drivers to know that the problem you are experiencing is that the drivers are not controlling the device properly.  Your machine will see a device sometimes even if it doesn't know how to use it - which is what the drivers do.  I would try redoing the ndiswrapper part.

---

### Post by tjwoosta on 2008-05-17
have you tried the patched linux driver?

here is a thread that might help you

[http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187b]("http://ubuntuforums.org/showthread.php?t=765671&highlight=rtl8187b")

---

### Post by mbarvian on 2008-06-24
here is a full tutorial that might be of assistance:

[http://ubuntuforums.org/showthread.php?t=839108&highlight=a215]("http://ubuntuforums.org/showthread.php?t=839108&highlight=a215")

---

### Post by searchesend on 2008-06-25
Hey, I don't know what I'm doing in terms of thread etiquette so sorry if I upset anyone. 
I installed Hardy and now cannot connect to wireless networks - networks don't even show up in the connection manager thing. When I go to restricted drivers there's nothing there - almost like Hardy isn't recognising any of my hardware. In system:preferences there's no hardware information tab either.
I'm using the gutsy livecd with no problems in connecting to wireless networks? Thanks in advance

---

### Post by mbarvian on 2008-06-26
Do you have an RTL8187b?

---

### Post by searchesend on 2008-06-26
Just read your guide. Can I download that driver and save it so when I reboot in Hardy (not the Gutsy Livecd i'm on now) I can use it? My laptop is a Tosh L30 Satellite - I think the wireless feature is Atheros?

---

### Post by mbarvian on 2008-06-30
OK, first off, are you dual-booting with Windows?

---

### Post by searchesend on 2008-07-02
Sorry to reply so late-been homeless! No I have Heron on my hard drive and in order to access the internet wirelessly im using a livecd of Gutsy.

---

### Post by tjwoosta on 2008-07-02
you can download the files you need with the gutsy live cd 

just mount the hardy partition ,should be auto mounted when running the live cd, go to Places-XXG Volume (where xx is the size for instance mine says 56G Volume)

then save the files to the volume

---

### Post by searchesend on 2008-07-02
cool, I'll give that a go then-cheers.

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---


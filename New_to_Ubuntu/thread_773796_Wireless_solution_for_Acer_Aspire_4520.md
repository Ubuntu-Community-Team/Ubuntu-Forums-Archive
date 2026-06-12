---
title: "Wireless solution for Acer Aspire 4520"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by liquerLOVER on 2008-04-29
Hi there all Ubuntu Hardy user.:) I just found a solution for troublesome wireless network for Atheros AR5007EG for Acer Aspire 4520.

Ok...1st of all, download a driver from [http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/) and click on 	madwifi-nr-r3366+ar5007.tar.gz which i know is the latest one based on the date :). 

after you download it, move the madwifi-nr-r3366+ar5007.tar.gz to your "home" and extract it there.

for the next step, open the terminal and follow this process;

1) cd madwifi-nr-r3366+ar5007.tar.gz
2) make
3) sudo make install
4) sudo modprob ath_pci
5) ifconfig
6) iwconfig 
   and presto!!!

dont forget 2 restart.

after that, try to scan for any network. however, for me, the LED did not even light up so i thought that my effort was useless for the 1st time. however, after few second, i'm able to detect my college wireless and connect to it.

well, i just want to remind that even this technique work with my "baby", this doesn't mean it will work for all kind of laptop or AR5007EG because before this, i had try few technique and guide that i copy from this forums however all i found is FAILURE!!!!

i'm lucky cause there is a HERO that willing to help me and teach me to install the driver. THANKS A LOT to him. 

for ur informstion, i just install ubuntu 8 few days ago and im really fall in love with it even it is really hard to understand especially the command for a new user like me.

anyway, for those who thinking about quit using linux because fed up of failure, just remember that linux have no ends and never stop like a journey.until that.... adios amigos...

p/s; will someone help me fix my graphic card; Nvidia GeForce 7000 M.:)

---

### Post by kesman on 2008-04-29
Its always nice to hear that someone as new as you already fixed problems and really found out what was going on that made things not work.

By the way, my acer 5021's wlan worked out-of-the box, I just had to enable the restricted driver in system->administration->hardware drivers. Maybe there's a driver for your graphics too? Otherwise, EnvyNG does a great job in installing graphic drivers for bot nvidia and ati cards. Search for it in synaptic.

---

### Post by Naguz on 2008-04-29
> **liquerLOVER said:**
> Hi there all Ubuntu Hardy user.:) I 
p/s; will someone help me fix my graphic card; Nvidia GeForce 7000 M.:)You must use the Hardware drivers-app to disable the nvidia driver, then restart. Then enable again, and it will download the driver. Some has reported that this does not work for them if they don't have a clean install, but it is possible to install the drivers using synaptic too.Don't remember the package name exactly, i'm not on my laptop (and on windows) right now.

The problem seems to be that the driver is not in fact installed, although hardware drivers says it is enabled.

Does your solution work for 64bit versions also? I think I have tried every possible fix out there, but with no luck.

---

### Post by kesman on 2008-04-29
[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

This helped me before, maybe it helps you too? If I understood correctly, you also have an acer laptop?

---

### Post by liquerLOVER on 2008-05-02
dude...i jus 1 2 say sorry to u all.it seems that something wrong with my laptop o wat i dont know. after settle wit my network, im suddenly remember bout my hard disk free space. so i decide to put the free space to my linux with partiton magic since im doing dual boot wit win XP.sudenly, my Grub cant load my ubuntu8 & 8 the same time wit my winXP. so,,, i hav 2 install my ubntu8 for the 3rd time becos b4 this though i had setle my network, suddenly i lost my sound.so i had to install ubuntu8 4 d 2nd time..afer installing ubuntu8 4 d 3rd time, i cant set up my wireless. i use every tips in every threads about network but it seems that it was useless. all i got is error...error...error... & ******* hell ERROR...as a new guy in Linux, i almost giv up even though i had mention bout linux is a journey & don quit wit linux. can somebody help me????? even my hero cant settle my problem eventhough he is quite experienced in linux & now he is using triple boot which is WinXP,ubuntu7 & backtrack 3. plis... i really love linux. witout wireless connection, there is no use using linux. im really disapointed wit my self. I AM A LOSER...damn me!!!! will somebody outhere help me plis.......... im tired of winXP

---


---
title: "ndiswrapper - no configuration tool"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by BlackAce on 2008-11-10
I just installed ndiswrapper for my wireless card. When I try to configure network I am getting an error "Could not find a newtork configuration tool". But I can configure it in network manager but it won't connect. Somehow I think that ndiswrapper is not seeing the network manager? Or am I missing something?

---

### Post by Skripka on 2008-11-10
> **BlackAce said:**
> I just installed ndiswrapper for my wireless card. When I try to configure network I am getting an error "Could not find a newtork configuration tool". But I can configure it in network manager but it won't connect. Somehow I think that ndiswrapper is not seeing the network manager? Or am I missing something?

You'll need both Ndiswrapper as well as Ndiswrapper-common as well as Ndiswrapper-utils.....how are you "configuring" your network?  Ndiswrapper is best done via command line IMHO (there IS Ndisgtk, a GUI front end to Ndiswrapper, but I've never gotten as good a result as just plain old typing).

---

### Post by BlackAce on 2008-11-10
I have installed all the packages for ndiswrapper - ndiswrapper-ulities, ndiswraper-common and ndisgtk!?

I also installed the windows driver for my wireless car.

---

### Post by Skripka on 2008-11-10
> **BlackAce said:**
> I have installed all the packages for ndiswrapper - ndiswrapper-ulities, ndiswraper-common and ndisgtk!?

I also installed the windows driver for my wireless car.

Well, whave you done exactly?  And what card do you have and what tutorial have you followed?  Lest we see your work it is hard to know where the problem is.

For myself All I had to do (example) was:
(after installing Ndiswrapper and utilities

```

cd...[to dir where windows drivers were]
sudo ndiswrapper -i drivername.inf
ndiswrapper -l (shows driver installed if things went well)


sudo modprobe ndiswrapper
iwconfig (check to see that worked)

ndiswrapper -m (adds ndiswrapper to boot-up)

sudo dmesg (check to make sure things are still working
sudo iwlist wlan0 scan
sudo iwconfig wlan0 essid Name-Of-Wanted-Wireless-Network
sudo dhclient wlan0


```

And BAM my wireless works

---

### Post by BlackAce on 2008-11-10
I had Unbuntu on my drive and wipped it out and wanted to try Mint Linux, then I went back to Unbuntu. When I had Unbuntu ealier it worked fine (tried Mint for about two days). The only difference I see from then and now is that the netwok manager is version 0.7.0 and I believe I have version 0.6.0 or 0.6.?

I'm not fimilar with terminal and the commands. I used ndisgtk installed my wn511b.inf and set up my wireless connection from network manager with no problems.

---

### Post by Skripka on 2008-11-10
> **BlackAce said:**
> I had Unbuntu on my drive and wipped it out and wanted to try Mint Linux, then I went back to Unbuntu. When I had Unbuntu ealier it worked fine (tried Mint for about two days). The only difference I see from then and now is that the netwok manager is version 0.7.0 and I believe I have version 0.6.0 or 0.6.?

I'm not fimilar with terminal and the commands. I used ndisgtk installed my wn511b.inf and set up my wireless connection from network manager with no problems.

Hmmmmmmmmmmmm....

1st thing I'd try, is uninstalling your driver via ndisgtk and "completely" removing all ndiswrapper bits and settings through synaptic---then reinstalling the same way you're accustomed too.  My guess is that in the back and forth between Mint and Ubuntu something may have gotten funnied up in Ndiswrapper, and it expects some network manager utility or feature to be present (that comes with Mint), that you no longer have.

---

### Post by BlackAce on 2008-11-10
I follow what you saying but I is that possbible even when each install was a fresh install?

---

### Post by BlackAce on 2008-11-10
Come to think of it now I think I was using Unbuntu verion 8.04? Now I am using 8.10? But either way not sure why it wouldn't be working?

---

### Post by Skripka on 2008-11-10
> **BlackAce said:**
> I follow what you saying but I is that possbible even when each install was a fresh install?

It depends on how you did your fresh install.....is your /media folder on seperate partition?  If yes-then it is more than possible :)

---

### Post by hydo1 on 2009-05-01
when i do 

sudo modprobe ndiswrapper
is says

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

what do i do.

---

### Post by hydo1 on 2009-05-01
> **Skripka said:**
> Well, whave you done exactly?  And what card do you have and what tutorial have you followed?  Lest we see your work it is hard to know where the problem is.

For myself All I had to do (example) was:
(after installing Ndiswrapper and utilities

```

cd...[to dir where windows drivers were]
sudo ndiswrapper -i drivername.inf
ndiswrapper -l (shows driver installed if things went well)


sudo modprobe ndiswrapper
iwconfig (check to see that worked)

ndiswrapper -m (adds ndiswrapper to boot-up)

sudo dmesg (check to make sure things are still working
sudo iwlist wlan0 scan
sudo iwconfig wlan0 essid Name-Of-Wanted-Wireless-Network
sudo dhclient wlan0


```And BAM my wireless works


when i sudo modprobe ndiswrapper
```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```
this it just comes up

can any one help

---

### Post by anewguy on 2009-05-01
When you are using ndiswrapper, there may be a conflicting "built-in" driver that needs to be blacklisted.  I would check for your device and see if there is a driver already included - if so, blacklist it.  I know more drivers where built in starting in 8.04, and I think they may have added more in 8.10.

dave :)

---

### Post by anewguy on 2009-05-01
How about you do this and post the output back here - it may help us.

If the device is USB, plug it in.

Open a terminal window (application/accessories/terminal) and log on using your normal userid/password.

Type:

sudo lsusb <press enter> post the output back here.  Use your normal password if it asks for a password.

sudo lspci <press enter> post the output back here.  Use your normal password if it asks for a password.

exit <press enter>

The first command, lsusb, lists all the USB devices known to your system.  If it's a laptop, some internal wireless adapters are actually attached internally to USB.

The second command, lspci, lists all the PCI devices known to your system.

With these lists, we should be able to determine the type of wireless adapter you have and that will help us guide you on what to do.

Dave :)

---

### Post by hydo1 on 2009-05-04
> **anewguy said:**
> When you are using ndiswrapper, there may be a conflicting "built-in" driver that needs to be blacklisted.  I would check for your device and see if there is a driver already included - if so, blacklist it.  I know more drivers where built in starting in 8.04, and I think they may have added more in 8.10.

dave :)

how do i blacklist the driver

---

### Post by anewguy on 2009-05-04
IF you know the name of the driver:

open a terminal window (applications/accessories/terminal)

type:

cd /etc/modprobe.d <press enter>

sudo gedit blacklist <press enter>  when prompted enter in your normal password

scroll to the bottom of the file and add a new line:

blacklist xxxxxxx  <- where xxxxxxx is the name of the driver

click save and exit

type exit and press return

reboot



Dave :)

---

### Post by hydo1 on 2009-05-06
i dont know the driver name
 
so how do i find the driver name

---

### Post by ngrieb on 2009-07-19
I need some help reconfiguring my network for ndiswrapper. I had it working, but it was kind of flaky so I tried the Network Config button, but as above the network config tool, so I tried using one separately. I can no longer connect to any wireless router. Please help, all I have is wireless without totally relocating my computer.

For more info I started my own thread here: 
[http://ubuntuforums.org/showthread.php?p=7631342](http://ubuntuforums.org/showthread.php?p=7631342)

I have tried full uninstall and reinstall of ndiswrapper with no luck.

---


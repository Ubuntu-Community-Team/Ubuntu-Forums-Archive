---
title: "Verizon USB720?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by dmalpack89 on 2008-11-24
Is there any way I can use the internet with my verizon wireless USB720?

---

### Post by cozmicharlie on 2008-11-24
Are you using Intrepid?

---

### Post by dmalpack89 on 2008-11-24
yes i am

sorry i forgot to give my info

AMD64, Ubuntu Intrepid, dv6000 pavilion laptop

---

### Post by cozmicharlie on 2008-11-25
OK - it should be supported natively.  I use a Sprint U727 on an HP Pavilion dv2000 and mine works great.  In your top panel you have a network daemon (you should have a network icon).  Right click on it and go to "Edit Connection" and you should have a tab for "Mobile Broadband".  You should be able to plug in your device and it will detect it.  A few things you need to do first though. Make sure any wireless is turned off.  You can do it by right clicking on the network daemon and clicking "enable wireless" or if you have a switch on your computer turn it off.  Also, unplug any wired connection.  I use a Sprint U727 and when I plug it in it mounts it as a cdrom (yours may not do this).  To use it I have to unmount it first.  I use a very simple script.
```
sudo eject /dev/scd1
```
Again, you most likely don't have to do this - I think it is unique to the Sprint device. Once you plug it in, the network should detect it.  If not then you will need to manually fill in the info.  Right click on the network daemon and go to "edit connections" and add it as a mobile broadband.  I have mine set up as automatic so it connects when I plug it in.  You can set it up either way though.  Once it is set up, if you left click on the network daemon it should have "cdma network connection".  If you set it up to automatically start then it should be connected if not you manually connect it by clicking on cdma connection.  That should do it.  Try it and see if it works.

---

### Post by dmalpack89 on 2008-11-25
> **cozmicharlie said:**
> OK - it should be supported natively.  I use a Sprint U727 on an HP Pavilion dv2000 and mine works great.  In your top panel you have a network daemon (you should have a network icon).  Right click on it and go to "Edit Connection" and you should have a tab for "Mobile Broadband".  You should be able to plug in your device and it will detect it.  A few things you need to do first though. Make sure any wireless is turned off.  You can do it by right clicking on the network daemon and clicking "enable wireless" or if you have a switch on your computer turn it off.  Also, unplug any wired connection.  I use a Sprint U727 and when I plug it in it mounts it as a cdrom (yours may not do this).  To use it I have to unmount it first.  I use a very simple script.
```
sudo eject /dev/scd1
```
Again, you most likely don't have to do this - I think it is unique to the Sprint device. Once you plug it in, the network should detect it.  If not then you will need to manually fill in the info.  Right click on the network daemon and go to "edit connections" and add it as a mobile broadband.  I have mine set up as automatic so it connects when I plug it in.  You can set it up either way though.  Once it is set up, if you left click on the network daemon it should have "cdma network connection".  If you set it up to automatically start then it should be connected if not you manually connect it by clicking on cdma connection.  That should do it.  Try it and see if it works.

Yea this didn't work for me. I followed all the steps but when I go to set up the connection it gives me a bunch of options for service providers, only to include AT&T and T-Mobile. But I have Verizon so I'm not sure how to go about setting up the connection.

---

### Post by cozmicharlie on 2008-11-25
The first post in this thread has the verizon info.
[http://ubuntuforums.org/showthread.php?t=343989&highlight=verizon](http://ubuntuforums.org/showthread.php?t=343989&highlight=verizon)

What happens when you plug in the device?  Is it recognized (if you open a terminal and type "dmesg" it should show you how it is being recognized.
Try starting the computer with the device attached.  Make sure the wireless is off.

---

### Post by Czaruno on 2008-12-01
Just wanted to add that I just installed XUbuntu 8.10 on an Sony Vaio laptop that is a few years old and the Verizon USB720 worked right out of the box.  I had to use the alternate Xubuntu CD installer because the main one would not work properly.

After installing Xubunutu,  I connected the USB adapter and it was detected right away.

I just went to the networking icon on the top right and selected 'Auto Mobile Broadband (CDMA) Connection' and a few seconds later I was online.

It might have been easier for me because this laptop has no network card and no built in wireless.

Laptop Details:
Sony Vaio PCG-SR33K
Processor  Celeron 600 MHz
128 MB (SDRAM)
10 GB IDE Hard Drive

Xubuntu runs surprisingly usable on this machine although I am going to try to see if I can max out the ram and get better performance.

I might also buy a right angle USB extension cord to make it easier to use the cellular adapter:
[http://www.usbfirewire.com/Parts/rr-aar04-16.html](http://www.usbfirewire.com/Parts/rr-aar04-16.html)

Next I will try to use a tethered cell phone connection on this laptop.

Good luck to others trying to use this USB cellular adapter.

---

### Post by tienkhoanguyen on 2009-03-05
> **dmalpack89 said:**
> Yea this didn't work for me. I followed all the steps but when I go to set up the connection it gives me a bunch of options for service providers, only to include AT&T and T-Mobile. But I have Verizon so I'm not sure how to go about setting up the connection.

I have Verizon USB720 too!  I chose the option of AT&T provider when it asked and it worked!!!!!!!!!! :)  I was able to connect to the internet even with a different provider selection.  Hope that works for you too...

---


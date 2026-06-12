---
title: "Removing Propietary ATI driver breaks the normal opensource one..."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Mazza558 on 2008-11-14
Hi all,

My laptop works fine with the normal open source ATI driver (Intrepid), but I thought I'd try the fglrx driver that's available. Since it's slower than the open source one, I tried to disable it in Hardware Drivers but it wouldn't let me. I then removed the package "xorg-driver-fglrx", which then broke Xorg on the restart - It crashes on the loading screen with a small, horizontal green line across the screen. I went into recovery and did a dpkg-reconfigure on xorg, which at least got X back. However, I no longer have hardware acceleration as Mesa's being used instead. When I tell xorg to use the opensource ATI driver, I get the same green line. How can I fix the open source driver and/or enable it properly?

TL : DR Version:

Removing fglrx driver breaks open source driver - how can I fix the open source driver and/or enable it properly? I'm on Intrepid with a clean Xorg file.

P.S - Why is Mesa so much faster than any 3D driver? Why have 3D drivers got such awful 2D performance?

---

### Post by Mazza558 on 2008-11-14
Anyone have any ideas?

---

### Post by Mazza558 on 2008-11-15
I've checked that the correct packages are installed, but still no luck...

---

### Post by jpichie on 2008-11-15
did you remake your xorg.conf file? /etc/X11/xorg.conf
It could still be trying to load up the fglrx driver.

Also do a remove on the open radeonhd driver, reboot and reinstall it. That may help.

---

### Post by Mazza558 on 2008-11-15
> **jpichie said:**
> did you remake your xorg.conf file? /etc/X11/xorg.conf
It could still be trying to load up the fglrx driver.

Also do a remove on the open radeonhd driver, reboot and reinstall it. That may help.

Yeah, I'm using a brand new Xorg. I'll remove the radeonhd, but I never had to do this originally, it just worked.

---

### Post by Mazza558 on 2008-11-15
I've reinstalled the ati and radeon drivers and it still defaults to mesa.

---

### Post by Mazza558 on 2008-11-15
...And installing fglrx again also defaults to mesa...

---

### Post by jpichie on 2008-11-21
If you can, try a fresh install, and add the "pre-release" packages to adept/synaptic. Do an update, and then install the fglrx-driver (should be version 8.552) as well as kernel 2.26.8.

This worked for me, and I am now running my fglrx driver without problems.

This is the link that helped me [http://ubuntuforums.org/showthread.php?t=983052]("http://ubuntuforums.org/showthread.php?t=983052")

Thanks to Gatman3

---

### Post by peakshysteria on 2008-11-21
If you would like an option before reinstalling and following jpichie's great tip. I got it working with: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22") 

The usual manual way is broken with Intrepid. Also when the howto says:
> Terminal Command:

```
sudo gedit /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf #for kubuntu users
```

In the device section, if it is not already there add:
File: /etc/X11/xorg.conf

Driver "fglrx" 

...I always put my resolution (1280x1024) as the first line (where you can see all the different resolutions. Not sure which section it is since this will be reconfigured after you run sudo aticonfig --initial -f ).

This method gave me the 8.10 (8.452) version of the driver. As mentioned above 8.11 is the latest and presumably the better one. I'm running very smooth on my system now with the 8.10 driver.

Besides that jpichie's tip seem to be a good way for getting the latest driver available.
[[img]http://bildr.no/thumb/291155.jpeg[/img]](http://bildr.no/view/291155)

---

### Post by jpichie on 2008-11-21
Actually, for me, after installing fglrx and rebooting X, I would get no GUI. I needed to do an aticonfig --initial to create a working xorg.conf.
After this I did a startx and away she went.

---

### Post by etherealeclipse on 2009-03-07
bump and other solutions I have this problem also don't want to reinstall ubuntu as I don't have the internet connection to re-update and install my applications.

---


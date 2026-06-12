---
title: "[SOLVED] Problems installing my modem driver package"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Vunutus on 2008-11-07
I finally got Ubuntu 8.04 up and running after some errors and am in the process of getting all my hardware up and running. The first step is getting my modem working (unfortunately I'm stuck with dialup). It makes things take significantly longer when I have to boot into Windows to get on the internet and research.

After some poking around, I found that my modem actually officially supports Linux and provides drivers for it (which surprised me). I got the .deb driver package and started it up to install it. I authenticated and went to the installation part with the progress bar. It pinged back and forth for quite a long time (5+ minutes). I  eventually stopped it. When I tried to run it again, I authenticated and it gave me an error saying that only one software manager can be running at one time, and to close programs like synaptic and aptget. I opened my process monitor and couldn't see any programs like that in the list, so I reboot my computer thinking that will clear it out. I log back in and no luck, same thing. 

How do I fix this? I really need to get my internet working on Ubuntu.

---

### Post by Sealbhach on 2008-11-07
Weird, you would think a reboot would halt anything handling it.

See if it installed. Look in:

```
sudo dpkg -l 
```

If it installed you could try unistalling it and installing again:

```
sudo dpkg -r *nameofpackage*
```


.

---

### Post by phidia on 2008-11-07
I think you need to follow the correct guide for the modem you have. There is a Ubuntu wiki on getting dial up working [here]("https://help.ubuntu.com/community/DialupModemHowto"). Don't forget to run the "sudo pppconfig" command from a terminal that is important.

---

### Post by Vunutus on 2008-11-07
> **Sealbhach said:**
> Weird, you would think a reboot would halt anything handling it.

See if it installed. Look in:

```
sudo dpkg -l 
```

If it installed you could try unistalling it and installing again:

```
sudo dpkg -r *nameofpackage*
```


.

I followed this and apparently is was installed, so I uninstalled it. After starting the installer again, it hung as before but I opened up the terminal option at the bottom and it was sitting there waiting for me to press enter. I did so, and it finished installing.

Even with it installed, however, I can't get it to connect. I tried configuration both with the pppconfig command and the System->Administration->Network tool. pppconfig doesn't detect any installed modem and wants me to manually specify a port. I tried /dev/modem as the port but when I use pon it won't connect, saying something about /dev/modem not being a valid modem. The graphical tool accepts all the values (and it suggested using /dev/modem apparently), but doesn't connect. I tell it to connect and it doesn't react at all.

Also, if it makes a difference this is an external USB modem.

---

### Post by Sealbhach on 2008-11-08
Type in the terminal:
 
```

sudo wvdialconf
```

This should detect your USB modem.


.

---

### Post by Vunutus on 2008-11-08
> **Sealbhach said:**
> Type in the terminal:
 
```

sudo wvdialconf
```

This should detect your USB modem.


.

No luck, says "No modem found" as well.

---

### Post by Sealbhach on 2008-11-08
OK, does it show up if you list the USB devices:

```
lsusb
```

Also, tell us what kind of modem it is.


.

---

### Post by Vunutus on 2008-11-08
> **Sealbhach said:**
> OK, does it show up if you list the USB devices:

```
lsusb
```

Also, tell us what kind of modem it is.


.

The specific name of the modem is "Zoom 56k USB Modem Model 3095 Series 1063". It shows up on lsusb but none of the modem configuration utilities can find it.

---

### Post by Sealbhach on 2008-11-08
Hi, looking on Google it seems you need to download a driver for it.Have a look at this post here where someone got it working:

[http://ubuntuforums.org/showthread.php?t=711646](http://ubuntuforums.org/showthread.php?t=711646)


.

---

### Post by Vunutus on 2008-11-09
Thanks for all the help. I got my internet working and am currently posting this from Ubuntu. Apparently Ubuntu has an untold number of dialup configuration devices, yet only one seems to work for my modem.

It's a little rough, but at least I can research things without having to reboot and switch operating systems.

---


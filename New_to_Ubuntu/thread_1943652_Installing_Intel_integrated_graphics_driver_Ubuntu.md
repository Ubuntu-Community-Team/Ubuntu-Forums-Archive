---
title: "Installing Intel integrated graphics driver Ubuntu 11.04"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by KennyJack on 2012-03-19
Hi, I'm new to the community as of this post and need a little guidance.  I recently installed (or so I think I did) the latest driver for my Intel graphics card because I was experiencing intermittent low-resolution start-ups.. the desktop and icons were really big as if I were in "safe-mode" under windows.  After installing the new driver, Ubuntu seems to load properly most of the time, but every once in a while reverts back to the issue I was having before, in which I have to restart my computer a few times back-to-back-to-back until it loads correctly.  When I run the lspci -k command I notice there are two Kernal modules.  Could this be the cause of the now less irritating yet still existing problem?  Thanks in advance for any help.   

$lspci -k

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
	Subsystem: Dell Device 0160
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

Dell dimension 2400 1GB ram.

---

### Post by KennyJack on 2012-03-19
Oh, and please let me know if I'm in the wrong area for this question.  I'll get the hang of the forums hopefully soon :)

---

### Post by NikTh on 2012-03-19
Hi ,
How did you installed the drivers for your graphics ? From system ? open a terminal and write ```
jockey-gtk
``` what you see ? are the [Recommended] drivers activate ? . 

Also you can install the latest drivers for your G.Card from a ppa. Give these commands in terminal
```
sudo add-apt repository** ppa:ubuntu-x-swat/x-updates**
```press enter when ask . Then```
sudo apt-get update 
sudo apt-get dist-upgrade
```These commands will add a ppa to your software sources and will update your drivers with the latest.
If something go wrong or for any other reason you want to remove it , go to your software sources (update manager-->settings-->other software ) and remove **ppa:ubuntu-x-swat/x-updates .** Then do in terminal ```
sudo apt-get update 
sudo apt-get dist-upgrade
```

---

### Post by KennyJack on 2012-03-20
Thanks NikTh for responding in such timely manner.

The driver was installed from a pre-compiled package using the Software Center.. probably a mistake since it's painfully slow and hangs all the time.  

Jockey-gtk showed no proprietary drivers not in use so I added the PPA manually since the terminal said the add-apt command couldn't be found (odd?)  I ran the "update" and "dist-upgrade" commands and all seemed ok, meaning my monitor didn't blow up or anything :) 

Is a restart needed for changes to take effect?  How can I tell if the driver was replaced by a new one?

---

### Post by Perfect Storm on 2012-03-20
Intel drivers are Open Source, so they won't show up in 'additional Drivers' (restricted drivers) and is installed by default.

If you added the PPA to get a newer version, you need to restart before it takes effect.

---

### Post by KennyJack on 2012-03-20
Restarted... it worked! :biggrin: I've restarted 6 times now and no issues-- the display even seems to be more clear and smooth.  Well done and thanks again.

---

### Post by NikTh on 2012-03-20
> **Artificial Intelligence said:**
> Intel drivers are Open Source, so they won't show up in 'additional Drivers' (restricted drivers) and is installed by default.

Ohhh man , where was my head ?? hah.. you have absolutely right. 
:p

---

### Post by ky2391 on 2012-11-06
the (sudo add-apt repository ppa:ubuntu-x-swat/x-updates)command doesnt work for me

---

### Post by becare on 2012-11-09
> **ky2391 said:**
> the (sudo add-apt repository ppa:ubuntu-x-swat/x-updates)command doesnt work for me


right command :
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

---


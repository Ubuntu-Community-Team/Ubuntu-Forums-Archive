---
title: "Ubuntu Desktop won't display GUI"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by moonsaber on 2012-06-12
So i decided to do a clean install of ubuntu 12.04 desktop version on my old laptop. While installing (using a cd) i was able to use the GUI and change display settings, volume, networks etc. However when i finished the installation and restarted it booted into command line rather than a GUI. I tried running the startx command but it came up with some error messages.

The main one that jumped out at me was:

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a useable configuration.

Fatal Server Error:
no screens found

This leads me to think that it is a graphics driver issue. However if so, why was it able to display the GUI fine during installation?

My laptop is an MSI GX600 (really old now, 5 years?)

The graphics card is an 8600GM if i remember correctly.

Anyways it would be great if anyone could help me with this problem. I have had some basic experience with linux but not too much.

Thanks,
moonsaber

---

### Post by mapes12 on 2012-06-12
> i was able to use the GUI and change display settingsTry the install again but without changing anything. Then when it's on your HDD you can enable any propritery drivers. The Live CD has clearly found settings that match your hardware so by leaving the defaults in place you should be good to go to install, then fine tune afterwards.

---

### Post by moonsaber on 2012-06-12
> **mapes12 said:**
> Try the install again but without changing anything. Then when it's on your HDD you can enable any propritery drivers. The Live CD has clearly found settings that match your hardware so by leaving the defaults in place you should be good to go to install, then fine tune afterwards.

sorry i should clarify, I've installed ubuntu twice. Initially i ran through ti quickly and just used default settings and everything. The second time i ran through it i fiddled around to see what sorts of things were available in the installation gui, i played around but didn't actually change anything. After both installations the same issue occurred.

---

### Post by mapes12 on 2012-06-12
If it were my machine I would completely wipe the disk with something like Killdisk and start again. In my experience formatting alone can leave stuff around that messes things up.

---

### Post by moonsaber on 2012-06-20
Ok so i wiped the disk with killdisk. Then i reinstalled it, same problem.

I also tried lubuntu to no avail.

It even lets me run the GUI off the live cd with no problems, im very confused....if i can run it with no problems off the cd why won't it work off the hard drive.

---

### Post by moonsaber on 2012-06-21
Sorry for the double post but i wanted to update on something that happend.

So I managed to get to the GUI login screen on lubuntu by running recovery mode. However when i try to login the screen flashes and it returns to the login screen again.

Weird problem...

EDIT: Forgot to mention it lets me log onto the guest account with no problems, just not my own.also it only works when i run recovery mode

---


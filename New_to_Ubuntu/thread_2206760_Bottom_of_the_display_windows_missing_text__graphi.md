---
title: "Bottom of the display: windows missing text / graphics / full screen video"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by Falken_Fakename on 2014-02-20
Hi all, 
I'm running Ubuntu 12.04 PPC on an old Mac Powerbook G4. Graphics card is NVIDIA NV34M [GeForce FX Go5200]
I've managed to struggle through various issues, but this one has me stumped!

On *just* the bottom of the screen text doesn't show up / windows are truncated / full-screen movies are not visible.

Here's some samples of what I mean.
(note the last image is to show you what the fullscreen movie from the first image *should* look like!)
[http://m.imgur.com/a/HQMww](http://m.imgur.com/a/HQMww)

When I mouse over these buttons they appear.
With text in the browser that's invisible, if I select/highlight it and then unselect it, it's now visible.

I've found that be changing the resolution down to 800x600, and maybe fiddling with the refresh rate betweem 60Hz and 59.9Hz, and then returning it to 1024x768 I can get it to work perfectly fine! That is, until I reboot, and the same thing happens again.

Is there any way I can make these changes stick?

Thanks all!

---

### Post by Falken_Fakename on 2014-02-21
B-B-B-Bump!

OK, so can anyone suggest a script I can have auto-run that will change my resolution to 800x600 just after the login screen, and then back to 1024x768 moments afterward? This would completely fix my problem: I am doing exactly this manually now, and it resolves the problem. This would be a perfect workaroud!

Thanks!

---

### Post by Vladlenin5000 on 2014-02-21
What driver are you using? Such issues are typical of the open-source driver... Have you tried the nVIDIA proprietary? Go to Software&Updates > Additional drivers (tab) to check the suggestions.

---

### Post by Falken_Fakename on 2014-02-22
Hey Vlad, thanks for responding.
Nothing is showing up in additional drivers but for my wifi card which is working correctly. I think the video driver I'm using is called nouveau or similar. I'll look into how I might install a different driver. Cheers!
Sorry, total noob at this.

---

### Post by Vladlenin5000 on 2014-02-22
Maybe this helps: [http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise](http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise)
Long story short, you can install the drivers using the packaged *.deb file available at Launchpad, this one: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638/+files/nvidia-173-updates_173.14.35-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638/+files/nvidia-173-updates_173.14.35-0ubuntu1_i386.deb)

---

### Post by Falken_Fakename on 2014-02-22
Thanks for the pointer!

---

### Post by Falken_Fakename on 2014-02-22
> **Vladlenin5000 said:**
> Maybe this helps: [http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise](http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise)
Long story short, you can install the drivers using the packaged *.deb file available at Launchpad, this one: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638/+files/nvidia-173-updates_173.14.35-0ubuntu1_i386.deb](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173-updates/173.14.35-0ubuntu1/+build/3597638/+files/nvidia-173-updates_173.14.35-0ubuntu1_i386.deb)

Unfortunately the i386 .deb doesn't work on this powerbook as it is pre-intel- I'm getting an error message "Wrong architecture i386".

Having followed another link to the nvidia site on one of the pages you linked I've found a .run file that may actually work for me.

[http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver.html](http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver.html)

I don't know ow to execture this file so via google on the ubuntu site I'm seeing a warning that running it may be very difficult to undo if it doesn't work, so I'm a bit reticent about ruining my partial functionality that I currently have and installing a driver that leaves me without a working display. :(

---

### Post by Vladlenin5000 on 2014-02-22
I'm very sorry because I missed the part about PPC and this a huge game changer. You can't install that from nvidia either.
I've found this regarding the use of the legacy driver 'nv': [http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644)

---

### Post by Falken_Fakename on 2014-02-24
Thanks Vlad, I'll take a look at that link as soon as I can.

---


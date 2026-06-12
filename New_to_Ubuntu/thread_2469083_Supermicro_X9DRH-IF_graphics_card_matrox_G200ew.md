---
title: "Supermicro X9DRH-IF graphics card matrox G200ew"
date: 2021-11-18
forum: New to Ubuntu
---

### Post by mw0sbx on 2021-11-18
Hi all

Recently had a windows 10 crash and found my graphics card failed  (gtx780) so then windows 10 failed with it and i installed ubuntu i used  to be a gentoo x64 user over 13 years ago.

Anyway's i cant find xorg.conf and was wondering how i proceed to setup  the resolution on the onboard server card a matrox G200 its currently  only displaying 1024 x 768 (4:3) and my monitor is 1920 x 1080 (16:9)

Its on a Supermicro X9DRH-IF MB

lspci

08:03.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a)

---

### Post by grahammechanical on 2021-11-19
Which version of Ubuntu did you install? For several years now work has been taking place on a replacement for the X-Server. We now have a video server based on a protocol called Wayland. With Ubuntu we can switch between X-Server and Wayland at the log in screen. I think that Ubuntu 20.04 defaults to the X-server and Ubuntu 21.10 defaults to Wayland. So, the version of Ubuntu that you installed will determine the default video server.

Have you not tried using System Settings>Screen Display to change the resolution? Of course the monitor must be capable of displaying the desired screen resolution. Modern monitors have an integrated circuit chip that holds all that information and the OS reads the information to select to optimum settings. It is called Extended Display Identification Data (EDID).

Are you using a proprietary video driver or the open source video driver? Some of this information can be found from System Settings>About. It will tell you the Windowing system in use and also the type of graphics. We can also open Software & Updates>Additional Drivers and if we are connected to the internet the application will find suitable proprietary video drivers and offer to install. 

Regards

---

### Post by ActionParsnip on 2021-11-19
What is the output of:
```

sudo lshw -C display
lsb_release -a
uname -a
xrandr

```
Thanks

---


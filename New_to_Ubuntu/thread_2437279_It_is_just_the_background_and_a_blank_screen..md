---
title: "It is just the background and a blank screen."
date: 2020-02-20
forum: New to Ubuntu
---

### Post by hlteo27 on 2020-02-20
I've booted up Ubuntu 18.04.4 LTS on a USB made using Rufus.  I boot into the "GUI" but there is no "Start button" (Gnome?).  It is just the background and a blank screen.  I can right click the blank screen and I know the OS is up and running.  I can switch workspaces by following these instructions [https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces-switch.html](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces-switch.html)


But where is the "Start button" and the apps?!  Any hints?  :-)

---

### Post by Frogs Hair on 2020-02-21
Hello and Welcome 

If there is no panel on the left with applications or top panel then the desktop is not loading properly on your system. There is no start button in the Gnome desktop system. Can you add some information about your computer ?

[https://help.ubuntu.com/stable/ubuntu-help/index.html.en](https://help.ubuntu.com/stable/ubuntu-help/index.html.en)

---

### Post by hlteo27 on 2020-02-22
Hi @Frogs Hair,

I'm using an ASRock IMB-183 motherboard with an i3 Intel Processor.  I've a 8GB Samsung DIMM installed on 1 slot (2nd slot empty).  I've made these variations so far:

1) To eliminate the USB thumb drive as a problem, I tried 6 different thumb drives.
2) To eliminate Rufus problem, I tried BalenoEtcher too.
3) To eliminate USB port problems, I tried all 5 USB ports.  
4) Then I made a Ubuntu Live on a HDD and boot it up using the eSata port.
5) I booted the Live (USBs and HDDs) on a Lenovo laptop and it came up fine.  

I'm running out of ideas........................

---

### Post by Frogs Hair on 2020-02-22
It is usually  graphics related when the desktop doesn't load. You could try a lighter flavor of Ubuntu such [Xubuntu ]("https://xubuntu.org/download/")which has a more traditional style of desktop. Flavors have only 3 years of support and the next  LTS Comes out in April 2020. I8.04 would only be supported until 20.21 with an option to upgrade.  

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

---

### Post by hlteo27 on 2020-02-22
I figured out the problem.  Live booted up correctly after I adjusted the BIOS/Graphics settings to disable Intel LVDS.  Moving on to the next problem... it just won't install.  Install just fails with some disk related error.  I'm starting to think that either (1) there is something wrong with my motherboard specifically the SATA controllers or (2) the default BIOS settings are no good.

---

### Post by Frogs Hair on 2020-02-22
Is there another operating system on this computer ? If so are you trying to overwrite it with Ubuntu or dual boot ?

---

### Post by yancek on 2020-02-22
>    Install just fails with some disk related error.  

What might those errors be?  Specifically.

---

### Post by hlteo27 on 2020-02-22
[SIZE=2]Hi Frogs Hair, I'm "recycling" a system so you can say I'm building a new system with one OS (hopefully Ubuntu).

Hi yancek, after spending more time researching online - I'm quite convinced it has something to do with my m/board implementation and/or BIOS implementation. The error seems to be related to "stolen reserved area" (memory?) related to "drm/i915" which is the integrated Intel GFX chipsets.

Other Ubuntu-related distros (e.g. Linuxmint) are throwing the same error. Arch-based Manjaro and Debian both boot up fine.

I've been trying to tweak the BIOS settings to see if I can overcome this but no luck so far.[/SIZE]

---


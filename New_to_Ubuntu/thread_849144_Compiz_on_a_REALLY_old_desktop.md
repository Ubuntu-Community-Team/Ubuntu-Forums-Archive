---
title: "Compiz on a REALLY old desktop"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by rockerphil on 2008-07-04
ok, i'm trying to get Comppiz running on my crappy 10 year old desktop, but first some info on the system. i'm running a 10 year old Dell Dimension desktop with 128 MB of pc133 SD RAM and a 500 MHz Intel Pentium processor. the OS is a "custom build" as i like to call it built from the Ubuntu 7.10 Gutsy Gibon minimal ISO where i installed a CLI then installed of course xorg, Fluxbox as my current window manager and a few other light weight apps. now, to the task at hand, i'm trying to get Copmpiz running. i don't want a whole lot of the REALLY fancy effects, basically just the cube and wobbly windows. i know how to pull up my video card type, but i really don't know what to do with it. here's the output of the command "lspci"


phil@phil:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:0a.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
01:0b.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)



so here's my question, is it at all possible to get some basic Compiz effects running on a machine this old? and if so, could one of you plz help me with a decent walk through or at least point me in the right direction? thanx in advance,


Phil

---

### Post by overdrank on 2008-07-04
Hi and please correct me if I am wrong but fluxbox and compiz do not work together. Also with 128 MB memory that is being shared with the onboard graphics that would tell me the amount would be around 8mb for the graphics and that may cause issues.

---

### Post by rockerphil on 2008-07-04
yes, Fluxbox and Compiz aren't compatible seeing as they're both window managers, and as far as the shared memory goes i'm not quite sure, sorry. but what i was wondering is if it's possible to replace Fluxbox with some basic Compiz effects, like i said, nothing fancy, basically just the cube and wobbly windows, and i'm sure there's gonna be some bugs seeing as i'm working with very limited resources by any standards, but i'm willing to work with them, and thank you for the reply



----------------
Now playing: [HellYeah - Hell Yeah](http://www.foxytunes.com/artist/hellyeah/track/hell+yeah)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by overdrank on 2008-07-04
> **rockerphil said:**
> yes, Fluxbox and Compiz aren't compatible seeing as they're both window managers, and as far as the shared memory goes i'm not quite sure, sorry. but what i was wondering is if it's possible to replace Fluxbox with some basic Compiz effects, like i said, nothing fancy, basically just the cube and wobbly windows, and i'm sure there's gonna be some bugs seeing as i'm working with very limited resources by any standards, but i'm willing to work with them, and thank you for the reply



----------------
Now playing: [HellYeah - Hell Yeah](http://www.foxytunes.com/artist/hellyeah/track/hell+yeah)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

Ok here are a couple of links that may help
[http://ubuntuforums.org/showthread.php?t=678487](http://ubuntuforums.org/showthread.php?t=678487)
[http://ubuntuforums.org/showthread.php?t=483613](http://ubuntuforums.org/showthread.php?t=483613)

:)

---

### Post by wdaniels on 2008-07-04
I believe it's possible to get compiz working with that graphics card - see [this thread for example]("http://ubuntuforums.org/showthread.php?t=655639"). You seem to be well aware of the limitations, so all I can do is wish you luck with it and ask that you report back here how well this works (or doesn't) :D

PS: You can often alter the amount of shared memory used for graphics in the BIOS.

---

### Post by rockerphil on 2008-07-05
ok, just a bit of an update, i've now got the Compiz packages installed along with Emerald and the CompizConfig Settings Manager which i can access by running "ccsm" from the terminal. i've got it configured pretty simply, like i said, nothing fancy. but here's my problem, i just can't figure out exactly how to get it running on my onboard video card, i tried installing the Intel 915 (i think) package through Synaptic, but when i type "compiz --replace" in terminal this is what i get:


Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
no /usr/bin/metacity found, exiting
phil@phil:~$ 

i've been pretty well beating my skull against a wall for a while trying to figure this one out, so i figured i'd kick this one to y'all and see if i can ease some of the headache, much thanx in advance,


Phil

----------------
Now playing: [Atmosphere - The Woman with the Tattooed Hands](http://www.foxytunes.com/artist/atmosphere/track/the+woman+with+the+tattooed+hands)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by rockerphil on 2008-07-05
ok, i just tried running it from just the command line by pressing Ctrl+Alt+F2 and running "compiz" and i got somthing about texture_from_pixmap: not present. any ideas?

----------------
Now playing: [Dark Lotus - I Wanna Die](http://www.foxytunes.com/artist/dark+lotus/track/i+wanna+die)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---


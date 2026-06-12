---
title: "Very bad experience upgrading from Hardy. Help please with nvidia."
date: 2008-11-10
forum: New to Ubuntu
---

### Post by bwallum on 2008-11-10
Hi

I have just tried to upgrade a Hardy to Intrepid using the online upgrade though the update manager. I have been trying to recover for hours now. I think the problem starts with a screen that asks if you want to keep old settings or upgrade to new ones. I suggest a lot of people would respond to the 'new' offering. I did.

It seems to dump the nvidia drivers. It then takes you through a screen that asks if you want to use default low res, reconfigure or a third option that I now forget. Choosing low res gets you to the desktop but you can't then reinstall the nvidia driver. Reconfigure leaves you with a black screen. Wait forever and it stays a black screen.

I have been with Ubuntu a while now and think I know a little about the system. Normal users would be completely stuck I suggest. I'm stuck! I'm very frustrated and need to reinstall the nvidia driver.

Can someone please help me with this?

Regards
Bob

---

### Post by Elfy on 2008-11-10
what card is it?

has the system tried to install a driver through hardware drivers?

If you have an oldish card youmight have been cauught with the legacy driver issue.

I'd reboot to start with - recovery mode, from the menu - xfix - resume

Should be back to vesa driver now - lets have the card model :)

---

### Post by Elfy on 2008-11-10
Sorry - see it in youe specs - shouldn't be the legacy issue assuming it's that card.

You might be able to use the 177. driver - I would make sure that all other nvidia- drivers are completely uninstalled before you start.

I'd use hardware drivers first - there were problems with that and older cards - it got proposed update which needed to be installed for them.

---

### Post by bwallum on 2008-11-10
> **forestpixie said:**
> what card is it?

has the system tried to install a driver through hardware drivers?

If you have an oldish card youmight have been cauught with the legacy driver issue.

I'd reboot to start with - recovery mode, from the menu - xfix - resume

Should be back to vesa driver now - lets have the card model :)

Thanks for the help. xfix - resume enabled a clean boot to Desktop, thanks. The card is a nVidia 6600 pci express, using vga for a Compaq V70 crt monitor. apolodgies for the misleading signature which refers to my machine. I'm upgrading my daughter's machine at the moment.

Hardware Drivers informs no proprietory drivers installed and does not offer any. I have tried loading nvidia-glx-177 with Synaptic which says it is loaded. Am I using the right driver? I can't see anything else offered which is similar.

---

### Post by bwallum on 2008-11-10
Well that xfix routine lasted for one boot only. These are the errors I get on booting up:-

(EE)Failed to load module "type 1" (module does not exist, 0)
(EE)NVIDIA(0): Failed to load the NVIDIA lernel module!
(EE)NVIDIA(0) ***Aborting***
(EE)Screen(s) found, but none have a usable configuration

I've opened the box to check the card connections, alls well (it's a Gigabyte nVidia 7600GS with 512Mb I've discovered)

I've attached the xorg.conf file for further information.

I must have the wrong driver I think. Which driver should I be using?

---

### Post by Elfy on 2008-11-11
I would make sure that you have the updated jockey installed - enable proposed updates in software sources then let it reload the repos. I would say that if you haven't done this then it's likely that hardware drivers could have a problem - it surely did with older cards, but tbh as I was affected by that I wasn't take a great deal of notice of anything else.

Remove the nvidia you have installed - revert to the vesa driver again with xfix - resume and see what driver it lets you install this time.

You might need the 173 driver possibly, also you could try using envyng - now that it is in the repos I don't believe some of the issues poeple had previously are as prevalent.

---

### Post by bwallum on 2008-11-15
Hi, thanks for the reply and sorry to be so long returning. Basically I tried all your advice but couldn't seem to break through the problem. The machine is now a few hundred miles away and i don't have access to it. What i have ended up with is a 22" widescreen monitor running 1280 by 960 resolution. It looks a mess but at least it is working. I presume I have the vesa driver running.

It used to be that I could edit /etc/X11/xorg.conf to solve these issues but now don't seem to be able to do that. Has the file structure for the xserver changed at all? I need to find out where the configuration files are and start from there I think. GUIs are nice if they work but I feel I am dealing with some fundamental issues that the gui approach is not addressing.

---

### Post by dark_harmonics on 2008-11-15
> **bwallum said:**
> Hi, thanks for the reply and sorry to be so long returning. Basically I tried all your advice but couldn't seem to break through the problem. The machine is now a few hundred miles away and i don't have access to it. What i have ended up with is a 22" widescreen monitor running 1280 by 960 resolution. It looks a mess but at least it is working. I presume I have the vesa driver running.

It used to be that I could edit /etc/X11/xorg.conf to solve these issues but now don't seem to be able to do that. Has the file structure for the xserver changed at all? I need to find out where the configuration files are and start from there I think. GUIs are nice if they work but I feel I am dealing with some fundamental issues that the gui approach is not addressing.

If you think xorg.conf is you problem you could let nvidia regenerate it by moving it to a backup (in case you want to revert):

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak
```

Then let Nvidia regenerate it:

```
sudo nvidia-xconfig
```

You can always try regenerating your xorg with:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If you want to see if the nvidia module is loaded try this command

```
sudo lsmod|grep nvidia
```

to try to force it to load (and produce errors if not) try:
```
sudo modprobe nvidia
```

Maybe some of that can at least get you an error message you can google on to find some answers. 
I hope any of this brain dump helps!

PS: I attached my xorg.conf as an example. I do run multiple displays on this computer through.

---

### Post by bwallum on 2008-11-15
Thanks for the advice. I really appreciate the support. I tried to open your attachment and got "/tmp/xorg.conf.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences."

Maybe because I used a link through Evolution...anyway I'll try to sort that one later.

I tried the 'sudo nvidia-xconfig' route and got a window at boot that said I had a problem, such as 

(EE)Failed to load module "type 1" (module does not exist, 0)
(EE)NVIDIA(0): Failed to load the NVIDIA lernel module!
(EE)NVIDIA(0) ***Aborting***
(EE)Screen(s) found, but none have a usable configuration

reported above. (btw I typed out the error message so please excuse the 'lernel' typo)

I also tried the 'sudo dpkg-reconfigure -phigh xserver-xorg' route and got a pretty much blank xorg.conf file that showed generic statements such as 'configured monitor' with no further explanation.

Is the /etc/X11/xorg.conf file still the primary configuration file for the xserver?

Regards
Bob

---

### Post by dark_harmonics on 2008-11-15
> **bwallum said:**
> Thanks for the advice. I really appreciate the support. I tried to open your attachment and got "/tmp/xorg.conf.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences."

Maybe because I used a link through Evolution...anyway I'll try to sort that one later.

I tried the 'sudo nvidia-xconfig' route and got a window at boot that said I had a problem, such as 

(EE)Failed to load module "type 1" (module does not exist, 0)
(EE)NVIDIA(0): Failed to load the NVIDIA lernel module!
(EE)NVIDIA(0) ***Aborting***
(EE)Screen(s) found, but none have a usable configuration

reported above. (btw I typed out the error message so please excuse the 'lernel' typo)

I also tried the 'sudo dpkg-reconfigure -phigh xserver-xorg' route and got a pretty much blank xorg.conf file that showed generic statements such as 'configured monitor' with no further explanation.

Is the /etc/X11/xorg.conf file still the primary configuration file for the xserver?

Regards
Bob

It really sounds like you dont have the driver installed correctly (or maybe an older version of the driver). I would highly reccomend you remove all nvidia components and reinstall from system--> administration->Hardware drivers. 

That file was ziped with gzip btw. If you want to open it then just save to your desktop and try executing gzip -d xorg.conf.gz on it.

Edit: did you see this link: [http://jdbausch.blogspot.com/2008/10/ubunt-810-ibex-upgrade-low-graphics.html](http://jdbausch.blogspot.com/2008/10/ubunt-810-ibex-upgrade-low-graphics.html)

---


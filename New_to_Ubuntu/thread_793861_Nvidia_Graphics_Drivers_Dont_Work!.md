---
title: "Nvidia Graphics Drivers Dont Work!"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by metasolaris on 2008-05-14
Hi,

I am running Hardy and have a Geforce 2 MX 400 graphics card. 

If I enable the restricted drivers option, the computer freezes during reboot and I have to reinstall everything.

I have tried ENVY on automatic and got the same result.

I have also tried downloading the correct driver off synaptic and got the same result !

Any ideas? Do you know how much of a performance hit I will have if I dont enable the restricted drivers and just stick with the unrestricted ones which do seem to work ok?

Thanks for your comments.

Meta

---

### Post by hermes0710 on 2008-05-14
Is this an AGP card?

---

### Post by metasolaris on 2008-05-14
> **hermes0710 said:**
> Is this an AGP card?

Hi yes
well, my pc has an agp 4x slot

---

### Post by hermes0710 on 2008-05-14
Then there is an option you should set in the /etc/X11/xorg.conf in the driver section, under "nvidia". I don't remember exactly what it is but something like:

Option "NvAGP" "0" (or 1 or 2...google it :) )

---

### Post by metasolaris on 2008-05-14
> **hermes0710 said:**
> Then there is an option you should set in the /etc/X11/xorg.conf in the driver section, under "nvidia". I don't remember exactly what it is but something like:

Option "NvAGP" "0" (or 1 or 2...google it :) )

Sorry, but I have no idea what you just said! have not the foggiest notion what to do!

---

### Post by gusjones on 2008-05-14
This could be a monitor recognition problem and not a driver problem.

I had a problem that might be similar. Your monitor is probably plug and play detected, prior to installing the Nvidia drivers try the following:

Enable "screens and graphics" on menu, (go to System-->Preferences-->Main menu, and Select other and enable "screens and graphics")

Then select your monitor from Applications-->other-->screens and graphics. Now enable the nvidia driver and reboot. This worked for me and I think I have the same card on the PC I had this problem on-- worth a try anyway.

Cheers.

---

### Post by PmDematagoda on 2008-05-14
Did you try installing the legacy package of the nvidia driver in the repositories with:-
```
sudo apt-get install nvidia-glx-legacy
```
and seeing if that fixed your problem?

---

### Post by metasolaris on 2008-05-14
Thanks. Ill try those suggestions when I get home.

---

### Post by pedro_orange on 2008-05-14
> **hermes0710 said:**
> Then there is an option you should set in the /etc/X11/xorg.conf in the driver section, under "nvidia". I don't remember exactly what it is but something like:

Option "NvAGP" "0" (or 1 or 2...google it :) )

What Hermes is saying is: edit your xorg.conf file.

[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-f.html](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-f.html)

The above link should tell you about using configuring AGP.

```
Option "NvAgp" "0"  ... disables AGP support
    Option "NvAgp" "1"  ... use NVAGP, if possible
    Option "NvAgp" "2"  ... use AGPGART, if possible
    Option "NvAGP" "3"  ... try AGPGART; if that fails, try NVAGP
```

You should be able to edit this file by doing:

```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by gusjones on 2008-05-19
> **metasolaris said:**
> Thanks. Ill try those suggestions when I get home.

Did you get home yet! :confused:

---

### Post by metasolaris on 2008-05-19
> **gusjones said:**
> Did you get home yet! :confused:


Yes thanks!

I tried the suggestions but each time the screen froze during reboot which means that I had to reinstall the OS each time. After the 3rd time it started getting real old so Im currently running with whatever drivers come preinstalled with hardy which dont work too bad i suppose especially since im not running any games. This machine is just a Net-puter:)

---

### Post by gusjones on 2008-05-19
> **metasolaris said:**
> Yes thanks!

I tried the suggestions but each time the screen froze during reboot which means that I had to reinstall the OS each time. After the 3rd time it started getting real old so Im currently running with whatever drivers come preinstalled with hardy which dont work too bad i suppose especially since im not running any games. This machine is just a Net-puter:)

OK, a shame none of the fixes worked. There is one other possibility, I had one PC which worked fine when I didn't use the nvidia drivers but as soon as I enabled them and did a reboot it would hang part way through the logon screen, I found that the graphics card was semi-fried and when I replaced it everything worked fine. I doubt this is your problem though.

Oh well, ho hum.

---

### Post by PmDematagoda on 2008-05-19
Did you try using the VGA drivers that Nvidia provides for it specifically? Since your VGA card is rather old that might have been the case.

---

### Post by handy on 2008-05-19
I'll just add the following link, in the interests of education, it helped me a great deal once, when I had to set up a pig of an nVidia AGP card:

***_[ftp://download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-12.html](ftp://download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-12.html)_***

---


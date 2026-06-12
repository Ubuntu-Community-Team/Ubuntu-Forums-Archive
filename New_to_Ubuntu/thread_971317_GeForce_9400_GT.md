---
title: "GeForce 9400 GT"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by samyardley on 2008-11-04
Clean install of Ubuntu 8.04, this machine has a new GeForce 9400 GT card, can someone tell me what needs to be installed driver and configuration utilities to take advantage of the enhanced graphics effects. 

Thanks in advance.

---

### Post by sgleo87 on 2008-11-04
just need the nvidia drivers enabled under system > administration > hardware drivers and that should install the nvidia drivers. Then you will have the nvidia settings under system > administration to adjust your video card settings.

---

### Post by samyardley on 2008-11-04
> **sgleo87 said:**
> just need the nvidia drivers enabled under system > administration > hardware drivers and that should install the nvidia drivers. Then you will have the nvidia settings under system > administration to adjust your video card settings.


I went to where you indicated and it shows no drivers to enable!  Can someone tell me what drivers out of synaptic to install ?

---

### Post by alienexplorers on 2008-11-04
Did you try using:
> sudo envyng -t
You can load envyng-core from synaptic or from terminal using:
> sudo apt-get install envyng-core

---

### Post by samyardley on 2008-11-05
> **alienexplorers said:**
> Did you try using:

You can load envyng-core from synaptic or from terminal using:


Your first command did not work, it was un-recognized, the 2nd command worked but I still have none of the options you described or the options under system> admin> hardware

---

### Post by robfindlay on 2008-11-05
> **samyardley said:**
> Your first command did not work, it was un-recognized, the 2nd command worked but I still have none of the options you described or the options under system> admin> hardware

*BUMB*

I'd actually like to see the answer here too...

---

### Post by RussW210 on 2008-11-05
I switched my card from an ATI Radeon to a Nvidia GeForce 9500GT and had the same issue where no graphics driver showed up in Hardware Drivers.  I even tried using Envy but my card wasn't compatible.

My friend said if I updated to 8.10 it would fix the problem and whaddayaknow there was a new graphics driver under Hardware Drivers.  8.10 does have some issues though.

If you go to the Nvidia.com website they should have a package with Linux instructions for you.

---

### Post by robfindlay on 2008-11-05
> **RussW210 said:**
> I switched my card from an ATI Radeon to a Nvidia GeForce 9500GT and had the same issue where no graphics driver showed up in Hardware Drivers.  I even tried using Envy but my card wasn't compatible.

My friend said if I updated to 8.10 it would fix the problem and whaddayaknow there was a new graphics driver under Hardware Drivers.  8.10 does have some issues though.

If you go to the Nvidia.com website they should have a package with Linux instructions for you.

Did you do a clean instlal or a dist-upgrade?

---

### Post by RussW210 on 2008-11-05
I did a dist-upgrade through the Upgrade Manager to get to 8.10.  It went OK, generally things work.  Two questions:

1) I installed the nvidia driver from the nvidia.com website under 8.04.  Then I upgraded to 8.10 and downloaded the driver from the Hardware Drivers section.  Did that overwrite the driver I installed under 8.04?

2) I am experiencing problems with k9copy.  I know, separate issue.  It won't burn an .iso image when I select a full movie to rip.  But it will burn a .iso image when I select individual smaller movie files.  Any ideas?

---

### Post by robfindlay on 2008-11-05
> **RussW210 said:**
> I did a dist-upgrade through the Upgrade Manager to get to 8.10.  It went OK, generally things work.  Two questions:

1) I installed the nvidia driver from the nvidia.com website under 8.04.  Then I upgraded to 8.10 and downloaded the driver from the Hardware Drivers section.  Did that overwrite the driver I installed under 8.04?

2) I am experiencing problems with k9copy.  I know, separate issue.  It won't burn an .iso image when I select a full movie to rip.  But it will burn a .iso image when I select individual smaller movie files.  Any ideas?

Even though 8.10 is out, my update manager never gave me an option to run  upgrade to 8.10.

Could someone point me to the directions for such an upgrade? using apt-get or update manager?

---

### Post by RussW210 on 2008-11-05
I know why but im not on ubuntu now... it is a setting you have to change in your synaptic pacakage manager i believe - set something to normal.  Damn, i forgot =/

---

### Post by RussW210 on 2008-11-05
Wait, here you go.  Follow these instructions:

[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html)

That will give you the option to upgrade.

---

### Post by robfindlay on 2008-11-05
> **RussW210 said:**
> Wait, here you go.  Follow these instructions:

[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html)

That will give you the option to upgrade.


Will 9.10 upgrade give our friend the nVidia drivers?

---

### Post by robfindlay on 2008-11-05
> **robfindlay said:**
> Will 9.10 upgrade give our friend the nVidia drivers?

Bumb....does anyone have an answer as I would like to use the same nVidia card myself.

-Rob

---

### Post by robfindlay on 2008-11-05
> **alienexplorers said:**
> Did you try using:

You can load envyng-core from synaptic or from terminal using:

"sudo envyng -t" 

Are you sure thats the right command. 


-R

---

### Post by robfindlay on 2008-11-05
*bumb* 

Does anyone have answers for the above questions?

---

### Post by schlichte on 2008-12-22
> **alienexplorers said:**
> Did you try using: sudo envyng -t

You can load envyng-core from synaptic or from terminal using:


Installed envyng-core through the package manager(search "nvidia" was 3rd hit) then in the terminal ran "sudo envyng -t" and did a manual install. After a restart everything is working perfectly.

Thanks!

[Ubuntu 8.04] BFG Nvidia GeForce 9400GT 512MB

---

### Post by Ben Page on 2008-12-23
Install a fresh downloaded copy of ubuntu 8.10 or Linux Mint 6. I have tried both and there were no problems at all installing drivers for 9400gt. 8.10 offered to dnld drivers at first startup automaticaly, everything went smooth, restart, activate compiz and woilla. It works flawlessly in maximum settings all eff. on with no stuttering.
I had problems with drivers in open SUSE 11.1 but that is not the issue here.

---

### Post by MontanaMax on 2009-03-20
alienexplorers had the right commands, but for those unfamiliar with the command line work they are in backwards order. Run them in this order:

```
sudo apt-get install envyng-core

sudo envyng -t
```

Then follow the prompts and it will detect the most appropriate video driver from nVidia or ATI's site and install it for you.

---

### Post by jamesrfla on 2009-03-20
Can't you just go to nvidia.com and get the drivers of off there web site. It is a .run file so it is easy to install.

---

### Post by MontanaMax on 2009-03-24
> **jamesrfla said:**
> Can't you just go to nvidia.com and get the drivers of off there web site. It is a .run file so it is easy to install.

There are a lot of ways to handle any particular task. I've never tried determining which particular driver I need from the nVidia site, but I have had great luck for several years with the Envy install software. Your mileage may vary -  just make sure you have any critical files backed up and then give one of them a shot.

---


---
title: "Intel G33/G31 or 3100 or x3100 chipset"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Mol_Bolom on 2008-11-17
I've looked all over trying to find information on this, basically, I just don't want to have to crack open the computer in order to find the correct number as to which chip I have on this bloody computer, lol...

Anyway, the monitor number is E228WFP, which few problems with that, the latest one is the darn thing set to the wrong resolution after trying to change the display driver. Since the monitor is a widescreen monitor, well, regular resolutions look rather odd...But that's no problem, if I have to I can edit the xorg.conf file to fix that...

However, finding the correct graphics driver has been rather hair pulling.  I've read that this computer might have a 3100 or x3100 chipset in it. In windows Vista it shows it having a G33 or G31 chipset in it, which I presume the G31 is in reference to 3100.

I opened the windows INF file and looked up the section iBLB0 trying to shed some light on this, but the only thing I could find anywhere in both Device manager as well as the inf file was VEN_8086, which was set in several variables in the display driver properties.

Anyway, here's some more information...

What Windows Vista gives:
Intel G33/G31 Express Chipset Family
Ver: 7.14.10.1437

What I've done:
Using Ubuntu Hardy 8.04 dual booted with windows Vista on Dell Inspiron 530.
Using Q35 intel display driver (in xorg.conf Boardname "intel Q35", Driver "intel"
Installed driver updates and extra xorg Intel drivers.

What I've noticed:
Using the Q35 driver, graphics is terrible. This computer has a dual core 2.2ghz processor which runs Graphical intense screen savers slower than a 2.0ghz single core computer I have running Zenwalk linux.

Anyway, any ideas?

Thanks...

---

### Post by nhasian on 2008-11-17
what does it say when you type in a terminal:

```
lshw -C display
```

---

### Post by Mol_Bolom on 2008-11-17
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0

```

---

### Post by bodhi.zazen on 2008-11-17
Use google, there are a number of how-to's on this chip set :)

---

### Post by nhasian on 2008-11-17
From your output it looks like you have an Intel 82G33/G31 Express graphics adaptor.  If your resolution was not setup correctly you can try to fix it with this command:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Mol_Bolom on 2008-11-17
Ok, got the resolution corrected again.  Tried that, however, didn't work, surprisingly enough, just had to do what I did before when it wasn't correct and voila, it corrected itself, somehow...

Anyway, this is as much as I can do today...

But out of curiosity, I looked over the xorg.conf and I can't find anything in it...

```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

So, what file has the settings that are normally in these at?

---

### Post by phidia on 2008-11-17
Xorg has changed. It would be good to know where those values are stored now.

---

### Post by Mol_Bolom on 2008-11-17
> **phidia said:**
> Xorg has changed. It would be good to know where those values are stored now.

<Edit> Haven't been able to find the files, and putting it off for now...

---

### Post by techningeer on 2010-09-01
You don't have the correct driver. Nowadays, x.org does not keep a config file, but just configures itself each time it starts. quite the problem. I suggest you look into using xfree86.

---

### Post by bodhi.zazen on 2010-09-01
> **techningeer said:**
> You don't have the correct driver. Nowadays, x.org does not keep a config file, but just configures itself each time it starts. quite the problem. I suggest you look into using xfree86.

This thread is almost 2 years old.

FYI : Although xorg.conf is depreciated as you say, you can manually write an xorg.conf

With that I will close this thread.

---


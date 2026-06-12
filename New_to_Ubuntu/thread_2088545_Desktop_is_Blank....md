---
title: "Desktop is Blank..."
date: 2012-11-26
forum: New to Ubuntu
---

### Post by galaxys on 2012-11-26
Hey guys, first post here. I am new to Ubuntu and I have encountered my first problem. I was trying to install nvidia drivers and it failed at the end. After, it rebooted and after I logged on everything was gone. No icons or bars or anything. I can right click and get into the settings but I am not sure what to do there in order to fix this. I have searched and tried numerous codes in the terminal with no luck. I am completely new with this, the Terminal is a new experience for me. Thanks in advance for any help or suggestions. If you need any information about my computer please let me know.

---

### Post by galaxys on 2012-11-26
Running Ubuntu 12.10 btw. Please I believe this is a problem that has occurred often if you can help at all it would be greatly appreciated.

---

### Post by newb85 on 2012-11-27
How were you installing drivers?  (Did you download them from the vendor's website?  Using Software Sources?)  Which drivers were you installing?  What hardware do you have?  (Run the following.)

```
sudo lshw -C video
```

A little more info is needed to know what is causing your problem...

---

### Post by galaxys on 2012-11-29
Thanks for your help. I thought this thread was closed by a mod so I hadnt checked in a few days. I was installing drivers through software sources. I chose the stable version of nvidia and it started to install and failed at the end. I ran the code in the termincal and here is what I got.

  *-display        
       description: VGA compatible controller
       product: GF108 [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:6000(size=128) memory:d1000000-d107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:7000(size=64)

I dont know if this is needed but the PC is a Alienware M11x R3

Thank you for helping me out. BTW I am on classic genome now and it works fine. I simply cant use the desktop that it starts out with on 12.10.

---

### Post by audiomick on 2012-11-29
How old is that?

---

### Post by galaxys on 2012-11-29
I am sorry... how old is what?

---

### Post by audiomick on 2012-11-29
The machine, or specifically the video card.

---

### Post by galaxys on 2012-11-29
I got it at the end of 2011, I believe it was released earlier that year...

---

### Post by audiomick on 2012-11-29
I know you said the install of the nVidia drivers had failed, but maybe you could try this anyway. You said you can get to a terminal, so do
```
sudo nvidia-settings
```

With any luck you might get the settings thing open and be able to correct whatever is wrong.

That is a bit of a stab in the dark, though. I've actually seen quite a few posts lately complaining of icons and task bars disappearing, but I can't remember what the solutions have been, sorry.

---

### Post by galaxys on 2012-11-29
That brings up NVIDIA X Server Settings which tells me that "I do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X Server"

I run that command and I get

WARNING: Unable to locate/open X configuration file.

ERROR: Unable to write directory '/etc/X11'.

---

### Post by galaxys on 2012-11-29
I was searching and tried these steps with no luck either...

 sudo apt-get update 
sudo apt-get -f install --fix-missing 
sudo apt-get install build-essential 
sudo apt-get install linux-headers-generic 
sudo apt-get remove --purge nvidia-current 
sudo apt-get remove --purge nvidia-settings 
sudo apt-get install nvidia-current 
sudo apt-get install nvidia-settings 
sudo reboot

---

### Post by audiomick on 2012-11-29
Ok, I believe the stuff you listed in your last post should have cleaned out any relics and leftovers and installed the nVidia drivers new.

To do this
> **galaxys said:**
> ... (just run 'nvidia-xconfig' as root), and restart the X Server"

do
```
sudo nvidia-xconfig
```
and then log off and log back on (or reboot).

As far as I remember, that will create the /etc/X11/xorg.config file if it isn't there already. Ubuntu doesn't use that file for screen configuration by default anymore, but the nvidia proprietary driver still does.

Having done that, if things are still strange, you might like to try
```
sudo nvidia-settings
```
again.

I am still guessing, but that is what I would do at this point.

---

### Post by galaxys on 2012-11-30
Ok I ran that first code and logged off and back on and now my graphics are way jacked up. My screen is in the shape of a square and everything is enlarged/blurry and I have two black bars on either side of the screen each about 2 inches thick running all the way vertical with the screen.

---

### Post by audiomick on 2012-11-30
So did you try the nvidia-settings again? Amongst other thíngs, that lets you change the apect ratio, which would get rid of the black bars at the sides.

---


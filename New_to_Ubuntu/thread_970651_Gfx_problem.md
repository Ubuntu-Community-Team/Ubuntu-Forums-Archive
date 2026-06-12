---
title: "Gfx problem?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Natocytes on 2008-11-04
I'm getting lines flickering through my screen. Mostly when i have Firefox or Pidgin open(few others as well). Does anyone know what might cause this?

I'm extremely new to Ubuntu. I don't think it's my videocard. I just bought an ATI Radeon 7000.

---

### Post by Peter09 on 2008-11-04
Most probably is the video driver.

Can you post the output from the terminal command

```
lshw -C display
```

---

### Post by Natocytes on 2008-11-04
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV100 QY [Radeon 7000/VE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8

---

### Post by Peter09 on 2008-11-04
Do not think you have the right driver running.
Check in System->Administration->Hardware Drivers

See if there is a third party driver waiting to be activated.

If not try booting into recovery mode and reconfiguring your x server.

---

### Post by Natocytes on 2008-11-04
Thanks for the quick replies.
There's nothing in the driver list. I know how to boot into recovery mode, but I've no idea how to configure the x server.
Is it something basically self explanitory? I don't wanna mess anything up.

---

### Post by Peter09 on 2008-11-04
You will just get a menu with that option in. (which version of Ubuntu are you using?)

---

### Post by Natocytes on 2008-11-04
8.04 hardy. If I did that x server thing right, I don't think it worked.

Can I install the drivers from the disc with Wine? 
Sorry if that's a dumb question. I'm slowing learning about all this.

---

### Post by Peter09 on 2008-11-04
With Hardy, in a terminal

```
sudo apt-get install envyng-core
```
then
```
sudo envyng-t
```

and follow the instructions.

with any luck it will setup your drivers

---

### Post by Natocytes on 2008-11-04
EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.




Should i do manual install?

---

### Post by Peter09 on 2008-11-04
Ouch - not sure - is your card a new type?

---

### Post by Natocytes on 2008-11-04
No. I think it's not more than a couple years old. The box says it works with Vista.

---

### Post by Peter09 on 2008-11-04
Here is a bug report about the problem.
There appears to be a fix using the LiveCD. It may be fixed in Intrepid.

[https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-video-ati/+bug/212510](https://bugs.launchpad.net/ubuntu/hardy/+source/xserver-xorg-video-ati/+bug/212510)

---


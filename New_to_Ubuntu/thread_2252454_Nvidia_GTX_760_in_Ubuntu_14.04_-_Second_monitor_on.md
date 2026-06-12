---
title: "Nvidia GTX 760 in Ubuntu 14.04 - Second monitor on DVI-D not detected"
date: 2014-11-12
forum: New to Ubuntu
---

### Post by Vijayanand_V on 2014-11-12
Have been trying to get dual monitor set up. My display card is NVidia GTX 760 and has a DVI-I (DL) and DVI-D (DL) [also has a HDMI and DP output]. My monitors are Dell-1715S and have VGA and DP in. 

I have a DVI-I to VGA and DVI-D to VGA adpaters to connect to the monitors.

Nvidia-settings recognises only 1 monitor. The monitor connected to DVI-I is working, but the monitor connected to DVI-D is not working.

NVIDIA Driver Version : 331.38

When i try 'xrandr' on terminal get the following output

DVI-I-0 connected primary ......
DVI-I-1 disconnected....
HDMI-0 disconnected....
DP-0 disconnected....
**DVI-D-0 disconnected...**
DP-1 disconnected

Have connected monitor thro DVI-D.

Both monitors function normally and cables are fine too. Tried checking switching monitors and cables  - they work fine.

Need forums help to sort this out. Thanks a ton.

---

### Post by Vijayanand_V on 2014-11-13
Finally the issue is with the DVI-D to VGA adapter. It seems what I have is not a "converter".

So will try with a new DP cable and report later today.

---

### Post by Vijayanand_V on 2014-11-13
Works like charm. DVI-D to VGA was the issue.

But the resolution of the screens are different. DVI-0-1 is at 1152x864 and DP1-0 is at 1280x1024.

---


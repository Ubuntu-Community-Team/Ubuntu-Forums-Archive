---
title: "Q-connecting TV to PC"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by paker on 2012-03-24
Goal: to watch hulu dot com on TV

Is there a way to switch between monitor and TV? One at a time. Current PC monitor is connected to DVI.

Video card: GeForce GT240 (nVidia), has DVI VGA HDMI.
TV: has VGA and HDMI.

I just connected PC HDMI to TV HDMI. TV doesn't recognize the HDMI port. Apparently, no signal there. But if I power off PC, disconnect DVI to PC monitor,connect HDMI to TV, and power on PC, it works. Is there a way to switch back and forth without connecting/disconnecting and rebooting?

Thanks.

---

### Post by paker on 2012-03-31
I found the solution: disper. 

I connected PC monitor to DVI and TV to HDMI and installed disper.

sudo add-apt-repository ppa:disper-dev/ppa
sudo apt-get update
sudo apt-get install disper

Run disper, "disper -l". Both the TV and monitor were recognized with correct native resolution. From there, it is a matter of running a simple command, "disper -s" or "disper -S". On my setup, "disper -s" turns off monitor and turns on TV. "disper -S" switches back to monitor. Yours may be reversed.

PS: I have no dual monitor setup. I just plugged TV to HDMI port of the video card. No need to add resolution to the disper command. I think "disper" will work between DVI and VGA, too. I haven't tried it myself.

---


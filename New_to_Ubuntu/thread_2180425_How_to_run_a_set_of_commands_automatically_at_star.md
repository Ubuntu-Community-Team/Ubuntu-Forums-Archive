---
title: "How to run a set of commands automatically at startup"
date: 2013-10-12
forum: New to Ubuntu
---

### Post by gbooty on 2013-10-12
My wireless driver doesn't load at boot. I have to re-make the file every boot, if I just do "sudo insmod wl.lo" there is an error. 

BCM4313 card is horrible, I spent a lot of time getting it to work the way I need it to, this is just a minor inconvenience.

I do this everytime at boot:

cd Downloads
cd lib
make clean
make API=CFG80211
sudo modprobe lib80211
sudo modprobe cfg80211
sudo insmod wl.ko

I am curious the best way to do this. gnome-session-properties only starts up programs, where as I need to run these exact commands.

---

### Post by tgalati4 on 2013-10-12
I don't understand why you can't simply load the modules (lib80211 and cfg80211 and wl.ko) each time you boot.  It doesn't make sense to me why you have to remake the modules each time.

You would normally list them in /etc/modules so that they load manually at each boot.  Have you tried that yet?

Just add the following lines to /etc/modules:

lib80211
cfg80211
wl

I'm running a bmc4311 and it uses the b43 driver.  The driver includes the firmware for the 4313 card.  Is there a reason that you are not using b43?

tgalati4@Mint14-Extensa ~ $ modinfo b43
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
**firmware:       b43/ucode13.fw**
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5C5408969167493023BD033
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

---


---
title: "Screen tearing with GT 730M (and no Sync to VBlank option in Nvidia settings)"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by 7blackandblue7 on 2014-08-23
I've got problems with screen tearing while using Geforce GT 730M (GPU is Optimus with additionally Intel 4000). Tearing appears during scrolling websites, watching movies, playing games etc. I've read on many forums that it should be checked Sync to VBlank option in Nvidia X Server Settings in OpenGL Settings but I don't have such option (there's only "Use Conformant Texture Clamping" which is marked).

Now I'm using nvidia 340.32 drivers from *xorg-edgers/ppa* but the issue was the same with 331.38 drivers from repository. With Linux Mint (my first linux at all) also the same. So far I've tried for example to set Nvidia Settings on "prefer maximum performance" or to add to */etc/environment/* the following: 

    CLUTTER_PAINT=disable-clipped-redraws:disable-culling
CLUTTER_VBLANK=True 

Nothing works. I really need your help and every try is welcomed. If it matters, in Windows 7 there was no problem with my GT 730M.

Regards

---

### Post by cariboo on 2014-08-27
I've got a GeForce 750 in my system, and I'm using the latest Nvidia 343 drivers from the xorg-edgers ppa. Evrything works without any problems here. To enable the ppa use the following commands:

```
sudo apt-add-repository ppa:xorg-edgers/ppa
```

Then run the following commands:

```
sudo apt-get update && sudo apt-get install nvidia-343
```

Reboot, and check if the problem still exists.

---

### Post by mc4man on 2014-08-27
> Geforce GT 730M (GPU is Optimus
If you're using nvidia-prime then there is [no possibility of vsync yet]("https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1260128")
Maybe bumblebee would treat you better for games. For videos Nvidia offers no advantage over Intel on optimus laptops,  here I only use Intel & vids are fine
(that includes very high bitrate vids over 40 Mbps

---

### Post by 7blackandblue7 on 2014-08-28
*cariboo907*, thnx for help but it doesn't seem to work.

*mc4man*, I've heard that bumblebee has difficulties with Ubuntu 14.04 Unity so I've never tried it before to be honest. I found an installation commands that worked for me so bumblebee solved the problem. THANK YOU.

---


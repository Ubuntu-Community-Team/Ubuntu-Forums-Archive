---
title: "Step by Step instructions to get nvidia driver installed under 8.10?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by gregphil on 2008-11-08
When I updated to ubuntu 8.10 (from 8.04.1) the vidio drivers reverted to the non-3D (brain dead) GPL drivers.  How can I get "restricted" Nvidia drivers working under Ubuntu 8.10 or Kubuntu 8.10?

The video card is a GeForce4 MX-8X card (MX440 8X) The brand is MSI.

My menus show the "system-administration-hardware drivers" entry, but when I click on it the dialog box has no available drivers shown.

Clicking on "system-administration-Nvidia X-server settings" says I am not using the NVIDIA X driver and suggests I run 'nvidia-xconfig' as root.  If I do that the X server video will only run in "low rez" mode  (I have a 1980 x 1200 LCD monitor).  So I restored teh saved xorg.conf and am back to full resolution but without any video effects.

Can someone please explain the step by step process a user is susposed to follow to get the video driver enabled under 8.10?

Thank You.
:confused:

---

### Post by alienexplorers on 2008-11-08
Use Envyng which can be loaded using:
> sudo apt-get install envyng-core
Once loaded type in terminal:
> sudo envyng -t
select 1) Load Nvidia Driver
select 2) 96.43.09 driver
wait for the driver to load and then reboot
open System>Preferences>Appearence
goto to the Visual Effects Screen
select Extra.
If you get a failure, just reselect Extra and try again.

---


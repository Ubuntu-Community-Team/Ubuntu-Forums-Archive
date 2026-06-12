---
title: "Update makes video driver wrong and EnvyNG doesn't start anymore"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by kramer65 on 2008-10-30
Hi,


I just upgraded to 8.10 just now and after my restart the old metacity thing was displaying again which makes me thinkthe videodriver is not working anymore.

About half a year ago I installed the video driver using EnvyNG which worked perfect. I now wanted to start EnvyNG again to install the driver again but EnvyNG doesn't start up anymore.

Any ideas?

---

### Post by alienexplorers on 2008-10-30
You need to start envyng like this:
> sudo envyng -t

---

### Post by kramer65 on 2008-10-30
I tried many many things in the meantime. I uninstalled and reinstalled envyng again. Reinstalled the driver that worked before but it doesn't do the trick anymore. I tried installing other drivers using the EnvyNG command line and using the Hardware drivers option in the system menu of Ubuntu.

Nothing worked.

Can anybody help me out here? I thought 8.10 would be making my computer progress, insteead of distress.

All help welcome!!

---

### Post by Zzl1xndd on 2008-10-30
Give this a try 

sudo dpkg-reconfigure xserver-xorg

follow it through and select the proper options.

---

### Post by kramer65 on 2008-10-30
sorry, posted my previous post by mistake again...

wait, let me try what you say...

---

### Post by phidia on 2008-10-30
The dpkg-reconfigure command doesn't provide any choices or selections to make since hardy and xorg 7.4

You can try > sudo dpkg-reconfigure -phigh xserver-xorg but that isn't considered the way to correct x anymore either.

Instead boot in recovery mode and enter "xfix".

---


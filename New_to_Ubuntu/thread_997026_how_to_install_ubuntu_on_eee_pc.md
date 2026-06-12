---
title: "how to install ubuntu on eee pc"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by bahsarie on 2008-11-29
how

---

### Post by w4ett on 2008-11-29
Probably the easiest method is to use Eeebuntu [http://www.eeebuntu.org/](http://www.eeebuntu.org/)

---

### Post by silkstone on 2008-11-29
I'm running Ubuntu-eee on a 901, and am very happy with it.

Go to [www.ubuntu-eee.com](www.ubuntu-eee.com) and download the ISO file. copy this to a USB stick (1GB or larger) using UNetBootin (Windows or Linux).

Ubuntu-eee is based on Hardy but uses the Array kernel which makes wi-fi and other things work out of the box. It saves installing the Array kernel separately.

You can boot from this either by pressing Esc during boot or by pressing F2 and changing the boot order. You can try it without changing anything, before deciding to install.

If you do install it, choose Manual partition, delete all existing partitions on sda and sdb (sdc will be your USB stick). Then format sda as / and sdb as /home. There is no need for a swap partition.

When it is up and running, check for a rogue cdrom entry in /etc/fstab caused by Ubuntu thinking that your USB stick was a cdrom drive. If there is a cdrom line, gksudo gedit /etc/fstab and either delete the line or comment it out.

If you have a 901 or any version with silver function keys, you can also run the Elmurato scripts which make these do something useful.

You may also need to enable the webcam (if you have one) in the BIOS.

Hope that helps.

---

### Post by starcannon on 2008-11-29
I like to set it up myself; if you prefer to set things up yourself then a great resource is:
[http://array.org/ubuntu/](http://array.org/ubuntu/)
Another great resource for all things Eee is the eeeuser.com wiki; it contains a lot of walkthroughs and tutorials; you can find it at:
[http://wiki.eeeuser.com/](http://wiki.eeeuser.com/)

And of course if you get stuck on some part of your install, these forums are excellent to get it moving again.

I have a 2g, a couple of 4g's, and an 8g, they all work great; though I found the 4g to be the easiest to set up.

GL and Have fun

---


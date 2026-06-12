---
title: "Failed to boot after installing Tuxonice"
date: 2016-07-16
forum: New to Ubuntu
---

### Post by mohammadbagheri2010 on 2016-07-16
I wanted to enable hibernate mode on ubuntu 16.04 LTS on my Lenovo laptop and i followed this > [http://askubuntu.com/a/763516/562389](http://askubuntu.com/a/763516/562389).
  And i also changed ResultActive=no to ResultActive=yes for 
  [Disable hibernate by default in logind], [Disable hibernate by default in upower]
  in this file /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

  First time i used hibernate option on GUI, it turned the computer off  and when i turned it on and tried to boot ubuntu, a screen appeared  displaying that it's loading a kernel and reading data(not quite sure  about exact message). After that there was just an underline(_) on top  left corner. I could user alt+F4 to go into non-graphical login.

  So i rebooted the laptop and it booted fine except that displaying something more than usual on boot!!
  [ 13.625137] iwlwifi 0000:03:00.0: Unsupported spix structure
  Now i'm not able to hibernate(just turns off my laptop, and not  turning on properly) and also see an additional message on normal boot.
  First, I want to get rid of that message.
  Second, I want to normally hibernate my laptop...
  Thanks for your answers.

---

### Post by DuckHook on 2016-07-16
My suggestion is to remove Tuxonice. It involves a PPA (possibly destabilizes your system), is an obscure app that few on these forums are familiar with, and is therefore both a security risk and a barrier to getting help. Moreover, your steps up to now are a mixture of different apps and configuration changes that probably conflict with each other and therefore make it impossible to diagnose what is happening with your system.

Up to 14.04, the method that I used to hibernate was the "official" one referenced in one of the posts in your link. The direct link to that wiki page is: [https://help.ubuntu.com/16.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/16.04/ubuntu-help/power-hibernate.html)

I stopped using hibernation around the same time (about 2 years ago) because it often destabilized my system and corrupted data that I was working on. Some updates also rendered the system unrecoverable from hibernation. Altogether, to me, hibernation was more trouble than it was worth. However, I do understand why some people still want it. If so, then I recommend that you use the documented method (in the wiki above) and not some third-party app from a PPA.

If you take my advice and use the pm-hibernate method, you need to be aware that:

From the same post that you linked to, a bug exists that breaks pm-hibernate. The workaround is contained in the launchpad bug report referenced in your link. For convenience, I reproduce the link here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1575466](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1575466)

In particular, note:> ...will only work if the entries [Disable hibernate by default in upower] & [Disable hibernate by default in logind] are commented out or removed from /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla.

The entries in /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla does not supersede the entries in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla...so it is not enough to follow the instructions in the official wiki, you must also (for the time being) follow the instructions in the launchpad bug report. Note that this is a very ugly workaround because policykit files are subject to system updates and will revert to their defaults should *polkit* or any of its components get updated. However, if you keep a simple log of your manual changes to the system handy, you can always re-enter the changes after any update that affects these policykit files.

If you run pm-hibernate and Tuxonice concurrently, I cannot help you any further because I have no idea what Tuxonice does or what changes it makes to your system.

---

### Post by DuckHook on 2016-07-16
Further note for general readers: the launchpad bug report also indicates that the bug has been fixed for Yakkety (16.10) which is currently a development release (and therefore not stable enough for the typical user). Therefore, this fix may also find its way into Xenial's first point release due out next week (or it may not). The point is that, sooner or later, this bug is scheduled to be fixed. Until then, instead of adding unknown PPAs like kids in a candy store, use the aforementioned workaround and live more safely within the boundaries of the default system.

---

### Post by mohammadbagheri2010 on 2016-07-17
I really appriciate your help.Can you help through removing Tuxonice?
Is is just sudo apt-get remove tuxonice?
How to remove it's PPA?

---

### Post by DuckHook on 2016-07-18
> **mohammadbagheri2010 said:**
> I really appriciate your help.Can you help through removing Tuxonice?
Is is just sudo apt-get remove tuxonice?
How to remove it's PPA?Since you are using Xenial, you can now use:```
sudo apt purge tuxonice
```...assuming that tuxonice was the spelling that you used when you installed it. Then:```
sudo apt install ppa-purge
``````
sudo ppa-purge ppa:tuxonice/ppa
```This should clean out tuxonice and at least get your system to a state where multiple apps are not conflicting with each other.

---


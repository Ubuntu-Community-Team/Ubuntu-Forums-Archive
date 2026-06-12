---
title: "Failing to install build-essentials"
date: 2014-05-31
forum: New to Ubuntu
---

### Post by craig18 on 2014-05-31
in terminal I'm trying to do:
*sudo apt-get install build-essential checkinstall*

It starts to install but then gives me this:

[I]Media change: please insert the disc labeled
 'Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)'
in the drive '/media/cdrom/' and press enter[/I]

When this pops up I'm putting the ubuntu install iso dvd I made into the dvd drive of the desktop. Then I hit enter but nothing happens. I'm not sure if this is because I build this PC myself and maybe the dvd drive is named something different? Idk. Any suggestion on how to get this to work so build-essental installs would be great. I need this as the first step to compiling my wireless drivers which are currently giving me a headache. 

Ty in advance for your help.

---

### Post by mc4man on 2014-05-31
Open up Software & Updates ( software-properties-gtk from a terminal
It's likely that the Cdrom box is enabled, if so uncheck it (- screen
Then reload your sources & proceed to install  
(leave that box unchecked

---

### Post by Modanung on 2014-12-14
mc4man's answer didn't help for me with Xubuntu 14.04.1.
What did was the following:
```
sudo sed -i '/cdrom/d' /etc/apt/sources.list
```
[Solution source]("http://ubuntu.aspcode.net/view/635400140124705175700610/when-i-try-to-install-my-kernel-headers-i-get-please-insert-the-disc-labeled-ubuntu")

---

### Post by deadflowr on 2014-12-15
> **Modanung said:**
> mc4man's answer didn't help for me with Xubuntu 14.04.1.
What did was the following:
```
sudo sed -i '/cdrom/d' /etc/apt/sources.list
```
[Solution source]("http://ubuntu.aspcode.net/view/635400140124705175700610/when-i-try-to-install-my-kernel-headers-i-get-please-insert-the-disc-labeled-ubuntu")

Typically you can access the software and updates window through synaptic, if installed, the software center, if installed, the update manager, or using a terminal this
```
software-properties-gtk
```
In synaptic, and I believe the other gui programs, it's in one of the menu settings under the name software sources.

---


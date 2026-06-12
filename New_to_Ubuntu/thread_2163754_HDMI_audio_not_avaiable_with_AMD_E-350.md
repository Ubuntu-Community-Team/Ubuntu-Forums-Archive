---
title: "HDMI audio not avaiable with AMD E-350"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by Tassadar on 2013-07-19
Hi all,
 
I've a problem with a computer based on a AMD Zacate E350 APU (Asrock E350M1).
 
I've install Kubuntu 13.04 and latest Catalyst 13.06 BETA drivers. I  know installing an AMD Beta driver on Linux seems to be a suicide, when  stable drivers have many problems, but the truth is that the combination  Kubuntu 13.06 + AMD 13,06 beta works good even with Trinity APUs.
 
My problem is very simple, when I go to Phonom I can't select HDMI audio  output, and I've only analog and SPDIF. It can't be a hardware problem  since I've try Openelec and it has HDMI audio with no problems.
 
I've try to enable SPDIF audio in alsamixer (no idea of relation, but I've read this in a forum), but problem persist.
 
It seems like HDMI audio is disabled by defaulf, what is weird when I've  try just same software combination on a Trinity APU and works ok; but  Zacate doesn't.
 
Any idea or help??
 
Many thanks in advance

---

### Post by maddogz007 on 2013-07-20
By default HDMI Audio is disabled on kernel 3.0 +. 

Just do the following with elevated privileges via the terminal, you should be fine.

```


gksudo gedit /etc/default/grub

**Change the following  line:**

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

**to**

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"



```

Save and exit gedit & issue the following

```
sudo update-grub 

```

That's it. Reboot the machine

HTH

---

### Post by Tassadar on 2013-07-20
Many Thanks, maddogz007,

I've do this and when I restart and open Phonon it show a window with the message:

> KDE detected one or more internal sound devices were removed

Do you want KDE to permanently forget about these devices?
 This is te list of devices KDE thinks can be removed:

and shows for HDA, ATI SB, ALC892 Analog devices.

No matter what I do, HDMI audio doesn't appear.

Any idea?

Many thanks

---

### Post by kogz on 2014-02-17
I have E350M1 but I use 12.04.4 there, below guide is great (maybe just little outdated..) - I hope you'll find something interesting.

-> [http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html](http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html)

---


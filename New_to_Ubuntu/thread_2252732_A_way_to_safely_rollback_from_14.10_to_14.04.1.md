---
title: "A way to safely rollback from 14.10 to 14.04.1"
date: 2014-11-14
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2014-11-14
Hello, thanks for reading.
1st-Problem. My desktop after a reboot is completely "non-interactive" and "BLACK"---It's not "Wallpaper"--as when I reboot, or ut in a usb stick that auto mounts--I can SEE it pop up, and if I go throgh framework, and can see items are still on my desktop. 

I'm using XFCE4. 

And if all else fails, how can I roll back an upgrade like this? 

Thanks  for the assistance.

---

### Post by Bucky Ball on 2014-11-14
> **whereismymindat2 said:**
> 

And if all else fails, how can I roll back an upgrade like this? 

You can't. Full install is it. There's that question answered. ;)

Best to retitle your thread and edit so it is an attempt to fix your current issues with 14.10, if that is what you want to do. Be advised that 14.10 has nine months support while 14.04 LTS has five years. I'd go for the latter, but that's me. I have three partitions for the interim releases and other distros, but the LTS releases are where I live. I have NO inclination to upgrade the entire OS every six months. 

Good luck, whatever you decide.

---

### Post by Toz on 2014-11-14
> **whereismymindat2 said:**
> Hello, thanks for reading.
1st-Problem. My desktop after a reboot is completely "non-interactive" and "BLACK"---It's not "Wallpaper"--as when I reboot, or ut in a usb stick that auto mounts--I can SEE it pop up, and if I go throgh framework, and can see items are still on my desktop.
Its difficult to tell what the problem is based on this description. You'll need to provide more information (a screenshot might help as well). 

It _sounds_ like it _might be_ an issue with **xfdesktop** not running. xfdesktop is the component that manages the desktop (e.g. wallpaper, icons, right-click menu). Try running:
```
xfdesktop
```
...in a terminal window to start it up to see if that helps.

---

### Post by JKyleOKC on 2014-11-14
Sounds very similar to the problem you just solved for me. Wonder if it might have been some very recent update that's causing this to happen?

---

### Post by whereismymindat2 on 2014-12-04
Thanks everyone for the help. Jim, I rolled back, didn't help. Eventually kept going through Synaptic History (File--->History)---and from day broken, backwards, (re)installed all that looked like was part of XFCE. 
That fixed it. 

I'm also using APTIK now.  have used it once to recover (broken dekstop). If you are using Synaptic, you can find in there. 
Screen shot attached (extremely easy to use) 

Thanks all.
@Bucky Ball advice taken (re-title-future posts)--left current/original title so anyone in future see's this, will "understand" the advice :-)

---

### Post by Bucky Ball on 2014-12-05
Good news and wishing you all the best. Hope it all works out and good luck! ;)

---


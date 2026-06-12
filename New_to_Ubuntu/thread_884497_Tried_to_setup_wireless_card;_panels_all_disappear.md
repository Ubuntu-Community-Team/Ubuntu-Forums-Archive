---
title: "Tried to setup wireless card; panels all disappeared!"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Eikokubyo on 2008-08-09
Hey everybody - 

I'm running Xubuntu on a Toshiba Dynabook SS 1610.

I wanted to configure it to work with my Buffalo wireless card, so I inserted the card, booted up the computer, went to the hardware section, and enabled the wireless driver that was there.

It asked me to wait a few minutes while it updated some stuff, and then restart the pc.

Oddly, when I hit the "quit" button, the panels all disappeared but no Shutdown, Suspend etc menu came up. The empty desktop just sat there. 

So after a few minutes I did a hard reboot. Actually, what happened was the Shutdown menu came up as soon as I hit the power button. So I chose Shutdown and the computer hung during the shutdown process on the black screen.

So then I held down the button and achieved an actual hard reboot. 

Started the thing back up after a bit, and when it came up, my panels were still gone!

Luckily I had desktop shortcuts for Thunar and the terminal, so I was able to poke around, but I couldn't find any way to get to control panels without the standard GUI menus.

Oh, and to top it all off, I tried logging in to the Windows side, and now Windows isn't letting me log in. So I'm stuck from that side too. 

Is there any way to right the Ubuntu side, or, failing that, a way to reinstall without booting up the Windows side?

Cheers,
Ei.

---

### Post by SZ07 on 2008-08-09
I don't use xubuntu much but try this:

In the terminal type:

```
killall xfce4-panel
```

Then press alt+F2 and type:

```
xfce4-panel
```

That should restart the panels. You might also want to check this thread out: [http://ubuntuforums.org/showthread.php?t=352685](http://ubuntuforums.org/showthread.php?t=352685)

About logging into Windows, I believe that I've had something similar happen like that in the past. On ubuntu I have my windows drives mounted. Once I did a hard shut down and couldn't access one of the partitions even in windows. After restarting, I remounted the drives and then did a proper shutdown. This fixed the problem. Long story short, try mounting the windows partitions, then unmount them. Then restart and see if booting into windows works.

---

### Post by Eikokubyo on 2008-08-09
Awesome. It worked!

Thanks!

---


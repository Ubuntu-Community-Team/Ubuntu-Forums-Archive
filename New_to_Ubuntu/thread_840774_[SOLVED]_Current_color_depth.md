---
title: "[SOLVED] Current color depth?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bubba_169 on 2008-06-25
Im guessing this should be a really simple answer and I'm just missing something... But how can you tell what color depth you are currently running at?

I know how to change this using xorg.conf just need to know what I'm using at the moment?

---

### Post by RomeReactor on 2008-06-25
Hi. Try:
```
cat /etc/X11/xorg.conf | grep Depth
```
or:
```
cat /etc/X11/xorg.conf | grep depth
```

Since the new X server doesn't depend as much on xorg.conf now, it may not be there, but it's worth a try.

---

### Post by bubba_169 on 2008-06-25
Can I just assume that the DefaultDepth in xorg.conf is what my box is using now then? I just changed it that's why I want to test! I think in theory it should but with computers nothing is for definite, that's why I wondered if there was a tool to do a 'live' check?

---

### Post by RomeReactor on 2008-06-25
If you haven't restarted the display, it should be using whatever was there before; if this is the first time you've changed it, it should be 24 bit. Hopefully this can be [added to the Screens and Graphics]("http://brainstorm.ubuntu.com/idea/5095/") application later on.

---

### Post by bubba_169 on 2008-06-25
Well at the reason I changed it was to move it down to 16bit. 24bit works fine but I'd rather have smoother animations in compiz and less lagging on my scrolling in firefox.

Only down side I've noticed to 16bit so far is some gradients don't render quite right but its a sacrifice I'm willing to make :D

---

### Post by RomeReactor on 2008-06-25
I don't know if this has been corrected yet, but with nVidia cards you need to set the [colordepth to 24 for Compiz to work]("http://forum.compiz-fusion.org/showthread.php?t=5410"). If you have ATI or Intel, then it shouldn't matter.

EDIT: If you do have a nVidia card, you can install **nvidia-settings**; look for it in Synaptic, or to install from the terminal:
```
sudo aptitude install nvidia-settings
```
after it's installed you can find it in 'System->Administration->NVIDIA X Server Settings'. There, go to 'X Server Display Configuration' and on the second tab (X Screen) you should see a drop-down menu where you can see the current color depth and change it as well. If you have an ATI card and use the fglrx driver, you can change the color depth in the Catalyst control center.

---

### Post by bubba_169 on 2008-06-26
It's an old laptop with an ATI Radeon 7500 mobility 32mb built in. I think its using either the open source ati or radeon drivers. 16bit is working fine now apart from a few gradients not as smooth as before, as expected really!

---


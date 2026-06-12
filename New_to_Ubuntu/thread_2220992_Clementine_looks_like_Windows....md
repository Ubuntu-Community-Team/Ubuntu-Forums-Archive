---
title: "Clementine looks like Windows..."
date: 2014-04-30
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-04-30
I'm running Ubuntu 14.04 and have installed Clementine as music player.
Been working fine until yesterday, something odd happened.
When I launched Clementine, it looked like an application right out of Windows 98 (same grey window, sliders, everything).
I know Clementine is a fork of Amarok and if I'm not mistaken, the KDE desktop is cross-platform.

And it's a linux native app. It can't be running in Wine, can it  (it couldn't really, haven't installed Wine yet).

So, anyone have any idea how this happened ?

---

### Post by LastDino on 2014-04-30
Clementine was working fine on my 14.04 till I shifted to something different. Is this fresh install of 14.04? 

Have you tried uninstalling and installing Clementine? Maybe there is some conflict, did you install something else before getting this problem?

---

### Post by Dr. McKay on 2014-04-30
Yes, clean install of 14.04, all updates installed, installed clementine from software center.
Will try uninstalling and reinstalling...

---

### Post by avesummathat on 2014-04-30
I had the same problem (especially when launching from the sound panel). Seems there were a few bugs that weren't fixed before release. Try upgrading via this PPA:

ppa:me-davidsansome/clementine

Or download the .deb from their website: [http://www.clementine-player.org/downloads](http://www.clementine-player.org/downloads)

Now it all seems fine to me.

---


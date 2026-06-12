---
title: "Win 7 Pro RDP/VNC to Ubuntu 14 primary desktop"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by HeroHog on 2014-08-04
I am new to Ubuntu but am strong in Win 7 and am trying to find a way to use VNC or RDP to get to the main desktop on my Ubuntu 14 machine that you see when you log into the  machine from the console. I can RDP to a "sub" desktop instance just fine but that isn't what I am looking for as I need to be able to remote control the active console that is hooked to a big screen entertainment center via an HDMIor VGA (whichever works best) connection.

I am running a clean, fresh install of Ubuntu 14 with the latest patches on an Intel CPU Toshiba Satalite laptop with Dual Cores and 4 Gig RAM and 500 Gig drive space on an internal network over 5G WiFi and/or 1k gb eithernet.

Can someone please point me in the right direction?

Thanks in advance!

Speedy "HeroHog" Mercer

---

### Post by KevinVernon on 2014-08-04
Install dconf-editor: sudo apt-get install dconf-editor => Start it.
Navigate to: org => gnome => desktop => remote-access => Disable "require-encryption"

---

### Post by HeroHog on 2014-08-04
OK, done. Now pardon my ignorance... Now what??? Also, when I edited that file and closed the app, the file "gnome-system-monitor.desktop" showed up on my desktop. What should be done with that file and is it a saved copy of the old version or what?

Sorry for the clueless newbie questions but, Hey, ya gotta start somewhere! ;-)

Speedy "Herohog" Mercer

---

### Post by HeroHog on 2014-08-04
Never mind. I figured out what I needed.
I installed X11VNC and was able to use it along with TightVNC on my Win7 machine to access the primary desktop.
Thanks for the help!

---


---
title: "Flash crashes firefox periodically"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Keinestijl on 2008-07-14
When I upgraded to Hardy, sound in flash stopped working. I searched the internet and found a fix, but I didn't really know what I was doing. After some time I found that when a flash file opens sometimes firefox crashes. When it's playing it won't crash, maybe that helps..

I'm sorry if the answer is really easy to find, but I don't want to do more stuff I don't understand/ know will work. That's also the reason I posted this in absolute beginner talk, I'm afraid I'll need detailed instructions.

---

### Post by Vadi on 2008-07-14
Try reinstallinf flash and firefox. Go to System - Administration - Synaptic Package Manager, and search for "flash" (in 'name') and 'firefox'. Remove them both (there might be several packages).

Then, install firefox-3.0. Run firefox, go to youtube.com, and let it install the 'Adobe Flash' plugin.

Let me know if that helps.

---

### Post by Zero Prime on 2008-07-14
Odds are, that won't help.  This is a good way to force Flash from crashing Firefox.

First download and Install nspluginwrapper from here
[http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

Now install libflashsupport using the following command

sudo apt-get install libflashsupport



Now Run the following commands

sudo apt-get remove --purge flashplugin-nonfree

sudo apt-get install flashplugin-nonfree

Now restart Firefox.  One thing I do as a substitute.  Instead of going through the install of Flash in the instructions I download Flash Player 10.  Every now and then Flash content may gray out.  Hitting refresh when using Flash 10 and nspluginwrapper fixes this.

---


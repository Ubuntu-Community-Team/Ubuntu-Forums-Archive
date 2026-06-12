---
title: "Acer Aspire One Ubuntu Installation"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by rabellamy on 2011-11-04
I recently bought an Acer Aspire One . What is the optimal Ubuntu release to install on this netbook?
I am planning on using a bootable live USB that I will create using Unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)). Any tips on how to optimize my installation process will be appreciated.

---

### Post by Steeperton on 2011-11-04
I'm using standard Ubuntu 11.10 with no issues on a 5 year old (ish) Aspire One...

---

### Post by lkjoel on 2011-11-04
Is this a laptop or a desktop? Could you give me the full model?

---

### Post by rabellamy on 2011-11-04
lkjoel,
Acer Aspire One D257-13404

Steeperton,
How did you install 11.10? How much of the hard-drive did it take up?

thanks for the help!

---

### Post by Stovey on 2011-11-04
Aspire One is a "netbook" (a miniature laptop).  I put the Netbook Remix on an Aspire One, but found the normal release worked better for me.

Rabellamy, every time I have installed Ubuntu on my Netbooks, I have found that Unetbootin works best; you are on the right track.

---

### Post by lkjoel on 2011-11-04
I'd recommend either Xubuntu or Lubuntu.
Lubuntu is lighter, and has multi-level menu features, but Xubuntu has more extensions made for it.

---

### Post by mike555 on 2011-11-04
I use Xubuntu. 11.10 on my netbook

---

### Post by retchid on 2011-11-04
use unetbootin 
download linux puppy 5.28
put on usb
and of course boot from usb

30 seconds bootup everytime no matter what you put on it

how brill is that system

ssd drive is dying now so  just using 2gb usb as operating system (sandisk £4 and the 8gb sd card (for storage)

No longer need to bother with any Hard drives and slow  boots

(macpuppy is faster running but prefer 5,28 from linux puppy)

p.s. if you use linux puppy 5.3 (slackpuppy) mouse pad will be slow until you change the settings for the mouse

---

### Post by I2k4 on 2011-11-04
I have the same netbook and have been experimenting with Persistent Live USB installs for about a year, and I recommend that approach:  Live USB is not as responsive as a hard drive install but runs surprisingly well and you can be sure the OS will run better from the hard drive. Eventually, Persistent Live USB has gone buggy but it provides a fine experience.  

I used the PenDrive installer Ubuntu recommends, here with bullet proof step by step, but at step 2 set "persistence" on the installer, to allow settings and installations to be saved between boots: 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I now have Lubuntu 10.10 installed for dual boot on the Acer hard drive.  It does not have the Software Center, comes with fewer preinstalled applications, and is generally less user friendly than Ubuntu itself, but Synaptic Package Manager is fine for adding what you want and getting rid of what you don't.  Chromium browser is installed by default and I replaced it with FireFox and Chrome.  

I found the version 11 Ubuntu and Lubuntu much too resource demanding for the little netty - very disappointing.  Plain old Desktop Ubuntu 10.10 runs quite well, and comes with OpenOffice and FireFox out of the box and has the software center, and you'll likely find it more user friendly to start.  I liked Xubuntu 10.10 but it would not recognize the hard drive on my Acer, so I dropped it.  I would avoid the 10.10 "Netbook Edition" as I found it very sluggish on the netbook (and don't like the Unity user interface, either.)

My main tips for running from USB are 1) run as much in RAM as you can configure your applications to do, e.g. with FireFox about:config tweaks, maximize RAM and minimize disk caching in Google Earth, etc. and b) configure your software to locate swap files, caches, etc. on the hard drive instead of the USB drive wherever possible, for example in GIMP.  I also disabled automatic updating and am careful to only install one or two packages at a time, since the laggy USB drive is too slow to handle large, difficult installations.  I also recommend Bleachbit to clean up unnecessary gunk from the USB drive - I had problems with "Janitor" that comes on the Ubuntu installs, but no problems with Bleachbit disk cleanup.

---

### Post by Steeperton on 2011-11-07
> **rabellamy said:**
> lkjoel,
Acer Aspire One D257-13404

Steeperton,
How did you install 11.10? How much of the hard-drive did it take up?

thanks for the help!

I've got the hard drive version, not the SSD, but the standard install took less than 5Gb, from memory. Downloaded ISO, then used startup disc creator to put on USB. Quick & easy!

---

### Post by Steel44w on 2011-11-07
I used pen-drive to install Ubuntu 11.10 on my Acer Aspire one kav60 everything as far as i can tell has worked right out of the box. used around 5 gigs of space.

Could be faster though. However it's faster than win xp.

Has anyone upgraded to 2 gigs of ram if so how much improvement did you notice.

---


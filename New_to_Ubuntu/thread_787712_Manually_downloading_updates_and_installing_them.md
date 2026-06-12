---
title: "Manually downloading updates and installing them"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Gr3ghammett on 2008-05-09
My laptop is partitioned.  I have win vista on one (X^P) and Ubuntu (Hardy Heron) on the other.  Vista has internet connectivity, but Ubuntu doesn't (i can only get internet wirelessly, and I'm having wireless card issues on ubuntu that i'm in the middle of working out).

My question is, for me to be able to fix my wirless issue, I need to pull and install updates.  Is there anyway I can download them on my vista partition, and manually install them on my ubuntu partition (transferred via flash drive of course)?  This will also be helpful for getting .mp3 codecs and DVD playability.  I really dont care as much about 3rd party updates, just kernel updates from the ubuntu.com repository.  Any ideas?

Thanks in advance

---

### Post by kwacka on 2008-05-09
As you are not connected to the repositories, apt will not be able to identify that updates are available.

You can go, in Vista, to the mirrors and download and, as you say, transfer to your linux partitions using a usb stick, although you should be able to see your Vista partition from within Ubuntu.

---

### Post by mikewhatever on 2008-05-09
Try [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/).

---

### Post by logos34 on 2008-05-09
updates may be a problem as kwacka said, although for everything else you can try this:

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

---

### Post by Gr3ghammett on 2008-05-10
Got it.  I went to packages.ubuntu.com and manually downloaded the ones I needed there (and got the dependencies from the ubuntu cd).  My wireless issue is fixed now that I got the Build Essential package and now am automatically downloading the rest of the updates.  Thanks for the help.

---


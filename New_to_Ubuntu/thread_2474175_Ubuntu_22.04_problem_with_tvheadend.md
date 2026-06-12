---
title: "Ubuntu 22.04 problem with tvheadend"
date: 2022-04-23
forum: New to Ubuntu
---

### Post by macchese on 2022-04-23
Hi to all.
When I try to install Tvheadend, from official repositories, fully functional in the previous version, I get this error.  **libssl1.1 (> = 1.1.0) but it is not installable**. The downloadable version from Snap is useless as it installs but does not work. Thanks

---

### Post by tea for one on 2022-04-23
I have installed the Snap (version 4.2.8) of TVheadend and it seems to be OK.
It recognised my DVB-T2 tuners and scanned channels.
Watch TV and timed recording is fine.
Channel list successfully exported to VLC and converted to xspf format.
Watch and record with VLC functions OK.

When you say that "the snap version does not work", it would be helpful to supply more details.

Open?
Recognise your TV Tuner?
Scan?

You could try this ppa [https://launchpad.net/~mamarley/+archive/ubuntu/tvheadend-git](https://launchpad.net/~mamarley/+archive/ubuntu/tvheadend-git)
I used this ppa for approx 3 years with no problems but the current version with Ubuntu 22.04 failed to complete a channel scan, hence my adoption of the snap version.

---

### Post by macchese on 2022-04-23
Thanks for the answer. Snap installs it but despite seeing the 2 tuners, it does not search me on the digital terrestrial. And the channels found on the sat, it does not map them. I also tried the version of mamarley, but this one, after having found the canals, he maps none.

---

### Post by tea for one on 2022-04-23
Another alternative is Kaffeine, available from the universe repository.
[https://www.linuxtv.org/wiki/index.php/Kaffeine](https://www.linuxtv.org/wiki/index.php/Kaffeine)
It is a KDE application so it may well pull in quite a few dependencies if you are using Ubuntu with Gnome 42.

TVheadend may have taken control of your TV Tuner.
You will probably have to remove all the TVHeadend configuration so that Kaffeine can recognise your device.

---

### Post by macchese on 2022-04-23
Thanks.
I try it

---


---
title: "packages held back stuck at kernel 3.0.0.11"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by robert shearer on 2011-09-29
For several days now apt-get upgrade has returned...
> The following packages have been kept back:
  deja-dup linux-generic linux-headers-generic linux-image-generic network-manager-gnome 


Meanwhile it upgrades a whole slew of other packages each time but not these.

I see some threads where posters are running the 3.0.0.12 kernel and so assume that the linux headers etc above are for that kernel ? but I seem to be stuck at 3.0.0.11 and sudo grub update has no effect.

Suggestions most welcome,
Thanks, Bob.
(running gnome-session-fallback if this has any bearing )

---

### Post by Harry33 on 2011-09-29
You should install synaptic for higher quality upgrading/updating.
That is the best way to find out why some packages cannot be installed.
Usually a package cannot be updated because of its dependency on another packages or higher version of other packages.
It may also be that a given package is part of a set of packages.

There is no problem with kernel updating to 3.0.0-12.13.
The meta packages are also in Oneiric repos.

You should perhaps use the main server for Oneiric repos.

---

### Post by plucky on 2011-09-29
> **robert shearer said:**
> For several days now apt-get upgrade has returned...


Meanwhile it upgrades a whole slew of other packages each time but not these.

I see some threads where posters are running the 3.0.0.12 kernel and so assume that the linux headers etc above are for that kernel ? but I seem to be stuck at 3.0.0.11 and sudo grub update has no effect.

Suggestions most welcome,
Thanks, Bob.
(running gnome-session-fallback if this has any bearing )

Try ```
sudo apt-get dist-upgrade
``` from a terminal, as that will tell you what it needs to do to install the held back packages.

Make sure it doesn't remove anything important before you give it the go ahead.

Good Luck

---

### Post by robert shearer on 2011-09-29
thanks for the replies..:D

Surprisingly, Harry33's suggestion to change to the Main server did the trick.
 (although download speeds were slower than a roach doing backstroke in treacle )

All held packages installed and I reverted to the New Zealand server.
No problems encountered and local download speeds are peachy again.

thanks again,
cheers, Bob.

---

### Post by Harry33 on 2011-09-29
> **robert shearer said:**
> thanks for the replies..:D

Surprisingly, Harry33's suggestion to change to the Main server did the trick.
 (although download speeds were slower than a roach doing backstroke in treacle )

All held packages installed and I reverted to the New Zealand server.
No problems encountered and local download speeds are peachy again.

thanks again,
cheers, Bob.

OK, fine that the issue is now fixed.
Generally, the local servers are lagging behind one or two days.
So, using the main server you get the updates sooner.
The drawback, however, is that this way you will get the bugs sooner too.

---


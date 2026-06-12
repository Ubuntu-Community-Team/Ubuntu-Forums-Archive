---
title: "Btrfs Support For Ubuntu's Update Manager"
date: 2011-05-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dext on 2011-05-13
> Eventually we will see Ubuntu Linux deploy Btrfs as the default file-system. While we will likely not see the switch from EXT4 to Btrfs with Ubuntu 11.10, there is work underway on Btrfs integration support into Ubuntu's Update Manager. 

With Fedora 13, Red Hat introduced system roll-back support whereby anytime a yum transaction takes place for installing a new RPM package on a Btrfs root file-system, a snapshot will be created. Btrfs supports efficiently creating copy-on-write snapshots. Fedora has been quicker to adopt Btrfs installation support and its features, but now Canonical is finally supporting this path. 

Ubuntu 10.10 gained Btrfs installation support as an alternative to using the EXT4 default. With Ubuntu 11.10 the default will more than likely be EXT4 still, but the update-manager program should gain snapshot creation support similar to the yum plug-in. 

For Ubuntu 11.10 "Oneiric Oncelot" is to call apt-btrfs-snapshot on update-manager build. A cron job would then delete these old Btrfs file-system snapshots after a defined time of being unused. 

One of the features worked on in the Fedora world was to also add GRUB support for booting to older Btrfs snapshots and the plan is to implement similar functionality under Ubuntu. Ubuntu would also like to have failure detection support in GRUB with a friendly-recovery menu.

As far as when Ubuntu will likely deploy Btrfs as the default Linux file-system for new installations, that probably will not occur until Ubuntu 12.10 due to Ubuntu 12.04 being a Long-Term support release where Canonical is much more conservative about making invasive changes. 

More details from the UDS Budapest notes.
 [http://www.phoronix.com/scan.php?page=news_item&px=OTQzNw](http://www.phoronix.com/scan.php?page=news_item&px=OTQzNw)

---

### Post by VinDSL on 2011-05-13
I was wondering about this...  :D

```

[ 3226.125592] Btrfs loaded

```

It was on the last line of the Dmesg.txt output, in a UbuOO bug report that I submitted.

Interesting times!

---

### Post by Yofel on 2011-05-15
I was positively surprised with btrfs in natty, even though it needs improvements on the performance side and using snapshots is rather complicated at the moment. I wrote a [blog post]("http://kyofel.wordpress.com/2011/05/15/btrfs-in-natty/") about my time with btrfs in natty so far.

The future looks bright though :D

---


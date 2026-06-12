---
title: "How to remove ALL traces of mono"
date: 2009-06-01
forum: Programming Talk
---

### Post by UbuKunubi on 2009-06-01
Hi folks,
Im not sure where to ask, so Im asking here, how do i remove all traces of mono?

For my purposes it is not required, and that includes the directories.
When I usse the 'rm' command I'm finding error messages telling me that there is no such file or directory when I try to empty it out for deletion!

Personally the difficulty encountered in trying to remove this is giving me an unpleasant reminder of the behavior of windows, and why I switched to Ubuntu  in the first place.

So, I'd be very grateful for any advice on how to remove this!

Many thanks,
Ubu

SOLVED:

rm -fr mono

---

### Post by crdlb on 2009-06-01
Err ... ```
sudo apt-get remove mono-common
```

You should never remove packaged files manually.

---

### Post by happysmileman on 2009-06-01
> **UbuKunubi said:**
> Hi folks,
Im not sure where to ask, so Im asking here, how do i remove all traces of mono?

You should probably ask your doctor, rather than the internet.

---

### Post by directhex on 2009-06-01
For Jaunty: mono-common and mono-jit are the packages to purge.

Additionally, there is a bug in Jaunty's release which can leave some cruft on disk - please remove /usr/lib/mono manually AFTER (and only after) removing the packages above.

---

### Post by UbuKunubi on 2009-06-02
> **crdlb said:**
> Err ... ```
sudo apt-get remove mono-common
```

You should never remove packaged files manually.

Worked a charm!

Thanks for your help.

Ubu.

---

### Post by UbuKunubi on 2009-06-02
> **happysmileman said:**
> You should probably ask your doctor, rather than the internet.

Ha ha ha!
He keeps telling me I'm way beyond hope and help..
But thanks for the reminder (now wheres the pills!)

---

### Post by zcat on 2009-06-04
To completely remove mono and the packages that depend on it;
```
sudo apt-get remove --purge mono-common libmono0
sudo apt-get --purge autoremove

```

To prevent it from being accidentally reinstalled download and install the Mononono metapackage, which sets up an intentional conflict with the real Mono packages.

```
wget http://tim.thechases.com/mononono/mononono_1.0_all.deb
sudo dpkg -i mononono_1.0_all.deb

```

---

### Post by directhex on 2009-06-04
> **zcat said:**
> To prevent it from being accidentally reinstalled download and install the Mononono metapackage, which sets up an intentional conflict with the real Mono packages.

Some of. mononono is broken by design and will not work for Karmic.

Correct behaviour is to add the following to /etc/apt/preferences:

```
Package: XXXXXX
Pin: release a=rabidparanoia
Pin-Priority: 999
```

Do so once per package, for the following packages, replacing XXXXXX:
Karmic (soon): mono-runtime, libmono0
Jaunty and below (and Karmic today): mono-common, libmono0

---

### Post by UbuKunubi on 2009-06-08
zcat,

Thank you, your post if very helpfull.
Cheers,
Ubu

---

### Post by Mirge on 2009-06-08
> **happysmileman said:**
> You should probably ask your doctor, rather than the internet.

Off-topic, but I like your signature:

> Saying that you "could care less" about something is implying that you **_DO_** care about it, regardless of common usage.
Using it as a way of saying you don't care is simply wrong.

That is one of my BIGGEST pet peeves... I absolutely cannot stand it when one of my friends says "I could care less"... if you CAN care less, that means you care at least a little bit. When I try to point that out to them, they don't care... lol.

---


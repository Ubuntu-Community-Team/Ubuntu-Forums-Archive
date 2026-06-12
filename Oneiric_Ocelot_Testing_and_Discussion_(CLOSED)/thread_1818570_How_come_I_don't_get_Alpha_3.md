---
title: "How come I don't get Alpha 3?"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-08-05
Hi, 

I got Alpha 2 about 2 weeks ago, and have kept updating regularly via "sudo apt-get update" and "sudo apt-get upgrade".  Just did the same 2 minutes ago.  Linux-header and linux-image are not among the held-back packages:

```

The following packages have been kept back:
  gnome-control-center gnome-control-center-data indicator-messages
  indicator-messages-gtk2 indicator-session indicator-session-gtk2
  libunity-2d-private0 unity-2d-launcher unity-2d-panel unity-2d-places
  unity-2d-spread

```

However, even after reboot my kernel is not as up-to-date as that of Alpha 3, i.e. kernel 3.0.0-7.9:

```

uname -r

3.0.0-7-generic

```

Any idea?  Thanks!

---

### Post by linuxman94 on 2011-08-05
Run a
```
sudo apt-get dist-upgrade
```
That will install the held back packages.

---

### Post by mc4man on 2011-08-05
Try uname -a

You shouldn't have any held packages, use synaptic to resolve
(and just because, -  click the reload button after opening synaptic

---

### Post by iClouseau88 on 2011-08-05
Hello mac4man & linuxman94,

Thanks for your reply. 

Synaptic > Reload > Linux-image 3.0.0-7-generic installed version 3.0.0-7.9.  Looks like I already got Alpha 3, despite both uname -r and uname -a showing 3.0.0-7-generic.  However, the held-back packages remain.  I am still reluctant to hit "apt-get dist-upgrade" for fear of messing up Oneiric. I am thinking perhaps some packages are being held back because some dependencies are still to be met.

Any suggestions?

---

### Post by MacUntu on 2011-08-05
There's nothing wrong here.

```
apt-cache policy linux-image-3.0.0-7-generic
```

---

### Post by meborc on 2011-08-05
> **iClouseau88 said:**
> ...I am still reluctant to hit "apt-get dist-upgrade" for fear of messing up Oneiric...

I **only** use ```
sudo apt-get update && sudo apt-get dist-upgrade
```

That is because before actually upgrading I go through the list and make an educated guess whether any breakage will follow. I have had 0 problems with dist-upgrading the last 2 months.

If you are running OO on a test machine/partition, dist-upgrade is the way to go

---

### Post by iClouseau88 on 2011-08-05
Thank you meborc for your reply.  I did "sudo apt-get update && sudo apt-get dist-upgrade". I no longer have held-back packages and now I get Alpha 3 in both Ubuntu and Kubuntu 11.10, even though uname -r still shows kernel 3.0.0-7-generic.

---

### Post by cariboo on 2011-08-05
Try:

```
uname -a
```

as meborc suggested, the result should look like this:

>  uname -a
Linux alexis-oneiric 3.0.0-7-generic #9-Ubuntu SMP Fri Jul 29 21:27:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


You won't get any indication anywhere saying you are using alpha 3.

---

### Post by jerrylamos on 2011-08-05
> **meborc said:**
> I **only** use ```
sudo apt-get update && sudo apt-get dist-upgrade
```

That is because before actually upgrading I go through the list and make an educated guess whether any breakage will follow. I have had 0 problems with dist-upgrading the last 2 months.

If you are running OO on a test machine/partition, dist-upgrade is the way to go

On Alpha 3 Live, I tried the update & upgrade and it wanted to upgrade 500 packages.  Well, did so, still no desktop, just a command line.

Alpha 2 running fine, ati radeon xpress 200.

Jerry

---

### Post by VinDSL on 2011-08-05
> **cariboo907 said:**
> You won't get any indication anywhere saying you are using alpha 3.
And, this confirms that there is no difference between a fully patched & mod'ed A2 install and A3, yes?


[INDENT](Click to expand)

[[img]http://vindsl.com/images/Screenshot at 2011-08-05 12:28:26(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-05 12:28:26.png")[/INDENT]

---

### Post by iClouseau88 on 2011-08-05
Hi,

uname -a also gives kernel 3.0.0-7-generic.

I do get Alpha 3 now, because:

Synaptic search: linux-image

```

linux-image-3.0.0-7-generic
installed version: 3.0.0-7.9
latest version: 3.0.0-7.9

```

:D

---


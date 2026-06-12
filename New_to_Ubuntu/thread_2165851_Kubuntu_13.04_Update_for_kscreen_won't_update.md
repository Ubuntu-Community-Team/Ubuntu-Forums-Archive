---
title: "Kubuntu 13.04: Update for kscreen won't update"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by Matt_Smigielski on 2013-08-06
Hello all,

I am running Kubuntu 13.04 and today I noticed an update for kscreen (via Muon Updater). When trying to update, it asks me to also update libkscreen1, to which I say OK. Then, I am back at Muon with no packages checked. If I manually check kscreen, it asks me to install libkscreen1 and remove libkscreen0, which I again say OK. Even after this, the Install Updates button is grayed out.

Doing a sudo apt-get upgrade, I get this:

The following packages have been kept back:
  kscreen
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

What does that mean?

---

### Post by Pondussi on 2013-08-06
sudo apt-get dist-upgrade? upgrade holt keine zusätzlichen Pakete rein.

---

### Post by Pondussi on 2013-08-06
Sorry, I was in a German forum at the same time ;). What I wanted to say: "apt-get upgrade" doesn't pull in additional packages, just updates existing ones. So if a package which is to be updated needs additional ones it is set on hold. Try "sudo apt-get dist-upgrade" instead.

---

### Post by Rob Sayer on 2013-08-07
I've had the same thing happen to me, but when I tried to mark it in muon update nothing much happened.

I then actually hit the check mark and it asked to OK removal of the old kscreen, which I allowed.

Then I got this:

> Version 1.0-0ubuntu1~ubuntu13.04.1:
This update was issued on 28/06/13 01:44 PM
  * SRU to Ubuntu 13.04 LP: #1195806

Version 1.0-0ubuntu1:
This update was issued on 25/06/13 07:18 PM
  * New upstream release. (LP: #1194491)

Version 0.0.92-0ubuntu2:
This update was issued on 08/05/13 01:11 PM
  * No change rebuild against updated libkscreen

Version 0.0.92-0ubuntu1:
This update was issued on 06/05/13 09:17 PM
  * New upstream release (LP: #1177333)
    - Drop upstream_l10n.patch, included upstream
    - Bump libkscreen-dev Build Depend to 0.0.92

And then it does nothing.  Muon greys out the Apply Changes button and I seem stuck in an endless loop.

I'm willing to try apt-get dist-upgrade but I'd still like to know what's going on with this.

---

### Post by Rob Sayer on 2013-08-07
OK, I just tried apt-get dist-upgrade. Voila ...

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kscreen
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

So that doesn't work either for me.

I don't know of any other apt-get command except do-release-upgrade, and I'm never going to use a pre release ubuntu release again if I can help it.  Ever.

---

### Post by Jonathan Precise on 2013-08-07
I had the same problem. However, I installed synaptic, opened it, and searched for libkscreen. Then I installed libkscreen1, which said that needed to remove libkscreen0 and update kscreen. I put OK and it updated kscreen perfectly!

[HR][/HR]
Hope this helps!

Jonthan

---

### Post by Rob Sayer on 2013-08-08
OK, I just installed linkscreen2 with synaptic.  I almost always use synaptic for installing software ... I actually prefer it for installing additional drivers ... but it never occurred to me to use it for an update.

It works so far (haven't rebooted yet) but I still think it should have worked with muon updater.

Thanks.

---

### Post by Rob Sayer on 2013-08-09
I rebooted and did another update.  Everything seems to work.  I can't mark this solved though.  It wasn't my thread originally.

---

### Post by screaminj3sus on 2013-08-14
"sudo apt-get install kscreen" is all that is needed to fix this.

---

### Post by StevenWR on 2013-09-07
someone mentioned missing dependencies in this update and i though AH HA 

sudo apt-get build-dep kscreen

Problem solved now it gladly updated after that.

---


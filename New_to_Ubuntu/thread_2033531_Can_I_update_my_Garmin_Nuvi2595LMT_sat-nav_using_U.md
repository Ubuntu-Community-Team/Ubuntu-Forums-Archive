---
title: "Can I update my Garmin Nuvi2595LMT sat-nav using Ubuntu?"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by bwallum on 2012-07-26
Hi

I would like to purchase a sat-nav for my car and find that they all use Microsoft software to updates maps and the like.

Does anybody have any experience in updating maps on a Garmin using Ubuntu?

---

### Post by Bufeu on 2012-07-26
Check [this site]("http://forums.gpsreview.net/viewtopic.php?t=12100") which links to [this thread]("http://ubuntuforums.org/showthread.php?t=231452").
Old, but it may work. You can install Wine via [this link]("apt://wine1.4"), or use the terminal:```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.4
```

I also found this site: [http://x2q.net/garmin-map-updates/](http://x2q.net/garmin-map-updates/).
You can also install [OSM]("http://www.openstreetmap.org/"), a free open source map project.

---

### Post by Zill on 2012-07-26
> **bwallum said:**
> ...Does anybody have any experience in updating maps on a Garmin using Ubuntu?
AIUI, it is impossible to update Garmin maps without using a Windows or Mac OS.  They *do* support Firefox (Garmin install their own "Dashboard" add-on) but *not* when running on a Linux OS. :-(

Although I have not tried personally, I understand that this does not run properly via Wine either.

I, and many others, have been complaining for years about this and I can only suggest that you contact Garmin and add your voice to the others demanding Linux support.

Incidentally, Garmin's arch rival, TomTom, also do not provide any Linux support for *their* devices.  IMHO, this is *particularly* hypocritical of them as they apparently use Linux and other GPL software within the satnav device itself!  It seems they are happy to take from the open-source community without giving anything back. :mad:

---

### Post by Zill on 2012-07-27
Well, I have just contacted Garmin again to see if the situation had changed and if they had finally "seen the light".  This is their response:
> Thank you for contacting Garmin Europe.

I am happy to help with your enquiry.

Unfortunately we do not support Linux operating systems; we only support
Windows and MAC Operating Systems.

I'm afraid we do not have any plans to introduce this.

I'm sorry for any inconvenience.

If there is anything else I can help you with then please let me know.
Alternatively you can search for a solution here: [http://www.garmin.co.uk/support](http://www.garmin.co.uk/support)

Kind regards,

Garmin Europe
I think we all have to shout a bit louder!

---

### Post by BBQdave on 2012-07-27
> **Zill said:**
> contact Garmin and add your voice to the others demanding Linux support.

Not sure if it is the same in Europe, here in the U.S. it is a hefty fee to update your Garmin maps. I ran into the same update issue (no linux support) 7 years ago with the purchase of a Garmin device. At first I was not happy, but then realized I did not want to pay the big fee to update the maps.

So I have been cruising along with a seven year old Garmin Map just fine (no system updates either). Let the Windows and Mac folks pay big update money, I am happy with Linux and no *Garmin update fees* :D

---

### Post by Zill on 2012-07-27
BBQdave:  Just the same situation in Europe I'm afraid. :-(

However, Garmin do generally offer the *first* map update "free" and this can be useful if your device was "on the shelf" for a while before purchase.  Garmin also offer device software updates from time to time and, as with most software, this sometimes(!) provides improvements in functionality.

So, I basically have to agree that the ability to update is not *essential* but still is, in my view, *desirable*.

Like you, I also am running old map data on my Garmin but, generally, I get from A to B - not many roads change too much over the decades. ;-)

---

### Post by mastablasta on 2012-07-27
> **BBQdave said:**
> Not sure if it is the same in Europe, here in the U.S. it is a hefty fee to update your Garmin maps. I ran into the same update issue (no linux support) 7 years ago with the purchase of a Garmin device. At first I was not happy, but then realized I did not want to pay the big fee to update the maps.

So I have been cruising along with a seven year old Garmin Map just fine (no system updates either). Let the Windows and Mac folks pay big update money, I am happy with Linux and no *Garmin update fees* :D

Perhaps the roads don't change so much there.  here they change quite a lot (especially one way roads in old towns). besides some of GPS devices (e.g. Mio Moov) could have 2 years free updates. and lately they also update speed limits which is always a good thing to have (i.e. alarm when you go over speed limit).

remember that in Europe plenty of countires are still building (or at leats they were before the crisis)  a larger road infrastructure (highways) that was already built quite some time ago in the US. so there could be quite a few changes there.

---

### Post by BBQdave on 2012-07-29
> **Zill said:**
> Like you, I also am running old map data on my Garmin but, generally, I get from A to B - not many roads change too much over the decades. ;-)

North Carolina is interesting, in that it is 2nd in most roadways in the Union. And we have a lot of roadway infrastructure development going on. Your right Zill, it can sometimes be challenging navigating (off - the Garmin Map), but most of the time you can get from A to B with the original Garmin Map.

It would be nice to have updated maps through a linux connection, but too, I can not (for me) justify the cost of new maps... especially with Mapquest and Google maps freely available. Even though I have the Garmin device, most times for big roadtrips, I use Mapquest. Up to date and free :)

---


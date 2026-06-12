---
title: "No Internet connection for Ubuntuone"
date: 2011-06-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2011-06-04
Bonjour,

Oneiric Alpha1 is surprisingly functional on my Acer5253 test laptop. But not UbuntuOne with it's main GUI saying that no Internet connection can be found on the PC, which is not the case. Thus I cannot log into UbuntuOne since the option is grayed out

---

### Post by coffeecat on 2011-06-04
Not just Oneiric. The Ubuntu One site has been problematic all day. I'm getting this in Natty with the Ubuntu One Control Panel: "File Sync is Disconnected." and "The information could not be retrieved. Maybe your internet connection is down." No, it isn't.

Also, if I go to the Ubuntu One site in Firefox and log in, I get a "Something has gone wrong. Sorry about that. The problem has been reported..." message.

Very frustrating. I bought two albums using Banshee in Natty this morning. I got a "Something has gone wrong" message in Banshee just after I had authorised payment. I've had an email saying thanks for the money but I haven't seen my mp3's yet. :(

**EDIT**: also brought up in this thread in the Ubuntu One subforum:

[http://ubuntuforums.org/showthread.php?t=1775199](http://ubuntuforums.org/showthread.php?t=1775199)

---

### Post by SevenMachines on 2011-06-04
Yes, greyed out here too, it also sends desktopcouch into a 100% cpu death spiral, think i might have a ubuntu sso problem as well though. something for a monday morning maybe :)

---

### Post by Roo79x on 2011-06-05
Hi all I'm having a similar problem with Ubuntu one, I did get the "No Internet connection" error but now I get the following error
```
Method "CreateItem" with signature "a{sv}
(oayay)b" on interface
"org.freedesktop.Secret.Collection" doesn't exist
```
I am running ubuntu oneiric 11.10 (oneiric-alternate-i386.iso) in virtualbox 4.0.8 r71778 on a 24" iMac with Snow leopard 10.6.7....

I'm new to alpha builds. I was reading through the forum and this thread and I just thought I would share my issue here, incase it is important or someone else is getting the same error. Also I am still able to get onto my Ubuntu one Dashboard and access all my stuff there.

thank you for your time
Ray

---

### Post by gnomeuser on 2011-06-05
Same problem, I am kinda disappointed with U1 so far. It is down or dreadfully slow far to often. Right now the situation means that my Tomboy notes are stuck on their server which is.. less than useful.

---

### Post by terry_gardener on 2011-06-12
I'm still getting this problem is everyone else

---

### Post by philinux on 2011-06-12
> **terry_gardener said:**
> I'm still getting this problem is everyone else

Ubuntuone is connecting on natty so it must be oneiric having a bad day.

---

### Post by coffeecat on 2011-06-12
> **philinux said:**
> Ubuntuone is connecting on natty so it must be oneiric having a bad day.

I think it's having a bad couple of weeks! :)

Ubuntu One is OK on my Natty, but I've just booted into my (virtual) Oneiric to see if I could set that up as a recognised device, but the "I already have an account" clickable link is greyed out and unclickable. The only thing I can click on is the "Learn more" button.

---

### Post by mc4man on 2011-06-12
could be related to this bug which has been fix for some things, not U1 yet
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/791548](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/791548)

---

### Post by Yahoé on 2011-06-18
Could indeed very well be related to this bug.
Still an issue on Oneiric daily 06/17/2011 amd64

---


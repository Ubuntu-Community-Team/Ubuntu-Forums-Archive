---
title: "possible virus?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by protpisys on 2011-10-29
for some reason my system will no longer stay logged into any sites, I also have this red exclamation point in an equally red arrow in the top bar of my desktop, it states that my update info is outdated, I run update manager and get the following error messages:

Failed to download repository information
W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

I'm dual booting 11.10 w/vista

---

### Post by lightwarrior on 2011-10-29
Is Vista behaving correctly and accessing the web?
Apparently you lost internet connection, perhaps a hardware driver update crashed your wifi/net card.
Try checking network devices.

---

### Post by Dangertux on 2011-10-29
You're getting the error message you got because those links are broken. You may wish to re-add the PPA to correct the problem.

Also no -- this is not indicative of a virus.

Hope this helps

---

### Post by Elfy on 2011-10-29
Those PPAs have no oneirc version.

You could try changing them to natty in software sources - other software - select the ppa and edit.

Or deselect them and reload.


[http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/)

---

### Post by sadaruwan12 on 2011-10-29
pixies right the 11.10 packages are not available in those PPAs thats why you're getting 404 errors.

And remember on the format of linux theres threat of a virus is very minimal so it's not a virus it's file missing issue.

---

### Post by protpisys on 2011-10-29
how do I re-add a ppa? I'm not sure I added it to begin with?

---

### Post by Dondermans on 2011-10-29
> **protpisys said:**
> how do I re-add a ppa? I'm not sure I added it to begin with?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Hope this helps.

---

### Post by protpisys on 2011-10-29
> **Dondermans said:**
> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Hope this helps.
would this also be why I have to sign into everything, including my wireless network every time I boot up? This just started yesterday as well

---

### Post by CharlesA on 2011-10-29
> **protpisys said:**
> would this also be why I have to sign into everything, including my wireless network every time I boot up? This just started yesterday as well
I don't think so. Have you tried changing your password and seeing if that does anything?

---

### Post by nogoodnamesleft on 2011-10-29
> **protpisys said:**
> would this also be why I have to sign into everything, including my wireless network every time I boot up? This just started yesterday as well

IMO that is the correct behaviour for a secure system... :) 

However assuming you don't want this (or disagree!) the PPA situation is as follows:

A PPA is an 'update channel' that delivers updates to your system. You had upgraded to a version of ubuntu for which those particular PPA have not yet been updated. You can manage/delete PPA from inside the 'Software Update' or Software Centre apps in Ubuntu.

**My question is what is that PPA and what does it do?** Why have you used it? I looked it up in launchpad and it doesn't say what it does. It looks to be some kind of mobile phone connection mod? So I can't say if it might or might not be affecting your wireless. 

EDIT: I am fairly sure that PPA is for mobile phone tethering, so it could indeed be affecting your wireless. I'd like more info to get to the bottom of this.

---

### Post by protpisys on 2011-10-29
so it appears what we have here is the law of unintended consequences...I did indeed bollox the thing up my ownself trying to get Ubuntu to recognize my iPhone so I could get my pictures off w/out having to boot into vista..but alas it just screwed something else up, or so it would appear...I'll have to undo that since it doesn't work anymore anyway...d'oh! Thanks to all for the assistance.

---

### Post by nogoodnamesleft on 2011-10-29
> **protpisys said:**
> so it appears what we have here is the law of unintended consequences...I did indeed bollox the thing up my ownself trying to get Ubuntu to recognize my iPhone so I could get my pictures off w/out having to boot into vista..but alas it just screwed something else up, or so it would appear...I'll have to undo that since it doesn't work anymore anyway...d'oh! Thanks to all for the assistance.

Suggestions: CLOUD or flickr.com

---

### Post by protpisys on 2011-10-30
I still need to get them off the phone, it takes forever to upload 30 or 40 pics directly from an iPhone

---

### Post by protpisys on 2011-10-30
OK, so what I did was I went into the "other software" page in the "software sources" program and uncheked the 2 lines for 
ppa:pmcenery/ppa  that I added their previously in order to get my iphone working in ubuntu, I then ran the update software thing and it appeared to work ok, though there were no updates...I think it may be ok, but I've been wrong before

---

### Post by nogoodnamesleft on 2011-10-30
ubuntu and phone both support wifi, you could just wifi them over without using some weird jailbreak tether whatnot

i do with mine and you don't pay for it either

although my phone is jailbroken, it also works with un-jailbroken phones

---

### Post by protpisys on 2011-10-31
> **nogoodnamesleft said:**
> ubuntu and phone both support wifi, you could just wifi them over without using some weird jailbreak tether whatnot

i do with mine and you don't pay for it either

although my phone is jailbroken, it also works with un-jailbroken phones
how exactly would I do that?

---

### Post by nogoodnamesleft on 2011-11-01
numerous wifi file xfer apps, see appstore

---


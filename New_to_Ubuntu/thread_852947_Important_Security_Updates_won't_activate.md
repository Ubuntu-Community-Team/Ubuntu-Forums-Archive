---
title: "Important Security Updates won't activate"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by WonderStivi on 2008-07-08
I've recently reinstalled Ubuntu, and noticed just now that for some reason the important security updates won't let themselves be activated. When I click the check box, it just blinks orange for a fraction of a second, and remains deactivated. Anyone know a fix for this?

---

### Post by Rocket2DMn on 2008-07-08
Can you please post your sources.list file?
```
cat /etc/apt/sources.list
```

---

### Post by WonderStivi on 2008-07-08
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by iaculallad on 2008-07-08
Try selecting other Download Servers in your "Software Sources" (try Main Server).

System->Administration->Software Sources, under the "Ubuntu Software" tab.

---

### Post by WonderStivi on 2008-07-08
Tried, but it didn't work...

---

### Post by iaculallad on 2008-07-08
What about commenting the last line in your sources.list file:

This line of text.

> deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

to

> **#**deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

in

```
gksudo gedit /etc/apt/sources.list
```

Save the edited file and drop to your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Then try to re-check if it enabled your security update.

---

### Post by WonderStivi on 2008-07-08
When you say comment, you mean inserting #?

Edit: Sorry, saw you had already written what to do. A bit distracted as I'm sitting with my new-born son on my arm, home alone for the first time.

Inserted comment, and no change.

---

### Post by iaculallad on 2008-07-08
> **WonderStivi said:**
> When you say comment, you mean inserting ##?

Yap, insert the # sign before the line of text.

---

### Post by WonderStivi on 2008-07-08
Did that, and no change.

---

### Post by WonderStivi on 2008-07-08
Is there any way to check if these updates has been installed? If it's just the tick that's missing, then I'm not really worried. I've already verified that I'm running 8.04.1. But I want to make sure I get the security updates.

---

### Post by Elfy on 2008-07-08
I'm the same - the little box won't tick, but I appear to have the security repos in the 3rd party tab

they are in your sources.list as are mine.

and congratulations> A bit distracted... 

---

### Post by WonderStivi on 2008-07-08
Then I will settle with this being a visual fault (after the .1 upgrade, perhaps?).

And thank you :)

---

### Post by philinux on 2008-07-08
It's the same in Intrepid Ibex too. Seems to have got caught up in the point release as well. I think it's a bug but not serious, since the security sources are activated.

---

### Post by Elfy on 2008-07-08
Next time I get a security update I can pm you if you like to make sure you did, as I suspect you'll be a bit busy for a while :)

---

### Post by WonderStivi on 2008-07-08
That'd be great :)

---

### Post by Elfy on 2008-07-08
Ok - I'll do that then.

---

### Post by azanutta on 2008-07-08
so, what's the prognosis?
must we wait for a release that fix this bug(?)
...
i don't know but... i haven't updates to download for my hardy for long time....

---

### Post by Elfy on 2008-07-08
Hi - no me neither, nor any proposed so I'd assume that all is well. If there is a bug the fix will turn up sometime over the next 3 years :)

---

### Post by fluteflute on 2008-07-08
Bug Report: [https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093](https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093)

---

### Post by Neo_The_User on 2008-07-08
> **WonderStivi said:**
> I've recently reinstalled Ubuntu, and noticed just now that for some reason the important security updates won't let themselves be activated. When I click the check box, it just blinks orange for a fraction of a second, and remains deactivated. Anyone know a fix for this?

OMG! I have the same problem! EXACTLY!

---

### Post by Rocket2DMn on 2008-07-08
That bug has been already been Confirmed, but the triage is incomplete.  I will mark is as High priority and upgrade to Triaged status, then a developer should start on it very soon.

---

### Post by ZabiGG on 2008-07-08
Same problem here. Been updating manually for the past few days. Noticed it for the first time two or three days ago. Sources are exclusively standard repos + restricted, all Hardy.

Cheers all,

Z.

---

### Post by WonderStivi on 2008-07-09
I got the BIND-update today, so I guess the security updates are activated. It was a total of 8 security updates. Bug confirmed!

---

### Post by Neo_The_User on 2008-07-09
> **ZabiGG said:**
> Same problem here. Been updating manually for the past few days. Noticed it for the first time two or three days ago. Sources are exclusively standard repos + restricted, all Hardy.

Cheers all,

Z.


Updating manually? Explain. How do you update manually?

P.S. Last night on July 7th 2008, I burned Ubuntu 8.04.1 to a CD then installed it. Works fine now.

---

### Post by ibuclaw on 2008-07-09
Not to forget that there is probably a newer package in the "**hardy-updates**" repository with the security fix embedded in ;)

If security is your absolute policy, just pin the security repo to have the highest priority over all others.

Regards
Iain

---

### Post by ZabiGG on 2008-07-09
@Neo

In case you ever need to, just click

System > Preferences > Administration > Update Manager

Reload and apply

Cheers,

Z.

---

### Post by Neo_The_User on 2008-07-12
> **ZabiGG said:**
> @Neo

In case you ever need to, just click

System > Preferences > Administration > Update Manager

Reload and apply

Cheers,

Z.

Yeah but I don't think im getting all the updates I want such as security. I love making updates to the kernel then my video gets all weird then I have to fix it. so much fun! seriously. i enjoy this stuff. P.S. this bug is in 8.04, 8.04.1, 8.10 all with fresh installed (not including 8.10.) you know what i think? somebody hacked into the ubuntu archives or something and replaces it all with junk thats why we can't check the thing because ubuntu is very paranoid with security which drives me crazy. Now what I did was put in like 30 new channels in the repository so now it will scan for like 30 extra things. None of them though relate to security. What I did with security was go into the software sources and go to third-party software and I put in MANUALLY [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security click add. highlight it and click edit. Distribution: hardy-security
Components: restricted main multiverse universe

WHA BOOM!

I also used to have this bug that would always say "malformed release file?" then I installed 8.04.1 and it got rid of it. I always found doing a fresh install working best.

---

### Post by ZabiGG on 2008-07-12
Turns out there is a now a workaround for this bug

[here]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/244093")

Once the source file is edited, it is advised not to try to check the checkbox until the bug is officially fixed.

Hope this helps!

Cheers,

Z.

---

### Post by zazanu16 on 2008-07-19
I`ve got the same problem but now is solved.....thank you for help

---


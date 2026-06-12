---
title: "Please Help! Problems with new LTS version upgrade"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by bobmac on 2012-06-20
Folks,

I have Update Manager set for 'Release Upgrade'|check for new distribution releases|Long Term Support releases only. However, the new LTS upgrade version has never shown up in Update Manager.

I left a thread some time ago with a similar request and received the following answers:

To set up update manager to get the latest LTS release, open a terminal and enter:

update-manager -d

or

sudo apt-get update
sudo apt-get dist-upgrade

I tried both of these with the result that more updates (not the LTS upgrade) showed up.

Does anyone know how I can get the upgrade without resorting to a totally new installation?

Regards,

Bob

---

### Post by blackflame2996 on 2012-06-20
what version of Ubuntu are you upgrading from?

---

### Post by blackflame2996 on 2012-06-20
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

check this if you are note running 11.10.

---

### Post by Bucky Ball on 2012-06-20
> **blackflame2996 said:**
> what version of Ubuntu are you upgrading from?

+1. LTS will upgrade to next LTS (10.04 to 12.04 for instance) but only last release will upgrade to next release (be that LTS or not). 

11.10 will upgrade to 12.04 as that is the most recent previous release. 11.04 will not. You need to go 11.04 upgrade to 11.10>12.04. Boring, possibly problematic and better off with a clean install of 12.04.

---

### Post by yiannis66 on 2012-06-20
Open the update manager-->Settings
At the window it will oppen go to Updates
and at the last line you will see a line that you choose
that is you looking for
"Long term support"

---

### Post by bobmac on 2012-06-20
I have all the latest updates installed for LTS 10.04 so I would like to go to the next LTS version. But, as I've indicated, it simply doesn't show up anywhere in the Update Manager. Is there any other way of getting the upgrade without having to reinstall everything?

Bob

---

### Post by blackflame2996 on 2012-06-20
it would seem you have to go through 10.10,11.04,11.10, and finally to the current version. I would recommend a fresh install. is it possible to backup your files?

---

### Post by Bucky Ball on 2012-06-20
> **blackflame2996 said:**
> it would seem you have to go through 10.10,11.04,11.10, and finally to the current version.

NOOOOO!!! Absolutely wrong. LTS upgrades to next LTS without going through that lengthy headache.

To the OP and just a thought. If your 10.04 is stable why are you wanting to upgrade when 12.04 is still getting ironed out? 10.04 still has ten month's support by which time 12.04 should be reasonably bullet proof. I'd do a clean install of 12.04 on another partition and play with it for awhile whilst keeping 10.04 as you regular, stable main squeeze. ;)

BTW: I just found your answer in two seconds, bobmac. Upgrades to next LTS not available til first point release. You might get some joy here further down the page:

[http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts](http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts)

---

### Post by bobmac on 2012-06-20
Now I'm utterly confused! I was under the impression that if you had the last version of LTS and had all the updates for that version, then when the new LTS version was released then the Update Manager (with the correct setting) would tell me when the latest LTS was available. OR am I missing something here.

As I mentioned my Update Manager is set to Check for updates Daily, and for an Upgrade Release for LTS versions. So have you any idea why I'm not getting the new LTS version instead of all the previous normal version upgrades. I was under the impression that if you wanted only the LTS versions then that's what you were going to get.

Bob

---

### Post by wilee-nilee on 2012-06-20
I believe the official LTS to LTS is in mid July, it does not happen immediately unless you force it.

Look at the wiki's.

If you set the for any new releases in software sources, and then run the update-manager -d code I think it will show.

Make sure it is 12.04 showing is all.

---

### Post by Bucky Ball on 2012-06-20
> **wilee-nilee said:**
> I believe the official LTS to LTS is in mid July, it does not happen immediately unless you force it.

Look at the wiki's.

If you set the regular release in software sources, and then run the update-manager -d code I think it will show.

+1. Bobmac, check the link at bottom of my last post. It tells the story and helps you force the issue. ;)

---

### Post by bobmac on 2012-06-20
Ah! ha!

Perhaps that's my problem us OAP's are a bit slow on the uptake. I was worried that somehow I had missed the upgrade altogether and, being a bit of a dimwit was going to have to try to reinstall everything again. With a bit of luck I can back up my data as soon as the the upgrade shows up, Upgrade to the new LTS and all will be well with the world.
Many thanks for your information
Regards,
Bob

---

### Post by bobmac on 2012-06-20
Bye the bye,

I only seem to know where the forums are, I wonder if you could point me at the wikis

Bob

---

### Post by wilee-nilee on 2012-06-20
> **bobmac said:**
> Bye the bye,

I only seem to know where the forums are, I wonder if you could point me at the wikis

Bob

On the web you just have to look for lts release stuff in general I would think.

Run this and post the text.
```
cat /etc/lsb-release
```

---

### Post by blackflame2996 on 2012-06-20
sorry, I was not aware of this.

---

### Post by afixane on 2012-06-20
Umm, if i'm not wrong, 10.04 will upgrade into 12.04.1, because there is a bug when you upgrading from 10.04 to 12.04

---

### Post by bobmac on 2012-06-20
calban@ubuntu-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
calban@ubuntu-desktop:~$

---

### Post by wilee-nilee on 2012-06-20
> **bobmac said:**
> calban@ubuntu-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
calban@ubuntu-desktop:~$

I just wanted to confirm that you were running 10.04, it would not be the first time a user has made a mistake here.

---


---
title: "What happens during a version upgrade?"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by vasa1 on 2012-04-20
I understand that Canonical recommends upgrading to a new version rather than doing a fresh install over the old version. I upgraded without any (noticeable) ill-effects from 11.04 to 11.10. I plan to upgrade from 11.10 to 12.04 as soon as 12.04 is released.

But I'm curious as to how such a complex task is done.

Are there any known potential problems that one has to look out for? 

For example, a power outage can be fatal and this is not limited to upgrading but also to fresh installs.

The less tweaked the system, the better the chance of the upgrade going smoothly.

From my experience limited to the one upgrade, the process is fairly tolerant of a crappy internet. If the net drops, the process largely (but not entirely) picks up from where it left off. The net dropped very many times during my upgrade.

**Question**: assuming a vanilla 11.10 (vanilla = very few ppas added, very few "tweaks"), fully updated, how many MB are required to upgrade to 12.04? With a 256 kBps connection how long would it take assuming no breaks?

Another comment: the upgrade process **required** user input at a few times so it's not something one would start and then leave well alone hoping to return and find it completely done.

---

### Post by Curtis6767 on 2012-04-20
I upgraded to 12.04 LTS Beta II at the first of the month.

According to my DSL provider, I have a faster connection than do you, however I don't believe that. Let's just say it's about the same speed as yours.

It's about 700mb's, though I not I'm not sure in an upgrade it would be that much, but maybe. Took me about 90 minutes to do the down load and then about another 90 to do the upgrade.  All my apps were upgraded in the process. 

I just followed the instructions and all went well.

I'm a noob to Ubuntu but OS seems very stable to me.

---

### Post by 3Miro on 2012-04-20
In the case of the clean install, it is easier for the developers of Ubuntu to predict what will happen. You will partition your HDD and install. However, during an upgrade, there is the potential of more things going wrong as the developers cannot predict every setting or extra ppa that you have installed.

I personally go for clean install, but when an upgrade works, it does work.

The amount of data that needs to be downloaded during an upgrade will depend on what you have installed. Basically, you have to redownload the equivalent of a CD image plus whatever else you have installed in addition.

During the first few days, the servers would be clogged, so there is a chance you will not be able to use the full potential of your 256 kBps connection. Torrent is the best way to get the .iso, unfortunately updates cannot be distributed in this way.

---

### Post by vasa1 on 2012-04-20
> **3Miro said:**
> In the case of the clean install, it is easier for the developers of Ubuntu to predict what will happen. You will partition your HDD and install. However, during an upgrade, there is the potential of more things going wrong as the developers cannot predict every setting or extra ppa that you have installed.
...
The amount of data that needs to be downloaded during an upgrade will depend on what you have installed. Basically, you have to redownload the equivalent of a CD image plus whatever else you have installed in addition.


True, that's why I asked about a situation in which 11.10 has been minimally altered.

> **3Miro said:**
> 
...
During the first few days, the servers would be clogged, so there is a chance you will not be able to use the full potential of your 256 kBps connection. Torrent is the best way to get the .iso, unfortunately updates cannot be distributed in this way.
Yes, I had the iso (by Torrent) already on a pendrive to check out 11.10 before upgrading.
And my experience this one time was that I managed to download the iso (via Torrent) and then additionally upgrade all in the first two days! (My connection gives me an effective download speed of <= 50 Kbps.)

---

### Post by Paqman on 2012-04-21
> **vasa1 said:**
> 
But I'm curious as to how such a complex task is done.


Essentially it's similar to running a normal update, the difference being that during the process the system switches from the old repositories to the new ones, then updates all the packages from them.

---

### Post by jerome1232 on 2012-04-21
> **3Miro said:**
> 
During the first few days, the servers would be clogged, so there is a chance you will not be able to use the full potential of your 256 kBps connection. Torrent is the best way to get the .iso, unfortunately updates cannot be distributed in this way.

Actually if you grab the alternate cd iso and burn it to cd, you can do an upgrade with it.

The servers get so clogged for the first week it's worth it imho, probably saves whoever admins the repo servers a few gray hairs too.

---

### Post by Zill on 2012-04-21
vasa1:  You will probably have fewer problems with a fresh install, rather than an upgrade.  Having said that, it may be worth trying an upgrade first because if this doesn't work properly you can still do a fresh install afterwards.

Ideally, you will already have your /home on a separate partition - this make upgrading far simpler as you can retain your data.  If you do need to do a fresh install, ensure that you do *not* reformat the /home partition. ;-)

In all cases, ensure you have good reliable backups elsewhere of *all* the data you wish to retain.

---

### Post by Curtis6767 on 2012-04-21
Just to throw out another scenario, but why wouldn't upgrading today be an option?

From what I understand from reading the Precise forum, there really isn't much going on now, just some finishing touches.

Wouldn't an upgrade today be almost the same as an upgrade on the 26th or later?


And please do correct me if I'm wrong because I would not want to get Vasa1, or anyone else who might be reading this thread, in a fix.

---

### Post by grahammechanical on 2012-04-21
An upgrade will take longer that a fresh install because everything is coming down the internet.

I recently tested an upgrade from default 11.10 to 12.04 as part of ISO testing (you do not need to be clever to do this). More than 1700 packages will be downloaded.

There are a lot of changes between 11.10 and 12.04 because 11.10 was still using a lot of Gnome 2 stuff which has to come out and be replaced. Further more, the libraries that are used to make 32bit applications run on a 64bit CPU & OS have also been changed to libraries that will run on different architectures. There are called multi-arch libraries.

So, there is a lot to be changed over.

Did you know that you can upgrade from a DVD?

Boot into the desktop. Put in the live DVD and you will be offered an opportunity to upgrade from it.

As regards upgrading now. Yes it is possible. The command is simple but the OS would not be up to date. You will need several mega bytes of updates over the next few weeks.

The ISO images may be fixed although we have been asked to test them daily during this week but that does not mean there will not be updates to come through. At this point in time waiting a couple of weeks is no hardship if you have a slow download connection.

Regards.

Please go here

[http://iso.qa.ubuntu.com/qatracker/milestones/214/builds]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds")

Notice this comment:

> Do not use the currently enabled 20120420.1 and 201204420 images for upgrade testing. Regression detected and being addressed.

The number of the image is the date. Notice that there are images dated 20120421. Yesterday these were number 20120420. So, there is still some changes being made. The images listed on this page are candidates for release. This is why they are being tested.

Who wants to join in this week?

---

### Post by Paqman on 2012-04-21
> **grahammechanical said:**
> An upgrade will take longer that a fresh install because everything is coming down the internet.


As opposed to? To do a fresh install you still have to download the ISO. All up you're downloading the same amount of stuff.

---

### Post by 3Miro on 2012-04-21
> **Paqman said:**
> As opposed to? To do a fresh install you still have to download the ISO. All up you're downloading the same amount of stuff.

I don't know what grahammechanical wants to say, but downloading a .iso via torrent is much faster than using a clogged server. Technically and CD/DVD upgrade is faster.

---

### Post by Paqman on 2012-04-21
> **3Miro said:**
> I don't know what grahammechanical wants to say, but downloading a .iso via torrent is much faster than using a clogged server.

Absolutely. Going near the official servers around release day (whether for packages or for ISOs) is pretty painful. Seems less so than in the past, though.

---


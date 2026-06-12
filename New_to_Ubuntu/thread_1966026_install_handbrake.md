---
title: "install handbrake"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by goodgriefpenfold on 2012-04-26
Hello,

I've just installed the new ubuntu os 12.04. I'm having trouble re-installing handbrake. Does anybody have any suggestions

Thanks

GGP

---

### Post by papibe on 2012-04-26
[B]EDIT: read first post #4 and #6 by JohnAStebbins.
[/B]
Hi goodgriefpenfold.

I usually used this ppa:stebbins/handbrake-snapshots, but as today, there's no version for Precise.

You can wait for it or, use this trick at your own risk:
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```
Then open the 'Software Center' and go to Edit -> Software Sources. Click on the tab 'Other Software'. Select the stebbins ppa and click Edit.

There change the field Distribution from Precise to Oneiric.

Then:
```
sudo apt-get update
sudo apt-get install handbrake-gtk
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by SeijiSensei on 2012-04-26
I'm using the release for Oneiric on Precise.  Works fine.  I prefer to use the handbrake-releases repository rather than handbrake-snapshots myself for stability reasons.

My /etc/apt/sources.list.d/ contains the file "stebbins-handbrake-releases-precise.list" with these contents:

```

# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main

deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main
deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu oneiric main

```

Once there a release for 12.04, I'll delete the last two lines and uncomment the ones for Precise.

---

### Post by JohnAStebbins on 2012-04-27
There should be a snapshot version of handbrake for Precise available within the next day.  It should get queued to the PPA build servers tonight.

I do not plan to add Precise to the releases PPA for 0.9.6. But we are preparing a bugfix release that I'm hoping we can kick out the door in the next month. There will be a version of this bugfix release for Precise.

---

### Post by anewguy on 2012-04-27
Hey, as long as your here.......I've tried many times over at least a year to add the PPA and install - it ALWAYS fails saying it can't find [http://ppa.launchpad.net/stebbins/handbrake-releases/whatever_release](http://ppa.launchpad.net/stebbins/handbrake-releases/whatever_release).  Always.  I have to go explore the releases and manually download a .deb from there.  Any ideas on that John?

And by the was.....THANK YOU FOR A *WONDERFUL* PRODUCT!!!!

Dave ;)

---

### Post by JohnAStebbins on 2012-04-28
> **anewguy said:**
> Hey, as long as your here.......I've tried many times over at least a year to add the PPA and install - it ALWAYS fails saying it can't find [http://ppa.launchpad.net/stebbins/handbrake-releases/whatever_release](http://ppa.launchpad.net/stebbins/handbrake-releases/whatever_release).  Always.  I have to go explore the releases and manually download a .deb from there.  Any ideas on that John?

And by the was.....THANK YOU FOR A *WONDERFUL* PRODUCT!!!!

Dave ;)

It should be as simple as...
```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots
sudo apt-get update
sudo apt-get install handbrake-gtk handbrake-cli

```
If that doesn't work, I don't know what's borked.

---

### Post by goodgriefpenfold on 2012-04-29
This forum is second to none. Thanks Guys. Obviously Mr Stebbins input has worked for me and all the other advice, as a new linux user, has got me exploring my system in other useful ways that I had not considered yet.

Kindest Regards and best wishes

GGP

---

### Post by nmyeti on 2012-04-29
Thank you for the install instructions. Love Ubuntu and love the Linux community!

---

### Post by anewguy on 2012-04-29
Thanks John - that works!  I had been following a how-to on the net but I don't think it pointed at the snapshots, I think it pointed somewhere else.  That resulted in a failure every time I tried to use it.  Going to the snapshots works, but how do I get the most recent stable release?

Thanks again!
Dave ;)

---

### Post by SeijiSensei on 2012-04-30
Look at John's earlier post:

> **JohnAStebbins said:**
> I do not plan to add Precise to the releases PPA for 0.9.6. But we are preparing a bugfix release that I'm hoping we can kick out the door in the next month. There will be a version of this bugfix release for Precise.

Your choices for the moment are the Oneiric build if you want handbrake-releases, or the Precise build in handbrake-snapshots.

---

### Post by anewguy on 2012-04-30
Jeez, you know, I *did* read the thread, but somehow I missed that!  Thanks, and sorry about that!

Dave ;)

---

### Post by ThickPizza on 2012-05-04
Is there something I'm overlooking or did HandBrake on 12.04 lose the function to choose the output file size? HandBrake is second to none and in actuality is a total life-saver, but for some of my larger BluRays I need to make sure that the MPEGs stay within a certain file size range to be able to be played through my Xbox. 

Sorry to thread-jack, but it's kind-off on topic and I didn't feel this was worthy of a whole thread.

---

### Post by JohnAStebbins on 2012-05-05
> **ThickPizza said:**
> Is there something I'm overlooking or did HandBrake on 12.04 lose the function to choose the output file size? HandBrake is second to none and in actuality is a total life-saver, but for some of my larger BluRays I need to make sure that the MPEGs stay within a certain file size range to be able to be played through my Xbox. 

Sorry to thread-jack, but it's kind-off on topic and I didn't feel this was worthy of a whole thread.

Yes, the file size setting was removed.

---

### Post by ThickPizza on 2012-05-06
> **JohnAStebbins said:**
> Yes, the file size setting was removed.


'Tis a shame, that was a very handy feature. Is there any other means of controlling file-sizes through HandBrake?

---

### Post by bearcatrp on 2012-05-12
Not to hijack this thread but is there some kill switch in handbrake? Reason I'm asking is I was on Ubuntu 10.10 dual boot with win7. Zero problem booting in from time to time to rip some dvd's. Went in couple nights ago and seems all the codecs were missing. Multiple errors. Wish I had wrote them down to post here. Anyways, ended up upgrading to 12.4 this morning.  Been searching for handbrake for 12.4. Ended up here on a search. Can't wait until its released. Best program I have used for many years. Keep up the great work.

---


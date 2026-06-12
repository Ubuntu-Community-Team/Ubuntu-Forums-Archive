---
title: "HOWTO: Connecting, Transferring &amp; Using Your Zen Touch"
date: 2005-11-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Resin on 2005-11-22
Hey All, this is my first HOWTO so feel free to comment on it and I will improve/cleanup as best I can.

**Note:** Please Visit these sites first to get some background info on what your doing. 
**Note:** This was written for Ubuntu 5.10 and might not be relevent any more please check the following thread : [http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

[http://gnomad2.sourceforge.net/]("http://gnomad2.sourceforge.net/")  - The projects homepage.
[http://gnomad2.sourceforge.net/?section=article]("http://gnomad2.sourceforge.net/?section=article") - Their guide on getting it to work.  Although I found doing it my way easier.

**Required Packages: **

First of all, fire up the Synaptic Package Manager.  Then do a search for the following; (Note.  Ensure you have multiverse and universe repositories)

* gnomad2 (version 2.8.0-2)
* libnjb1 (version 1.1-1)
* libnjb5 (version 2.2.1-2)
* libnjb-doc (version 2.2.1-2)
* libnjb-hotplug (version 2.2.1-2)
* nbjtools (version 0.0.1-1ubuntu1)

After the above have been downloaded and installed, simply connect your Zen Touch via usb, then venture to:

*Applications* >* Sound and Video* > *Gnomad 2*

Your Zen Touch should then display the 'Docked' screen and you can now use your player in Linux!

Cheers!

---

### Post by jurij20 on 2006-05-05
Thanks alot! Works perfectly

Although I couln't find nbjtools, but after a typos I found that the name is actually njbtools :)

---

### Post by mike_m on 2006-06-20
I used this to get my Zen Touch to work in Kubuntu 6.06, Thanks.
Although it works, I couldn't find libnjb-hotplug in Adept package manger, eventhough I found all other packages & I have universe multiverse.
But maybe because I'm using Kubuntu I need to load a different repo, can anyone suggest a deb address I can add to my Adept?

Thanks, Mike

---

### Post by wastrel on 2006-06-20
mike_m, 

libnjb-hotplug doesn't exist in 6.06 (presumably) due to the change from the usb hotplug system to udev.

---

### Post by mike_m on 2006-06-20
Thanks Wastrel, guess I'm all set with that.

Only 1 app left to install, then I can dump WinXP..... X10 ActiveHome Pro,
wish me luck as wine don't seem to work with it.

---

### Post by Aurdal on 2006-07-07
I noticed this also, does this mean I've to reinstall 5.10 to get my Zen Touch working?

---

### Post by mike_m on 2006-07-08
no, it's working great with 6.06

---

### Post by Aurdal on 2006-07-08
Well, Gnomad won't find my Zen Touch...

---

### Post by Aurdal on 2006-07-08
I've the lastest firmware, the windows protocol thngy. Is this a problem when using this solution?

---

### Post by le_vainqueur on 2006-12-03
I'm using Edgy, and I could not find hotplug

I tried running Gnomad2, and got the following error

> Could not open jukebox:
usb_set_configuration: Operation not permitted


---

### Post by ntetreau on 2006-12-07
Hi, for anyone reading this thread, there is quite a bit of effort already deployed in this thread
[http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

The Howto is quite up to date and lots of questions are stil being asked/answered there.

Good luck!

Nic

---

### Post by harman0 on 2008-12-30
You need root!
sudo gnomad2 &

---


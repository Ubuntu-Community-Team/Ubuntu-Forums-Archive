---
title: "How to get Firefox 3 RC ?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by metasolaris on 2008-05-20
Hi,

Ive just finished installing Firefox 3 RC in my XP SP3 partition and I noticed that I'm still working with Firefox 3 Beta 5 in my Hardy partition.

How does software like Firefox and Miro get updated in Hardy when new versions become available? Do you install the new versions direct from the website (and how do you do it if you do?) or do you wait for the new version to become available in the Repos?

Thanks

meta

---

### Post by dca on 2008-05-20
I don't think Firefox3 (final) will be a natural progression of updates in UBuntu 8.04LTS...  Don't quote me on that, it may very well be included when 8.04.1 is released in a couple months.

---

### Post by drs305 on 2008-05-20
With the usual disclaimers...
[http://www.mozilla.com/en-US/firefox/all-rc.html](http://www.mozilla.com/en-US/firefox/all-rc.html)
Note: it's a .tar.bz2 file

---

### Post by Technoviking on 2008-05-20
Most of the Ubuntu-Mozilla team is at UDS-Intrepid this week. Updates for Firefox will be available sometime soon, after the conference.

---

### Post by metasolaris on 2008-05-20
> **Mike said:**
> Most of the Ubuntu-Mozilla team is at UDS-Intrepid this week. Updates for Firefox will be available sometime soon, after the conference.

Thanks Mike - always helps to have someone with inside knowledge...:lolflag:

---

### Post by motin on 2008-05-28
[HERE is the Firefox 3 RC repository for Ubuntu]("http://forum.notebookreview.com/showthread.php?t=251922")

Cheers

---

### Post by psychok7 on 2008-06-03
> **motin said:**
> [HERE is the Firefox 3 RC repository for Ubuntu]("http://forum.notebookreview.com/showthread.php?t=251922")

Cheers

but is this an official repository?? i was reading something the other day were they advised everybody to wait for an update. but this update is taking 2 long..

---

### Post by Paqman on 2008-06-03
> **metasolaris said:**
> 
How does software like Firefox and Miro get updated in Hardy when new versions become available? Do you install the new versions direct from the website (and how do you do it if you do?) or do you wait for the new version to become available in the Repos?


As a general rule, it's always better to stick to the repos. Some people like to have the absolute latest versions of everything, even if that means compiling from source. That's risky, as it's untested software, and compiling reduces the stability of your system.

---

### Post by psychok7 on 2008-06-03
i heard the firefox rc2 is coming out middle of june..so we dont get to test rc1??and i heard rumors that there wont be updates in the repositories until the final version.. please tell me this is not true..

---

### Post by irrdev on 2008-06-03
> **psychok7 said:**
> i heard the firefox rc2 is coming out middle of june..so we dont get to test rc1??and i heard rumors that there wont be updates in the repositories until the final version.. please tell me this is not true..
RC1 is already under testing to make it into the repositories. Usually updates are performed relatively fast, but between the conference and releasing important security updates, the Ubuntu Team has been very busy. Firefox 3b5 is already *very* stable, and I don't believe that RC1 implements many changes. Within two weeks I expect the updates to (finally) be available in the repositories. ;)

---

### Post by Archmage on 2008-06-03
> **metasolaris said:**
> How does software like Firefox and Miro get updated in Hardy when new versions become available?

There won't be a new version for Miro in Hardy. Only securities updates will be in Hardy. The new version of Miro will be in Intrepid.

If you can't live with a new version of Miro you should use the responcibiles on the webpage. But of course they are not official. (I did it once and it breakes my whole Miro, therefore I'm DEFENETLY sticking with the version in Hardy, till Intrepid comes out.)

---

### Post by Stefanie on 2008-06-03
i installed firefox 3 RC 1 with synaptic. first go to system -> administration -> software sources . then go to the tab "third party software" and click add. enter this url :```
http://ppa.launchpad.net/fta/ubuntu hardy main
```
click close and an update of your sources list will start. when that's done you can install RC1 through the update manager.

it worked for me, but this is not the "official" way to install RC1 and it's on your own risk. I didn't experience any problems though. I upgraded to RC1 because gmail would crash all the time in beta5.

---

### Post by Anicka on 2008-06-03
The RC1 is in the hardy-proposed repos. Just enable it in software sources or by editing your source file.

---

### Post by Bubba64 on 2008-06-03
The launchpad link just released FF3 rc2 when Hardy will only be rc1.

---

### Post by Sef on 2008-06-03
> The RC1 is in the hardy-proposed repos. Just enable it in software sources or by editing your source file.

System > Administration > Software Sources > Updates 

The 'Hardy-Proposed' repo contains updates that may cause instability with your system.  They are basically beta software updates.

---

### Post by diegops on 2008-06-03
I used the same trick to install Firefox 3.0 RC2 that I used in the RC1.

I added this line on the /etc/apt/sources.list:

deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main


[http://blog.rosanegra.org/2008/06/02/how-to-install-firefox-3-rc-2-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/06/02/how-to-install-firefox-3-rc-2-on-ubuntu-hardy/)

---

### Post by Joeb454 on 2008-06-03
I believe using the LaunchPad repo's can cause issues if you want to remove it.

You can enabled hardy-proposed, then upgrade Firefox 3, and disable hardy-proposed again if you really want it :)

---

### Post by Bubba64 on 2008-06-03
Whether you use Downloads for FF3 from Hardy, Proposed, or launchpad I don't think it matters if your familiar with how to completely remove anyone of them if needed. They are all aiming for the final release and will overwrite each other without problems at least on my ancient recycled computers.

---


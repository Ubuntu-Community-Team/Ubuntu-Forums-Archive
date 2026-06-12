---
title: "Showstoppers in Natty that really should be fixed before / in Oneiric"
date: 2011-05-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bonzini on 2011-05-10
Right now I have Natty installed on two laptops but there are two bugs that prohibit me from upgrading my work desktop and my family's other computers.

I think these bugs need to be fixed in Natty or at least before Oneiric.

These bugs are not related to Unity.  I recognize that Unity is a key part of Ubuntu strategy moving forward but this is the first time since hoary that I have had show-stoppers that preclude me from moving to a new release...

I wonder if others have such problems.  I will describe my show-stoppers as an invitation to others to relate their problems, if any.

My two problems:

1. Broadcom STA driver does not work.  In my case, I can get rid of the STA driver and install the old driver, but I don't believe this works for everyone.  There are a number of bugs and many users (including, I believe, Mr. Shuttleworth) affected by this.  See for example bug #732677.  There is a lot of discussion on this thread but no good solutions (like a nice clean way of moving back to previous working versions such as that in 10.10).

2. I cannot copy large numbers of big music files (either by ftp or by USB hard drive) to either Toshiba or Dell laptop hard drives without the system hanging and becoming inoperative, requiring a hard boot.  This is a show stopper for me, but I can't see anyone else having this problem recently in Natty. This is bug #758384.  There are similar sounding bugs affecting others, either in the past or on non-Intel hardware, but I seem to be the only one suffering (could I possibly be the only one with a big pile of FLACs to copy).

---

### Post by teachop on 2011-05-10
Yes, plus one.  This is the point I was trying to make with the "Hardware support" thread.  You have made the point better.

---

### Post by coffeecat on 2011-05-10
> **bonzini said:**
> 1. Broadcom STA driver does not work.  In my case, I can get rid of the STA driver and install the old driver, but I don't believe this works for everyone.  There are a number of bugs and many users (including, I believe, Mr. Shuttleworth) affected by this.  See for example bug #732677.  There is a lot of discussion on this thread but no good solutions (like a nice clean way of moving back to previous working versions such as that in 10.10).

I've noticed a number of threads where people have upgraded from Maverick and lost broadcom wireless functionality. My experience was somewhat different in that I made a fresh install and somewhat different in that Broadcom wireless worked out of the box:

[http://ubuntuforums.org/showthread.php?t=1744983](http://ubuntuforums.org/showthread.php?t=1744983)

This was my first hands-on experience with Broadcom wireless and, after everything I'd read, you could have knocked me over with the proverbial feather when it just worked and continued to do so.

I presume that the brcm80211 driver is the new open source driver developed now that Broadcom are working with the FOSS community - but I'm happy to be corrected. And, of course, it may not work so well with chipsets other than the one I used. Also, from some of the threads I've read, all sorts of stuff is being written to /etc/modprobe.d/blacklist.conf by the STA and b43 drivers which must be complicating things.

A suggestion. Have you tried running the Natty live CD and seeing if your Broadcom device can connect in the live session? If it does, then check to see if it's using the brcm80211 driver. If so, then there must be residual rubbish from the STA and/or b43 driver interfering in your permanent install.

---

### Post by ronacc on 2011-05-10
Its not just broadcom , my RTL8185 has been rock solid since I installed it during gutsy , that is until natty came along , I can connect but only after some "monkey motion" and then it randomly disconnects for no reason I can find in any of the logs . Also my printer , which has worked no problem since jaunty hasn't printed a single character from natty . I suspect that both problems are related to indicator applet .

---

### Post by bonzini on 2011-05-10
For the record I have been installing fresh from the install Cd on both laptops since beta 1.

Thanks for the help suggestions, but I was not looking for a workaround here but rather trying to point out that nasty was the first Ubuntu release I have ever tried that i could not adopt, due to showstopper bugs, and to suggest that these kind of bugs should be a pretty high priority for oneiric.

---

### Post by Quackers on 2011-05-10
> **ronacc said:**
> I can connect but only after some "monkey motion" 

:-)  Excellent terminology, ROFL  Love it!

---

### Post by beew on 2011-05-10
+1 to fixing bugs in Natty before frantically moving all developmental resources to Oneiric. It is ridiculous that after the day of release they immediately move on as if they just churn out a release every 6 months to meet deadlines. In Unity window buttons still missing when applications open full screen from time to time.

---

### Post by Harry33 on 2011-05-10
> **beew said:**
> +1 to fixing bugs in Natty before frantically moving all developmental resources to Oneiric. It is ridiculous that after the day of release they immediately move on as if they just churn out a release every 6 months to meet deadlines. In Unity window buttons still missing when applications open full screen from time to time.

Unfortunately, this is the cost we pay for the 6 month cycle.

---

### Post by dnewkirk on 2011-05-10
Realize that part of this push is a balance of manpower to reach broader goals regarding future LTS versions. The LTS versions are those that will receive the most attention, bug fixes, and interest (from a corporate, etc. perspective). The in-between cycles are as much about testing out new ideas and features as anything else. They won't have the same level of polish that a LTS (should) will. With each set of new ideas, programs, and implementations, there will need to be beta testing, which is what your 'tween releases are for. Updating to a new release will have a cost associated with it, no matter what. You can often get around that by modification of a previous release, but it depends on the level of stability and support the user requires. LTS versions are where one goes for dependability; the tweeners for when you can really use a new feature at the expense of some stability/usability.

---

### Post by Harry33 on 2011-05-10
> **dnewkirk said:**
> Realize that part of this push is a balance of manpower to reach broader goals regarding future LTS versions. The LTS versions are those that will receive the most attention, bug fixes, and interest (from a corporate, etc. perspective). The in-between cycles are as much about testing out new ideas and features as anything else. They won't have the same level of polish that a LTS (should) will. With each set of new ideas, programs, and implementations, there will need to be beta testing, which is what your 'tween releases are for. Updating to a new release will have a cost associated with it, no matter what. You can often get around that by modification of a previous release, but it depends on the level of stability and support the user requires. LTS versions are where one goes for dependability; the tweeners for when you can really use a new feature at the expense of some stability/usability.

Yes we know all that.
But I have also found out that the two last LTS releases have not been more stable than the other releases.
Why is that then?
That is because a lot of applications still derive from upstream.
LTS still has the latest stable kernel, latest xserver, latest gcc and so on.

It is however true that the development phase is more calm, not so much the actual release version.

---

### Post by beew on 2011-05-10
> **dnewkirk said:**
> Realize that part of this push is a balance of manpower to reach broader goals regarding future LTS versions. The LTS versions are those that will receive the most attention, bug fixes, and interest (from a corporate, etc. perspective). The in-between cycles are as much about testing out new ideas and features as anything else. They won't have the same level of polish that a LTS (should) will. .

Well then don't tell people they should upgrade their OS the first day after release so they end up breaking it. 

On the very day when Natty was released I got a popup from update manager inviting me to upgrade. Of course I declined and disabled  notification from update manager immediately. But I expect many inexperienced users (not that I am very experienced, mind you) would just click "yes" (without backing up their data of course when they are prompted out of the blue like that) and ended up with a broken system and many threads on the forum.

The thing is, each new release is being hyped so much that many users (especially new users) would feel they should upgrade. If they issue warnings more prominently that non LTS are essentially beta then I think less people would risk to upgrade/update their OSes.  

Also don't tell people that they should upgrade every 6 months to get software updates. Either put more work in the intermediate releases or make the LTS rolling.

---

### Post by bonzini on 2011-05-10
ok everyone - "deep breath, count to five"

I think there's too much heat here and not enough light.

With respect to "not enough polish" - cool, we can all live with "not enough polish" but showstoppers are different.  In my case, I lived with random hangs in dapper until I figured out that I needed to set noacpi or something like that (sorry for the vague memory).  I found a kernel with lower latency so that I could play music in 10.04 (an LTS if I am not wrong).

Not being able to copy my home directory back from either FTP or a USB-attached hard drive - that's a big serious issue.  Maybe I am the only one experiencing it but I am experiencing it on two completely different platforms from two completely different manufacturers.

And tens of users not being able to use wireless because the newest Broadcom driver is unserviceable (probably this means hundreds since tens have found the bug and are jumping on it)... that is a big serious issue too.

I am sure that many Unity problems are of equal seriousness but getting Unity perfect and leaving other serious problems unattended kind of seems like Rome burning and Nero fiddling...

---

### Post by rubenverweij on 2011-05-11
Okay, I will post another showstopper then:
the "open file with" selection dialog in Firefox. I was trying to open a .doc document and Firefox suggested gedit. I then had to browse to /usr/bin and pick libreoffice and the checkbox for making it default was greyed out. Seriously!
I don't believe an average user could pull this off, and if Firefox is to remain default in Oneiric, I believe it should be fixed.
BTW, here is the 6 year old bug report: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/18995](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/18995). It is marked as low importance and has been around for a really long time.

---

### Post by seeker5528 on 2011-05-11
> **Harry33 said:**
> Unfortunately, this is the cost we pay for the 6 month cycle.

Hardware support is like a game of whack-a-mole, fix something over here, something breaks over there. Do something that improves the support for a certain class of hardware and you have different issues with different hardware and driver combinations as the drivers migrate to the new things and bugs are discovered either in the new thing or that may already have existed in the driver but was just less apparent.

The benefit of 6 month releases is that you can skip releases that don't work as well with your specific hardware or delay in hopes that a fix is found.

The ability to find information about some of the bigger issues that have been found and fixed in a release after it's initial release leaves something to be desired. Don't know how often the known issues in the release notes gets updated.

Later, Seeker

---

### Post by beew on 2011-05-12
> **rubenverweij said:**
> Okay, I will post another showstopper then:
the "open file with" selection dialog in Firefox. I was trying to open a .doc document and Firefox suggested gedit. I then had to browse to /usr/bin and pick libreoffice and the checkbox for making it default was greyed out. Seriously!
I don't believe an average user could pull this off, and if Firefox is to remain default in Oneiric, I believe it should be fixed.
BTW, here is the 6 year old bug report: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/18995](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/18995). It is marked as low importance and has been around for a really long time.

Installing mozplugger would open the .doc in the browser with LibreOffice (not just FF, but any browser). Not exactly what you want but iMO even better.

---


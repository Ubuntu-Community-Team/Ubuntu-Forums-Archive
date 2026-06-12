---
title: "[SOLVED] Some users can't login to a Gnome Session on Intrepid"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by rlogan on 2008-11-05
Hi all

Looking for some help with this one.

We have four logins on one machine, two users can login just fine, yet two logins just land on a black screen and sit indefinitely.

I have tried to create a new login and the same result, which I thought was rather strange.

It appears to be a Gnome issue as the same users that can't login to Gnome can login to a KDE4 session.

Any thoughts ?

Cheers 
Richard

---

### Post by bscbrit on 2008-11-05
OK, I've got no quick solution for this one.  The first thing that I think you should check is the permissions on each users' area.  Are they the same on each area?  (Presumably YES because they can log in under KDE)  Then check the permissions on the hidden .gnome files and compare them with the permissions on the appropriate .kde files (or whatever they are called).  It would also be worth doing a diff between the relevant files in a working area and those in a non-working area.

Hope this is at least partially helpful!

---

### Post by adipradana on 2008-11-05
Same problem here. The user i've upgraded with works fine, other users hang after login (blank desktop showing with mouse cursor). Tried using KDE and works fine.

---

### Post by rlogan on 2008-11-05
I agree it is most likely to do with the Gnome specific files for the particular logins, so I will try and get time today to check it our further. It just strike me as strange that the two users with admin access don't have probs, yet the ones that didn't when the upgrade was performed are having problems. When I give admin access to the other users it doesn't make a difference. I feel there is a permissions issue with some files related to Gnome. Just one of those annoying probs, the ATI machine went fine but the NVidia one is the pain.

Cheers

Richard

---

### Post by bscbrit on 2008-11-05
Can the users log in to failsafe Gnome by choosing an alternative session from the session manager?

---

### Post by bscbrit on 2008-11-05
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/279450](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/279450)

There seem to be similarities between the fault you are describing and this bug report.  If you move to the last few entries near the bottom of the page there are a few potential solutions, if indeed your problem is related.

If you decide that it is not the same bug, please let me know and I will continue to investigate it.

---

### Post by pi.boy.travis on 2008-11-05
> **rlogan said:**
> I agree it is most likely to do with the Gnome specific files for the particular logins, so I will try and get time today to check it our further. It just strike me as strange that the two users with admin access don't have probs, yet the ones that didn't when the upgrade was performed are having problems. When I give admin access to the other users it doesn't make a difference. I feel there is a permissions issue with some files related to Gnome. Just one of those annoying probs, the ATI machine went fine but the NVidia one is the pain.

Cheers

Richard

Did you upgrade or do a clean install?

---

### Post by rlogan on 2008-11-05
Thanks for all your help !

It was an upgrade from 8.04.1 to 8.10 that seems to have had the issue. 

The bug #279450 does sound similar but it does specify a light brown screen and this is a black screen with only two logins. The mouse pointer is up and moves freely. I will check out the options/possible solution when I get back in a couple of hours.

Cheers

Richard

---

### Post by rlogan on 2008-11-05
Thanks bscbrit

I have tried the failsafe login for one of the users that cannot login and it works fine. Any thoughts ?

---

### Post by rlogan on 2008-11-05
Thanks for the tip of the Launchpad link, I took the suggestion of Mark McSweeney and removed the .gnome .gnome2 .gconf .gconfd files/folders and logged in on one login that was having difficulty. 

So it all is lookign positive, will repeat the effort with my daughters login.

Thanks heaps, one other thing I need to do is to mark this thread as solved any thoughts as to how I do that ?

Cheers

Richard

---

### Post by rlogan on 2008-11-05
Just rebooted and tried to login again and back to the black screen.... What a pain !!!

---

### Post by rlogan on 2008-11-05
We have a winner !!!!

I changed permission on .gnome .gnome2 .gconf .gconfd to the particular users create/delete and read/write, also when logging in hit the session type to gnome (just to be sure) and when requested to if I wanted this as the default I said yes of course.

All is now working just fine after reboot and a couple of logins.

An interesting thing I found is that I don't have  a .metacity on this machine and the the other machine that worked from day one of Intrepid RC was just fine. Might be just a conincidence ???

Thanks all for your help

Cheers

Richard

---

### Post by bscbrit on 2008-11-06
Richard - I am pleased that you have found your solution!

You can mark this thread as SOLVED by using the Thread Tools near the top of the page.

Good Luck and hope to see you around the forums.

---

### Post by rlogan on 2008-11-06
Many thanks

Cheers 

Richard

---


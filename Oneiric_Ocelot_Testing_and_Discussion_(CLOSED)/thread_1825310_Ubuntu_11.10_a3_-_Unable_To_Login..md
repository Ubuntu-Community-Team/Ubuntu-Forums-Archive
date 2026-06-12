---
title: "Ubuntu 11.10 a3 - Unable To Login."
date: 2011-08-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-08-15
I find myself reluctant to ask for help after my last post got no attention whatsoever. But here I go anyway.

A few weeks ago, I was at Alpha 2. All was smooth sailing, until one day the X server wouldn't boot up at all. As I said, my petition for help went unanswered, so I found myself running back into the loving arms of The Narwhal; all the while, hating myself for not keeping a backup of my files.

Now I decide to give Alpha 3 a try (this time backing up my precious files), however, the going is not so good.

From 11.04, ran the upgrade, no problems.

Reboot into 11.10. Loved the new LightDM login screen.

Typed in password. The screen flashes, the command-line is showed (along with boot messages), screen flashes white, then back to login screen (whole process takes roughly a second).

Typed in password again. Same thing.

Each time I try to login to my user area, I am just kicked back to the login screen. Using the "Other" option with my username yields the same results.

Strangely enough, only the guest session seems to work.

At first, I thought that the Nvidia driver was to blame, so I used Jockey-GTK to remove it, but the problem persists.

Any help would be greatly appreciated.

---

### Post by meborc on 2011-08-15
I strongly suggest you do a fresh install of alpha 3, NOT a upgrade from 10.04

GDM was removed and replaced by lightDM and major other stuff has been changed.

Upgrading to a development release (which has not been proof-tested for upgrade) is asking for trouble :) The upgrade path will be tested and fixed later in the cycle 

Fresh install is the way to go!

---

### Post by jamlam on 2011-08-15
I'm having the same issue. In my case the problem seems to be down to having an encrypted home dir, which for some reason doesn't get mounted correctly via lightdm. If I Ctrl-Alt-F1 to a console and login as my normal user I can then login via Lightdm fine.

---

### Post by dino99 on 2011-08-15
from recovery mode:
- sudo apt-get purge gdm 
- sudo apt-get install lightdm lightdm-gtk-greeter

---

### Post by dino99 on 2011-08-15
> **jamlam said:**
> I'm having the same issue. In my case the problem seems to be down to having an encrypted home dir, which for some reason doesn't get mounted correctly via lightdm. If I Ctrl-Alt-F1 to a console and login as my normal user I can then login via Lightdm fine.

should be fixed with the coming next kernel 3.1 rc2

---

### Post by PhantmKllr on 2011-08-15
> **dino99 said:**
> from recovery mode:
- sudo apt-get purge gdm 
- sudo apt-get install lightdm lightdm-gtk-greeter

This did not help.

> **jamlam said:**
> I'm having the same issue. In my case the problem seems to be down to having an encrypted home dir, which for some reason doesn't get mounted correctly via lightdm. If I Ctrl-Alt-F1 to a console and login as my normal user I can then login via Lightdm fine.

Yup, I think that we're having the very same problem. I'm starting to rethink the purpose in using EcryptFS. I've read around the forums that using encryption can really slow down your computer (although I haven't yet noticed any detrimental effects.

But knowing my files are encrypted does help to put my mind at ease.

> **dino99 said:**
> should be fixed with the coming next kernel 3.1 rc2

So you're saying that there's a problem between LightDM, EcryptFS, and the current kernel?

---

### Post by grahammechanical on 2011-08-16
A week ago I could not log in at all with Light DM. I had to install and use GDM in order to login. And then I could only use 2D as 3D would give me a desktop background without any panels or launcher and no way to shutdown short of the command line.

I waited, did daily updates from the command line and this morning switched back to Light DM and now I can log in and I get Unity 3D.

We are still a long way from a suitable release candidate but what do we expect? Enjoy the ride or stick with distribution releases.

Regards.

---

### Post by pressureman on 2011-08-16
> **jamlam said:**
> I'm having the same issue. In my case the problem seems to be down to having an encrypted home dir, which for some reason doesn't get mounted correctly via lightdm. If I Ctrl-Alt-F1 to a console and login as my normal user I can then login via Lightdm fine.

I had exactly the same problem, and resorted to exactly the same workaround.

FWIW, GDM has no problems logging in.

---

### Post by rbrick49 on 2011-08-16
well you are all lucky I had to do a fresh install to fix my mess after yesterday updates. I dont know what the confliction was but I guess fglrx and compiz had a lot to do with it

---

### Post by rbrick49 on 2011-08-17
well today after another crash and a fresh update I had the same trouble again today. I downloaded the latest build and installed did all the updates back to wont boot I found my boot loader was missing reinstalled all a ok except unity is still kapoot from some bug

---

### Post by meborc on 2011-08-18
> **rbrick49 said:**
> well today after another crash and a fresh update I had the same trouble again today. I downloaded the latest build and installed did all the updates back to wont boot I found my boot loader was missing reinstalled all a ok except unity is still kapoot from some bug

yep... fun times during dev-testing ;)

sometimes people complain that nothing is broken and it is too boring. this cycle has been quite entertaining compared to some

---

### Post by PhantmKllr on 2011-08-19
> **grahammechanical said:**
> A week ago I could not log in at all with Light DM. I had to install and use GDM in order to login. And then I could only use 2D as 3D would give me a desktop background without any panels or launcher and no way to shutdown short of the command line.

I waited, did daily updates from the command line and this morning switched back to Light DM and now I can log in and I get Unity 3D.

We are still a long way from a suitable release candidate but what do we expect? Enjoy the ride or stick with distribution releases.

Regards.
Yup, the updates fixed my install as well.

Marking as solved.

---

### Post by moore.bryan on 2011-08-19
And the updates broke my system... I love testing!!!!

---

### Post by PhantmKllr on 2011-08-20
> **moore.bryan said:**
> And the updates broke my system... I love testing!!!!
+1

Testers = Ubuntu Elite

---

### Post by moore.bryan on 2011-08-20
And I solved it by installing ubuntu-desktop, which was so very intelligently removed by a recent upgrade. ;-)

---


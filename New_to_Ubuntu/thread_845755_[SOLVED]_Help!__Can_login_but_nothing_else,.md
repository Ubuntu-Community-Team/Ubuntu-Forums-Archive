---
title: "[SOLVED] Help!  Can login but nothing else,"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by ebeckhusen on 2008-06-30
Okay, I don't know what I did (as usual, :D) but my system was running fine until I messed with something this morning.

Currently, I can log in and it will take me to my desktop with no trouble.  But, I can't do anything once I get there.  The panels are gone, and I can't bring up a terminal.  Compiz is working, as is Awn (well, Awn is sort of working).  I can only run add/remove, synaptic, and update manager right now, from the menu plugin for Awn.

I don't really know what I did to cause it because I was doing a few different things this morning and the problem only started on reboot.

I can start in safe graphics mode and everything works perfectly, so I susupect it's something to do with my start up files.  But, I don't know what scripts are used in start up or where to even begin finding them.
Any help is appreciated, and I'll add whatever information you need provided you let me know how to find it.

---

### Post by phidia on 2008-06-30
Desktop issues can be hard to track down.
Have you already got a test user? You can create another user, in safe graphics mode if need be, and see how that account behaves. > sudo adduser. If that account is alright you can try replacing preference files or even backup your current user and replace that user.

---

### Post by ebeckhusen on 2008-06-30
Okay, I added a test user and that worked fine (though I didn't try out everything, and it obviously didn't have the customizations I had made on my regular account).

So, I guess I'm going to wait for some other ideas, and failing that will either back up my user files and make a new account or start over from scratch.

---

### Post by ChameleonDave on 2008-06-30
> **ebeckhusen said:**
> 

So, I guess I'm going to wait for some other ideas, and failing that will either back up my user files and make a new account or start over from scratch.

There is no need to lose much.  Keep an archive of your old user directory.  It still contains all of your personalisations.  By going into it manually, you can rescue stuff like your Firefox profiles, for example.

Or, you can go in and selectively delete stuff, looking for the config file that is incorrect.

---

### Post by ebeckhusen on 2008-07-01
> **ChameleonDave said:**
> There is no need to lose much.  Keep an archive of your old user directory.  It still contains all of your personalisations.  By going into it manually, you can rescue stuff like your Firefox profiles, for example.

Or, you can go in and selectively delete stuff, looking for the config file that is incorrect.
Thanks for that.  I ended up deleting all the hidden folders except for those that I knew for sure had some special personalization and everything works fine now.  Did have to make a few adjustments once I got it working again, but nothing major, and I still don't know what I did wrong in the first place.

---


---
title: "Disk Usage Steadily increases to full"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by FGPonce on 2012-12-19
[SIZE=2]Hi,
  since upgrading to 12.0.4 my hard drive regularly and rapidly fills up (1Gig /min...ish).

I tracked this to an error log in the cups directory (gets up to 251GB) then disk full errors all over the place.

Only work round is to delete cups directory after a restart.

However, recently started again with a steady fall (should be getting on  for 300 GB free). No directories ballooning now so have no idea whats  going on.

Any suggestions welcome. Its a major pain in the bum. I was nice and  happy before the upgrade but got told my ubuntu version was no longer  supported so took the plunge....[/SIZE]

---

### Post by Pjotr123 on 2012-12-19
I advise a clean reinstall with the 12.04.1 CD. If the problem persists, this will at least make debugging easier. But I expect that this might very well solve the problem once and for all.

Get the 12.04.1 iso here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

A clean reinstallation can be done like this:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

Good luck! :)

---

### Post by mcduck on 2012-12-19
Since you even found out the exact log file in question, did you take a look what are the error messages that are causing thwe log to grow that large? There is definitely going to be some repeating error message that would tell you what's the problem and point to right direction to fix it... ;)

---

### Post by FGPonce on 2012-12-20
Hi Guys,
 thanks the the advice. I'll look into a clean install. However would be nice to know why......so here is some info.

Just restarted and cups directory reappeared. It was not accessable so used chmod to change permissions. Error log was there and filling up again with :

E [21/Dec/2012:10:58:50 +1300] Unknown directive SystemGroup on line 16 of /etc/
cups/cupsd.conf.
E [21/Dec/2012:10:58:50 +1300] Directory "/usr/lib/cups/notifier" has insecure p
ermissions (040755/uid=1000/gid=0).
W [21/Dec/2012:10:58:50 +1300] Notifier for subscription 8 (dbus://) went away, 
retrying!
E [21/Dec/2012:10:58:50 +1300] Directory "/usr/lib/cups/notifier" has insecure p
ermissions (040755/uid=1000/gid=0).
W [21/Dec/2012:10:58:50 +1300] Notifier for subscription 8 (dbus://) went away, 
retrying!
E [21/Dec/2012:10:58:50 +1300] Directory "/usr/lib/cups/notifier" has insecure p
ermissions (040755/uid=1000/gid=0).
W [21/Dec/2012:10:58:50 +1300] Notifier for subscription 8 (dbus://) went away, 
retrying!
..............................................etc

Rob

---

### Post by audiomick on 2012-12-20
Can you think of anything you have done that might have changed the permissions of /usr/lib/cups/notifier ? The folder should belong to root. Have a look and see if it does.

---

### Post by FGPonce on 2012-12-20
Thanks M,

It was set to my current user not root. Just changed it to root with chown.

Its a bit worrying though. Should there be a list of system files that should only have root ownership? If that has been changed am I in trouble? Is there an easy way to check?

R

---

### Post by squakie on 2012-12-20
I would think it would be more important to know not to just change permissions on files - there are reasons they are set up the way they are and a lot of novices seem to have a need to (1) make sure "I" own everything and (2) delete a bunch of folders and files because they don't know what they are.  Not saying that's what you did, but it's common amongst the novice.  Best advice is if you don't know, don't touch.  If you didn't change this permission, via directly at the file level or by the folder level, I would be more concerned about how the ownership changed.

---

### Post by mcduck on 2012-12-21
> **FGPonce said:**
> Thanks M,

It was set to my current user not root. Just changed it to root with chown.

Its a bit worrying though. Should there be a list of system files that should only have root ownership? If that has been changed am I in trouble? Is there an easy way to check?

R

*All* system files should be owned by root. The only files belonging to users are the ones in their home directories.

As far as I know there isn't any complete list of the permissions required for all the system files, so I'd be very very careful about changing the permissions of any system file either. Messing with them usually results in having to reinstall the system, as that's quicker than trying to manually track correct ownership & permission for each file and directory.

---

### Post by Pjotr123 on 2012-12-21
mcduck +1

Furthermore: today there was a new cups in the updates for 12.04. Does the problem persist after installing those?

---

### Post by FGPonce on 2012-12-22
Its a fair cop. I must admit the thing I hate about Ubuntu is regularly being told I don't have permissions to save files to a particular hard drive etc. I think this current problem was caused by me setting the owner of the usr/lib directory to my username since I'd tried to run something or cd in, or save sometyhing can't quite remember.....and not had permission. I was having Xauthentication messages popping up about that time as well. They seem to have gone away however since my disk isn't full.

Thanks for all the feedback by the way the learning curve is still in the fun log phase.
;)

---

### Post by arpanaut on 2012-12-22
For educational purposes this link should serve you well.
Once you understand the concept things will become easier.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by squakie on 2012-12-22
And as I stated in my post, and others after me, don't change ownership, permissions, etc., on anything not in your folder tree.  That way you won't mess up the system - only yourself.

---


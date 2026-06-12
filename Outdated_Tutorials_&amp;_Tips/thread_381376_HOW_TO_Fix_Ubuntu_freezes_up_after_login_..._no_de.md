---
title: "HOW TO: Fix: Ubuntu freezes up after login ... no desktop"
date: 2007-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by alienseer23 on 2007-03-10
I had a problem some time ago where I would put in my login name and password, and then the system would hang forever with no desktop, no splash screen, nothing. Rebooting did not fix this. X was dead. The only work-around that would help was to create a whole new user and start over, killing the old user. 
This is for Edgy, 32bit. Tested, reproduced and it works. 
It may not work for all hang issues, but I have helped more than one system recover using this fix, and have not yet had to do anything else. This also should work on other releases and architecture types.
I do not plan on supporting this thread, it is simple beyond belief.

Simply press ctrl+alt+F1.                                       (switch to the first console)

Enter in your login name and password.                 (log in)      

enter in: "rm /tmp -r"                                             (clear out your /tmp directory)
**you may want to do that as root, or use sudo if there are files that won't go away** 
edit: if you try this as root **make certain you do not actually remove the tmp directory itself!!!**

reboot for good measure.                                       (reboot for good measure)

That's right. Simply clear out your temp files. Did you press ctrl+alt+backspace and then tried to log in, or cut power to the system and forgot to mention that? When X is shut off in this way, the OS and other programs do not get to clean up after themselves, so whatever caused your hang to begin with, was still in there, causing your system to hang when you tried to log in again.

I hope this helps someone!!! I smashed my head into a brick wall for a few weeks before stumbling onto this very simple fix.   GOOD LUCK

Alienseer23

---

### Post by an0nu4nc3 on 2009-05-11
And if i accidently remove the tmp directory?

I guess i was supposed to be 'in' the directory, before i ran the 'rm /tmp -r' command? Because just running it deletes the tmp directory... so either i'm missing something or you've failed to specify exactly how one does not remove the directory you're telling the terminal to purge.

Hope you can reply in the next 5 minutes because my essay is due... and it's lost in some weird 'hang' limbo restart failure.

Update: This even older thread got me out of that pickle and back into the no desktop problem / session lasting less than 10 seconds problem. So my chmod is either wrong or i should delete the tmp folder again and follow the aforementioned thread, found here:

[http://ubuntuforums.org/showthread.php?t=236156](http://ubuntuforums.org/showthread.php?t=236156)

---


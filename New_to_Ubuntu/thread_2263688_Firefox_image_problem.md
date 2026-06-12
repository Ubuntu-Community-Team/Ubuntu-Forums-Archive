---
title: "Firefox image problem"
date: 2015-02-02
forum: New to Ubuntu
---

### Post by fibberts on 2015-02-02
Hello everyone,

Randomly, when I try to open a large image in firefox it will hang for a few seconds.  Then the screen goes black and I'm back at the log-in screen and ubuntu is asking me pick a profile, as though I had logged out.  I've switched to chromium for now which seems to be working but I prefer firefox.

So, two questions:
1 - How do I stop firefox from pulling these shenanigans?
2 - For the sake of googling what is this obnoxious behavior called?  It's not "crashing" or "hanging".  What would you call it?

Thank you in advance! :)

---

### Post by haplorrhine on 2015-02-03
Then I guess you can't report the problem, can you... :(
My help might be better than nothing, but I'm sure that other users could critique my advice.  :P

You could try reinstalling firefox with a different utility (e.g. Software Center versus the "apt-get" command line utility).
Note, the "apt-get purge" option gives a more thorough uninstall.



If you're willing to learn AppArmor sandboxing, you could use it to test whether firefox is doing something that it shouldn't.  Unfortunately, I'm such a noob that I have _*absolutely no clue*_ how likely this is to work.
To install some basic apparmor utilities:[B]
sudo apt-get install apparmor-utils[/B]
and some standard profiles
[B]sudo apt-get install apparmor-profiles
[/B]parser in the standard FF profile
[B]sudo apparmor_parser /etc/apparmor.d/usr.bin.firefox
[/B]and set it to enforce[B]
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
[/B]and check that it's enforcing
**sudo apparmor_status**
If FireFox is doing something it shouldn't be doing, this should put a stop to it.

---

### Post by Holger_Gehrke on 2015-02-03
I'd say it's not Firefox but the X-server that crashes, possibly because of something FF did. Errors like that are notoriously hard to track down. I've just googled "firefox crashing X server" and had 1.1 million results dating back to 2008, often with nobody knowingly fixing it; after some update the problem was just gone ...

You could take a look in ~/.xsession-errors or ~/.xsession-errors.old and in various logs in /var/log/, perhaps FF or X gave out an S.O.S. saying what happened ...

---


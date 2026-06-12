---
title: "How Do I Downgrade my Ubuntu Install?"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by playing_with_matches on 2014-04-29
So I upgraded to 14.04, and it has been nothing but headaches for me.  Things that worked in 13.04 and 13.10 just don't work in 14.04 (most critical right now: ipod classic causes every application to crash: Rhythmbox, GTKPod... think it has something to do with the libg4pod library, but I have no idea what I'm doing outside of that).  

I haven't been able to fix it, and I see my only two options now is to either switch back over to Windows (rather not, been using ubuntu since 2006-07), or downgrading to a version of Ubuntu that just works.  How do I go about downgrading? Is it possible to do without formatting everything and running a new install?

Alternatively, if anyone knows how to fix this ipod issue that would be even more awesome.

---

### Post by Mark Phelps on 2014-04-29
>  How do I go about downgrading? Is it possible to do without formatting everything and running a new install?

There is no "downgrade" option that will let you rollback to a previous Ubuntu version.  You will need to reinstall the old version.

---

### Post by Impavidus on 2014-04-29
There is no simple downgrade, but you could install 12.04 from the live disk. I think you can even do so without wiping your home directory (depends on whether you have a separate /home partition). I found that 14.04 is clearly less polished than 12.04, although usable. But I kept 12.04 just in case. Try again in a few months, or dual boot both releases for a while.

---

### Post by sudodus on 2014-04-29
Unfortunately there is no way to downgrade a system. Upgrading is always risky, so it is a good idea to ***backup*** the system before upgrading.

Anyway, before changing the system again, I suggest that you backup the whole system or at least your personal files.

Maybe the best option is to copy your /home directory into a separate partition, and then install 13.10 telling it to use the /home partition ***wihout formatting***. By the time of end of life (in July), 14.04 LTS will probably be debugged and polished and external applications (like your ipad one) should work.

If that does not work, a clean install is the only alternative if you have to downgrade the system to a previous version.

Good luck :-)

---

### Post by LastDino on 2014-04-29
Well, unfortunately, like everyone else said, there is no downgrade. But Ubuntu did say that most things installed on previous version of Ubuntu might not work after update. Have you maybe tried re-installing those applications? And since this is going to need fresh install anyway if that doesn't work, go for newer version of Ubuntu only, most of those things you mentioned are working fine here.

---

### Post by playing_with_matches on 2014-04-29
Thanks for the advice everyone.  I did try to uninstall the programs (Rhythmbox, it's libraries like libg4pod) and reinstall and still no luck.  I'm going to attempt to use the live CD for 14.04 and see if it works in there, because maybe something just got messed up during the upgrade process.  If not, looks like I need to do a clean wipe, since my home drive is on the same partition as the OS.

---

### Post by playing_with_matches on 2014-04-29
Unfortunately I have the same exact problem running from the live CD :-( .  Oh well, time to try out an old version of ubuntu if I can find one or Linux Mint.

---


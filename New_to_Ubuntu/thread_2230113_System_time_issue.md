---
title: "System time issue"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by BernardCayeux on 2014-06-17
Hi,

I have similar issue. 

Just re-installed (not upgraded but fresh install) ubuntu 14.04 in dual boot with W7. My previous set up was with Ubuntu precise and all was fine.
 
Since I installed Trusty Tahr, the clock is going all wrong. It is running much faster than real time, and irregularly. This is irrespective of whether I set it to synchronise on Internet or not. I installed ntp without change.

Don't think it can be the motherboard / Bios because I don't have this issue with Windows 7.

I have tried to set local time to different places having same time zone as where I live... no better.

Can anyone help?

Thanks in advance

---

### Post by sandyd on 2014-06-17
Ive moved your post to a separate thread.

---

### Post by BernardCayeux on 2014-06-17
Hi,

Update.
Looks like bug is now solved after some daily updates... I think I saw that there was more ntp updates in the pack...

Will post again if bug comes back

---

### Post by BernardCayeux on 2014-06-18
2nd Update.

Bad news, the issue is back again; whether I set to sync with Internet or not.

One additional info which looks irrelevant: When it worked yesterday it was from a location where I had normal Internet connection speed. When it is bugging is from a location where connection is very slow...

Thanks to help

With best regards

---

### Post by Karlchen on 2014-06-18
Hello, BernardCayeux.

You are absolutely sure the root cause is not much more trivial:
 Windows 7 assumes your hardware clock uses your local timezone and sets the hardware clock accordingly when time is synchronized with a time server.
Ubuntu 12.04 had been instructed to use the same approach by writing **utc=NO** into the file **/etc/default/rcS**.
Ubuntu 14.04 has not yet been instructed to use the same approach. It is still using the default setting **utc=YES** in **/etc/default/rcS**, which will make it assume your hardware clock returns UTC and which will make it set the hardware clock accordingly when the time is synchronized with a time server.
Could this be the root cause?

Kind reagrds,
Karl

---

### Post by BernardCayeux on 2014-06-27
Hi Karl,

Thanks for you time and help; I had not been able to login to the forum over the last week. My UTC=no, so it's not the cause.

Another important detail: when I watch the clock turning, the seconds accelerate drastically every minute then go back to normal. When watching a "slideshow" on a website the pictures start flipping fast then back to normal approx. every minute. It is a real clock problem.

I have checked again my CPU / Bios clock and compared to a stopwatch. It runs perfectly...

Do you think a re-install from the CD will help?

Looking forward to your suggestions

Regards

---

### Post by Karlchen on 2014-07-01
Hello, BernardCayeux.

Hm. As a matter of fact, I had really hoped UTC=yes might be the cause. It is not. Fine. Yet, this was the only idea that occurred to me. So I am clueless right now.
Before you try re-installing, would it not make sense to use a bootable live system in order to find out whether the problem can be observed there as well. In case the problem is present when running the live system, in this case a re-installation would not make much sense, would it.

Kind regards,
Karl

---


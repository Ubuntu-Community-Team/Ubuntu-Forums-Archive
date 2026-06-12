---
title: "[SOLVED] apt-get ridiculously slow"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by drewcoon on 2008-11-01
I've always used apt-get to get and install programs off of the repos, but recently (starting about two days ago), apt-get has been working VERY slow, as you can see:

```
andrew@linbeast:~$ sudo apt-get install ntp
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ntp-doc
The following NEW packages will be installed:
  ntp
0 upgraded, 1 newly installed, 0 to remove and 15 not upgraded.
Need to get 432kB of archives.
After this operation, 1069kB of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com hardy/main ntp 1:4.2.4p4+dfsg-3ubuntu2 [432kB]
40% [1 ntp 173397/432kB 40%]                                     674B/s 6min23s
```

674B/s download speed and I have high speed cable? Actually, this is pretty much peak speed (most of the time it doesn't download anything at all, took about five minutes to get this 432Kb download to 40%, where it is stuck). Is Ubuntu having problems with it's Canadian servers or something? I can't update or anything :(

Would it help to switch from the Canadian servers? How? There is nothing wrong with my internet connection, it's just getting updates from Ubuntu that's slowed to a crawl for the past two days.

I'd really appreciate any help, thanks :)

---

### Post by OrangeCrate on 2008-11-01
Not sure, but I would assume the servers are really smoking, if not on literally on fire, with the heavy demand for downloads of the new 8.10 release. My suggestion would be to wait a couple of days, and see if it all settles out...

---

### Post by drewcoon on 2008-11-01
Oh man, I was totally oblivious to 8.10 being released, guess I won't be getting that either... For a while.

I guess that would explain the slow speeds I'm getting, Thanks!

---

### Post by dsurge on 2008-11-01
switching from the canadian servers does help. there are also two posts on speeding up dns times:

[http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

I've been having the same problems and those two things helped a lot. I'm still going slow (between 10-40kb/s) but its better than 5.

See if they work

---

### Post by drewcoon on 2008-11-01
> **dsurge said:**
> switching from the canadian servers does help. there are also two posts on speeding up dns times:

[http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

I've been having the same problems and those two things helped a lot. I'm still going slow (between 10-40kb/s) but its better than 5.

See if they work

I don't know if that's related to my problem or not, but I've bookmarked those pages and I'll tinker around with my DNS settings... Tomorrow though, I'm going to sleep now :p

thanks!

---

### Post by doan_1 on 2008-11-13
Any word on this?  I have not been excited to see my connection reach dial up potential speeds in almost 10 years!  BTW, <24 with UBUNTU.  Hopefully ifs all that I expect and maybe switch everything over (I need to sync both my iPhone and WM6.1 devices, and a Symbian.  Or at least one!),

---

### Post by hyper_ch on 2008-11-13
you could try instead apt-p2p

---


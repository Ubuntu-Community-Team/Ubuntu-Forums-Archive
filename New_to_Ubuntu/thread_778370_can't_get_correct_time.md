---
title: "can't get correct time"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by kaston on 2008-05-02
i have set my clock to be synchronized with servers but my time is off by about half an hour.  how can i fix this?

---

### Post by Xiong Chiamiov on 2008-05-02
Is it half an hour off, no matter which server you tell it to sync to? (half hour off what the server should be, that is)

---

### Post by kaston on 2008-05-02
yeah, i've tried a couple different servers.  i am in vancouver so i normally have it set to the NRC server.

---

### Post by Xiong Chiamiov on 2008-05-02
So, just to clarify, is it always 30 minutes off what you expect, no matter the server, or is it only off on that particular time zone?

---

### Post by kaston on 2008-05-02
seems to be wrong in all north american time zones.  right now it is 10:40pm PST but my clock says 9:55pm

---

### Post by Xiong Chiamiov on 2008-05-02
That certainly is odd, as my clock shows 10:40 as well (well, 10:43).  So it's not the servers... hmm.  Stumped.

---

### Post by kaston on 2008-05-02
is there anything i can check from the command line?  is it possible i have a virus?

---

### Post by Xiong Chiamiov on 2008-05-02
Hmph, virus.  Besides the fact that there are very few (if any, I haven't kept up) viruses that would run on Linux, unless you've been giving root access to things that you shouldn't have, it wouldn't be able to do too much (aside from deleting your home directory).

---

### Post by Monicker on 2008-05-02
Have you verified that your time zone is set correctly?

---

### Post by Xiong Chiamiov on 2008-05-02
> **Monicker said:**
> Have you verified that your time zone is set correctly?
It's not just his specific time zone, as he tried syncing to the PST zone and it was off as well.

---

### Post by Monicker on 2008-05-02
> **Xiong Chiamiov said:**
> It's not just his specific time zone, as he tried syncing to the PST zone and it was off as well.

He said it was off in the PST zones, not that he synced to them.  It is most likely something with his tzdata being incorrect, or his time zone settings.

---

### Post by kaston on 2008-05-02
i am on the west coast (PST).  i tried central, eastern and mountain time zones and they were all incorrect also.  what is this tzdata you speak of?

---

### Post by Monicker on 2008-05-02
> **kaston said:**
> i am on the west coast (PST).  i tried central, eastern and mountain time zones and they were all incorrect also.  what is this tzdata you speak of?

It lets your system know how to handle different time zones.

```

~$ apt-cache show tzdata


Package: tzdata
Priority: required
Section: libs
Installed-Size: 6172
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: all
Version: 2008b-1ubuntu1
Replaces: libc0.1, libc0.3, libc6, libc6.1, locales
Provides: tzdata-lenny
Depends: debconf | debconf-2.0
Filename: pool/main/t/tzdata/tzdata_2008b-1ubuntu1_all.deb
Size: 655616
MD5sum: 55cee996324a5025a9011662c13c8b99
SHA1: fe3a918cee2590ce6e44c482ea8d9173a23fff0a
SHA256: f20566f65b15b382fcced6427702c26c2578e26311fe7c2c704ebe462fe86720
Description: time zone and daylight-saving time data
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: minimal

```

You go over the settings again from a terminal:

```
sudo dpkg-reconfigure tzdata
```

If that does not help, the only other thing I can think of is a problem with hwclock.

If you run "date" and "hwclock" from a terminal, do the times match?

---

### Post by kesman on 2008-05-02
If you have enabled the "synchronize clock with internet servers" it probably installed the ntpd -daemon for you. It synchronizes the time always at boot, so you will have to restart the kernel(your pc) for it to get the time from servers.

---

### Post by kaston on 2008-05-02
> **Monicker said:**
> It lets your system know how to handle different time zones.

```

~$ apt-cache show tzdata


Package: tzdata
Priority: required
Section: libs
Installed-Size: 6172
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: all
Version: 2008b-1ubuntu1
Replaces: libc0.1, libc0.3, libc6, libc6.1, locales
Provides: tzdata-lenny
Depends: debconf | debconf-2.0
Filename: pool/main/t/tzdata/tzdata_2008b-1ubuntu1_all.deb
Size: 655616
MD5sum: 55cee996324a5025a9011662c13c8b99
SHA1: fe3a918cee2590ce6e44c482ea8d9173a23fff0a
SHA256: f20566f65b15b382fcced6427702c26c2578e26311fe7c2c704ebe462fe86720
Description: time zone and daylight-saving time data
 This package contains data required for the implementation of
 standard local time for many representative locations around the
 globe. It is updated periodically to reflect changes made by
 political bodies to time zone boundaries, UTC offsets, and
 daylight-saving rules.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: minimal

```

You go over the settings again from a terminal:

```
sudo dpkg-reconfigure tzdata
```

If that does not help, the only other thing I can think of is a problem with hwclock.

If you run "date" and "hwclock" from a terminal, do the times match?

i tried running sudo dpkg-reconfigure tzdata but after finishing it still gave me the wrong time.  

i ran date and hwclock.  they both give the same incorrect time.

rebooting does not solve the problem

any other ideas?

---

### Post by kaston on 2008-05-02
anyone?

---

### Post by Monicker on 2008-05-03
Hrrm. If you run "sudo ntpdate pool.ntp.org" does the time get corrected, or is it still off by half an hour?

---

### Post by HyperHacker on 2008-05-03
I'm having the same problem, whether I have it set to sync or manual. If I actually go into the control panel and sync it, it's correct, but after a day or so it's off by half an hour. I had it set to manual in Windows (stupid DST bugs) and it was always accurate.

---

### Post by jlabomb on 2008-05-20
I have had the wrong time displayed since I upgraded to hardy heron. It was 4 hours behind. So when it was Noon it displayed 8 AM. My quick fix was to set my location to a time zone 4 hours ahead and now my time is correct. But I noticed when i viewed the clock it says EDT - 4. I am not sure if that is the same problem you seem to have or not.

[IMG]http://scalos.webs.com/clock.jpg[/IMG]


[SCALOS - I Searched the Web So You Don't Have To]("http://scalos.webs.com")

---

### Post by ectospasm on 2008-05-28
I've got a similar problem, in that I come home every day and my time is off by anywhere from 1 to 5 hours.  To fix it, it's easy:

```
sudo /etc/init.d/ntp stop && \
sudo ntpd -g -q && \   # this actually resets the time
sudo /etc/init.d/ntp start 
```

And my time will be correct, probably until my laptop screen goes to sleep.  My timezone is correct, at least tzdata is pointed at the right place.  I just can't figure out how to make it permanent.  I guess I could throw it into a cron job, but that doesn't actually fix the problem, and gives me gaps in the logs...

---

### Post by Franko30 on 2008-06-03
Hi,

I get these ntpd problems, too with my Ubuntu 8.04 install.

When I disable the ntp deamon (set time manually in the clock applet) and I run ntpdate manually, everything works.

But still my laptop clock loses about 30-40 minutes in one day since I installed 8.04...

Cheers

Franko30

---


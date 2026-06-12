---
title: "Reading database takes forever"
date: 2006-02-28
forum: Repositories &amp; Backports
---

### Post by ashrack on 2006-02-28
When doing the following on my NOTEBOOK
```
apt-get install ****
```
or
```
dpkg -i ****
```
I have to wait for
```
reading database
```
for almost half a minute. Anyway to decrease this time?

Hope this is of some use
```
(Reading database ... 95102 files and directories currently installed.)

```

ps.heres my 'source.list'
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```

---

### Post by 5-HT on 2006-03-01
Has it always taken so long?

I'm not sure but believe that 'Reading Database' refers not to the repositories, but rather your system's database of installed packages.

If so, it seems to reason that the duration should be dependent upon your system's resources as well as the number of packages you have installed; 95102 being quite large.

In regards to speeding it up, apart from leaning out the packages on the system or adding resources, I'm not certain if there would be (but would like to know myself if there is).

Based on the specs posted in your sig, looks like it may be the number of packages you have that is the major influence in your case.

My system is much slower that either of the two in your sig, but I have greatly less packages. For me, the 'Reading Database' step is a bit of a hang, but not near the one minute mark.

HTH

---

### Post by ashrack on 2006-03-02
> **5-HT][/quote]
> Has it always taken so long?
no! First it was quick but then gradually the speed was decreasing as I was installing packages.

> I'm not sure but believe that 'Reading Database' refers not to the repositories, but rather your system's database of installed packages.

I concur

> If so, it seems to reason that the duration should be dependent upon your system's resources as well as the number of packages you have installed said:**
> 
What is your number of packages? 

[QUOTE]In regards to speeding it up, apart from leaning out the packages on the system or adding resources, I'm not certain if there would be (but would like to know myself if there is).

I removed about 15000 packages with a help of DEBFOSTER. So now I believe I have only the most needed packages. So reading database is tollerable now.

[QUOTE]Based on the specs posted in your sig, looks like it may be the number of packages you have that is the major influence in your case.

Its my believe that READING DATABASE is mostly HDD related so a faster one would achieve this quicker. Unfortunerly I have one of those notebooks that still have the 4300RPM HDDs.

> My system is much slower that either of the two in your sig, but I have greatly less packages.

On my desktop computer which  has a 7200RPM HDD 'Reading Database' is below 10sec and probably has even more packages...

> For me, the 'Reading Database' step is a bit of a hang, but not near the one minute mark.
Sory, I meant I have to wait almost half a minute, have edited the first post

---

### Post by 5-HT on 2006-03-03
[quote=ashrack]
What is your number of packages? [/quote]

Sorry, assumed that number meant packages, but it's actually 'files and directories'.

I'm at around 75000, so I guess it isn't that much at all when it relects files and directories.

[quote=ashrack]
I removed about 15000 packages with a help of DEBFOSTER. So now I believe I have only the most needed packages. So reading database is tollerable now.


Its my believe that READING DATABASE is mostly HDD related so a faster one would achieve this quicker. Unfortunerly I have one of those notebooks that still have the 4300RPM HDDs.


On my desktop computer which  has a 7200RPM HDD 'Reading Database' is below 10sec and probably has even more packages...
[/QUOTE]

I'm glad it's quicker now that you've cleaned out some uneeded things.
Looks like the harddrive does have quite a bit of influence on it as well.

I did a rough estimate, and it takes about 15 seconds for me (on a notebook HD which I think is about 4300-4500 RPM).

---

### Post by t.alex on 2009-03-12
sorry to bring up such an old topic...

the waiting doesn't bother me that much, i would just like to know if one could somehow reset/delete the stored informations

on a fresh install it doesn't take longer as a couple of seconds to read the database. After ~2 months of (normal) install/uninstall the difference becomes quite noticeable.

---


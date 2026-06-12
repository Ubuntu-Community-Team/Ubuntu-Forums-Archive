---
title: "Lubuntu upgrade query"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by Philip_Edwards on 2015-02-18
HI group. I had Lubunto installed on an Acer Aspire One netbook some years ago. Then, I loaned it to my daughter. It came back today and surprise, surprise, it still works, even though it hasn't been switched on for about three years. As soon as it was turned on it started updating itself....but gave an error message saying that it could only complete a partial upgrade. It has now completed two upgrade cycles, but maybe I should just get the newest district and install it from a USB drive?

yours,

phil

---

### Post by haplorrhine on 2015-02-18
I would try an *in vivo* upgrade first since a live-install failure will just leave a bigger mess.

Whether there are pros/cons, I have no clue.

---

### Post by Bashing-om on 2015-02-18
Philip_Edwards; Hi ! Welcome to the forum.

Yeah, 'buntu is very robust -> release upgrade; maybe YES, maybe not so yes,
Factors:
a) Was the starting release 13.10 ?
b) no to 13.10, did you alter the sources.list to "old.releases" ?
c) What method did you employ to effect the release upgrade ? command line, GUI update manager ?

The bottom line is to look and see where you stand presently:
activate a terminal, and post back - Between code tags - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The current LTS releases are 12.04 & 14.04, the most recent release is 14.10 and upcoming in April is 15.04. There are those times when it is advisibe to do a clean fresh install - this may NOT be one of those times.

[INDENT][INDENT]let's see what tale gets told
[INDENT][INDENT][INDENT]before we go there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Philip_Edwards on 2015-02-18
As soon as I turned it on, a message appeared on the screen saying that an upgrade was available. Pretty sure it said 14. Something. Anyway, it did the upgrade and everything is working. What do I do to find which version of the distro I have?


you know, turning this old computer on was a bit like finding an old friend..

thanks,
phil

---

### Post by deadflowr on 2015-02-18
To see the current version try:
```
lsb_release -a
```

---

### Post by Philip_Edwards on 2015-02-18
```
Tried that. It says Ubuntu 12.04.2 LTS code name precise

```

---

### Post by Bashing-om on 2015-02-18
Philip_Edwards' Hello;

> **Philip_Edwards said:**
> ```
Tried that. It says Ubuntu 12.04.2 LTS code name precise

```

12.04 is good but is up to 12.04.5 now.
What returns:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

``` See if we can get ya updated.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2015-02-18
12.04.2 seems about right.
Lubuntu 12.04 only had 18 months support...

---

### Post by Bashing-om on 2015-02-18
> **deadflowr said:**
> 12.04.2 seems about right.
Lubuntu 12.04 only had 18 months support...

Uhhhh !
My error, thought it were 3 years (ubuntu is 5 years). Past time to go for 14.04 . Huh ?

What returns:
```

ubuntu-support-status --show-all

```

[INDENT][INDENT]goes to show what I do not know
[/INDENT][/INDENT]

---

### Post by deadflowr on 2015-02-18
I think some of the other flavors like lubuntu's and xubuntu's support cycle's are confusing when compared to that of normal Ubuntu.
In that they are supported for briefer periods than normal Ubuntu, but also contain the Ubuntu base, which indeed does get a full 5 years support for lts releases.

I'm not sure if it is meant to be set to 12.04.2, but it certainly correlates with it's support cycle.

12.04.2's point release would have been a year into the release, and I don't think moving Lubuntu 12.04 onto the 12.04.3 and up point releases would have been of any use, since it (12.04.3) would have only been supported for a couple of months at that point...

Having stated all that garblish stuff, I'm not sure which way would be best to move forward.
First off, I'm not sure how well a release-upgrade works for Lubuntu >> going from 12.04 to something supported like 14.04.
So i hesitate to recommend such a method.
Might be best to a quick personal file backup and download and install a fresh copy of 14.04, or even newer.
I think a clean install will save a lot of headaches down the road.

---

### Post by Rex Bouwense on 2015-02-19
Since there never has been a Lubuntu LTS release until 14.04 and the Lubuntu 13.04 and 13.10 have both reached End Of Life I would back up and do a new install of 14.04 if you want a LTS release or 14.10 if you want the newest release.  For your information though there will be another release in a couple of months so you do have several options.

---

### Post by Bucky Ball on 2015-02-19
I'd go for Lubuntu 14.04 LTS. Three years support (until April 2017). Good luck. ;)

---

### Post by Philip_Edwards on 2015-02-19
Thanks everybody.

Managed to get Lubuntu 14.04 onto USB this morning. Installation was flawless.
Treated the netbook to  a new mouse and SD card.
I now have a rather nice netbook.

Thanks again.

Phil

---

### Post by Bucky Ball on 2015-02-19
Excellent news. ;)

Please mark the thread as solved to help future travelers. (See the second link in my signature for how.) Good luck.

---


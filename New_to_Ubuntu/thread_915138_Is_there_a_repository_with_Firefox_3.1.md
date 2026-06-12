---
title: "Is there a repository with Firefox 3.1?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by kiev on 2008-09-09
Probably where that exists repository with Firefox 3.1 ?

---

### Post by anders_c_ on 2008-09-09
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main

edit: i think its only for intrepid though...

---

### Post by SunnyRabbiera on 2008-09-09
If you refer to version 3.0.1 it should be available when you next update apt.

---

### Post by Titan8990 on 2008-09-09
He is probably referring to 3.1 which is still in Alpha stage of testing. For something so early in testing stages I highly recommend getting it directly from Mozilla.

---

### Post by skymera on 2008-09-09
Alpha builds won't be in the repos.

Giving software out in the repos means it would automatically upgrade everyone to the latest.

Go to Mozilla's site and have a looksies around.

---

### Post by hyperair on 2008-10-21
I think it's mentioned in the second post that there is a PPA with firefox 3.1 around.

---

### Post by jdpipe on 2008-11-10
I checked that PPA and it only contains Firefox 3.0.4, not Firefox 3.1. Anywhere else to try?

---

### Post by hyperair on 2008-11-10
Look again. The package is called firefox-3.1

---

### Post by jdpipe on 2008-11-10
Strange, I tried it on my laptop yesterday and it didn't show up. Today on my desktop, it does appear, and it installs, and runs very well. Thanks!

---

### Post by tpischke on 2008-12-09
As of right now, no firefox-3.1 package in that repo

---

### Post by stevoo on 2008-12-09
offcourse there is :
> Package: firefox-3.1-gnome-support
Source: firefox-3.1
Priority: optional
Section: gnome
Installed-Size: 176
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.1~b2+build1+nobinonly-0ubuntu1~fta1~intrepid
Provides: gnome-www-browser
Depends: libasound2 (>> 1.0.17), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.12.0), libgnomevfs2-0 (>= 1:2.17.90), libnspr4-0d (>= 1.8.0.10), libstdc++6 (>= 4.1.1), firefox-3.1 (= 3.1~b2+build1+nobinonly-0ubuntu1~fta1~intrepid), xulrunner-1.9.1-gnome-support
Filename: pool/main/f/firefox-3.1/firefox-3.1-gnome-support_3.1~b2+build1+nobinonly-0ubuntu1~fta1~intrepid_i386.deb
Size: 85204
MD5sum: d60351e48a55f7145ce8d72026708672
Description: Support for Gnome in Mozilla Firefox
 This is an extension to Firefox that allows it to use protocol
 handlers from Gnome-VFS, such as smb or sftp, and other Gnome
 integration features.



---

### Post by philinux on 2008-12-09
You can download it direct from mozilla. Just unpack it in a directory in /home and make a launcher on the desktop to it.

Dont forget it's still beta.

[edit]
Two precautions.
[http://tombuntu.com/index.php/2008/10/20/test-drive-firefox-31-beta-1/](http://tombuntu.com/index.php/2008/10/20/test-drive-firefox-31-beta-1/)
[http://vivapinkfloyd.blogspot.com/2008/10/test-firefox-31-beta-1-in-debian.html](http://vivapinkfloyd.blogspot.com/2008/10/test-firefox-31-beta-1-in-debian.html)

---

### Post by altonbr on 2009-02-09
I'm using this PPA just fine: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main

---

### Post by kansasnoob on 2009-02-09
I've tried it and it's terribly unstable!

3.06 is much, much better!

---

### Post by altonbr on 2009-02-10
> **kansasnoob said:**
> I've tried it and it's terribly unstable!

3.06 is much, much better!

Personally, I like it a lot but don't use it for my day-to-day browsing. Remember, it's only the third beta. It's not a release candidate yet!

What's so unstable about it though? I'm sure the Firefox developers would like to know.

---

### Post by hyperair on 2009-02-10
> **altonbr said:**
> I'm using this PPA just fine: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
Thanks for this. It's awesome. Just what I've been looking for.

> **kansasnoob said:**
> I've tried it and it's terribly unstable!

3.06 is much, much better!
Really? I'm using 3.2 happily and am yet to notice any crashes.

---

### Post by jdpipe on 2009-02-10
I've been using 3.1 for a few months now. It was a bit unstable at the start but the latest packages have been very reliable.

---

### Post by theApokalypsis on 2009-02-25
> **hyperair said:**
> Thanks for this. It's awesome. Just what I've been looking for.


Really? I'm using 3.2 happily and am yet to notice any crashes.

3.2 eh. damn im falling behind on my FF updates. you know any feeds about that? or any PPA's with 3.2? lol


anyways. that PPA link was aswesome as well



EDIT: ADUHHH... its in THAT PPA. my bad

---

### Post by zika on 2009-02-25
try Minefield (3.2)(nightly)! better than Shiretoko (3.1)(nightly) for a mile!
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)
recommended!

---

### Post by hyperair on 2009-02-25
I'd actually prefer using the PPA. It updates daily, just a little slower than Mozilla, but you get automated upgrades via apt.

---

### Post by zika on 2009-02-25
> **hyperair said:**
> I'd actually prefer using the PPA. It updates daily, just a little slower than Mozilla, but you get automated upgrades via apt.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
I prefer to keep installed "regular" FF in place and just use Minefield from a directory in ~. that way they share history, settings etc and I have a backup ... ;)  if I get angry with Minefield just rm will do ... ;) [SIZE=2][COLOR=Black]De gustibus non est disputandum.[/COLOR][/SIZE]

---

### Post by hyperair on 2009-02-25
Ah yes, that's true. the ones from PPA create a new directory in ~/.mozilla.

---

### Post by SuperSonic4 on 2009-02-25
Looks nice enough but my bank insists I use a stable browser to check my account and konqueror doesn't count >_>

I just have minefield in my home directory

---

### Post by hyperair on 2009-02-25
> **SuperSonic4 said:**
> Looks nice enough but my bank insists I use a stable browser to check my account and konqueror doesn't count >_>

I just have minefield in my home directory
Heheh I don't think that Minefield really counts as a stable browser does it? =P

---

### Post by zika on 2009-02-25
> **hyperair said:**
> Heheh I don't think that Minefield really counts as a stable browser does it? =P
does IE counts as a stable browser ... ?[-X

---

### Post by hyperair on 2009-02-25
Of course it does! It sucks and crashes **consistently**!

---

### Post by zika on 2009-02-25
> **hyperair said:**
> Of course it does! It sucks and crashes **consistently**!
sorry, You are right. very stable ...

---

### Post by t3k on 2009-02-25
update manager in Gutsy lists that there are update for firefox 3.0 but will not let me check the boxes. What am I doing wrong?

---

### Post by altonbr on 2009-02-25
> **t3k said:**
> update manager in Gutsy lists that there are update for firefox 3.0 but will not let me check the boxes. What am I doing wrong?

In a terminal (Application > Accessories > Terminal), what does this command produce?
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by t3k on 2009-02-26
I ran it and it upgraded flashplugin-nonfree. I ran it again and it mentioned "The following packages have been kept back: firefox-3.0 firefox-3.0-gnome-support"

---

### Post by sharon.gmc on 2009-02-26
I am sure, yes, there is.  Firefox 3.1 has a repository.

---


---
title: "Latest browser from Mozilla..."
date: 2018-05-12
forum: New to Ubuntu
---

### Post by Innernet on 2018-05-12
Hi.
Browsing around, found that the new Firefox is Quantum version 57.  Downloaded/executed and seemed not to install.  Closed Firefox and then seemed to install, but nothing prompted at all.  Reopened Firefox, checking the "About Firefox" showed version 60, in 32 bit.
Closed browsing session.
Reopened browser, it is not version 60 any more.  Went back to 56.0

What is going on; and how to trade for 64 bit?  There is a chance my 64 bit laptop is wrongly running 32 bit Ubuntu.

Guidance to identify/clarify/straighten my clumsiness will be appreciated.

---

### Post by deadflowr on 2018-05-13
What does
```
uname -m
```
show?
(x86_64 is 64-bit
i686, i586, or i386 is 32-bit)

---

### Post by Impavidus on 2018-05-13
On any supported release of Ubuntu (14.04, 16.04, 17.10, 18.04) and any of its other flavours you should automatically get Firefox 60, unless you removed it yourself. If you haven't updated in the past few days, you may still have Firefox 59. There should be no reason (some exceptions notwithstanding) to download and install Firefox directly from Mozilla. 32 bit or 64 bit should match the rest of the OS, as told by uname -m.

Which release of Ubuntu are you running?

---

### Post by PaulW2U on 2018-05-13
@Innernet, further to what Impavidus has said please don't rush to download the latest release of either Firefox, Thunderbird or Chromium directly from sources other than the Ubuntu repositories.

The latest Firefox package that has been made available for Ubuntu 18.04 is **firefox_60.0+build2-0ubuntu1_amd64.deb**. The package name implies that it has been **patched** to better work with Ubuntu than a direct download from the Mozilla site would do.

I haven't checked but different downloads may well install to different locations, create their own desktop shortcuts and allow multiple versions of the browser to be simultaneously installed.

The [Ubuntu Security Team]("https://wiki.ubuntu.com/SecurityTeam") decide which updates will be made available to us and when. If there is a delay in the latest version being made available for download then I am sure they will have a very good reason for delaying the update.

---

### Post by Innernet on 2018-05-13
Hi deadflowr.
uname -m  shows i686 ---> 32bit.
Does 'uname -m' shows the Ubuntu installed flavor or the hardware in the laptop ?
Something is not matching...

Impavidus : Am running 14.04 in this laptop triggering the thread.

---

### Post by oldos2er on 2018-05-13
uname shows the kernel version, in your case it's 32-bit, which won't be able to run 64-bit software. You would need to install a 64-bit version of Ubuntu to do that.

---

### Post by deadflowr on 2018-05-13
> Does 'uname -m' shows the Ubuntu installed flavor or the hardware in the laptop ?
Only what's installed.
Has nothing to do with hardware, really.

Is this 14.04 from 4 years, or more recently installed?
Might be from back when the default offering from Ubuntu.com was 32-bit.
(I cannot remember when it changed to 64-bit as the default offering)
Which would make sense, though, as you had to actually consciously select 64-bit.

---

### Post by Innernet on 2018-05-13
Thanks, deadflowr.  14.04 was installed 4 years ago...

I suppose that upgrading to 18.04 would autoselect 32bit again to match the current existing flavor.  Any chance to replace the existing 14.04-32bit with 14.04-64bit without losing all settings and preferences and tweaks and data ?

My other machine runs on 18.04

---


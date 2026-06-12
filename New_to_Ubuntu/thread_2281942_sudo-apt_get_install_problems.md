---
title: "sudo-apt get install problems"
date: 2015-06-10
forum: New to Ubuntu
---

### Post by jaraqui2 on 2015-06-10
I had this problem (for several packages)

[http://ubuntuforums.org/showthread.php?t=2078996&p=12330242#post12330242](http://ubuntuforums.org/showthread.php?t=2078996&p=12330242#post12330242)

And I used this solution.

[http://ubuntuforums.org/showthread.php?t=2078996&p=12330277#post12330277](http://ubuntuforums.org/showthread.php?t=2078996&p=12330277#post12330277)

After this procedure, when I try to run any sudo-apt install, this error message appears:


********************************************
Package xxx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'xxx' has no installation candidate
********************************************

I attached my /etc/apt/sources.list file, if it is necessary to better understand my problem.

Any help would be appreciated

---

### Post by v3.xx on 2015-06-10
13.10 _Saucy Salamander

Reached end of life about a year ago.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
And no longer receiving updates or support.

---

### Post by cariboo on 2015-06-10
> **v3.xx said:**
> 13.10 _Saucy Salamander

Reached end of life about a year ago.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
And no longer receiving updates or support.

+1, it's time to upgrade to 14.04.

---

### Post by jaraqui2 on 2015-06-11
Thanks for the answer.

The machine that runs salcy works basically in text mode.
For this environment are there any upgrade commands that do the job (13.10 to 14.04.2 LTS) with two or three lines?

If 'yes', what are they?

---

### Post by cariboo on 2015-06-11
It's pretty simple, just run the following commands:

```
sudo apt-get install update-manager-core
```

and

```
sudo do-release-upgrade
```

---

### Post by QIII on 2015-06-11
... and I'd also recommend uninstalling any proprietary drivers and disabling any PPAs you may have first ...

:)

---


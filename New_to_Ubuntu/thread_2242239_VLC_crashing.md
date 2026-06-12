---
title: "VLC crashing"
date: 2014-08-31
forum: New to Ubuntu
---

### Post by micahpage on 2014-08-31
I have VLC crashing randomly at different points, different files, at different times. VLC closes and a popup saying internal error with the option to send an error report shows up. If i re-play the same segment when it crashed, it doesnt crash. It is probably once a day or so. I send this every time. 

The report contains:
```
ProblemType: Crash
Title: vlc crashed with SIGSEGV in start_thread()
Package: vlc-nox 2.1.2-2build2
DuplicateOf: https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1288206

```
There was more to the report, but there is no way to capture the text from the popup

Is this just a bug in 14.04/VLC or is there something i am missing, a package?

---

### Post by uRock on 2014-08-31
According to the Launchpad link, it a fix was released in May. Is your system up to date?

I haven't had this issue with VLC.

---

### Post by micahpage on 2014-08-31
Yes it is up to date.

EDIT:
VLC keeps crashing every 5 minutes or so with a mkv file. At different points of the file too.

---

### Post by mc4man on 2014-08-31
> **micahpage said:**
> Yes it is up to date.


Let's see.
```
apt-cache policy vlc libavcodec*
```

---

### Post by micahpage on 2014-08-31
```
metulburr@ubuntu ~ $ apt-cache policy vlc libavcodec*vlc:
  Installed: 2.1.2-2build2
  Candidate: 2.1.2-2build2
  Version table:
 *** 2.1.2-2build2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
libavcodec-dev:
  Installed: (none)
  Candidate: 6:9.11-2ubuntu2
  Version table:
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libavcodec-extra-52:
  Installed: (none)
  Candidate: (none)
  Version table:
libavcodec-extra-53:
  Installed: 6:0.8.6ubuntu2
  Candidate: 6:0.8.6ubuntu2
  Version table:
 *** 6:0.8.6ubuntu2 0
        100 /var/lib/dpkg/status
libavcodec-extra-54:
  Installed: (none)
  Candidate: 6:9.11-2ubuntu2
  Version table:
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
libavcodec53:
  Installed: (none)
  Candidate: (none)
  Version table:
     6:0.8.6-1ubuntu2 0
        100 /var/lib/dpkg/status
libavcodec54:
  Installed: 6:9.11-2ubuntu2
  Candidate: 6:9.11-2ubuntu2
  Version table:
 *** 6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
libavcodec-extra:
  Installed: (none)
  Candidate: 6:9.11-2ubuntu2
  Version table:
     6:9.11-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
metulburr@ubuntu ~ $ 



```

---

### Post by mc4man on 2014-08-31
Neither vlc or libav is updated past 14.04 release
Current libav -  libav (6:9.16-0ubuntu0.14.04.1)
Current vlc - vlc (2.1.4-0ubuntu14.04.1)

Open up Software & Updates from Dash or terminal - 
```
software-properties-gtk
```
Under the updates tab make sure the first 2 are enabled as in screenshot
Then reload your sources and update all.

---

### Post by micahpage on 2014-09-01
Thank you. Those were not checked....im not sure why. I tested it for a couple hours after that, and it appears to be working OK now. Thanks again.

---


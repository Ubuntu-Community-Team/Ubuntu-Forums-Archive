---
title: "libass with harfbuzz support"
date: 2013-12-01
forum: Packaging and Compiling Programs
---

### Post by ProgramErgoSum on 2013-12-01
Hi,
Ubuntu-13.10, 64-bit.

I require [libass]("http://code.google.com/p/libass/") with [harfbuzz]("http://www.freedesktop.org/wiki/Software/HarfBuzz/") support. I had initially installed FFmpeg from Software Centre. I have now uninstalled it (with apt-get purge). I am now looking at the following dpkg output.

```

user@dabba:~$ sudo dpkg -l *libass*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                     Version                   Architecture              Description
+++-========================================-=========================-=========================-======================================================================================
ii  libass4:amd64                            0.10.1-1ubuntu1           amd64                     library for SSA/ASS subtitles rendering
ii  libassuan0:amd64                         2.1.0-1                   amd64                     IPC library for the GnuPG components

```

```

user@dabba:~$ sudo dpkg -l *libharfbuzz*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                     Version                   Architecture              Description
+++-========================================-=========================-=========================-======================================================================================
ii  libharfbuzz-icu0:amd64                   0.9.19-1                  amd64                     OpenType text shaping engine ICU backend
un  libharfbuzz0                             <none>                                              (no description available)
ii  libharfbuzz0a:amd64                      0.9.19-1                  amd64                     OpenType text shaping engine (shared library)

```

I want to know, if this (the dpkg output) is how a 'clean' 13.10 installation looks like ? Also, how do I find out if libass indeed has harfbuzz support ?

---


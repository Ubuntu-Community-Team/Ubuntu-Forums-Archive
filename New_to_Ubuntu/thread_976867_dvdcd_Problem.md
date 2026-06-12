---
title: "dvd/cd Problem"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-11-09
Since installing 8.10 I haven't been able to play dvds or use acidrip or the like.
I have installed ubuntu-restricted-extras and I believe all the libs are there but still nothing.
I think it may be related to the fact that my device files are /dev/dvd1 and not /dev/dvd as it normally is.

The VLC Error is 
```
user@user-laptop:~$ vlc /dev/dvd1
VLC media player 0.9.5 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.5 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure 
[00000001] main libvlc debug: translation test: code is "C"
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: SIMPSONS_SEASON4_DISC4
libdvdnav: DVD Serial Number: 307E7A0C
libdvdnav: DVD Title (Alternative): SIMPSONS_SEASON4_DISC4
libdvdnav: Unable to find map file '/home/user/.dvdnav/SIMPSONS_SEASON4_DISC4.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!

```
any help is appreciated.

---


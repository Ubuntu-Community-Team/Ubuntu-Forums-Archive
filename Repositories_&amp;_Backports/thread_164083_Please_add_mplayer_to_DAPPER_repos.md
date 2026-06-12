---
title: "Please add mplayer to DAPPER repos"
date: 2006-04-22
forum: Repositories &amp; Backports
---

### Post by ashrack on 2006-04-22
I just looked looked at available packages thru SYNAPTIC and only KMPLAYER is found but not MPLAYER. 
WHY??

ps. my sources.list:
```
# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted


#deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
 deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by htinn on 2006-04-22
It's in the "multiverse" repo.

---

### Post by ashrack on 2006-04-22
so I must enable this 2:
 > deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

---

### Post by Buffalo Soldier on 2006-04-22
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper multiverse
```

---

### Post by encKe on 2006-04-23
Thx for the response on this issue. Working great now!

---

### Post by ashrack on 2006-04-24
Am curious how come MULTIVERSE isn't by default in SOURCES.LST when U install DAPPER BETA

---

### Post by SgtDude on 2006-04-27
Multiverse isn't in the default sources.lst because of various software patent issues with the software in the Multiverse repository.

Take Mplayer for example.  Mplayer is capable of playing just about any type of media file you can throw at it.  A lot of these media files are encoded using patented compression techniques and the software to decode them may be illigal in your country if you don't have some arrangement with the patent holder (i.e. money has changed hands).

Ubuntu tries to make as much software available to you while still protecting you from inadvertantly breaking your country's laws.  So you have to manually enable the Multiverse repository, therefore taking responsibility for the legality of the software you're downloading.

More info at [http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by ashrack on 2006-05-02
SGTDUDE
I understand all that. But why isnt in SOURCES.LST at least a commented line for the MULTIVERSE??? And then we could just uncomment it instead of looking for an address to it on the net??

---

### Post by wpshooter on 2006-05-08
[QUOTE=ashrack]SGTDUDE
I understand all that. But why isnt in SOURCES.LST at least a commented line for the MULTIVERSE??? And then we could just uncomment it instead of looking for an address to it on the net??[/QUOTE]

Very good question.

---

### Post by 3rdalbum on 2006-05-11
I'm not sure, but having a seperate line for the multiverse repos at the same address might cause problems with Apt.

---

### Post by sharperguy on 2006-05-16
the thing is, there are lots of distro's that come with support but non-free software.

so why not ubuntu?

most people wont go near something that dosn't do what they want, and a lot of what people want revolves around mp3's, mpg's and other media that their hardware will play.

---

### Post by mirshafie on 2006-06-02
I'm also mad that there isn't even a commented line in the sources.list. And it's not like google were to much help, all search results give useless junk about hoary.

There's no way putting a commented multiverse line in the sources.list by default could do any damage. :)

---

### Post by tom56 on 2006-06-02
[QUOTE=3rdalbum]I'm not sure, but having a seperate line for the multiverse repos at the same address might cause problems with Apt.[/QUOTE]

Nope, there's a separate line for universe and that works fine.

[QUOTE=mirshafie]There's no way putting a commented multiverse line in the sources.list by default could do any damage. [/QUOTE]

Especially considering that I'm pretty sure Breezy had one.

---


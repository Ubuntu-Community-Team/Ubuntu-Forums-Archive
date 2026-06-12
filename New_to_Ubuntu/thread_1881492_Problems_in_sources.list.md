---
title: "Problems in sources.list"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by fattyz on 2011-11-15
I started copying and pasting into terminal and now I got this

E: Type 'sudo' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

somehow I got internet working, please help update manager won't work

thanks

fattyz

---

### Post by Sigma1 on 2011-11-15
Hm, when you do any commands that mess with the system files, you have to put "sudo" first, which effectively makes you an administrator, for as long as the command takes to execute. It looks like you were trying to modify /etc/apt/sources.list, the list of software sources, directly from the command-line, in order to install some new software, perhaps, and stuck sudo in the wrong place!
That's what the error messages were about, no harm done, though.
"Update manager won't work" is a bit vague. What errors is it giving you? What system are you using, 11.10?

---

### Post by arochester on 2011-11-15
You have a mistake in your sources list.

In the Terminal issue the command: gksudo gedit /etc/apt/sources.list

Either tell us what line 55 says, or copy and paste the whole thing here so we can take a look.

---

### Post by fattyz on 2011-11-15
#deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiversesudo gedit /etc/apt/sources.list
sudo aptitude update && sudo aptitude full-upgrade

sudo aptitude install vlc mplayer



sudo aptitude install non-free-codecs libxine1-ffmpeg gxine mencoder mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0 totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 libjpeg-progs libmpcdec3 libquicktime1 flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux liba52-dev
sudo aptitude install simple-ccsm

Now navigate to System &#8594; Preferences &#8594; Simple CompizConfig Settings Manager .

thanks for the quick replies

fattyz

---

### Post by searchfgold6789 on 2011-11-15
REMOVE all of these lines and save:
```
sudo aptitude update && sudo aptitude full-upgrade

sudo aptitude install vlc mplayer



sudo aptitude install non-free-codecs libxine1-ffmpeg gxine mencoder  mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0  totem-mozilla icedax tagtool easytag id3tool lame  nautilus-script-audio-convert libmad0 libjpeg-progs libmpcdec3  libquicktime1 flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac  libmpeg3-1 mpeg3-utils mpegdemux liba52-dev
sudo aptitude install simple-ccsm

Now navigate to System &#8594; Preferences &#8594; Simple CompizConfig Settings Manager
``` Also modify the line before that instead of ```
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiversesudo gedit /etc/apt/sources.list
``` it says:```
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
```

---

### Post by JayKay3OOO on 2011-11-15
and then stick

sudo aptitude install non-free-codecs libxine1-ffmpeg gxine mencoder mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0 totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 libjpeg-progs libmpcdec3 libquicktime1 flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux liba52-dev
sudo aptitude install simple-ccsm

into the terminal if you want to install them all in one go.

---

### Post by mörgæs on 2011-11-15
Changed the title to a more descriptive one.

---

### Post by fattyz on 2011-11-18
Hi sorry I am less able than that.  All I can do is cut and paste.  I can't do your great answers.  So I tried to cut the last one and paste a new one but I can't.

Thanks '
Fattyz

---

### Post by Rex Bouwense on 2011-11-18
OK so what did you do (exactly) and what happened (exactly).  Did you copy and paste into the LXTerminal exactly what was written?  What happened?

---

### Post by 3rdalbum on 2011-11-18
> **fattyz said:**
> Hi sorry I am less able than that.  All I can do is cut and paste.  I can't do your great answers.  So I tried to cut the last one and paste a new one but I can't.

Thanks '
Fattyz

Remove all this stuff from your /etc/apt/sources.list file:

> sudo gedit /etc/apt/sources.list
sudo aptitude update && sudo aptitude full-upgrade

sudo aptitude install vlc mplayer



sudo aptitude install non-free-codecs libxine1-ffmpeg gxine mencoder mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0 totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 libjpeg-progs libmpcdec3 libquicktime1 flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux liba52-dev
sudo aptitude install simple-ccsm

Now navigate to System &#8594; Preferences &#8594; Simple CompizConfig Settings Manager .

The above stuff doesn't belong in this file, especially not the plain English text about navigating to CompizConfig.

Also, in the previous line, you've wrongly added "sudo gedit /etc/apt/sources.list" to the end of the line. Remove that part as well. ONLY that part that starts with 'sudo'; the previous part of that line is fine.

Save your changes, now go into the terminal and run the following command:

```
sudo apt-get update
```

This should fix everything up.

I don't know about Lubuntu, but in Ubuntu there's a program called "Software Properties" or "Software Sources". In future, if you want to add a repository to your system, use the Software Properties/Sources program as it stops these sorts of mistakes from happening.

---

### Post by fattyz on 2011-11-23
Happy Thanks!  That I can do.  I will update in a couple hours.  I started with 9.1 a couple years ago and got a really old dell laptop that would not run XP really humming along on it and I'm hooked ever since.  I'm just really simple at it!

FattyZ

---

### Post by fattyz on 2011-11-23
OK! I am back in business.  Thx guys really, I hated not having my installation right.  Now I can finish updating it and get everything working.

FattyZ

---

### Post by mörgæs on 2011-11-23
Good, then please mark the thread 'solved'.

---


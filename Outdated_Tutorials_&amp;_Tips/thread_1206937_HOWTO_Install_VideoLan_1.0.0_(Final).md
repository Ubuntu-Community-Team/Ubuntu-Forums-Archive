---
title: "HOWTO: Install VideoLan 1.0.0 (Final)"
date: 2009-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by The-Don on 2009-07-07
> 
[LIST]
[*]Free, Open Source and cross-platform
[*]Independant of systems codecs to support most video types
[*]Live recording
[*]Instant pausing and Frame-by-Frame support
[*]Finer speed controls
[*]New HD codecs (AES3, Dolby Digital Plus, TrueHD, Blu-Ray Linear PCM, Real Video 3.0 and 4.0, ...)
[*]New formats (Raw Dirac, M2TS, ...) and major improvements in many formats...
[*]New Dirac encoder and MP3 fixed-point encoder
[*]Video scaling in fullscreen
[/LIST]
**_[[COLOR=Blue]Ubuntu Installation[/COLOR]]("https://launchpad.net/%7Ec-korn/+archive/vlc")_**
```
# **gksudo gedit /etc/apt/sources.list**
# **deb http://ppa.launchpad.net/c-korn/vlc/ubuntu [COLOR=Red]jaunty[/COLOR] main** [COLOR=Blue]<-- ADD THAT LINE[/COLOR]
# **sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D**
# **sudo aptitude update**
# **sudo aptitude upgrade**
```Replace '[COLOR=Red]**jaunty**[/COLOR]' if running a different version.

---


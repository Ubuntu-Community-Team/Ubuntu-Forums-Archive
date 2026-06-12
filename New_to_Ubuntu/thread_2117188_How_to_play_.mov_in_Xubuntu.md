---
title: "How to play .mov in Xubuntu"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by mathsgirl on 2013-02-17
Hi everybody!

I'm quite new in Linux, so I need some help with this.

I've read every single thread about hot to play .mov in Ubuntu but nothing worked for me.

I've installed SMPlayer and VLC, they play perfectly sound but video didn't worked. When I tried to uninstall SMPlayer i've got an error.

I've also tried to install restricted extras package, but i've got this message:
"

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 176683 files and directories currently installed.)
Preparing to replace ttf-mscorefonts-installer 3.4ubuntu3 (using .../ttf-mscorefonts-installer_3.4ubuntu3_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/ttf-mscorefonts-installer_3.4ubuntu3_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/ttf-mscorefonts-installer_3.4ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

Please, somebody help me! I don't want to switch to windows for watching videos.

Thank you!


Maths girl

---

### Post by ibjsb4 on 2013-02-18
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process

You can have only one package manager open at a time.  Processes will be locked and not available for use.  Maybe you had the software center open and you tried to use apt-get?  Or something like that.

> ttf-mscorefonts

I bet you didn't sign the agreement when installing restricted extras.  Try this in terminal:

```
sudo apt-get install  --reinstall ubuntu-restricted-extras
```

---

### Post by varunendra on 2013-02-18
Welcome to the forums mathsgirl!

I don't have a solution at the moment, so am posting this just for confirmation and tracking purpose.

> **mathsgirl said:**
> debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
for this, +1 to what *ibjsb4* suggested -
> **ibjsb4 said:**
> You can have only one package manager open at a time.  Processes will be locked and not available for use.  Maybe you had the software center open and you tried to use apt-get?  Or something like that.

However, I don't think installing/reinstalling restricted extras is going to make any difference.

I have them installed not too long ago *(and yes, I did sign the EULA while installing them)*, yet still I found the same problem as OP described, with some test mov files.

My test files are some tutorial videos with maybe non-standard specs, but I don't have any standard mov files at the moment to test with. However, those test files **also failed to display video on VLC in a XP VM**. They do have video as totem is able to display it, but it can't play the audio.

So, mathsgirl, can you confirm that the same file are playing fine on windows? Because mine don't.

If they do, can you post their codec details? In VLC you can get that by pressing ctrl+alt+J while the video is playing.

Even more details can be extracted using MediaInfo-GUI (available in repositories and also available for windows).

Shall post back if found any solution, and please you do the same if you find one. Thanks!

---


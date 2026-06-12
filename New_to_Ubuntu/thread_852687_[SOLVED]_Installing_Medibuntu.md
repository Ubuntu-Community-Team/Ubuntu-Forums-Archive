---
title: "[SOLVED] Installing Medibuntu"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by deejaypip on 2008-07-07
Hello--
I tried to install medibuntu by going to Terminal and typing
 
```
 sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

But it gave me this

```
Error parsing proxy URL http://:8080/: Invalid host name.

```

What do I do now? I want to play DVDs on my computer...

---

### Post by sharks on 2008-07-07
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by aktiwers on 2008-07-07
Place them there manually:
```
gksu gedit /etc/apt/sources.list
```

And copy paste this to the end of the text document:
> 
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Then add key and update repos:
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

That should do it.

---

### Post by kansasnoob on 2008-07-07
For some reason the GPG key works better from the Ubuntu link:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Sharks probably had it right anyway, but I learned long ago that the Medibuntu site is not well maintained.

! always look for what I want in official Ubuntu docs before going outside.

---

### Post by deejaypip on 2008-07-09
Thanks ---
I tried the gksu gedit approach, and Totem Movie Player opened my DVDs. (I tried *Amelie* and *Fight Club*.) However, it said "error occured -- could not read from resource."

By the way -- could you explain how gksu gedit works? Thanks...

---

### Post by mc4man on 2008-07-09
did you install libdvdcss2 and ubuntu-restricted-extras?
In the long run you'll find totem-gstreamer not that well suited for dvd playback, vlc or totem-xine are much better. Read here (run the line from 3rd code box, the rest is optional)
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

---

### Post by cariboo on 2008-07-09
gksu is a graphical front end for sudo and su for more info in a terminal type:

```
man gksu
```

There is a man page for almost every application listed in /usr/bin

Jim

---

### Post by deejaypip on 2008-07-09
Thanks...

I tried that but it gave me

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by k3lt01 on 2008-07-09
Take a look at the [Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683") thread.

---

### Post by deejaypip on 2008-07-09
Thanks for this link... I feel kind of dumb now. Is that post stickied somewhere?

But I can play movies now! Even my obscure Soviet films like *The Cranes Are Flying*! YAY!

---

### Post by k3lt01 on 2008-07-10
> **deejaypip said:**
> Thanks for this link... I feel kind of dumb now. Is that post stickied somewhere?Don't go feeling dumb, we're all noobs at one time or another, just remember to share your knowledge when the time comes to help another noob. Yes it is stickied from what I remember, anyway its in the Multimedia section if you need to find it again.

> **deejaypip said:**
> But I can play movies now! Even my obscure Soviet films like *The Cranes Are Flying*! YAY!Oh I'm jealous. I want a copy of Stalin's Ivan the Terrible.

---


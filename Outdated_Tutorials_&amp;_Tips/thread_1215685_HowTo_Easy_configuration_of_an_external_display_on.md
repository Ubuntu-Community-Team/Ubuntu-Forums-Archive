---
title: "HowTo: Easy configuration of an external display on startup"
date: 2009-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by elektronaut on 2009-07-17
Preamble: At the moment, this only works if you have a NVidia card. If you have an Intel card, you might be interested in [**my other HowTo**](http://ubuntuforums.org/showthread.php?t=1189938).

If you are tired of the 'clicking orgy' in nvidia-settings each time you attach the external display to your laptop, here's what to do:

Install [**disper**](http://willem.engen.nl/projects/disper/). First, you need to add [**this repository**](https://launchpad.net/~wvengen/+archive/ppa) by editing your sources list:
```
sudo nano /etc/apt/sources.list
```
Append these lines at the end:
```
deb http://ppa.launchpad.net/wvengen/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu jaunty main 
```
Add the authentication key for the repository:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F6EFB904
```
Update
```
sudo apt-get update
```
and (finally) install:
```
sudo apt-get install disper
```

Now you are able to try it out.
```
disper -l
```
should show you all currently available displays. If I do this on my laptop with the external display attached, I get this:
```
display DFP-0: AUO
 resolutions: ...
display DFP-2: Samsung SyncMaster
 resolutions: ...
```

I was mainly interested in automatically switching to the external display on startup. Looking at the man page for disper, I found
```
-s, --single
      only enable the primary display

-S, --secondary
      only enable the secondary display
```
It's really cool, if you are on the external display and enter
```
disper -s
```
the whole desktop is automagically switched to the laptop display. And vice versa if you enter
```
disper -S
```

Here is the script that is run during boot up (simply add it via the start programs option in the Gnome system administration menu):
```
#!/bin/sh
# disper-conf.sh

if disper -l|grep -q "Samsung SyncMaster"
  then
  disper -S
fi
exit 0
```

Couldn't be simpler. You certainly have to replace the model name with your display's name.

---

### Post by geostrydar on 2009-08-09
Thanks elektronaut!

My connected TV was not being recognized after a reboot. I had to detect displays and change resolutions to get it to work. I was looking at disper as a way to go and stumbled on your howto and the repository list you gave. After installing and testing, for my purposes, disper -e ran at start up fixes the issue. I am anxious to use it with my laptop and try the script you suggest.

Thanks for the howto!

---


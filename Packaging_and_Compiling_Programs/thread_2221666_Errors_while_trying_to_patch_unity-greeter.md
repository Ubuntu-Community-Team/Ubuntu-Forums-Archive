---
title: "Errors while trying to patch unity-greeter"
date: 2014-05-03
forum: Packaging and Compiling Programs
---

### Post by dominic-comtois on 2014-05-03
Not being very keen on purple, I followed instructions on the following post: [http://ubuntuforums.org/showthread.php?t=1958162](http://ubuntuforums.org/showthread.php?t=1958162)

I realize this topic is from 2012 and I'm using 14.04, but still I gave it a shot. The Plymouth part went well. However, following NHclimber's instructions (2nd message in mentionned thread), I got a bunch of HUNK errors and 2 .rej files were generated (one for main-window.vala and one for user-list.vala). Here is the sequence I followed:

```
sudo apt-get install build-essential devscripts
sudo apt-get build-dep unity-greeter
apt-get source unity-greeter
cd unity-greeter-14.04.9
wget -q https://launchpadlibrarian.net/100026654/lightdm%20backgroundcolor2.patch
patch -p0 < "lightdm backgroundcolor2.patch"



```

I stopped there, not doing the debuild and dpkg steps. My question is: should I reinstall lightdm or do anything about it, or should I just leave it as is?

Also, if you have indications as to how to get rid of purple for good, I'm all ears!

---


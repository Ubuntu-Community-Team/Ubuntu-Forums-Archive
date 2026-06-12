---
title: "ubuntu minimal install no sound"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-11-02
using this tutorial [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
I installed ubuntu on an old p2 thinkpad. its model is a 600E. And I have no sound. And I cant find any kind of volume control sound drivers thing either. Its using the IceWM window manager

---

### Post by jimrz on 2008-11-02
check out thinkwiki.org ... seem to remember seeing some posts there about getting sound going on the older 600 series TP's, but my 600x did not have that issue so did not really pay much attention

---

### Post by SpenceMakesSense on 2008-11-03
hmm should help but wouldnt know the first place to look. Thanks though!

---

### Post by urukrama on 2008-11-03
The volume might just be muted. Open a terminal and type *alsamixer*. You can unmute the channels that are muted by selecting them with the arrow keys and pressing M.

---

### Post by SpenceMakesSense on 2008-11-03
> **urukrama said:**
> The volume might just be muted. Open a terminal and type *alsamixer*. You can unmute the channels that are muted by selecting them with the arrow keys and pressing M.
```
sspence@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```
I tried running sudo apt-get install alsamixer but it cant be found. Maybe I have found my problem?

---

### Post by jimrz on 2008-11-03
> **SpenceMakesSense said:**
> hmm should help but wouldnt know the first place to look. Thanks though!

just search on thinkwiki.org (or these formums or google) for 600e + linux + sound and you should find how others solved the problem

---

### Post by mshipman on 2008-11-03
Make sure that you have alsa installed in the first place.
```
sudo apt-get install alsa
```
Then you should be able to run alsamixer and unmute PCM.

---

### Post by SpenceMakesSense on 2008-11-04
```
spence@ubuntu:~$ sudo apt-get install alsa
[sudo] password for spence: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Maybe Alsa Mixer goes by something else in ibex?

---

### Post by SpenceMakesSense on 2008-11-06
bump

---

### Post by gladstone on 2008-11-13
I'm in the same position with a minimal install at the moment. I have installed:
```
sudo apt-get install alsa-base alsa-utils linux-sound-base
```
but running *alsamixer* gives me:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

---

### Post by gladstone on 2008-11-13
Solved it by adding my username to the *audio* group:
```
sudo usermod -a -G audio [user]
```
:)

Reference:
[Add user to group]("http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/")
[Remove user from group]("http://www.cyberciti.biz/faq/howto-linux-remove-user-from-group/")

---


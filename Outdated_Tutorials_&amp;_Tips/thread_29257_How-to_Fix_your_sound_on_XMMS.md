---
title: "How-to: Fix your sound on XMMS"
date: 2005-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by keyshawn on 2005-04-23
After upgrading from warty to hoary, my audio could no longer play on xmms, frustrating me, and I found as well, a few others in the IRC room who had problems as well.

1. using apt-get or synaptic, make sure you have gstreamer0.8-plugins installed.

2. Start up xmms and Going to its preferences [right-click on the gui, > options] , let the output plugin be "esound  output plugin"

3. on the desktop, go to "system" [on top of your screen]  
   - then Preferences > "multimedia systems selector"
 
Change both the output and input to " ESD - enlightenment sound daemon"

Enjoy...

NOTE: This solution WILL NOT apply to everyone who has a problem with XMMS not playing sound, rather it's just a possible solution for some people, depending on their sound cards, kernel, and previous configurations. 

[note2: How about appending this to this wiki page - [http://www.ubuntulinux.org/wiki/SoundProblemsHoary](http://www.ubuntulinux.org/wiki/SoundProblemsHoary)

---

### Post by nad on 2005-04-23
This is probably because the init scripts are borking alsa. Alsa is starting but the hotplug subsystem is interfering with alsactl and resetting the alsamixer channels to all muted and 0%.

The devs have their hands full with the hal subsystem. Calling alsa later in the init scripts would fix this problem, but I imagine that causes other problems.

Dan M

---


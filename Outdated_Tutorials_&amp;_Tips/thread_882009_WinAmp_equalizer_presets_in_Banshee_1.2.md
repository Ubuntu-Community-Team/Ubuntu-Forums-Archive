---
title: "WinAmp equalizer presets in Banshee 1.2"
date: 2008-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2008-08-06
The Winamp equalizers presets are the best equalizer settings I have found. The following guide will get the default WinAmp presets working under Banshee 1.2.

1. Download the equalizer presets
```
wget http://www.mikesplanet.net/files/equalizers.xml.gz
```

2. Install equalizer presets in Banshee 1.2 (Please note, this will write over existing presets)
```
gunzip -c equalizers.xml.gz > ~/.config/banshee-1/equalizers.xml
```

3. Start Banshee, Goto **View -> Equalizer** and choose what preset you want to use.

---

### Post by MatthewPlanchard on 2008-08-11
Thanks very much for this post.  I'd been playing with the equalizers a while, with varied results, but these presets are excellent!
:guitar:

---

### Post by Minipalmer on 2008-08-20
Hey there,

I just downloaded Banshee and I don't see an equalizer at all, much less a way to access Winamp settings. Am I missing something here?

I know the equalizer was implemented in a newer version, so how can I update my current  version if that's what the problem is?

---

### Post by tgalati4 on 2008-08-21
You probably need to add the following line to the bottom of your /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) gutsy main 

From a terminal:

sudo apt-get update
sudo apt-get install banshee-1

The new player is called "Banshee Media Player".  The old player is called "Banshee Music Player".  The old player should continue to work.

Much more info at:

[http://banshee-project.org/](http://banshee-project.org/)

---

### Post by KongKNoob on 2008-09-22
I've tried this a few times now, Banshee overwrites the changed file back to the pristine original at startup. Tried as superuser as well. Any thoughts? :confused:

---

### Post by MooseDog on 2008-10-28
worked like a charm!! thank you.

---

### Post by xrecar on 2008-11-06
Thankyou soooo much

---

### Post by mirko_3 on 2009-11-07
Thanks a lot, this is great!

---

### Post by wersdaluv on 2009-11-09
> **Technoviking said:**
> The Winamp equalizers presets are the best equalizer settings I have found. The following guide will get the default WinAmp presets working under Banshee 1.2.

1. Download the equalizer presets
```
wget http://www.mikesplanet.net/files/equalizers.xml.gz
```

2. Install equalizer presets in Banshee 1.2 (Please note, this will write over existing presets)
```
gunzip -c equalizers.xml.gz > ~/.config/banshee-1/equalizers.xml
```

3. Start Banshee, Goto **View -> Equalizer** and choose what preset you want to use.
How about 1.6 beta 2? hehe

---

### Post by spongypants23 on 2009-12-09
> **KongKNoob said:**
> I've tried this a few times now, Banshee overwrites the changed file back to the pristine original at startup. Tried as superuser as well. Any thoughts? :confused:

The same happens for me. Any help?

---

### Post by fossn8 on 2009-12-28
> **KongKNoob said:**
> I've tried this a few times now, Banshee overwrites the changed file back to the pristine original at startup. Tried as superuser as well. Any thoughts? :confused:

This thread is dated but I thought I'd help future posterity.

I'm using Banshee 1.5.1 on Ubuntu 9.10 and had the same issue.  I resolved the issue by:

[LIST=1]
[*]unchecking the 'Enabled' checkbox in the Equalizer window for New Preset
[*]quitting out of banshee (I made sure it wasn't running in the background as well)
[*]gedit ~/.config/banshee-1/equilizers.xml file
[*]copy-paste the Winamp equilizers into the file, preserving the xml structure.  I wanted to keep the 'New Preset' equilizer anyway.
[*]Save the file
[*]Run banshee, select your (new) WinAmp preset and check the Enabled checkbox for the preset.
[/LIST]

Alternatively you could probably copy the Winamp file directly into the ~/.config/banshee-1 directory after disabling the Equalizer preset but I didn't try that.

I hope this helps someone.

---


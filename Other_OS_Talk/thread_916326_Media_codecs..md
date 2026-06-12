---
title: "Media codecs."
date: 2008-09-10
forum: Other OS Talk
---

### Post by XxsydenxX on 2008-09-10
Hello, i have been wondering one little thing. You know how linux mint comes pre installed with audio and video codecs for viewing pleasure, and ubuntu doesn't. How does a distro get to come pre installed with these things. 
For example if i were to make a distribution of based off of debian how would i go about securing audio and video codecs already installed.. Would i have to have it install something like mplayer and vlc? And amarok with mp3 support and so forth?

---

### Post by Rocket2DMn on 2008-09-11
Moved to Other OS Talk - please don't post help requests in the Tutorials & Tips forums, it is for guides and HowTos only and requires staff approval.  Thank you.

---

### Post by SunnyRabbiera on 2008-09-11
> **XxsydenxX said:**
> Hello, i have been wondering one little thing. You know how linux mint comes pre installed with audio and video codecs for viewing pleasure, and ubuntu doesn't. How does a distro get to come pre installed with these things. 
For example if i were to make a distribution of based off of debian how would i go about securing audio and video codecs already installed.. Would i have to have it install something like mplayer and vlc? And amarok with mp3 support and so forth?

Well its more on philosophy then anything else, though Ubuntu being a commercial distribution makes things more difficult for it to pre package say flash or windows codecs.
The reason?
Microsoft, with smaller distrobutions like Mint or Mepis the codecs and stuff preinstalled are overlooked, but ubuntu and most other commercial distros are direct competition to Microsoft so they have to turn tail on preinstalling codecs and junk.

---

### Post by doas777 on 2008-09-11
> **XxsydenxX said:**
> Hello, i have been wondering one little thing. You know how linux mint comes pre installed with audio and video codecs for viewing pleasure, and ubuntu doesn't. How does a distro get to come pre installed with these things. 
For example if i were to make a distribution of based off of debian how would i go about securing audio and video codecs already installed.. Would i have to have it install something like mplayer and vlc? And amarok with mp3 support and so forth?

ubuntu theoretically is a bigger target than some of the other distros out there (discounting suse and rh, of course), so it's a good idea if they keep their noses clean.

one of the first things i do with a new build is to install the [medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu") and then install the win64codecs (or win32codecs for x86).

I also install the restricted codecs, by enabling the multiverse repos, and running:
```

sudo apt-get install ubuntu-restricted-extras

```

I havn't come across too many files that i can't get going. 

have fun
frank

---

### Post by pelle.k on 2008-09-11
Or if you run kubuntu "apt-get install kubuntu-restricted-extras".
Basically, if you run kde, you rely much on xine, and thus you need libxine1-all-plugins, and w32codecs. If you run gnome, you need gstreamer codecs, such as gstreamer0.10-plugins-ugly etc. Most of these are incuded in the *-resestricted-extras (meta) packages.

---


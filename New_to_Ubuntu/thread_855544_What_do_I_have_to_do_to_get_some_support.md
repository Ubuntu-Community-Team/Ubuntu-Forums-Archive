---
title: "What do I have to do to get some support?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by El_Matthews on 2008-07-10
Dear,


First of all this is not a complaint against Ubuntu or any kind. I love Ubuntu even now in those dark times for me. I'm just getting a little desperate to find a solution. 

What I am doing wrong, I posted a question on the Beginners forum, then I found a forum of Mythbuntu so I posted the same question there. I also posted the question on launchpad but I don't get any answers.

Is it me or am I doing something wrong? Please help, what do I have to do to find a solution? 
 

Hereby the links;
[https://answers.launchpad.net/ubuntu/+question/37722](https://answers.launchpad.net/ubuntu/+question/37722) on 2008-06-29
[http://ubuntuforums.org/showthread.php?t=850012](http://ubuntuforums.org/showthread.php?t=850012)
[http://ubuntuforums.org/showthread.php?t=828356](http://ubuntuforums.org/showthread.php?t=828356)

---

### Post by halitech on 2008-07-10
depending on the questions or problems you are having, it might take time for the right person to come along with an answer. Just be patient and someone will come along with the answers you need.

---

### Post by philinux on 2008-07-10
You could try in system>prefs>sound and changing from the default autodetect to pulse-audio and then try alsa.

Just use the test button to see if any sound is forthcoming.

---

### Post by kansasnoob on 2008-07-10
Well, I've never installed Mythbuntu, but I've done some K,X,Ubuntu so I'm going to start with a real stupid question:

Do you have any sound at all in any programs? No start-up sounds?

No audio at all?

---

### Post by kansasnoob on 2008-07-10
I know this may have already been tried, or may not apply, but I'm going to give you all I've got so here we go (and I'm not going to prefix every post I make hereafter), OK?:

> Some users report problems with video playback in the GNOME movie player, and audio playback in other applications, due to an error when connecting to the PulseAudio sound server. Investigation of this possibly hardware-specific issue is ongoing. A workaround is to enter the System -> Preferences -> Sound dialog and change the Music and Movies sound playback option from 'Autodetect' to 'ALSA'. 

From: [http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

---

### Post by kansasnoob on 2008-07-10
I like to install > gnome-alsamixer from synaptic. It seems to have more options IMHO.

[ATTACH]77178[/ATTACH]

[ATTACH]77179[/ATTACH]

Lots of toggles!

---

### Post by kansasnoob on 2008-07-10
Now we get into the possibility that your audio needs "non-free' support:

If you haven't already installed the Medibuntu Repo do so now:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE: remember the GPG key!

Then go to synaptic and install:

> alsa-firmware
alsa-firmware-loaders

---

### Post by kansasnoob on 2008-07-10
Since this is all about sound in video (why else would you be using Myth?) install the following from synaptic:

ALL > gstreamer good, bad, and ugly! If it starts with gstreamer install it!

Install > totem-gstreamer maybe? I love totem but I don't know how Myth plays with totem. (it shouldn't interfere with other libraries anyway)

Install all > sun-java6 except -doc & -source!

Install > flashplugin-nonfree

Now > non-free-codecs

---

### Post by BGFG on 2008-07-10
Hi, 
Check out this thread. if it doesn't help then message the thread starter. He seems to be an authority on sound.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kansasnoob on 2008-07-10
And finally I've found this helpful:

[http://ubuntuforums.org/showthread.php?t=849792](http://ubuntuforums.org/showthread.php?t=849792)

---

### Post by kansasnoob on 2008-07-10
> **BGFG said:**
> Hi, 
Check out this thread. if it doesn't help then message the thread starter. He seems to be an authority on sound.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Great link! I bookmarked that one, thanks!

---

### Post by El_Matthews on 2008-07-10
> **philinux said:**
> You could try in system>prefs>sound and changing from the default autodetect to pulse-audio and then try alsa.

Just use the test button to see if any sound is forthcoming.

Mythbuntu is based on xubuntu which doesn't has this menu. Maybe this can be done somewhere else in xubuntu but I didn't manage to find it.

---

### Post by El_Matthews on 2008-07-10
To all, thanks for the replies. Now I have a lot of info and a lot of work. Tommorow I will start investigating those links.


ps: kansasnoob, yes I have sound but not in tv applications. mplayer etc are working fine when watching movies.

---

### Post by kansasnoob on 2008-07-10
> **El_Matthews said:**
> To all, thanks for the replies. Now I have a lot of info and a lot of work. Tommorow I will start investigating those links.


ps: kansasnoob, yes I have sound but not in tv applications. mplayer etc are working fine when watching movies.

Then I suspect it's a "library" problem. Libraries are like:

(my defaults)

libao2
libasound2
libesd-alsa0
libpt-1.10.10-plugins-alsa
libsdl1.2debian-alsa
linux-sound-base

Of course libraries will vary due to dependencies.

It couldn't hurt to do something as simple as running:

```
sudo apt-get -f install
```

just to try and meet any unmet dependencies.

Sorry you didn't get a better response earlier, but I've never used Myth so i skip over those threads.

---

### Post by El_Matthews on 2008-07-11
gents,


Thanks for the links, they gave me useful information. Example Xubuntu on which Mythbuntu is based doesn't use pulse!

So it has nothing to do with pulse. The problem has to be found elsewhere.


PS: after testing now I have sound vlc and xine but not anymore in mplayer.

---

### Post by El_Matthews on 2009-04-20
Gents, this works now. How can I close this thread?

---

### Post by freak42 on 2009-04-20
are you sure you have a bt**v**878 chipset? I can't find a lot of info about it:
In case you have a bt878 chipset: check out this (very useful) wiki:
[http://www.linuxtv.org/wiki/index.php/Bt878](http://www.linuxtv.org/wiki/index.php/Bt878)

look at the botom.. it has some notes about conflicting ALSA (sound) stuff

hth

---

### Post by juancarlospaco on 2009-04-20
*You can pay Canonical Support, Desktop Basic isn't expensive.*

---


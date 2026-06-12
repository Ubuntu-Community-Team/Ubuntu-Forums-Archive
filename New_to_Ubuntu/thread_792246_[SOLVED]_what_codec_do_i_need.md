---
title: "[SOLVED] what codec do i need"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by DarinB on 2008-05-12
what codec do i need to get audio cd extractor to rip to mp3

the mp3 is not a choice in the preferences.
it says it needs a lossy mp3 codec??????
where do i find this thing?????????????????????

---

### Post by JoshuaRL on 2008-05-12
> **DarinB said:**
> what codec do i need to get audio cd extractor to rip to mp3

the mp3 is not a choice in the preferences.
it says it needs a lossy mp3 codec??????
where do i find this thing?????????????????????

Make sure you have the Restricted Extras installed, and the lame engine for encoding too:

Go into System->Administration->Software Sources and check to see if all the sources are checkmarked except for the CD and source code.  Then:

```

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras lame

```

---

### Post by DarinB on 2008-05-12
I installed the lame package and audio cd extractor still won't give the option to rip as mp3

---

### Post by HotShotDJ on 2008-05-12
> **DarinB said:**
> I installed the lame package and audio cd extractor still won't give the option to rip as mp3
Is there some reason why you won't or can't install ubuntu-restricted-extras?

---

### Post by DarinB on 2008-05-12
i did i cut and pasted your commands.
but when i open the extractor the choice still doesn't appear for mp3??????

---

### Post by nynoah on 2008-05-12
You need the Lame codecs.  Then you need to configure your ripper to rip as an MP3.  Just because you installed the ability to rip MP3 does not meant that it has been changed to MP3 by default.  You may also want to experiment with some of the other ripping programs.  K3B is a good one, Audio CD extractor is another.  You can just do a search through synaptic using words like MP3 and ripper.

---

### Post by HotShotDJ on 2008-05-12
> **DarinB said:**
> i did i cut and pasted your commands.
but when i open the extractor the choice still doesn't appear for mp3??????Ok.  If you did that, then MP3 support should be installed.  Lets just be sure... run the command:```
sudo apt-get install ubuntu-restricted-extras
```One of two things should happen, the package will be installed OR you'll get a message that the newest version is already installed.  I'm wondering if you might have to log-out and log-in for the new MP3 support to get picked up by gnome.  It can't hurt to try.

---

### Post by zvacet on 2008-05-13
[Here]("https://help.ubuntu.com/community/CDRipping")

---

### Post by DarinB on 2008-05-13
thanks got that working but now i got a mew problem 

I posted this in multimedia

Running Hardy. I run a second HD that mounts automatically with my music.
I use Rhythmbox. I added the Lame restricted repos and now>>>>
Rhythmbox doesn't see my music!!!! the total songs goes backward to 0
i have to import my music folder at each boot takes for ever (10070 songs)
What do i do???????????????????????????????????????????????? ??
to tried to fix it i installed the lame package,,,now at least i can rip to mp3 with audio cd extractor
still same problem at boot??????????????????????????????????
no music at boot

---


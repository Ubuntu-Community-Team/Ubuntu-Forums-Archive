---
title: "sometimes music will not play (no sound or stays at 00)"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by mikeftl on 2008-11-12
a very annoying problem i temporarily fix when I log out and then back in.

---

### Post by alwez_loner on 2008-11-12
What program are you using and what kind of system do you have?

---

### Post by mikeftl on 2008-11-12
> **alwez_loner said:**
> What program are you using and what kind of system do you have?

firefox (using java) and rhythmbox usually.
sometimes i use pidgin

---

### Post by coldcoffee on 2008-11-12
I have found that when you run Java applications in a browser you cant get sound from any other source. You have to close out the browser, then  you will get sound again from other sources, then you can open up the java application but it will have no sound. I have talked to a few others on the Internet and It sounds like this is an issue with Ubuntu, maybe other Linux distros too?

If I run java, I can't get sound from youtube or even a cd. Close browser and I have sound from cd and youtube and any other sound source.

Edit: If I have a java based game open in a browser, things like youtube not only have no sound but they some of the times won't play the video. It will load, I can even see the progress bar showing it has loaded. But the video will pause after a few seconds. I just mentioned this in another thread on similar issues. I asked for any information on this. Because from what I have heard from others this is not an issue of missing drivers or such. More of an issue that there just seems to be  a problem with this in Ubuntu. I myself would really like someone that is knowledgeable on this to let us know what, if anything is being done to correct these issues.

---

### Post by CLomax on 2008-11-12
At one time I could actually play YouTube videos and music in Rhythmbox at the same time but didn't do anything to get it like that. It just happened... I can't do it now though :p

So it is possible.

---

### Post by alwez_loner on 2008-11-12
Try this it might be that there are certain codecs missing. [here]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by CatKiller on 2008-11-12
There are a range of sound server solutions for Linux - OSS, ESD, ALSA, JACK, PulseAudio... They are currently in a state of flux with none dominant over all the others, and don't all necessarily play that well with each other. Proprietary software (Flash, I'm looking at you) sometimes has one of these choices hard wired in without the configurability to change it. Which means that if you want sound in other things at the same time as that application then you need to configure everything else in a way that will work with whichever method that application uses.

You can change the default, system-wide sound settings with System -> Preferences -> Sound. You can also change the sound output in some applications like Wine, Rhythmbox, Amarok. You can also use audio wrappers (like aoss or padsp) to make an old application that uses OSS use one of the newer sound servers - ALSA and PulseAudio, respectively.

ALSA was the most supported method for a while, and still works well. Development is moving towards PulseAudio now for its greater flexibility. As long as you get all the applications that you want running to use the same method, it should generally work.

---

### Post by AndyCooll on 2008-11-12
As discussed by catkiller the problem is with pulseaudio. I too have had instances of being able to have sound in either the web-browser and the audio player but not both. Changing the default sound settings to ALSA solved the issue.

:cool:

---

### Post by boof1988 on 2008-11-12
I have the same problem as well... But I finally decided I prefer it the way it is.  If I have music playing in Rhythmbox, I don't want interruptions of sound from internet sites (flashy-plugin-pleyery-things).  So (for now) I think I'll keep it the way it is and maybe in the future fix the issue as a learning exercise and then change it back due to preference.

This way I can choose where my sound is coming from.

---

### Post by coldcoffee on 2008-11-12
I don't think it is a problem with missing codecs. I could be wrong though. They say it sometimes has sound. Which means it is working, just not all the  time. I can also play a music cd and have sound from it and a youtube video at the same time. If I do though, no sound in a online java based game. If I open up the java based game first it has sound and nothing else.

I have to close out all browsers and before I can get sound from anything else. And a lot of the time I may have two to three browsers open with several tabs in each. I can't just close the tab with the java applet in it either. The reason this is so annoying is I may not really want to bookmark these tabs, but I really don't want to close them at the moment either. And should one really have to remember all the sites open. This is really not an acceptable problem in a OS that is this far advanced.

I am guessing a lot of people don't play a java based game that much so really don't understand the issue. I am also guessing this is the issue original poster is having since they did mention java.

I have heard from others that I would consider to be rather geek/tech savvy with Linux that this is an issue with Ubuntu. I gather from them that it is an issue that falls more on Ubuntu than the end user having configuration problems. I would really like to hear someone with Ubuntu/Canonical speak out on this, or an article that discusses the issue in detail.

---

### Post by mikeftl on 2008-11-12
changing the sound settings to ALSA seemed to fix the problem.

---

### Post by sirebral on 2008-11-12
it is caused by a driver conflict.

If you are running pulse audio try this in a terminal.

```

pulseaudio -k
pulseaudio -D

```

---

### Post by CatKiller on 2008-11-12
> **coldcoffee said:**
> I have to close out all browsers and before I can get sound from anything else. And a lot of the time I may have two to three browsers open with several tabs in each. I can't just close the tab with the java applet in it either. The reason this is so annoying is I may not really want to bookmark these tabs, but I really don't want to close them at the moment either.

Edit -> Preferences -> Main.
When Firefox starts: Show my windows and tabs from last time

---

### Post by CatKiller on 2008-11-12
> **mikeftl said:**
> changing the sound settings to ALSA seemed to fix the problem.

Excellent.

---


---
title: "Still no sound on You-tube videos"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-19
Despite following this
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I still cannot get any sound to work on you-tube videos or other videos on the internet.
Scratch last, Got pulse audio device chooser to work.

Help? :[

---

### Post by Ryadt on 2008-07-19
Try this in terminal```
sudo apt-get install libflashsupport
```

You nicked my avtar:lolflag:

---

### Post by projecthikari on 2008-07-19
> **Ryadt said:**
> Try this in terminal```
sudo apt-get install libflashsupport
```

You nicked my avtar:lolflag:

*gasp!* Avatar Awesomeness!! :guitar:

Anyway, I tried that, didn't work! T_T

---

### Post by Ryadt on 2008-07-19
Trying restarting your browser and see if it works.

---

### Post by projecthikari on 2008-07-19
> **Ryadt said:**
> Trying restarting your browser and see if it works.

still nothing... T_T

---

### Post by daimaru on 2008-07-19
make sure you dont have any other apps open (like vlc player, mplayer of audio players) i know this sucks, but sadly my browser based video sound only works if i do not have any other sound or video apps open at the time.

if it still does not work it might have to do with the hardware adress of your sound card. I had that problem and was able to solve it by binding my hw adress to a specific address (meaning the first one) eg. hw 0,0 instead of hw 1,0 or hw 0,1

---

### Post by exaviorn on 2008-07-19
Would restarting or logging off and back in possibly fix the problem?

---

### Post by projecthikari on 2008-07-19
none of it seems to be workng, still...

That hw thing,
"if it still does not work it might have to do with the hardware adress of your sound card. I had that problem and was able to solve it by binding my hw adress to a specific address (meaning the first one) eg. hw 0,0 instead of hw 1,0 or hw 0,1"
How is that done?

---

### Post by YaroMan86 on 2008-07-19
I know it sounds obvious, and I don't mean to insult your intelligence in any way... but having done tech support-ish work in the Army I have one very simple suggestion.

Is everything plugged in? Have you checked the volume everywhere? On the YouTube video applet? Ubuntu's system volume? Speaker volume?

People tend to overlook these things more often than not.

---

### Post by sdowney717 on 2008-07-19
double click the volume icon and see if the sliders are up

---

### Post by projecthikari on 2008-07-19
> **YaroMan86 said:**
> I know it sounds obvious, and I don't mean to insult your intelligence in any way... but having done tech support-ish work in the Army I have one very simple suggestion.

Is everything plugged in? Have you checked the volume everywhere? On the YouTube video applet? Ubuntu's system volume? Speaker volume?

People tend to overlook these things more often than not.

Oh, don't worry about Insulting my intelligence or something, because I know all too well the "obvious problems" people have. :)
I'll re-check everything to be sure, But I'm working on a laptop, so I don't think it's hardware trouble. ALL other sound works EXCEPT youtube. Not that it's important, it's just a bit frustrating. 
Everything's up, connected, audio is enabled... I'm trying to think what could be wrong...

Now, in the PulseAudio Applet, It says I have output devices and input devices but under "playback" it says "No streams Available."

---

### Post by sdowney717 on 2008-07-19
pulse audio applet,
that pulse audio might be it. 
Use alsa-base

---

### Post by projecthikari on 2008-07-19
> **sdowney717 said:**
> pulse audio applet,
that pulse audio might be it. 
Use alsa-base

It merely added Totem to the streams...
I just feel like it's something *I* must be doing wrong. T_T

---

### Post by Promaster91 on 2008-07-19
Try to install the flash 10 beta.
I tried using this...
```

sudo apt-get install libflashsupport

```
... but it causes Firefox to crash alot!!
First remove the current flash plugin then go [here]("http://labs.adobe.com/downloads/flashplayer10.html"), and install it. See if that works.

---

### Post by Ryadt on 2008-07-20
> **projecthikari said:**
> Despite following this
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I still cannot get any sound to work on you-tube videos or other videos on the internet.
Scratch last, Got pulse audio device chooser to work.

Help? :[

Hi..
Try stopping pulse audio and see if it solves it.
```
killall pulseaudio
```

or go end it in System Monitor > Preferences.

---

### Post by susanpenter on 2009-06-26
I am having the same problem I think.  All my system audio and Amarok have sound as usual but there is no sound whilst you tube films play.

And yes I exited fully from Amarok and all the cables are still plugged in and the speakers working and vulume turned up.

---

### Post by eMJayy on 2009-06-26
That's pretty weird. 

If flash video (with sound) is working on one site, it really should be working on all sites, especially if everything was ok previously. 

Here's my suggestion - I assume that you are using Firefox as your browser? Try testing the issue using another browser (I recommend tryin YouTube with [[COLOR="Red"]Opera[/COLOR]]("http://www.opera.com/")). If the problem is replicated in the other browser, then it may be that you *might* need to uninstall and then reinstall your flash plugin. Make sure that you are using version 10 of the adobe flash plugin and are not unknowingly using any other flash plugin simultaneously. 

To verify that Firefox is using the adobe flash plugin, type **about:plugins** in the address bar and scan the list that appears to confirm that only *Shockwave Flash 10.0 r22* is being used (that's the 32bit plugin; I think the 64bit version is still in beta).

ps. that should be "about : plugins" without the spaces - the emoticon is not intentional

---


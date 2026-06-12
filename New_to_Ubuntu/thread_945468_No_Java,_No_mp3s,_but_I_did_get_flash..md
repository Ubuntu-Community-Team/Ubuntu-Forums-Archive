---
title: "No Java, No mp3s, but I did get flash."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by JakeWatkins on 2008-10-12
For some reason, I can not install Java. And as I'm writing this.. I'm trying to install Java. It seems to be working. I am sorry for wasting your time.

Mp3s, however, are giving a good fight.

I installed GStreamer, but every time I got to open them with Rhythmbox, it says: The GStreamer plugins to decode "MP3" files can not be found.

So I uninstalled and, and reinstalled it. No luck. Any ideas, guys?

Oh, yeah, forgot to say: I did get Flash working on the first try. ;- )

OK - so I just tried using Flash... going to skreemr.com for some music.. and it would play about 5-10 seconds of music, and disappear. So I guess I didn't get flash to work...

---

### Post by SuperSonic4 on 2008-10-12
Add the medibuntu repos by the following if you haven't already

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Copy and paste to get:

```


sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

Source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by JakeWatkins on 2008-10-12
Thank you, very much.. but I doubt you saw my new problem: Flash isn't working anymore.. any tips on that?

---

### Post by JakeWatkins on 2008-10-12
And now it's working.. it was working up until the point I changed the tab, then it just shut off...

Oh, and this is what I got back:
```
jake@Jake:~$ sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package icedtea-gcjwebplugin is not installed, so not removed
E: Couldn't find package libflash-mozplugin

```

---

### Post by SuperSonic4 on 2008-10-12
What's the output if you type [noparse]about:plugins[/noparse] into a firefox window? Hopefully it will say shockwave flash or something

```
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```


All I can suggest otherwise is to remove any packages that come up with that error message and try again

---

### Post by JakeWatkins on 2008-10-12
```
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by SuperSonic4 on 2008-10-12
It could be a flash version 10 thing because mine works perfectly with 9. I know it sounds foolish but does resetting your browser do anything?

---

### Post by JakeWatkins on 2008-10-12
Restarting Firefox doesn't help...

How can I go back to Version 9?

---

### Post by SuperSonic4 on 2008-10-12
I guessed it wouldn't :(

Flash player 9 is available from the adobe website [Here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") and installation instructions are [here](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

Someone else on the forums might know more about it than me so you could wait and see if you get replies?

---

### Post by JakeWatkins on 2008-10-12
[IMG]http://img253.imageshack.us/img253/8315/errorbj3.png[/IMG]

OK - I can wait. That picture was regarding to Java install.

I'll try the Flash thing. Thank you for all of your help, SuperSonic4.

---

### Post by SunnyRabbiera on 2008-10-12
Well if that message pops up it means you have to go into synaptic, a application located under system> administration> synaptic package manager.
Synaptic is a gateway to the packages for your system, when add/remove may not display all that is needed synaptic will if you configure it right.
to fix broken packages go to "custom filters" and then go to broken.
To remove broken packages click the box next to the name (right or left click will do"" and select "remove packages"
So that the error you got will go away.
But if you need help installing packages especially multimedia ones its usually better to ask us about it instead of going off on your own and taking a guess.
Ubuntu is a different OS then windows, and even though the learning curve can be a bit rough sometimes once something works, it works.

---

### Post by JakeWatkins on 2008-10-12
I'm also using Ubuntu 8.10 Alpha, or Beta.. or whatever it is in right now. :p

VLC Media Player plays my m4as/mp3s but rhythmbox won't. Hope that helps..

---

### Post by SunnyRabbiera on 2008-10-12
> **JakeWatkins said:**
> I'm also using Ubuntu 8.10 Alpha, or Beta.. or whatever it is in right now. :p

VLC Media Player plays my m4as/mp3s but rhythmbox won't. Hope that helps..

Now right there is probably to blame for most of your issues.
Ibex is beta, meaning it needs time to develop before it is ready.
You should use hardy instead until Ibex comes out and is ready for everyday use.

---

### Post by JakeWatkins on 2008-10-12
Is there a way to downgrade? Because I upgraded using sudo update-manager -d -c

---

### Post by JakeWatkins on 2008-10-14
[[IMG]http://img366.imageshack.us/img366/5347/screenshot1nr1.th.png[/IMG]](http://img366.imageshack.us/img366/5347/screenshot1nr1.png)

---


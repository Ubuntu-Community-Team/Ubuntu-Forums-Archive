---
title: "Flash/YouTube problem in Hardy."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by KrisScofield on 2008-04-27
I did a fresh install of Hardy 8.4 last night and downloaded the latest Adobe flash player so I could get on YouTube, and then installed Gnash plugins (as I would with Gutsy and the Hardy Beta) but now there is no sound and the videos won't load. 

There were two other optional Adobe plugins above the Gnash one. How do I get to the screen that lets me install those?

/noob 

Thanks:)

---

### Post by TeoBigusGeekus on 2008-04-27
If you are using Opera
[http://ubuntuforums.org/showthread.php?t=745325]("http://ubuntuforums.org/showthread.php?t=745325")

---

### Post by grazed on 2008-04-27
Go to system > administration > Synaptic Package Manager

do a search for gnash, and mark them for uninstallation. Then go ahead and press apply.

you can re navigate back to any flash site, you tube works fine, and it will prompt you with your choices once again. I would suggest using adobe's version, least amount of issues for me.

good luck.

---

### Post by KrisScofield on 2008-04-27
> **TeoBigusGeekus said:**
> If you are using Opera
[http://ubuntuforums.org/showthread.php?t=745325]("http://ubuntuforums.org/showthread.php?t=745325")

Thanks, I forgot to mention I'm using Firefox.

---

### Post by KrisScofield on 2008-04-27
> **grazed said:**
> Go to system > administration > Synaptic Package Manager

do a search for gnash, and mark them for uninstallation. Then go ahead and press apply.

you can re navigate back to any flash site, you tube works fine, and it will prompt you with your choices once again. I would suggest using adobe's version, least amount of issues for me.

good luck.

Hmm, that seemed to get the videos to play, but still no sound :( Not an audio issue either, Amarok works.

---

### Post by metol on 2008-04-27
> **KrisScofield said:**
> Hmm, that seemed to get the videos to play, but still no sound :( Not an audio issue either, Amarok works.

I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```

From the description: *Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.*

You will need to restart Firefox after installing this utility.

Hope this works for you,
Metol

---

### Post by Wynne G Oldman on 2008-04-27
Try going to "Synaptic Package Manager" and install "Ubuntu Restricted Extras". Then go to the Medibuntu website and follow the instructions on the "Repository How to" page to copy and paste the commands into Terminal. This should enable everything that you need for all multimedia, including allowing you to play/copy encrypted DVD's and ripping to MP3 with Sound Juicer. Hope this helps. 
PS. I'm sure that I didn't have to do anything at all to play Youtube video's with a bog standard installation of Hardy. Perhaps you should try removing the Gnash plugin.

---

### Post by KrisScofield on 2008-04-27
That worked! :) Thanks,

---

### Post by Wynne G Oldman on 2008-04-27
> **KrisScofield said:**
> That worked! :) Thanks,If you're talking to me, it's a pleasure.:)

---

### Post by pieisgood4589 on 2008-04-27
> **Wynne G Oldman said:**
> Try going to "Synaptic Package Manager" and install "Ubuntu Restricted Extras". Then go to the Medibuntu website and follow the instructions on the "Repository How to" page to copy and paste the commands into Terminal. This should enable everything that you need for all multimedia, including allowing you to play/copy encrypted DVD's and ripping to MP3 with Sound Juicer. Hope this helps. 
PS. I'm sure that I didn't have to do anything at all to play Youtube video's with a bog standard installation of Hardy. Perhaps you should try removing the Gnash plugin.

Worked for me. Thanks! :guitar:

---

### Post by wastedfluid on 2008-04-27
> **metol said:**
> I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```

From the description: *Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.*

You will need to restart Firefox after installing this utility.

Hope this works for you,
Metol

You are my savior.  Sound in Flash hasn't worked for me since I upgraded from Gutsy to Hardy.

---

### Post by lloydlloyd on 2008-04-29
> **metol said:**
> I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```

From the description: *Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.*

You will need to restart Firefox after installing this utility.

Hope this works for you,
Metol


this worked for me. thanks a bunch :)

---

### Post by Helios38 on 2008-04-29
for any1 who does not find a fix doing that, try this


uninstall gnash (yuckey flash component, never works.)


```
sudo apt-get purge gnash
```


and install flash (along with many other useful codecs and tools)


```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by lanchongzi on 2008-04-29
> **metol said:**
> I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```



that helped, thanks a bunch

---

### Post by tliotis on 2008-04-29
thank you works for me fine!

---

### Post by Nevyn on 2008-04-29
Sorry to barge in like this.

> **Helios38 said:**
> 
```
sudo apt-get purge gnash
```
```
sudo apt-get install ubuntu-restricted-extras
```

I tried this and got the error message 

```
E: Couldn't find package ubuntu-restircted-extras
```

Also tried to install flashplugin-nonfree, but I already had the latest version.

My flash-error consists of flash-videos playing without sound for 2 secs, then stops. If I fastforward, it continues to play for exactly 2 seconds, then stops again.

I have universe, multiverse and restricted enabled in Software Sources.

---

### Post by Aranmanoth80 on 2008-04-29
sudo apt-get install libflashsupport

For me this did the trick.
I don't understand why this package is not installed by default!

---

### Post by Gwaihirjp on 2008-04-29
> **metol said:**
> I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```

From the description: *Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.*

You will need to restart Firefox after installing this utility.

Hope this works for you,
Metol
This worked perfectly for me, thanks very muchly! ^-^

---

### Post by Auslegung on 2008-04-29
> **Nevyn said:**
> Sorry to barge in like this.



I tried this and got the error message 

```
E: Couldn't find package ubuntu-restircted-extras
```

Also tried to install flashplugin-nonfree, but I already had the latest version.

My flash-error consists of flash-videos playing without sound for 2 secs, then stops. If I fastforward, it continues to play for exactly 2 seconds, then stops again.

I have universe, multiverse and restricted enabled in Software Sources.
You misspelled restricted.  In your error message it says E: Couldn't find package ubuntu-restIRcted-extras while it's supposed to be restRIcted.

---

### Post by Auslegung on 2008-04-29
> **Wynne G Oldman said:**
> Try going to "Synaptic Package Manager" and install "Ubuntu Restricted Extras". Then go to the Medibuntu website and follow the instructions on the "Repository How to" page to copy and paste the commands into Terminal. This should enable everything that you need for all multimedia, including allowing you to play/copy encrypted DVD's and ripping to MP3 with Sound Juicer. Hope this helps. 
PS. I'm sure that I didn't have to do anything at all to play Youtube video's with a bog standard installation of Hardy. Perhaps you should try removing the Gnash plugin.
Worked great for me, thanks!

---

### Post by Nevyn on 2008-04-29
Should proof-read before I hit enter ;)

Anyway, the problem remains since ubuntu-restricted-extras already is the newest version.

---

### Post by ediblestarling on 2008-04-29
> **metol said:**
> I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```

From the description: *Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.*

You will need to restart Firefox after installing this utility.

Hope this works for you,
Metol

This fixed it for me. I'm using the Pulseaudio ALSA devie.

---

### Post by metol on 2008-04-29
Thanks for the feedback everyone.  This forum has helped me countless times since I switched to Ubuntu.  It is very nice to know that I can give a little bit of help back to the community.

Metol

---

### Post by nrayever on 2008-04-29
> **metol said:**
> I had a similar problem.  The following fixed it for me...

```
sudo apt-get install libflashsupport
```

From the description: *Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible.*

You will need to restart Firefox after installing this utility.

Hope this works for you,
Metol

thanks metol!, works like a charm!

nrayever

---

### Post by paddy2 on 2008-06-11
:guitar:Not being able to playback you tube videos in Hardy Heron was driving me crazy,until a saw the posting above about uninstalling gnash,I done that, and everything works perfectly.:)

---

### Post by tbscmc on 2009-05-29
Youtube video doesn't work with hardy right now, anyone got a fix? my system is updated, i never installed gnash, tried both flashplugin-nonfree and .deb from adobe's website

---


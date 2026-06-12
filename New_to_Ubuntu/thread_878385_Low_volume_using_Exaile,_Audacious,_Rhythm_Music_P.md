---
title: "Low volume using Exaile, Audacious, Rhythm Music Player"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-08-02
Good morning

Having problem getting any more than conversation loudness out of my speakers (laptop and otherwise) when playing mp3 audio.  The laptop has mainboard integrated sound, I dont know the details (is there a tool for finding this like there is for video?) 

Have tried to use Exaile, Audacious, and Rhythm.  The output seems to be about 1/3 to 1/4 of what I would have expected.  

Volume is up both in the software, on the Master, and on the speakers and laptop's physical volume controls.  Have been into the Sound and Volume Control in the system --> preference menu.  All devices are at max.

I notice that if I use the Audacious equalizer the output is largely increased (only in Audacious obviously) but the quality goes very bad no matter the settings in the equalizer.

Any help?  Thanks.

---

### Post by perlluver on 2008-08-02
> **SonOfOdin said:**
> Good morning

Having problem getting any more than conversation loudness out of my speakers (laptop and otherwise) when playing mp3 audio.  The laptop has mainboard integrated sound, I dont know the details (is there a tool for finding this like there is for video?) 

Have tried to use Exaile, Audacious, and Rhythm.  The output seems to be about 1/3 to 1/4 of what I would have expected.  

Volume is up both in the software, on the Master, and on the speakers and laptop's physical volume controls.  Have been into the Sound and Volume Control in the system --> preference menu.  All devices are at max.

I notice that if I use the Audacious equalizer the output is largely increased (only in Audacious obviously) but the quality goes very bad no matter the settings in the equalizer.

Any help?  Thanks.

lspci will give you the output of all the devices on your system.  As for poor sound quality if the master and the PCM is all the way up it will crackle.

---

### Post by K2712 on 2008-08-02
> **SonOfOdin said:**
> 
Volume is up both in the software, on the Master...

I assume by Master you mean alsamixer?

---

### Post by SonOfOdin on 2008-08-02
yeah, it does crackle a little bit.  If I have it down just a notch it clears up, but of course then it gets harder to hear, specially away from the pc.

Thanks for the lspci command.  The Audio device is an ALi AC'97.

---

### Post by SonOfOdin on 2008-08-02
Thats correct.

I have been through the rest of the sound preferences, everything except sound capture is on Autodetect.  Have had a fiddle, and Alsa mixer is the only thing that produces sound.

---

### Post by pi.boy.travis on 2008-08-02
Try typing alsamixer into a terminal, and making sure the outputs you want are set to max.

---

### Post by Mr_Freez3 on 2008-08-02
SonOfOdin,

Did you try double clicking the speaker icon in the Gnome panel (top or bottom of the desktop)?  This will pop up a window with some volume settings.  Maybe the PCM setting is set really low...seems like I remember having a similar problem before.

---

### Post by SonOfOdin on 2008-08-02
Pi, thanks for the AlsaMixer idea.  Yep, PCM is set to max.

---

### Post by SonOfOdin on 2008-08-02
Hey Mr Freez,

Yep, thats what I meant by Master.  Its all the way up @ 100%

---

### Post by cybrsaylr on 2008-08-03
> **Mr_Freez3 said:**
> SonOfOdin,

Did you try double clicking the speaker icon in the Gnome panel (top or bottom of the desktop)?  This will pop up a window with some volume settings.  Maybe the PCM setting is set really low...seems like I remember having a similar problem before.

Thanks, I was wondering how to get more volume also.
Did what you suggested and it worked.

---

### Post by XanTrax on 2008-10-15
I had the same problem.  Totem was producing amazingly louder output where as Audacious was significantly lower (approx: 25%). 

Don't know if this is resolved yet but I found something that may help. 

Inside Audacious do this:

Preferences -> Plugins -> Effects -> "AudioCompressor AGC Plugin"

Then, play with the "maximum gain" and "target audio level" and enable "agressively prevent clipping"

This allowed me to nearly match the volume output of Totem.

---

### Post by pyromanic123boom on 2008-10-15
Sometimes you can open 

alsamixer 

in the terminal and then boost center/master up. different settings in there could fix the issue.

---

### Post by XanTrax on 2008-10-15
> **pyromanic123boom said:**
> Sometimes you can open 

alsamixer 

in the terminal and then boost center/master up. different settings in there could fix the issue.

I did that.  This only started for me on Intrepid.  Like I said, Totem was producing proper volume output whereas Audacious was producing approx 25% less than other applications, which is what tipped me off that it wasnt anything like alsamixer volumes.  I played around with some plugins in audacious and found the ones mentioned above, which is what gave me back that missing 25%.

Also, since I went on intrepid when I do "alsamixer" in a shell, it automatically defaults to the PulseAudio volume.  If I do:

"alsamixer -c 0"

it loads my proper card (HDA Nvidia) to where I can edit the master, pcm, front, center, etc..

---

### Post by H.R.Rambler on 2009-02-17
> **XanTrax said:**
> 

Inside Audacious do this:

Preferences -> Plugins -> Effects -> "AudioCompressor AGC Plugin"

Then, play with the "maximum gain" and "target audio level" and enable "agressively prevent clipping"



Thank you, I was having this exact problem in Audacious and this was a good solution.

---


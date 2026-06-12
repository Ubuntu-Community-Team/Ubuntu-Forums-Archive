---
title: "MP3 songs not played"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-06-14
Hi all,

  i am a newbie to linux. i tried to play a mp3 file from CD and after that it prompts to "search" for mp3 codecs and i also give "search". then it ask for some "G......." download packages and installed itself. but even after that i am not getting my mp3 CD played when i opened it in rhythmbox player (my ubuntu can recognize CD automatically and opens) it prompts me the error "cannot stream: invalid argument". please help me in this guys.

thanks in advance.

---

### Post by ad_267 on 2008-06-14
Go to system - administration - synaptic package manager.

Search for the package ubuntu-restricted-extras. Put a tick next to this and hit apply. You will then be able to play mp3 and flash and other things. See here for more info: [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by canthus13 on 2008-06-14
You need the restricted extras installed (Unless you have some moral aversion to using non-open source software).  Go to applications > Accessories > Terminal, then type

```
sudo aptitude install ubuntu-restricted-extras
```

It will ask you for your password.  type your account password.  Once this is done, you should have everything you need installed.  You may need to close the MP3 program and reopen it if it was open while you did this.  same goes for Firefox.

--Me

---

### Post by mailtwogopal on 2008-06-14
> **ad_267 said:**
> Go to system - administration - synaptic package manager.

Search for the package ubuntu-restricted-extras. Put a tick next to this and hit apply. You will then be able to play mp3 and flash and other things. See here for more info: [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

hi ad_267,

  i did as u said, but still getting the same error. i tried it playing thru both "rhythm box" as well as "movie player" refer screenshots attached. pls help.u can see the 2 screenshots out of one represents the "ununtu-restricted-extras" installed (did thru command mode) and another screenshot represents the error which i got.

Please help n thanks in advance.

---

### Post by ad_267 on 2008-06-14
Can you play mp3's that aren't on a CD fine?

What happens if you browse to the mp3 file in the file browser and open it from there?

---

### Post by mailtwogopal on 2008-06-15
> **ad_267 said:**
> Can you play mp3's that aren't on a CD fine?

What happens if you browse to the mp3 file in the file browser and open it from there?

hi,

  i ll try that and post u the results here. but i could play mp3 songs via the digital editing tool called audacity. yesterday i installed it thru synaptic manager and i played songs via audacity tool but not with "rhythm player". y is it so? plz help. thanks in advance.

---

### Post by mailtwogopal on 2008-06-15
hi,

  i copied one mp3 file from CD to user folder to music using "cp" command. but even that i clicked it opens rhythm box and thrown me same error. rather i could play that mp3 file in pc thru audacity. plz help me.

---

### Post by ad_267 on 2008-06-15
Can you right click on the file, select properties and then the audio tab and post what it says under audio.

---

### Post by mailtwogopal on 2008-06-15
> **ad_267 said:**
> Can you right click on the file, select properties and then the audio tab and post what it says under audio.

hi,

under audio it is as below:

codec      : MPEG 1 Audio, Layer 3 (MP3)
channels   : stereo
samplerate : 44100HZ
bit rate   : 128KBPS

but i installed vlc media player and that is playing all kinds of stuff in mp3 songs. is that the incompatibility of "rhythm box" player to play it. now i set mp3 songs to open with vlc by default. please clarify me.

---

### Post by ad_267 on 2008-06-15
The songs should play in rhythmbox and also in totem if you have the ubuntu-restricted-extras package installed. I'm sorry I don't know why they wouldn't be playing as the file is a proper mp3 and you should have the correct codecs.

---

### Post by pelle.k on 2008-06-15
Are you using ubuntu 8.04? If so, doesn't totem media player ask you if you wanna install codecs to play the file?

Install (if not installed already) gstreamer0.10-fluendo-mp3, gstreamer0.10-plugins-ugly and gstreamer0.10-ffmpeg (those should take care of youre multimedia needs) through synaptic package manager. :)
Have fun!

[B]EDIT!
I took a look at your error message, and that is not an indication of a codec error. It's an error having to do with playback of sound from your soundcard.
Open System->Preferences->Sound and change all from "Autodetect" to "Alsa".
It's a problem some people seem to be having with the new sound server, "pulseaudio", that is being worked on.[/B]

---


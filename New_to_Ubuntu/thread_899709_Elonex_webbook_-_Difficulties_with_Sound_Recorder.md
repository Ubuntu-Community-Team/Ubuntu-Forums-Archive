---
title: "Elonex webbook - Difficulties with Sound Recorder"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by webbooknovice on 2008-08-24
Dear all, I'm using a recently purchased Elonex Webbook. With the help of this forum I've got most of the applications working correctly - has been challenging, but all in all I think I actually prefer Linux to Windows. For some reason I can't get the Sound Recorder programme to work properly, I can't seem to record from the inbuilt microphone, and when I try and use Skype, I can hear callers, but they can't hear me. Is anyone able to help me with the correct settings?  Thanks in advance.

Andy

---

### Post by webbooknovice on 2008-08-26
I have played around with the settings and can now record using an external microphone. For some reason the front mic is inaudible. When I use Skype with the external headset and microphone I can hear the caller clearly, but my 'transmission' can barely be heard. Is anyone able to send me the 'ideal' settings for Soundrecorder seup using an external and the internal mic? One other problem I'm encountering is that the earphone socket on the Webbook doesn't disable the sound from the speakers. I've looked up the help file on the subject but it's 'lost me' due to my very limited knowledge of Ubuntu. As always, any help would be gratefully received. Thanks. Andy

---

### Post by unutbu on 2008-08-26
Go to System>Preferences>Sound. Does it say you are using ALSA? If so, open a terminal and type
```

alsamixer
```

Use the arrow keys to move between channels, and increase volume.
Press the 'm' key to mute/unmute channels.

Hope this helps.

---

### Post by Alan Bell on 2008-08-30
not too sure about the internal microphone to be honest. I did have it working with Audacity at one point but it wasn't very good because it picked up a lot of sound from the fan just behind it (although I was using a hand built prototype at the time - the production ones may be better) I can help with the speaker muting though, it will be fixed fairly soon in an automatic update, but you can set a module option to tell the soundcard a bit more about the layout the laptop has. In short add a line somewhere in /etc/modprobe.d/ containing options snd_hda_intel model=lenovo-101e. I blogged some[ details on how to do this]("http://webbookblog.com/?p=140").

---

### Post by rob_munro on 2008-09-09
I dont guess you would have any links for instructons on installing this would you? (Mainly how do you get a terminal and root access) The OS that comes with it is quite ropey I'd like to get ubuntu on it.

regards,
rob

---


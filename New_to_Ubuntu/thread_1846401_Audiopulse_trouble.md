---
title: "Audiopulse trouble"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by tikitikimaji on 2011-09-19
got the newest version of audiopulse to stream over my airport express.  But couldn't follow the instructions at [http://www.1ph0ne.com/2009/10/16/how-to-setup-ubuntu-to-works-with-airport-express/](http://www.1ph0ne.com/2009/10/16/how-to-setup-ubuntu-to-works-with-airport-express/) because when I go to pulseaudio preferences, I don't have the option to click on the second box under network access (as in, only the top box is white and clickable, the second one about the airport is grey and you can't click it.)

Do I have to change something to be able to click it?

Thanks

---

### Post by Lisiano on 2011-09-19
Type this into a terminal (Ctrl+Alt+T)
```
sudo apt-get install pulseaudio-module-raop
``` then restart pulseaudio by killing it
```
pulseaudio --kill
```
It should restart in a few seconds, it it doesn't type
```
pulseaduio -D
```

---

### Post by tikitikimaji on 2011-09-19
ok thanks!  So now I can click on the second box, but when I open the volume control, rhythmbox isn't under the playback tab, it only has System Sounds

Also, when I executed the pulse audio restart, it cut out the pandora music I was listening to, and now I can't get pandora to play through my computer speakers...

---

### Post by Lisiano on 2011-09-19
Pulseaudio is a sound server, once you kill it, any sounds stop playing, just restart the Pandora stream. If you still can't hear sounds, check that Pulseaudio is loaded by ```
pulseaudio -D
``` If it errors and says that another instance is running, everything is okay, else post the error here. But usually a relogin is good enough.
Also Rhythmbox will only be in the list while it is running.

---

### Post by tikitikimaji on 2011-09-19
Awesome, thanks!  The restart got everything going wonderfully!

---

### Post by tikitikimaji on 2011-09-19
ok, it worked fine for a bit, but when I left and came back, there is no drop down menu to change the output from "internal audio speakers" to airport express in the playback tab.  When I enter the "pulseaudio -D" into terminal, it said "E: main.c: Daemon startup failed."

sorry to keep coming back with issues.

---

### Post by Lisiano on 2011-09-19
If I'm not mistaken, don't you have to open Sound Preferences and select the default output in the Output tab? You are probably mistaking that for the Pulseaudio Volume Ccontrol, there you can change it by "Playback"

---

### Post by tikitikimaji on 2011-09-19
In sound preferences, the output tab also only has "internal audio analog stereo."  There's no airport to choose.  I tried restarting the airport also.

---

### Post by tikitikimaji on 2011-09-19
ok, I got it working again.  By unchecking and re-checking the "make discoverable apple itunes...available" box under pulseaudio preferences.  I don't know why it disappeared in the first place, but it seems fine now.  Thanks

---


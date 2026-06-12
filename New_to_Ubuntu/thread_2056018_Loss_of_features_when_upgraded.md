---
title: "Loss of features when upgraded"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by Kedster on 2012-09-10
Hello, it has been awhile since i have had any activity on here, this used to be a home for me. it is nice to be back for a bit.

I have upgraded to 12.04, actually i did months ago, but now I am back in school and use my TV as a second monitor for movie nights A LOT. 

When I was with ubuntu 11.10 I it was really awesome sound controller, One feature, wich I noticed right away was missing in 12.04 was that It does not have differrent volume levels for headphones and speakers. Before i could have speakers always muted and then when i plugged my headphones it it would remember the last volume, this was super convienent. I listen to music while i work in the library and now i have to remember to mute then unplug, kind of sucks. 

Secondly 
Now i do not have HDMI as an audio output, before if i pluged in HDMI it switched automatically, and now it is not even an option. I am unsure of how to fix this. 

any ideas or workarounds or even telling why it is like this would help. Thank you everyone

---

### Post by Epodx64 on 2012-09-10
To get back your volume controls try 
sudo apt-get install gnome-alsamixer 

or even better might be

sudo apt-get install veromix
>   p, li { white-space: pre-wrap; }  Veromix is a mixer for the PulseAudio sound server.
 

 Features:
  • control volume of each playback stream
  • control volume of devices (hardware)
  • control volume of input devices (microphone)
  • move playback streams between different devices (drag icon of playback stream and drop it on target device)
  • mute/unmute (click icon)
  • volume meter (on mouse over)
  • PopUp-Applet (icon-representation if inside panel)
  • can life in system tray or notification area
  • kill playback streams
  • set default output device
  • Middle-click on panel icon mutes default output
  • Mouse-wheel over panel icon increases/decreases volume of default output
  • supports global hotkeys
  • set volume above 100%
 

 This package contains the GTK+ frontend for GNOME and others.


as for the HDMI audio problem I have no idea

---

### Post by Kedster on 2012-09-10
Well although these could give more control over some aspects they do not seem to do what i was looking at.

Before when I would plug in headphones it would have a volume for them. so like i could have it set half for headphones and then unplug them and the speakers would be at 75% then i would plug headphones back in and they would be at half. 

And I really would like HDMI audio out somehow

---

### Post by newb85 on 2012-09-10
> **Kedster said:**
> When I was with ubuntu 11.10 I it was really awesome sound controller, One feature, wich I noticed right away was missing in 12.04 was that It does not have differrent volume levels for headphones and speakers. Before i could have speakers always muted and then when i plugged my headphones it it would remember the last volume, this was super convienent. I listen to music while i work in the library and now i have to remember to mute then unplug, kind of sucks. 



I'm currently running 12.04, and I definitely have different volume levels for speakers and headphones.  Are you using exactly the same hardware as you were with 11.10?

---

### Post by Kedster on 2012-09-10
Yess, i am. well i had a fan replaced i believe
But that shoudlnt matter

---

### Post by newb85 on 2012-09-10
> **Kedster said:**
> 
Now i do not have HDMI as an audio output, before if i pluged in HDMI it switched automatically, and now it is not even an option. I am unsure of how to fix this. 

Yeah, the fact that it doesn't work automatically is inconvenient.  Look in the Sound Settings dialog, under the Outputs tab.  If the HDMI isn't there, reboot the machine and check again.

---

### Post by Kedster on 2012-09-10
As in with hdmi connected?

---

### Post by newb85 on 2012-09-10
Yes.  I don't think the HDMI output will be listed if it's not connected.

---

### Post by Kedster on 2012-09-10
This seems to have worked, at least for this boot up, but this will be semi annoying to have to boot with hdmi plugged in to get audio.

---

### Post by newb85 on 2012-09-10
You're right.  There has to be a way to refresh the list without rebooting.

---

### Post by newb85 on 2012-09-10
Found the answer at [this other thread]("http://http://ubuntuforums.org/showthread.php?t=1974473&page=2").

```
$ pulseaudio --kill
```

Pulse Audio will restart automatically, and the list will refresh.

---

### Post by Kedster on 2012-09-11
Thank you guys very much, for now this is a lot of help. I hope that 12.10 wokrs out of the box tho. thanks have a great week

---


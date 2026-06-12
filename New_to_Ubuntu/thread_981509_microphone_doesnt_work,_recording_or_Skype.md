---
title: "microphone doesnt work, recording or Skype"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by jmcgovern on 2008-11-13
hi,

Been having some problems with sound.  Specifically, am unable to use the microphone in my Altec Lansing headset.  I can hear just fine out of the earpieces but the microphone will not record sound in any way.   I also cannot be heard in Skype either.

Here are my system specs.

[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=desktops&a1=Brand&v1=HP+Pavilion+Slimline&series_name=s3600t_series](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=desktops&a1=Brand&v1=HP+Pavilion+Slimline&series_name=s3600t_series)

---

### Post by starcannon on 2008-11-13
In skype, on every one of my computers, I have to:

[LIST=1]
[*]Open Options Menu
[*]Open Sound Devices sub-menu
[*]Change each drop down from Default device(defualt) to the first item under it on the list, usually  device 0; the format is something like"SOMEDEVICE Some-chipset (hw:Some-chipset,0)
[*]Press "Test Sound" if that works then press Test Call, if you can hear yourself in the test call play back, your set.
[/LIST]
GL and keep it fun.

---

### Post by jmcgovern on 2008-11-13
I tried every single option there and none of them play back, some of them wont even complete the call.  Also just using SOund recorder doesnt work.

---

### Post by GoManVanGogh on 2008-11-13
I'm having a similar problem. Was fine under 8.04. Sound works, but I can't record or use the mike. Skype immediatly goes to PROBLEM WITH AUDIO PLAYBACK as soon as I hit a call button.

More like no microphone is present.

---

### Post by jmcgovern on 2008-11-14
I can get Skype to make a test call with some settings but it never plays back my voice.  Audio recording just doesnt play back, period.

---

### Post by starcannon on 2008-11-14
On a few systems I've dealt with I've had to go into System>Preferences>Sound and set everything to Alsa, and choose my sound device from the bottom most drop down menu.

Outside of that you may have to go as far as uninstalling Pulse Audio; I've never had to do that, but I've read that some people have.

GL Keep us posted on how your coming along.

---

### Post by GoManVanGogh on 2008-11-14
Are we all using GNOME? In another thread on the forum, I found that some people had to us the terminal to open the Gnome sound preferences panel. I did that, and found that the microphone had been turned off. 

I'm not jumping for joy, because turning it back on didn't make anything work. The sound panel from the menu items is not the same as the gnome sound preferences panel. I think that may control the other.

---

### Post by jmcgovern on 2008-11-14
> **GoManVanGogh said:**
> Are we all using GNOME? In another thread on the forum, I found that some people had to us the terminal to open the Gnome sound preferences panel. I did that, and found that the microphone had been turned off. 

I'm not jumping for joy, because turning it back on didn't make anything work. The sound panel from the menu items is not the same as the gnome sound preferences panel. I think that may control the other.

GMVG,

I am indeed using GNOME.  Didn't know about the separate control panel.  what terminal command do i use to access that? maybe that will work.  It'll at least be another place that the microphone is turned on.....

---

### Post by GoManVanGogh on 2008-11-16
> **jmcgovern said:**
> GMVG,

I am indeed using GNOME.  Didn't know about the separate control panel.  what terminal command do i use to access that? maybe that will work.  It'll at least be another place that the microphone is turned on.....

Execute the following command: gnome-volume-control

I've made some progress - have been able to get the sound recorder to recognize the microphone. So it's not totally broken. I found the RTFM principle (Read the Manual, Sir!) to be helpful. [www.gnome.org](www.gnome.org) has a good set of docs. [http://library.gnome.org/users/gnome-volume-control/stable/gnome-volume-control-getting-started.html.en](http://library.gnome.org/users/gnome-volume-control/stable/gnome-volume-control-getting-started.html.en) is about the volume control.

I note that the Ubuntu 8.10 upgrade seems to have the very latest GNOME desktop - the release notes say that it has "improvements" in sound and audio for internet conferencing. 

Best of luck! Now to see if Skype works.

---

### Post by GoManVanGogh on 2008-11-17
More Tweaks needed in Skype - Success

OK, I've now got Skype working. There's nothing intuitive. 

Go to Skype Options. It will let you make test sounds. You will see a drop down for sound in and out. From other reading it was suggested that I try setting it to PULSE for both. That did not work, but using PULSE on Sound Out got me some headway with the test call.

I went down my option list, and the setting that worked for me (an older Intel motherboard for sound, yours will likely be different) was Intel 82801 DB-ICH4 (hw:I8201DBICH4,0). Durned if I know what that means, but I have been able to not only hear the nice British lady's voice, but my own voice back at proper levels. 

YMMV, of course :guitar:

---

### Post by feimotion334 on 2008-11-17
what is the fastest way to make 1mil in runescape....[http://www.coolrunescape.com/](http://www.coolrunescape.com/)i am currently making 5k bow string which will get me about 500k but i don't know what to do after that.if u would like to look at my skills look at the highscores! plz help me.........!!!!!!!!!!![Runescape](http://www.coolrunescape.com/index.html)[Runescape gold](http://www.coolrunescape.com)Well.. around 3-4 years ago when i heard about runescape from a friend i decided to go check it out, i created 'Chavforlife' lol, you may laugh but it's true, i have no idea what made me think of that name, but yeah.. [runescape powerleveling](http://www.coolrunescape.com/runescapepowerleveling.html)But anyway, since then i've only used this account but now it's got to the stage i actually really regret making this name in the first place, everyday my name get's commented by random player's, some "nice" comments suprisingly and some just pure hate which i understand ;p. But like with this name i'm forever getting judged, flamed when they have never actually spoken to me but meh.[runescape cheats](http://www.coolrunescape.com/runescape-cheats.html)What about you guy's, any of you regret making your runescape account name?[http://www.maplemsmesos.com](http://www.maplemsmesos.com)   other game gold selling [http://www.coolrunescape.com/vgolds](http://www.coolrunescape.com/vgolds)

---

### Post by Pat T on 2009-06-22
I have been trying to get the microphone to work. I even bought a new headset! But still no luck. I am on jaunty jackaloupe. I have tried all the suggestions already in this forum.

---


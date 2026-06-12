---
title: "HowTo: get USB speaker buttons working"
date: 2006-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by haiku99 on 2006-09-10
first off, most of this info was adapted from LadyDoors excellent post on multimedia keyboard buttons in this thread [http://ubuntuforums.org/showthread.php?t=237408](http://ubuntuforums.org/showthread.php?t=237408)
I don't know much, but her post enabled me to get my Logitech V20 speaker buttons to work, and AFAIK others would have similar buttons...

the track control buttons are easy to set up, just go to **system>preferences>keyboard shortcuts**, select the desired action (i.e. skip to next track, etc.) and press the corresponding button on the speaker. While there you need to remove the links (by pressing backspace) for volume up, volume down, and mute, these were set up to control the main sound card which is disabled when the USB speakers are plugged in....these buttons need to be reprogrammed to control PCM levels and mute instead.

Next step is to get the keycodes for the volume and mute keys by running **xev** in a terminal window (xev was already installed on my machine running Dapper)  and pressing the keys.  In my case the codes were as follows:
[B]keycode 174 = LowerVolume
keycode 176 = RaiseVolume
keycode 160 = Mute[/B]
from what I've read these are standard, so you might get away with skipping this step....if it doesn't work out you can go back later and get the correct codes.

you now need to add these these codes to the xmodmap file (xmodmap was also already installed by default on my machine)
in a terminal window type       **nano -w .Xmodmap**
and at the end of the file paste the following text:

[B]keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 160 = XF86AudioMute[/B]

or whatever your keycodes are
type cntrl-O to save followed by enter, then cntrl-X to exit the editor

running xbindkeys is next, and this was NOT installed, but I corrected this by entering    **sudo aptitude install xbindkeys**   in the terminal window.
then enter    **xbindkeys --defaults > .xbindkeysrc**
and edit this file by typing       **nano -w .xbindkeysrc**
at the end of this file paste the following lines

[B]"amixer sset PCM 5-"
  XF86AudioLowerVolume
"amixer sset PCM 5+"
  XF86AudioRaiseVolume
"amixer set PCM toggle"
  XF86AudioMute[/B]

ctrl-O and enter to save, ctrl-x to exit as before.
these settings will cause a single button push to vary the volume setting by 5dB, this value worked well for me after some experimentation, but others might prefer someting different, like 3dB, 8dB, etc...
now load **xbindkeys **by typing it in the terminal window and all the buttons should work.  To have xbindkeys load automaticaly at boot, go to 
**System -> Preferences -> Sessions -> Startup Programs** and add it...

---

### Post by groggyboy on 2006-11-12
thanks for the howto!
finally, i can use all the functions of my logitech v20 speakers...

---

### Post by orawax on 2007-03-29
> **haiku99 said:**
> 
now load **xbindkeys **by typing it in the terminal window and all the buttons should work.  To have xbindkeys load automaticaly at boot, go to 
**System -> Preferences -> Sessions -> Startup Programs** and add it...

Thanks! But I just don't get it: This works perfectly for the user account I first configured it, but for the second account it doesn't. I added xbindkeys to startup programs, and it asks whether to load the module, I answer yes... but no luck. Strange. Any suggestions?

EDIT: It appeared that xbindkeys loads quite right... for some reason, though, .xbindkeysrc kept changing back to default/example file, didn't keep the lines I added. But now it seems to be working all right.

---


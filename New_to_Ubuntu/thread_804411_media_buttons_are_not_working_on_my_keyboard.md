---
title: "media buttons are not working on my keyboard"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by koba101 on 2008-05-23
Hi,

I used to be able to turn the volume up and down from my keyboard itself.  However right now, it seems that i can't do that.  I mean when i turn the volume up and down i see a control appearing on the screen showing the volume going up and down, but it doesn't affect the real volume.

Can someone help me out with this?

---

### Post by Technoviking on 2008-05-23
What type of keyboard is it?

---

### Post by koba101 on 2008-05-23
acer///it used to work fine

---

### Post by PinkFloyd102489 on 2008-05-23
I have the same problem, no idea how to fix it either. I have a Saitek Eclipse if it helps.

---

### Post by HotShotDJ on 2008-05-23
> **koba101 said:**
> I mean when i turn the volume up and down i see a control appearing on the screen showing the volume going up and down, but it doesn't affect the real volume.Ok.  This means that the keyboard mapping is just fine.  The problem lies elsewhere.

I need you to make sure that you have a Volume Control on either your top or bottom panel.  If it is not there, please add it by right clicking on any empty portion of the panel, choosing "Add to Panel" and then selecting "Volume Control" then click on "Add"

Once this is done, right click on the panel icon and select "Open Volume Control."  Verify PCM setting.  Adjust as required.  If this does not help, then click on "File" inside the Volume Control dialog and select "change device" -- make sure to write down which device is currently selected, and then start experimenting with other selections.  Please report back your findings.

---

### Post by PinkFloyd102489 on 2008-05-23
Another addition, using your suggestions. Mine's coming over the ALSA PCM like it should and I have the same problem described, volume is shown changing but isnt actually changed.

---

### Post by HotShotDJ on 2008-05-23
> **PinkFloyd102489 said:**
> Another addition, using your suggestions. Mine's coming over the ALSA PCM like it should and I have the same problem described, volume is shown changing but isnt actually changed.Does adjusting the Master slider in Volume Control have any effect?  What does the "File --> Change Device" pop up menu look like?

---

### Post by koba101 on 2008-05-24
the control is right there...do you think this is a drive problem?

---

### Post by koba101 on 2008-05-25
ok now it works...i bought a USB headset and it started working for both...i don't konw though...i just set the playback to alsa (Was on autodetect) in the sound menu

if someone has an explanation please feel free to let me know

---

### Post by markbuntu on 2008-05-25
You need to set your System/Preferences/Sound to alsa. Automatic does not seem to work or it prefers pulseaudio which is what I suspect. I just set all my sound preferences in all my sound programs to alsa and set my default alsa sound card with

asoundconf-gtk 

which is a tiny little program to set your default sound card for alsa that lives in the System/Preferences menu.

It is very handy if you have more than one sound card.

If you have programs that use xmms2 or oss or pulseaudio be sure to get the alsa plug-ins.

---

### Post by enduser000 on 2009-03-13
I've had this problem twice.  The first time I was messing with skype and it's settings and when I used the keyboard keys it wouldn't actually turn the sound down.  To fix that one I just reinstalled.

Recently, I hooked this up to a 42 inch tv, after figuring out how to get the sound out of that I was pretty happy, but then the buttons wouldn't turn it down.  Not wanting to reinstall again, I looked at forums, finally, I went into system > preferences > sound. On the bottom where it says  "Default Mixer Tracks" there is only one thing for me, "Master".  This was highlighted, I unhighlighted it by ctrl+clicking on it and now it works.  Can't tell you why, but I hope this helps someone.

enduser

---


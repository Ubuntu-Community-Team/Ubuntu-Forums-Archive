---
title: "screen problems"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-05-21
I just installed Kubuntu to my parents computer and I installed it with the wrong screen width configurations because they don't know them and neither do I. Is there anyway of fixing this without reinstalling? If so how? Also, how might I go about finding the screen demintions?

---

### Post by shifty_powers on 2008-05-21
well, what is the model/make of the monitor?

---

### Post by perillux on 2008-05-21
It should autodetect the screen settings.  But you can try this:
**sudo dpkg-reconfigure xserver-xorg**

also, I'm assuming you mean screen dimensions as in resolution, and not physical dimensions.  If you do mean physical then the above command should work, just read it carefully because you have to select something so it will allow you to input that.

if you mean resolution, then you can define resolutions inside you xorg.conf file:
**sudo gedit /etc/X11/xorg.conf**
locate *Section "Screen"*
to give you an idea, here's what mine looks like:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "640x400" "640x480" "800x500" "800x600" "1024x640" "1024x768" "1280x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "640x400" "640x480" "800x500" "800x600" "1024x640" "1024x768" "1280x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "640x400" "640x480" "800x500" "800x600" "1024x640" "1024x768" "1280x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "640x400" "640x480" "800x500" "800x600" "1024x640" "1024x768" "1280x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "640x400" "640x480" "800x500" "800x600" "1024x640" "1024x768" "1280x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "640x400" "640x480" "800x500" "800x600" "1024x640" "1024x768" "1280x768" "1280x800"
	EndSubSection
EndSection
```

Don't change your Identifier, monitor, or Device.  And the Default Depth should be 24.
NOTE: if you don't have any of those, or if you have extra ones, just leave it that way.
The only things you should change are the **Modes** lines.  There is one for each screen depth.  You really only need the one that has Depth 24.  NOTE: *Depth 24* is 32-bit.
But you can do all of them just to be safe, I did :)

So ya, just delete all my modes and add your own resolutions that you would like to be available to you.  I don't know if it's required to go in order from smallest to largest, but just do it anyway to be safe.

does that help you at all, or am I way off?

---


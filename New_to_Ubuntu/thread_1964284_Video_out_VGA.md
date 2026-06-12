---
title: "Video out VGA"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by Cosa1 on 2012-04-23
Hi,

When I connect my laptop to my TV using a VGA cable it only supports the display in 4:3 mode and I want the 16:9 ratio. Can't tell why it's doing this. Any help would be appreciated.

---

### Post by audiomick on 2012-04-23
Hallo.
I think you will get better help if you supply more details. What sort of TV, what graphics card, which Ubuntu version, stuff like that.

First thing, though: are you sure the TV is capable of displaying 16:9 ?

Oh, and welcome to the forum. ;)

---

### Post by grahammechanical on 2012-04-23
Have you tried System Settings>Displays - Detect Displays? That will not work if you are using a proprietary video driver? Are you?

Regards.

---

### Post by Cosa1 on 2012-04-24
Thanks for replying so quickly guys.

I'm using an HP-mini 210 netbook with Ubuntu 11.10 and Intel® IGD x86/MMX/SSE2 graphics card.

I originally had windows on this laptop and when using that operating system to display on my TV, it was fine, providing full resolution and the correct ratio. I've got a 32" Sony HD TV so all the capabilities are there.

I've tried the detect display setting on a few occasions and it has made no change.

Thanks for any help

---

### Post by audiomick on 2012-04-24
I can't look to confirm this on this machine which is using nVidia drivers, but can't you choose a resolution in the Display Settings utility?

---

### Post by Cosa1 on 2012-04-24
The displays utility allows the selection of two resolutions only, 1024x768 (4:3) and 800x600 (4:3)

---

### Post by Docaltmed on 2012-04-24
Make sure the "mirror displays" box (in System Settings > Displays) is *not* checked.

---

### Post by Cosa1 on 2012-04-24
It's not although, interestingly, when it is, my laptop screen changes from 16:9 to 4:3 in line with the display on my tv.

---

### Post by audiomick on 2012-04-24
Sounds like it is considering the TV to be the primary display. Is there a setting for that? There is on the nVidia-settings thing. :-k

---

### Post by Cosa1 on 2012-04-24
It is no less than glorious that I can ask stupid questions on here because it is the beginners forum.

nVidia settings? I haven't seen anything to do with nVidia on my Ubuntu set up. Can't find anything of that nature. I totally identify with it being the primary monitor, all new windows open in the TV section.

Ich sehe, dass Sie einen Australien in Deutschland sind. Sprechen Sie Deutsch oder?

---

### Post by audiomick on 2012-04-24
> **Cosa1 said:**
> 
Ich sehe, dass Sie einen Australien in Deutschland sind. Sprechen Sie Deutsch oder?
Jahwohl, und nicht so schlecht, nach 16 Jahren. ;) Aber wir sollten hier bei Englisch bleiben.

Don't worry about nVidia-settings. It is the equivalent to the display settings utility that you use if you have an nVidia card and are using the nVidia proprietary drivers. It doesn't apply to you; you have Intel graphics, so you wont have nVidia stuff installed.

I know nVidia-settings better than the standard thing, as I have been using nVidia drivers for years, and practically never have had to use the standard utility. I only mentioned it sort of like thinking aloud, the logic being that if the one utility has a particular setting, another utility for more or less the same purpose should have it too.

---

### Post by Cosa1 on 2012-04-24
Ja beneide ich Sie. Kein Problem.

Ah ok, well the standard display settings are extremely limited in what they provide in terms of options. It's been quite frustrating watching stretched people.

---

### Post by audiomick on 2012-04-24
Here, have a look at this

[http://askubuntu.com/questions/107085/how-to-set-resolutions-with-xrandr-using-multiple-monitors]("http://askubuntu.com/questions/107085/how-to-set-resolutions-with-xrandr-using-multiple-monitors")

And also the link to the blog post on there

[http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/]("http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/")


The bloke whose blog that is, bodhizazen, is a moderator here.

I think this is the way you need to go to sort out your problem.

---

### Post by Cosa1 on 2012-04-24
Yeh I had a good look at that blog page. It seems that the modes required to make the screen 16:9 aren't supported. I've searched through the settings on my TV and found that the screen was set to stretch. I've turned it to normal, so I'm now getting a standard 4:3 with black bars on either side, instead of the stretched 4:3 I was previously getting. The availability of resolutions was very restricted on xrandr

---

### Post by Cosa1 on 2012-04-24
I tried to force the 16:9 mode on the external display by mirror displays but I got this error:

could not assign CRTCs to outputs:
Trying modes for CRTC 64
CRTC 64: trying mode 1024x600@60Hz with output at 1024x600@60Hz (pass 0)
    none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)

CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 1024x600@60Hz with output at 1024x600@60Hz (pass 1)
    none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)

CRTC 64: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)
Trying modes for CRTC 63
CRTC 63: trying mode 1024x600@60Hz with output at 1024x600@60Hz (pass 0)
    CRTC 63 cannot drive output LVDS1
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 0)
CRTC 63: trying mode 1024x600@60Hz with output at 1024x600@60Hz (pass 1)
    CRTC 63 cannot drive output LVDS1
CRTC 63: trying mode 800x600@60Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1024x600@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1024x600@60Hz (pass 1)

---

### Post by audiomick on 2012-04-24
Hmm, that is beyond me, I'm afraid. I reckon you should be able to write a new modeline for it, but I don't know how, sorry. I hope someone else who has a better idea has a look here.

---

### Post by Cosa1 on 2012-04-25
Danke Ihnen fur Ihre Zeit, Mick.

---


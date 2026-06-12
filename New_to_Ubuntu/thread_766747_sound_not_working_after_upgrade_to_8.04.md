---
title: "sound not working after upgrade to 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by adi116 on 2008-04-25
my sound is really really messed up! i just upgraded to hardy heron, and the sound has really poor quality coming for either the internal speaker or the headphones of my laptop. there's lots of background noise, and it's very difficult to make out the lyrics of a song because of all the white noise. it's similar to when you turn up a car audio system really loud and the audio gets distorted.

---

### Post by joshsmith on 2008-04-25
try turning the volume down

go into the full volume control enable all of the channels, and mute all except the one you want to hear (for example if you have the line in as unmuted, but that is just static, this could cause the sound)

is there background sound when there is nothing else playing

try turning the volume of everything down, and your speakers volume up. this can help with clipping (which is probably what you mean by distorting) where you are maxing out your soundcard

:)

---

### Post by TheZergcorp on 2008-04-25
I'm having the exact same problem after upgrading last night, I'm not quite sure how to go about fixing it. I've tried adjusting every sound option both in the regular sound applet and the sound preferences option, but nothing helps. All sound from my computer, no matter if it's loaded from the web or local audio tracks, comes out painfully static-loaded and indecipherable. The Gmail chat noises were even distorted beyond recognition.

I have no idea how to fix this, does anyone have any ideas? I don't see any drivers or anything in the package manager that have been removed that might be the source of the issue, either. :confused:

---

### Post by TheZergcorp on 2008-04-25
Knock on wood, but I believe I've found a way to fix this problem.

My roommate, who also had sound issues with Gusty previously had to download GNOME Alsa Mixer in order to play sound normally. I did this as well, and it seems to have straightened out my issue with the tinny gross distorting of my sound. The Alsa mixer can be found using the package manager or with add/remove apps. I hope this helps others with this same problem.

Anyone more Ubuntu-knowledgeable have any idea why this would fix the sound issue?

---

### Post by dldeskins on 2008-04-28
> **TheZergcorp said:**
> Knock on wood, but I believe I've found a way to fix this problem.

My roommate, who also had sound issues with Gusty previously had to download GNOME Alsa Mixer in order to play sound normally. I did this as well, and it seems to have straightened out my issue with the tinny gross distorting of my sound. The Alsa mixer can be found using the package manager or with add/remove apps. I hope this helps others with this same problem.

Anyone more Ubuntu-knowledgeable have any idea why this would fix the sound issue?

I too had to install Alsa Gnome mixer after upgrading to 8.04.  Thanks guys.

---


---
title: "sound won't work"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by pecosaville on 2008-06-28
I just switched to Ubuntu as my operating system and I can't get sound to work.  Video plays just fine.  When I try to test sound playback in sound preferences, I get this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

When the computer first turns on, or when I try to add volume control to the toolbar, I get this message:

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

and asks me to delete it.

---

### Post by LuisGMarine on 2008-06-29
Let me be the first one to welcome you to the Ubuntuforums! :lolflag:

Anyhow, back to your problem.  So you got sound problems?  No problem, I'll be here to help you fix your problem.  So just hang in there and I'll try to guide you with a top notch explanation of how to go about fixing your sound.

First things first, we on the forums need to see what sound card you have.  This is going to help us understand your hardware and how to properly make it work in Ubuntu.

Go ahead and open up a terminal window by going to 

**Applications > Accessories > Terminal**

Once the terminal is running, copy and paste this command into the terminal pressing *<enter>* after you paste it:

```
sudo lshw -C multimedia
```

Once this is done it's going to spit all your information about your multimedia hardware.  In there we should be able to find an entry for your sound card.  

So go ahead and copy all the info that it gave you and paste it back here on a reply.

-xkill

---


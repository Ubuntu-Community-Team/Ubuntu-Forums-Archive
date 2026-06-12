---
title: "Crackly/Static-y audio"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-18
Okay, so, by fooling around on my own, I seem to have gotten the audio to work on Cheese. However, the audio is very crackly/static-y ... 

I am not sure if this is the program, or the mic that I am using. It was the only one they had at WalMart for $9. Of course its in one of those plastic cases that you have to mangle to open, so therefore I'd imagine non-returnable. 

My point is, if there is a way to determine if this is an issue with the program itself, or my system, I'd like to know. This way I can avoid buying yet another piece of equipment that doesn't work!

So far very few have been willing to help with this problem. Can someone show  me a little "community spirit" here and help out? I'm getting very very frustrated. 

The particulars:

- Ubuntu 8.1 on a 64 bit system.

- Logitech Quickcam deluxe (video feed works just fine)

- cheapo no-name microphone.

- camera works fine on ekiga, but I don't use ekiga so I don't know about sound.

---

### Post by django0909 on 2008-06-18
The first thing to ask would be is the sound output from any other program crackly?

---

### Post by OKnotOK on 2008-06-19
> **django0909 said:**
> The first thing to ask would be is the sound output from any other program crackly?

Such as? Not that I know of, no. 

Also, if I speak directly into the microphone, it sounds crackly on the speakers. 

I'm almost sure its the mic.

---

### Post by OKnotOK on 2008-06-19
Okay, so I borrowed a Logitech usb mic/headset combo, and plugged the cheapie Walmart mic into its adapter. It sounds just fine in audacity. But audacity is not the program I wish to use, it does me absolutely no bit of good -- since I'm trying to make a webcam recording. 

Help me someone PLEASE?

---

### Post by markbuntu on 2008-06-19
Doesn't your camera have a built in microphone?

I got the microphone for mine working by using the USB section of the mixer. I use the gnome-alsamixer which is just a gnome front end to alsamixer. You could also try changing the capture section of Sys../Pref../Sound to usb audio which is where the camera's microphone lives. I leave mine in alsa and it works just fine.

---

### Post by OKnotOK on 2008-06-19
Tried that. 

Here is a video of the "Crackly" audio...

[http://launchpadlibrarian.net/15444818/SoundBug.ogg](http://launchpadlibrarian.net/15444818/SoundBug.ogg)

---


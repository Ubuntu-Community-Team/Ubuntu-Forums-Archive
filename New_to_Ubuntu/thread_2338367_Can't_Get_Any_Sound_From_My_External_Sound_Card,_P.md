---
title: "Can't Get Any Sound From My External Sound Card, Please Help!"
date: 2016-09-27
forum: New to Ubuntu
---

### Post by oskarlothe on 2016-09-27
Hi, I'm completely new to Ubuntu and Linux in general, so I think I might need an easy explanation. I just installed Ubuntu, but there are no sound coming from my speakers when listening to music on YouTube. I really wonder why. I have an external sound card (Focusrite Scarlett 2i2), and two main speakers (KRK Rokit 6) and one subwoofer (KRK 10s). Anyone know what I should do?? :(

---

### Post by Geoffrey_Arndt on 2016-09-27
Some links here:
[URL="http://askubuntu.com/questions/508989/audio-interface-how-to-use-it-as-a-sound-card"]
[http://askubuntu.com/questions/508989/audio-interface-how-to-use-it-as-a-sound-card](http://askubuntu.com/questions/508989/audio-interface-how-to-use-it-as-a-sound-card)

[http://wiki.linuxaudio.org/hw/focusrite_scarlett](http://wiki.linuxaudio.org/hw/focusrite_scarlett)
[/URL]

---

### Post by Bucky Ball on 2016-09-28
Welcome. Open Pulse Audio Volume Control. Install it if not already installed. Do you see the Focusrite there? Play a clip from Youtube and check out the 'Playback' and 'Output' tabs in PAVControl. Check the device the audio stream is using. Is it the Focusrite or the internal soundcard (or headphone socket)?

You might also want to check the 'Configuration' tab and see if you have the Focusrite available there. With the Focusrite in and on, please open a terminal and run this command:

```
sudo lshw -C sound
```

Post the output here (between code tags, see the green link in the first line of my signature at bottom of this post). Hopefully you will see your Focusrite in there. You also don't mention the release and flavour of Ubuntu you are using. Please, always include this info when posting for info. Thanks. :)

* Also, if you are using this card only and don't intend to use the internal sound at all, boot to the BIOS and *switch off the internal sound card*. This will prevent confusion, take the internal card out of the equation altogether and you will know any changes you make and any sound you hear are down to the Focusrite.

---


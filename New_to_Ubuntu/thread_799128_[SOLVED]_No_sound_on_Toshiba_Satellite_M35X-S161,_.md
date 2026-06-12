---
title: "[SOLVED] No sound on Toshiba Satellite M35X-S161, fresh install of 8.04"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-18
I just did a fresh install of 8.04 but I don't have any sound on this laptop.  I'm not exactly sure how to troubleshoot this problem.  What should I do first?

---

### Post by wolfen69 on 2008-05-18
good luck. intel sound can be very tricky. [HERE]("https://help.ubuntu.com/community/HdaIntelSoundHowto") is a how-to. i'm far from a noob, but this problem is one of the only things i couldnt get working. (on others machines)

---

### Post by barney385 on 2008-05-18
Same here. I think mine is a real-tek though...7.10gg.

What's the terminal command to find out exactly our cards are?

Thank for starting this thread BTW...

---

### Post by diablo75 on 2008-05-19
Well, I've formated and installed Windows with some space left over for Ubuntu.  The soundcard that's in this (according to device manager) is a Realtek AC97.  How might I get that to work in Ubuntu?

---

### Post by diablo75 on 2008-05-19
I'm starting to think there's a problem with the laptop itself and not Ubuntu.  Windows is seemingly unable to produce sound as well, even though the drivers are correctly installed and show no conflicts.  I'm going to have to dig into this a little deeper...

---

### Post by diablo75 on 2008-05-19
I got the sound to work in Windows....

[IMG]http://forums.techguy.org/attachments/132136d1211241724/volume.jpg[/IMG]

Now let's see if it works in Ubuntu.....

IT WORKS NOW!

This kind of problem reminds me of the time a friend suddenly lost his Wifi connection.  Turns out he had accidentally disabled it via the BIOS using a Function Keyboard shortcut.

---

### Post by sudipta_cht on 2008-06-01
> **barney385 said:**
> Same here. I think mine is a real-tek though...7.10gg.

What's the terminal command to find out exactly our cards are?

Thank for starting this thread BTW...

From here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

>     *

      First you must find which model of sound card you use, so run this command:

cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260. 

---


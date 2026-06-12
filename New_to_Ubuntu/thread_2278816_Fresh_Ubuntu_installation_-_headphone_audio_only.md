---
title: "Fresh Ubuntu installation - headphone audio only"
date: 2015-05-19
forum: New to Ubuntu
---

### Post by Matthew_Williams on 2015-05-19
Hi All,

I took the plunge and installed Ubuntu for the first and everything appears to be working except for one thing.
If my Headphones are connect to the computer sound will only come through them and not from the speakers, if i disconnect them the speakers will start working.

When i go into sound settings both the headphones and the speakers appear seperatly , however sound test done via either option comes through the headphones.

I tested Linux mint and found the same result in there, thinking it is possibly the motherboard but not sure (dual booting with windows 8.1) .

Computer is a desktop, running cpu i5 4590 with 8GB of RAM, 120GB SSD , asrock mobo(can get model number if needed) .

Ive seen various threads about this issue previously but there seem to be lots of possible solutions (with a lot of replies saying they didnt work).

Any thoughts?

windows 8.1 audio is working normally .

also, headphones are not USB connected

---

### Post by leunam12 on 2015-05-19
That is how it works for me and that is how I expect it to work. That is also how it works on my Windows computer at work.

---

### Post by sammiev on 2015-05-19
Hi,

I would expect that to happen. When the headphones are plugged in, the sound should only be from the headphones.

When the headphones are unplugged, sound should be from the speakers.

---

### Post by RobGoss on 2015-05-19
I don't  believe that's  how it works, when never you plug a head set in to your computer it will play what ever sounds through your headset and you won't  be able to hear anything from your speaker.

---

### Post by Matthew_Williams on 2015-05-19
So there is no way to toggle between the two audio devices? in my windows set up I have the option to swap back and forward between the two devices without disconnecting the headphones.

Im a little confused by the responses that say this is how it worked for them in Windows as well.

---

### Post by Vladlenin5000 on 2015-05-19
It's mostly driver dependent and yes, most of times that's exactly what happens irrespective of the OS. Some hardware can behave differently in Windows than it does in Linux.

---

### Post by Geoffrey_Arndt on 2015-05-19
Hmm, I guess I've never had hardware that has that switch feature . . . (Lenovo H410 is current windows machine).   Or perhaps am not aware of that capability.

Wonder how Blue Tooth headphones affect switching between sound output?

---

### Post by leunam12 on 2015-05-20
> **Matthew_Williams said:**
> So there is no way to toggle between the two audio devices? in my windows set up I have the option to swap back and forward between the two devices without disconnecting the headphones.

Im a little confused by the responses that say this is how it worked for them in Windows as well.
Most devices that output audio work this way (stereos, radios, cellphones, laptops, etc.) when you plug the headphones in the speakers go mute. My guess is that that feature in your computer (being able to switch devices without disconnecting the headphones) is a particular feature of that particular sound card and the manufacturer provides the driver functionality exclusively for Windows. I don't know if there is a workaround for Linux.

---

### Post by Vladlenin5000 on 2015-05-20
Correct.

However, I've seen it happen at least in one desktop (Gigabyte board) where indeed the audio output would change to speaker with the headphones still connected. Again, it's a driver feature, some have it, some don't, and some can do that easily in both OS while some do it only in one OS.

---

### Post by Matthew_Williams on 2015-05-21
hmm, slightly frustrating, i must admit i have taken it for granted as its worked that work on all windows and OSX computers ive used, never really thought about if it was a driver feature or not. hopefully there is some program for linux that can emulate it.
thanks all for the responses!

---


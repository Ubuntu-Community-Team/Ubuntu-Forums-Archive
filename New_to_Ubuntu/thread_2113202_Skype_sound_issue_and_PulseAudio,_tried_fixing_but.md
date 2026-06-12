---
title: "Skype sound issue and PulseAudio, tried fixing but caused more issues"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by Californian Raccoons on 2013-02-06
Okay so to start off, I'm in that "New to Linux and no idea what I'm doing" crew. I'm far from the most intelligent person, I've never had a good grasp at how computers work, what codes go where, etc etc... I can do Internet, and I can use Skype... and that's it



So naturally I'm hitting more than a few issues using Ubuntu 12.04 64-bit on dual boot (tried Windows 8, liked it but didn't like it)

Well the first thing I did was install Skype of course, went to the site and it took me to the Software Center and so on. Upon starting Skype the first thing I notice is that there's no sound, like, whatsoever

No notification sounds, no login/log off sounds... and as well as that, I couldn't make or answer calls. Tried the Echo/Sound test, all it did was close 3 seconds later. I did some extensive Googling but found no fix

Well, after installing the latest Ubuntu software updates, it's fixed itself!... sort of. I do have Skype sounds now, but they're extremely distorted, and interfering with other program sounds

But I'm not here to figure out how to disabled them... well, I am... I tried doing that using [Skype's recommended fix]("https://support.skype.com/en/faq/FA10964/can-i-change-the-sound-system-used-by-skype-for-linux#disable_pulse")... it worked but it worked too well, all it did was kill all my sounds on my computer, *completely*

So yeah, disabling PulseAudio clearly wasn't the fix, after a little panicking and restarting the laptop, I took to Google and found that entering **"pulseaudio -D"** into the Terminal was the solution to reversing *(did it reverse?)* Skype's apparent "fix" 

Quick summary; I've encountered that oh-so common Skype Ubuntu sound issue, [similar to this actually]("http://ubuntuforums.org/showthread.php?t=2071981&highlight=Ubuntu+SKype+distortion"). Tried fixing it only to find that it fixed itself through the Software updates, but *now* I'm encountering the apparently common distortion issue 

I've muted Skype's sounds in the Sound Settings but Skype is still interfering with other program's sounds. It distorts Turpial's notification sounds, it distorts the sound on YouTube videos... it's driving me a little insane, considering I haven't a clue how to fix it, and considering that I was under the impression that I had already fixed it (several times)


-If possible, how do I get Skype's sounds back without distortion? Having looked at Skype's sounds settings in Options>Sound Devices, they're all automatically set to "PulseAudio server (local)". It wont allow me to change or edit the settings in Skype, which is why I just went and muted Skype in the Sound Settings

-Above all... all I want to do is use other programs like Turpial without all this violent distortion whenever a Skype message comes through. If it's impossible to bring back Skype's sounds without distortion... how do I do this and prevent it from distorting other programs?

Any help would be greatly appreciated, very greatly

---

### Post by Thee on 2013-02-06
Are you using the latest version of Skype? (4.1)
Did you try to disable "Allow Skype to automatically adjust my mixer settings" in Options > Sound Devices. That works for some people.
Also what sound card are you using?

---

### Post by Californian Raccoons on 2013-02-07
> **Thee said:**
> Are you using the latest version of Skype? (4.1)
Did you try to disable "Allow Skype to automatically adjust my mixer settings" in Options > Sound Devices. That works for some people.
Also what sound card are you using?
4.1.0.20

I did make an attempt at disabling that setting (I think it auto-disabled it) but it's done nothing 

I've no idea how to find the soundcard on Ubuntu

---

### Post by Thee on 2013-02-08
Type this into a terminal to see audio hardware list, and post it here.

```
sudo aplay -l
```

Also check this thread, it might help:
[http://ubuntuforums.org/showthread.php?t=2071981](http://ubuntuforums.org/showthread.php?t=2071981)

---


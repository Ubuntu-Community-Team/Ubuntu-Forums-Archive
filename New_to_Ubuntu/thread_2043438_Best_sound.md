---
title: "Best sound?"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by asmith2306 on 2012-08-16
Hi,

this isn't a problem but just looking for direction.  Is there any way to get audio effects programs on ubuntu for your soundcard?  I just switched from Windows 7 and it had a Realtek program that let you equalise, add bass to your sound, etc.  Is there anything like this I can get on Ubuntu?

ps. how do I even check what sound card I have on Ubuntu??!  

Thanks,
Alan

---

### Post by kc1di on 2012-08-16
> **asmith2306 said:**
> Hi,

this isn't a problem but just looking for direction.  Is there any way to get audio effects programs on ubuntu for your soundcard?  I just switched from Windows 7 and it had a Realtek program that let you equalise, add bass to your sound, etc.  Is there anything like this I can get on Ubuntu?

ps. how do I even check what sound card I have on Ubuntu??!  

Thanks,
Alan
Hi Alan
welcome to Ubuntu and the forums.

I use Audacity for most of my sound needs but their are many other sound card programs available also. 

to see which card you have type the following command in in a terminal ```
lspci
``` it will give you a list of all pci devices on your machine.  the sound card will be listed under audio devices: 

Audacity is available in the software center.

you may also want to look at this [web page]("http://www.iloveubuntu.net/easy-guide-ubuntu-1204s-audio-world")for a good article on ubuntu sound options.
Good Luck
Dave

---

### Post by ajgreeny on 2012-08-16
Many of the music players, eg vlc, audacious, rhythmbox (a plugin), have their own equaliser, some of which work better than others, so check out your player as well.

I think I have also read about a full system equaliser as well, but have no info on that.

---

### Post by Frogs Hair on 2012-08-16
This still works for 12.04 . [http://askubuntu.com/questions/72679/is-there-any-sound-enhancers-equalizer](http://askubuntu.com/questions/72679/is-there-any-sound-enhancers-equalizer)

---

### Post by asmith2306 on 2012-08-21
> **Frogs Hair said:**
> This still works for 12.04 . [http://askubuntu.com/questions/72679/is-there-any-sound-enhancers-equalizer](http://askubuntu.com/questions/72679/is-there-any-sound-enhancers-equalizer)

It does, but it significantly reduces the volume from your speakers when its enabled :-( any idea why?

---

### Post by Frogs Hair on 2012-08-21
> **asmith2306 said:**
> It does, but it significantly reduces the volume from your speakers when its enabled :-( any idea why?

No, I have been using this EQ since 9.10 with the opposite result . I have modified the rock setting to reduce the bass. You have to play with the presets in the drop-down menu to find what works best. You can create your own presets also and I use rock as my starting point. Be sure to apply the setting and check the volume levels in the applications in use also.

---


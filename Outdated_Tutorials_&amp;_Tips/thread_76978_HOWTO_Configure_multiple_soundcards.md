---
title: "HOWTO: Configure multiple soundcards"
date: 2005-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by CAE on 2005-10-16
I have no idea if there will even be useful for anyone else, but I've had this problem a couple of times, so if anything, this post will act as posterity for me. ;)

I've got two "soundcards" in my system, one of which I can't disable for various reasons. Device 0 is the onboard sound, which I do not use and cannot disable. Device 1 is a PCI soundcard which I do use.

KDE has an advantage over Gnome through aRts. A unified sound system is a pretty awesome thing and means we have to do slightly less configuring than our Gnome brothers. So, firstly, let's set that up properly. I'll just describe the clicking you have to do...

K Menu > System Settings > Sound & Multimedia > Sound System > Hardware (tab)

Here we have the option to override device location, and this is what we want. Now, on my system, because the PCI card is the "non-default" sound device it's device 1. Thus I check 'Override device location' and enter the following:

```
hw:1,0
```

Of course, if you have more than 2 soundcards, adjust the first number appropriately. Hit 'Apply' and you're done for aRts! That wasn't too hard, was it? 

Alas, not all applications use aRts, such as amaroK, so we're going to have to deal with this. amaroK is pretty cool in that it allows you to override the device location, exactly the same as you did above, however not all apps will allow you to do this, such as Kaffeine. 

There are two ways around this. The first is to install gstreamer0.8-arts, which will attempt pipe all gstreamer output through aRts, which would be awesome if the implementation wasn't buggy. **Disclaimer: I'm going on reports it's buggy, I've never actually tried it myself because I find the following method easier!**

Our other option is to ensure that ALSA, which is the default output for gstreamer, knows which device to send output to. This is a really simple method and only requires the editing of one configuration file. Simply edit /etc/asound.conf (it'll probably be created) to reflect a new default soundcard. So, that'd be:

```
sudo kwrite /etc/asound.conf
```

And enter the following:

```
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}
```

Again, you'll have to change that 'card 1' to reflect the card you want to be default. Save the file, and you're done. Now, I'm slightly embarassed to admit that I don't know how to restart ALSA, since the init.d script is apparently deprecated. If anyone knows, let me know and I'll edit it in. ;)

Anyway, once ALSA has been restarted by whatever method, you'll be able to hear sounds through any application!

I hope this HOWTO helps someone. Let me know if you think I've missed something.

---

### Post by GameManK on 2005-10-19
aRts outputs to ALSA, or at least that's what you should have it set to, so if you do the second part of the howto (change alsa to output to your sound card) you dont have to change it for aRts (the first part of the howto)

[QUOTE=CAE]Now, I'm slightly embarassed to admit that I don't know how to restart ALSA, since the init.d script is apparently deprecated. If anyone knows, let me know and I'll edit it in. ;)[/QUOTE]

the init.d script still works:
sudo /etc/init.d/alsa restart

you can also restart it in the aRts settings by changing something. I do it by using the box to change the output to alsa (which it's already set to, but clicking it makes KDE think you changed it) and hitting apply.

---

### Post by binarysleeper on 2005-12-30
I would just like to say thanks for your posting. I tried putting all sorts of things into the "Device Location" box. Hair tearing ended. Cheers.

---

### Post by jadugarr on 2006-04-02
I know this is an old thread, but I have a related question.

I have an chaintech av710 and sb audigy installed, w/ the av710 set to default.  I use the av710 only for the high-res wolfson DAC out to my amp and headphones while listening to music.

I would like to be able to switch my sound to the audigy, which is hooked up to my speakers, for doing everything else.

Right now I have my lineout of the av710 connected to the audigy which allows the sound output on both cards, but this is a poor solution for games and other applications, because the av710 only allows 1 sound output at a time.

---

### Post by PixelCloud on 2006-08-27
how do you do this in dapper drake?

i've bene ******* around for a while and i havent figured out how to do it yet

i basically dont want to use my onboard soundcard and use my pci one

---


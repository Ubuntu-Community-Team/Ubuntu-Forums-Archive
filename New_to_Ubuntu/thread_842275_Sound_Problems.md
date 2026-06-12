---
title: "Sound Problems"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by will_s54 on 2008-06-27
Not major but maybe I am missing something. Mr X-fi card wont work on Ubuntu and it doesnt even see it. So to get sound I went into Bios and enabled the onboard sound (Azalia ) and as soon as I booted into Ubuntu it worked ( impressive). The thing is the audio when turned up to max is low ( using headphones ). Anyway to increase volume ? Also how do I access the mixer so I can increase bass setting ?

btw: will keep an eye on [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)  and when good drivers are available will give them ago

---

### Post by nothingspecial on 2008-06-27
If you`re using Gutsy 7.10 type

```
alsamixer
```

into the terminal and check nothing is muted. Navigate the channels with the arrow keys and unmute using 'm'.

I believe Hardy uses pulse audio which I am not familiar with.

---

### Post by kansasnoob on 2008-06-27
I can't help you on the X-fi card, but if using alsamixer doesn't solve your problem w/Azalia I'd try installing gnome-alsamixer from synaptic.

It'll then show up in the menu Sound & Video > Gnome Alsa Mixer. Pay special attention to the 3 toggles furthest left and the 4 toggles furthest right on the gui.

[ATTACH]75474[/ATTACH]

[ATTACH]75475[/ATTACH]

---

### Post by will_s54 on 2008-06-28
> **kansasnoob said:**
> I can't help you on the X-fi card, but if using alsamixer doesn't solve your problem w/Azalia I'd try installing gnome-alsamixer from synaptic.

It'll then show up in the menu Sound & Video > Gnome Alsa Mixer. Pay special attention to the 3 toggles furthest left and the 4 toggles furthest right on the gui.

[ATTACH]75474[/ATTACH]

[ATTACH]75475[/ATTACH]
I have solved my problem. Have speakers that have dual input and have digital in for Vista and your normal stereo for Ubuntu ( just a matter of pressing a button on my speaker control unit to switch ). This is great as it suits my dual boot system to the ground .

Now am definitely after a mixer that has bass/treble settings for use with my speakers.

[http://packages.ubuntu.com/hardy/gnome-alsamixer](http://packages.ubuntu.com/hardy/gnome-alsamixer) lists a few different downloads. I assume that i386 ( I have intel duo core) is the one I should install ?

last edit...solved Amarok does what I want  :-)

---


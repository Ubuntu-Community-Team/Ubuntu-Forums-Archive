---
title: "HDMI audio card vs the native sound card"
date: 2015-01-16
forum: New to Ubuntu
---

### Post by mark_edwards2 on 2015-01-16
hello all - first time posting -

i installed the latest lubuntu and was very impressed.  unfortunately, i could not find a way to get the chrome-flash browser to play over the hdmi sound.   getting the vlc-media-player was fairly easy once i selected

htmid:CARD=NVida,DEV=1(HDS NVidea, HDMI 0 HDMI Audio Output)

i could switch between the hdmi and the native one easy enough with VLC, but not with the chrome-flash browser.

out of desperation, i installed the regular latest ubuntu instead because there is an easy sound setting right there to toggle between the two sound cards.   

is there a way in libuntu to have this option to toggle between the sound cards?   or should i investigate what it would take to install this ubuntu card option in libuntu?

thank you all !

---

### Post by DuckHook on 2015-01-16
Hi mark_edwards2.

Welcome to Lubuntu and the forums.

If you right click the volume button on the task bar, it should present an option called *"Volume Control" Settings*. Clicking on it should bring up *alsamixer.* This app isn't pretty because it is based on an *ncurses* command-line interface, but it gets the job done. Pressing <F6> should allow you to select sound card. What you will need to select will depend on your video card but it will be something like "HDMI" or "HDMI / DisplayPort *n*" or "S/PDIF".

---

### Post by mark_edwards2 on 2015-01-17
hi duckhook - yes i tried alsamixer right away but the HDMI option was not listed.  i saw something like nVidea1 and nVidea2 but nothing to do with HDMI.  i am tempted to just stick with regular ubuntu since it does everything i need it to right out of the box, but there is something pretty cool about using lubuntu instead.

oddly enough, one of the native audio-players let me select either the sound-card built into the motherboard or the sound-card on the HDMI card.

i am wondering aloud if its possible to install this regular-ubuntu sound option on libuntu, or if there is another way, WITHOUT getting into installing linux-drivers!

---

### Post by Bhavin_Prajapati on 2015-01-17
I had a similar problem, I stream some of my audio via bluetooth to my stereo system but I also have a analogue audio connection to some basic speakers on my desk. The stereo is only when I play music. When I would play music, it would sometimes just switch to the analogue without warning, then I would have to reset it back to the bluetooth. I had a strange fix, I just unplug the stereo jack when I want to play music and it works 100% of the time, it doesn't switch to the analogue. Part of me is happy, but the other half of me is going... why is it doing this? I think the problem was that my bluetooth adapter was connected on the usb hub in the monitor and it may have not have been getting the sufficient power so I connected it to the computer directly. Either way, it works now when I want it to. I just thought I share that. 

Does Ubuntu also have alsamixer?

---

### Post by mark_edwards2 on 2015-01-17
ubuntu alsamixer - i never bothered to look since ubuntu did just what i wanted it to.  i suspect if alsamixer is not there that its a very easy install, but that is just a pure guess.  but again, i would much rather use lubuntu instead.   i would like to think there is an easy way to get the ubuntu sound-GUI option on lubuntu.

---

### Post by DuckHook on 2015-01-17
> **mark_edwards2 said:**
> ...i tried alsamixer right away but the HDMI option was not listed.  i saw something like nVidea1 and nVidea2 but nothing to do with HDMI.One of those nVidia options is likely exactly the one you want. Give them both a try. I suspect that these are the descriptions that your card uses for its HDMI interfaces.> i am tempted to just stick with regular ubuntu since it does everything i need it to right out of the box, but there is something pretty cool about using lubuntu instead.I use everything under the sun, depending on the situation. I tinker with old boxes a lot and just love how light and efficient Lubuntu is. But my main box runs Ubuntu and I have secondary machines scattered elsewhere in the house that run Xubuntu. Really old laptops are running SliTaz and Tiny Core. Others are running Bodhi and CrunchBang. One of the best beauties of Linux? Run whatever you want. Run one inside of another in a VM if you like. Can't help you much choosing between them because they are very much a matter of personal preference and specific usage needs.> ...oddly enough, one of the native audio-players let me select either the sound-card built into the motherboard or the sound-card on the HDMI card.Yes, some apps give you finer grain control. Others try to avoid confusing complexity by allowing only the system default. Try selecting the nVidia option in *alsamixer* above to set a different system default.> ...i am wondering aloud if its possible to install this regular-ubuntu sound option on libuntu, or if there is another way, WITHOUT getting into installing linux-drivers!It is not only possible but relatively easy. However I would strongly recommend against it. You do so by going to synaptic, or just using apt and install the specific package by name. This is how you can install just about anything from the repositories. Except in your case, in order to install that one little applet, it would end up dragging in all of *Gnome* and most of *Unity*, effectively turning your install into a "hybrid" of Lubuntu and Ubuntu. Since the whole point and purpose of using Lubuntu is to stay lean and mean, it is awfully counterproductive (and I would find it aesthetically offensive, but that's just me) to bloat up the OS for the sake of a little applet.

But Linux is also about choice. If you really want to go there, I can help you look into it.

---

### Post by DuckHook on 2015-01-17
> **Bhavin_Prajapati said:**
> Does Ubuntu also have alsamixer?Yes it does. Just open a terminal and do:```
alsamixer
```However, for general users, it isn't necessary. The "Sound Settings" applet does pretty much the same thing. In fact, it's not much more than a GUI for alsamixer and pulseaudio. Lubuntu does not ship with a pretty GUI because it is trying to be lean.

---

### Post by mark_edwards2 on 2015-01-19
hey duckHook - here is what i am seeing (booted on the thumbdrive without doing an install, but the view is the same)

1) alsamixer when first started up:

[IMG]http://edwardsmark.com/images/lubuntu/alsa-1.png[/IMG]

2) F6 Pressed and selecting the second option:

[IMG]http://edwardsmark.com/images/lubuntu/alsa-2.png[/IMG]

3) what displays when the second option is selected:

[IMG]http://edwardsmark.com/images/lubuntu/alsa-3.png[/IMG]

i cant really do anything here to make any sound-card changes.

> [COLOR=#000000]I use everything under the sun, depending on the situation.[/COLOR]

Lubuntu will (hopefully) be used to replace win-7 on a media-computer.  the 'puter is a little old for win-7 and i want to use lubuntu for the most lightweight alternative.  also, there is something just plain _**sexy **_about using lubuntu over regular ubuntu although i cant really explain why.

ubuntu/lubuntu also seem to have the most brain-dead easy chrome-browser installs of all the linux distros.

for my old(er) micro-dell i started running [http://chromixium.org/](http://chromixium.org/) and love it (notice that's not the chromium which is not very well maintained but this one is: [http://chromium.arnoldthebat.co.uk/](http://chromium.arnoldthebat.co.uk/)).     the really old OLD dell gets puppy-linux, while the webserver gets centOS.

but what is obviously the most important factor here is to ensure that every 'puter is running a different non-M$ OS.

---

### Post by DuckHook on 2015-01-19
Your nVidia card likely has two HDMI outputs. This is why you have two choices when selecting <F6> (on your screen 2). Many times Linux systems will start numbering from '0' (zero), so if the second output doesn't work for you, try selecting the first one. HDA NVidia stands for "High Definition Audio" and is the audio component of HDMI. One of these two should work. A good clue is what your initial post showed:> htmid:CARD=NVida,DEV=1(HDS NVidea, [COLOR=#00ffff]HDMI 0[/COLOR] HDMI Audio Output)...note the output that I've highlighted in cyan, pointing to the "0" (zero) output.

Given your polyglot collection of OSes, you are clearly not a "new user"! Good for you. A fellow explorer on the shores of the Linux ocean.

I agree with you about Lubuntu. What a lot of people don't like about it&#8213;it's plain plebian looks&#8213;is exactly what I find charming about it. Sorta brings me back to the days when more focus was put on function over form. But that's just you and me. One of the wonderful things about Linux is the choice it gives people of all stripes and shapes.

---

### Post by mark_edwards2 on 2015-01-19
hello duckHook - before i forget to say,  THANK YOU for helping me !

i tried all the alsamixer settings and none of them produced HDMI sound, all the sound kept going out the native sound-card.   however, this one worked:


[IMG]http://edwardsmark.com/images/lubuntu/new.png[/IMG]


i am still hoping that i can get a simple sound-control just like regular ubuntu has. 

this particular media-server is dedicated to everything the **spice-girls** ever did, both video and audio.  i believe we can all agree the world was never quite the same after Ginger Spice left the greatest music group in history.

also, for those of us who slept through high-school vocabulary,  here is the definition of [Polyglot]("http://en.wikipedia.org/wiki/Polyglotism") (no its not something the skin-doctor removed) and here is the definition of [plebian]("http://www.merriam-webster.com/dictionary/plebeian")

---

### Post by DuckHook on 2015-01-19
> **mark_edwards2 said:**
> ...for those of us who slept through high-school vocabulary,  here is the definition of [Polyglot]("http://en.wikipedia.org/wiki/Polyglotism") (no its not something the skin-doctor removed) and here is the definition of [plebian]("http://www.merriam-webster.com/dictionary/plebeian")...oh gawd :redface: caught out using big words again... sorry, sorry, sorry.

<sigh> Sometimes, I forget to turn off the bubble machine.

So happy things worked out for you. And you solved it all on your lonesome too, so no contribution from me actually.

Good luck and Happy Lubuntuing!

---

### Post by trag on 2015-01-20
[COLOR=#4B4B4B][FONT=Arial]HDMI audio output is disabled by default. To enable it you need to pass the nvidia.audio=1 option to the kernel at boot.[/FONT][/COLOR]
[COLOR=#4B4B4B][FONT=Arial]To do so:[/FONT][/COLOR]

[LIST=1]
[*]Edit /etc/default/grub and add radeon.audio=1 to the GRUB_CMDLINE_LINUX line, it should look like: GRUB_CMDLINE_LINUX="... radeon.audio=1 rhgb quiet"

[*]Update grub's config: $ sudo grub2-mkconfig -o /boot/grub2/grub.cfg

[*]Reboot.
[/LIST]
[COLOR=#4B4B4B][FONT=Arial]I also recommend you install pulseaudio control and set it up through that
good luck
Tragic[/FONT][/COLOR]

---

### Post by mark_edwards2 on 2015-01-20
hello all - i have installed pulseaudio as previously suggested.  from everything i can see, it "appears" that lubuntu thinks its putting sound out over the hdmi sound-card as the following pictures will hopefully illustrate.  but once again, no hdmi sound, at least not from firefox or chrome.

did i understand from trag's last comment that i can do all this through pulseaudio?  or is the edit of the grub boot file still required?

again, any suggestions are very appreciated!



[IMG]http://edwardsmark.com/images/lubuntu/2015-01-21-013256_1920x1080_scrot.png[/IMG]
]]


[IMG]http://edwardsmark.com/images/lubuntu/2015-01-21-012428_1920x1080_scrot.png[/IMG]


i would think the use of "simultaneous output" would have fixed it  - notice the sound meter shows sound going out:


[IMG]http://edwardsmark.com/images/lubuntu/2015-01-21-013446_1920x1080_scrot.png[/IMG]

---

### Post by mark_edwards2 on 2015-01-20
duplicate post - sorry !

---

### Post by mark_edwards2 on 2015-01-20
duplicate post - sorry

---

### Post by DuckHook on 2015-01-21
> **mark_edwards2 said:**
> ...or is the edit of the grub boot file still required?Editing of GRUB may still be required. It doesn't hurt and can always be reversed.

---


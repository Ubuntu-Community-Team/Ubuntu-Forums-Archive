---
title: "HOWTO: Get your microphone to work"
date: 2007-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Cappy on 2007-03-16
[SIZE="2"]**I wrote this when I was new to Ubuntu. Most of the time people are having microphone problems it is from driver problems and not just the sound settings as described in this guide. I'm leaving the guide up because it contains some potentially useful information for a small minority of newcomers.**[/SIZE]

A big thanks to *pppoe_dude* who initially helped me get my microphone working on IRC when I didn't know what I was doing.

> 
If you have a problem then say what steps you tried and what didn't work about it. For instance, you should make your post as specific as possible: "I tried enabling all of the check boxes in the preferences but after I raised the volume and turned the "Capture on" for the "Capture Control" I still don't have my mic working!". Without such information it is impossible to diagnose anything. Finally, you can attach a screenshot if you're confused (Alt+PrintScreen).


This Guide is specifically for Ubuntu (GNOME).

_Overall Objective_: Explain how to enable and configure the microphone capture for a sound card.

_Specific Objective_: Enable hidden sound channels, raise the volume and enable the capture for them, and test the microphone. 
If all else fails, use alsamixer (console) to select which channels to capture from.
Finally, "Common Fixes" are listed at the bottom.



Before you do this, you'll want to make sure your **_Sound Capture_** in **System-->Preferences-->Sound** is set to **ALSA** (or OSS if you know ALSA doesn't work for some reason).


Goto your Volume Control
[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide3.png[/IMG]

Goto **Edit-->Preferences** inside the volume control and check every check box.
(The controls you need to enable may be named something such as "Microphone", "Mix Capture", "Capture", or "Front Mic". If you are unsure then just enable everything.)
(For instance, if you hear yourself echoing when you have a playback control called "Analog Mix" enabled, the control that needs to be enabled will be named something like "Analog Mix Capture" or "Analog Mix Mic".)
[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide4.png[/IMG]

Now, click on the **Capture** tab and you should see a few (or a lot!) of controls here. Make sure every control on the Capture tab doesn't have an 
"X" on the microphone icon. Now, raise the volume of each control to maximum.
 
[Sidenote: On one of my sound cards I have the PCM's Capture (the microphone icon) turned off because that Captures (records) anything that
 is playing on my speakers.]

My Audigy 4 Non-Pro's Capture settings:
[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide5.png[/IMG]

My nForce2 sound card's Capture settings:
[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide6.png[/IMG]

Now, on the **Switches** tab you'll want to make sure "Mic Boost (+20dB)" and "Microphone Capture" are checked (if you have them).

My Audigy 4 Switches Tab:
[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide7.png[/IMG]

My nForce2 Switches Tab:
[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide8.png[/IMG]

Hopefully, now your microphone works! You can test your settings by running 
```
vumeter -r &
```
 on the shell. You should see vumeter light up while you tap on the microphone (I recommend tapping in case there is a temporary problem with the capture volume being too low). If you change your sound settings correctly, you should immediately be able to see your microphone activity on the vumeter (without restarting vumeter, that is).





Finally, if you are still having problems, your capture may be set on the wrong channels.

[http://www.ubuntuforums.org/showthread.php?t=255071#10](http://www.ubuntuforums.org/showthread.php?t=255071#10)
[Quote=danielph]Run ```
alsamixer
``` in console.. Go into the playback "tab" and mute mic. Go into the capture tab, I think f4 and hit space on Mic and space on capture until **L R Capture** is red under both Mic and Capture. make sure you turn up the volume using the up arrows.[/Quote]



Here are screenshots from **alsamixer** for each of my soundcards.

[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide9.png[/IMG]


[IMG]http://www.boundlesssupremacy.com/Cappy/soundguide/soundguide10.png[/IMG]

List of other common fixes:
Enable "Full Duplex" for your sound card.
Disabling "IEC958" on the capture tab.
In Volume Control, when you goto **File-->Change Device..** make sure your (Alsa mixer) is the device enabled.

If anyone has criticisms or additions to this post I'll update it.

---

### Post by snl on 2007-03-24
I only have one soundcard and alsamixer shows something similar to your second last screenshot, except that I only have line, mic and capture. How do I turn the volume under mic to full. I tried the arrow up but nothing happen.

Thanks.

---

### Post by Cappy on 2007-03-24
You control the volume on the **Capture** control, not the microphone control. Turn the L R CAPTURE on for both of those controls with the _Space Bar_.

---

### Post by snl on 2007-03-26
The volume on the Capture control is already at maximum from beginning but my microphone is still not working. My card is HDA Intel.

Please advise.
Thanks.

---

### Post by Cappy on 2007-05-18
*bump*

---

### Post by brigit on 2007-05-19
none of the above worked for me, but  I changed from ubuntu to kubuntu, at first the mic still wasn't working, then I used automatrix and all the problems with the mic and sound were gone!
I don't know if it was to do with the codex s or what. On ubuntu I hadn't installed them yet, so I don't know. I just thought it might help some one.

---

### Post by Cappy on 2007-06-03
> **brigit said:**
> none of the above worked for me, but  I changed from ubuntu to kubuntu, at first the mic still wasn't working, then I used automatrix and all the problems with the mic and sound were gone!
I don't know if it was to do with the codex s or what. On ubuntu I hadn't installed them yet, so I don't know. I just thought it might help some one.

If you had problems with sound also then it would be a completely different problem. It is possible you were missing some kind of library and automatix installed it while installing other things.

---

### Post by asafm on 2007-09-01
Hi,

I tried exactly what this guide said:

1. I made sure that on the recording tab (which contains microhphone only),  the Capture slider is at it's max, and the microphone icon is not with red x.
2. On the switches tab, I checked: 
       Microphone Capture, microphone boost, iec958 capture, Analog to iec958 output.

Why can't  I still get the mic to work?

---

### Post by plamen_todoroff on 2007-09-14
My first post, after reading 17646823787364 ones about mic not working, here is what i did after trial and error to get my mic working (also the crashing of sound recorder stopped :). Right click sound icon in tray > open volume control > edit > preferences > checkmark all what is there > close. At the playback tab microphone should be UNMUTED. At the capture tab, CAPTURE should be UNMUTED, both "columns". At the switches tab, THE CULPRIT SEEMED TO BE "IEC958 CAPTURE", UNCHECK IT!, check microphone capture, micboost, iec958 (the clear one), duplicate front and external amplifier. At the options tab mic select > mic1. Close everything. Applications > Sound & Video > Sound Recorder, record from input: microphone (worked with capture for me, too). HIt record, say alphabet, hit stop. To not crash the sound recorder don't hit the toolbar save icon, use file > save as, and finally play button. Hope this will work for you too.

---

### Post by dgermann on 2007-09-24
Hi Cappy and all--

Sure hope you can help me get this working.

I have 6.06, with an HDA intel card, ALSA mixer is selected. I have checked my microphone (external) on another computer, and it works there. System >preferences > sound is set to enable ESD; play system sounds. System beep is enabled, but not visual system beep.

gnome-volume-control has all these things in playback, all enabled and set to highest level: PCM, front, front mic, surround, center, lfe, line-in, cd, microphone, pc speaker. (I have no blue plug on the front for the microphone--only on the back. Yup, it is plugged in!) There are no other options.

Under the capture tab, both capture and capture 1 are enabled and at full volume. There are no other options.

Under the switches tab, headphone is checked. There are no other options.

Under the options tab, the only options are Channel Mode (set to 2 ch); input source (set to Mic) and a second input source (also set to Mic).

Under preferences the selected tracks are all that are available: headphone, pcm, front, front mic, surround, center, lfe, line-in cd, microphone, pc speaker, capture, capture 1, channel mode, input source, input source.

When I run vumeter -r & I get two bars: the top one has one green bar that flashes, the bottom one has one bar lit continually, and the second flashes a little less often than the top one. It does not react to talking into the microphone.

Sound Recorder records no sound.

I am wondering: is it possible that I need to install some software to make this work? Seems to me I needed to do so on my Feisty laptop yesterday....

Other ideas? How should I trouble-shoot this?

Thanks for your help!

---

### Post by qubodup on 2007-10-01
I have the Realtek ALC655 rev 0 (NVidia nForce2) and mic is not working. If I connect the normal audio output to my amplifier, or whatever the big fat device is called that connects all input and output sound and video stuff, then I can hear the mic, but my computer doesn't (volume meter does not notice) I use spdf though.

I followed your advice and used OSS instead of ALSA but it didn't help (did I have to restart something?)

Well it did help... read on..

The strange thing is: If I record sound in, for example, **Sweep** it gets catched (the 'main device') is "plughw:0,0" and i see no other config options. I can't play the recorded sound back, but save it as a file and then hear it with another app (vlc for example)

I also can record with Sound Recorder, but not play back..

---

### Post by Chriswaterguy on 2007-11-15
Thanks! I think it's working. (I don't know how to test my microphone on my desktop, but I tried a Skype test call, and heard a garbled version of my voice, which is what I should probably expect, being on a very unreliable connection in Jakarta).

What I can't understand is that under Capture (apparently Recording in Ubuntu 7.10) the microphone is switched off by default. That was the only problem I had. Why on earth would this be the case? Makes life very hard for newbies. I put off looking into this for several weeks as I've been flat out with work, and now I find itwas just switched off by default, I feel really exasperated. 

Now there may be a good reason for having things set up this way, but there really should be something (default tutorial linked from the download site, or even better a tutorial or text file which opens on startup) which tells the user some key things like this that they really need to check. Having to find this kind of essential information by searching the forums makes no sense (but many thanks to those who provide the information!)

---

### Post by Lifeisabug on 2007-12-23
Hi,
i tried this tutorial and now i dont have any sound at all :(
i followed the steps as good as possible as some options just werent available. when i ran vumeter -r i got an error message which told me to run the command esd in console. to do that i had to install the package pulseaudio-esound-compat which i did.
Im not sure where my sound actually stopped working. I removed the installed package again and tried pretty much any settings in the Volume Controle but i cant figure out what the default was :( The vumeter reacts on microphone input now and when i push up the volume for my mic i can hear some noise on my earphones. Also when i restart mu computer i can hear the sound for the login manager but as soon as i login the sound is gone. I tried to create a new user but there i dont have sound either.
Im pretty desperate because i need the sound very bad. Im about to rinstall the whole operating system which would take a lot of time though.

---

### Post by dnvikram on 2007-12-23
I have gutsy installed on my Inspiron 1420N and having issues with the microphone.Enabled all that stuff in alsamixer and still the same problem,microphone not working.Checked some dell linux resources and they seem to say that they are aware of this issue/bug ,working on it and no workaround or a fix as of now.So,is there no way I can get this working?Its really important I get this fixed as I have only gutsy on my laptop and I need to use skype and ekiga for voip.

Any help or suggestions appreciated.

Thanks.

---

### Post by empty_spaces on 2007-12-24
Check out my thread below. I was having some mic and sound issues, but was able to solve them by upgrading alsa version 1.0.14 to 1.0.15

[http://ubuntuforums.org/showthread.php?t=637285](http://ubuntuforums.org/showthread.php?t=637285)

Hope this helps.

---

### Post by steevc on 2007-12-25
I've been trying to get microphone (or any input) recording working for a while. I've got an Asus nVidia board that I believe has the Intel sound chips. Sound out works fine. This is a pain for Skype, but even more annoying as I would love to do some music recording with something like Jokosher.

I see various comments about upgrading Alsa to 1.0.15. Is this going to be available from the repositories any time soon? I would rather get it that way is possible.

Today I discovered that I can record in Audacity, but only because that is using OSS for input with ALSA for output. I assume that this does not help me with Skype and I can't see how I can set that mix for KDE in general.

This is the sort of problem I might have expected a few years back, but with Ubuntu in 2007 I would expect it to 'Just Work'. I would hope that we will not have to wait another 4 months for a fix in the Heron.

Just had to get that off my chest. Happy Xmas/New Year etc

---

### Post by 7chaos on 2008-03-12
How come both ASLA and OSS do not work in my computer...when i set the sound to ASLA, and click the test button, it gives error message 

"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available."

when set to OSS, and click the test button, also gives error message like:

"gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Unable to open device /dev/dsp for recording: Device or resource busy"

so can anyone help me? my sound recorder does not work now and also youtube does not gives sound...

---

### Post by Grimmy on 2008-04-26
Thanks for this howto... just got my Audigy4 mic input working on Hardy using this guide.

Now Skype is working!

Cheers,
Grimmy.

---

### Post by Th3Professor on 2008-05-04
Trying to get the laptop built-in mic to work...

Manipulating "Volume Control" (multiple settings enabled and turned up) didn't seem to do anything. Not immediately at least.

Using alsamixer made the immediate difference.

On the laptop... alsa mixer "capture" has, from left to right:

Front Mic (set to 100)
Mic Boost (set to 100)
Capture (currently about 50)
Capture (currently about 50)
Digital (currently 50)
Input Source (options: mic or front mic; currently "mic")
Input Source (options: mic or front mic; currently "front mic")
(If the 2nd input source is also set to "mic" there's a high-pitch squeal.)
(If the 2nd input source is set to "front mic" there's a fuzz/distortion.)

I left vumeter -r running during the adjustments made in alsamixer.

Apparently the built-in (front panel, on Toshiba) volume "scrolling" wheel affects the microphone volume as the recording level (in vumeter) goes up or down with the scrolling wheel.

The prob right now is that there's a fuzz/distortion.

Leaving "input source" set to "mic" and the 2nd "input source" to "front mic";
the scrolling-volume (front panel of laptop) adjusts the 1st "capture" bar in alsamixer;
the 2nd "capture" bar increases/decreases the fuzz/distortion as I adjust it within alsamixer.

I try using just 1 "capture" bar, then just the other. Same with "mic" or "front mic";
it looks like both capture bars are required (???). Okay correction, maybe not...

AlsaMixer [Capture] settings appear to work with laptop built-in mic like this, from left to right:
Front Mic - 100
Mic Boost - 100
Capture (1st one) - any level (mic (input) level)
Capture (2nd one) - 0 (this is to avoid the fuzz/distortion)
Digital - 50 (probably could be 0 but leaving it here for now)
Input Source (1st one) - Mic
Input Source (2nd one) - Front Mic

Now to open up a recording app and test the laptop's mic...

Okay, maybe the recording program isn't set up right. (Trying Audacity (am new to it, so going to have to test settings.)) Nope... still no luck.

I amplified the recording and it just played back pulsed fuzz/distortion.

EDIT:
Oh boy... now my front panel volume (scrolling wheel on laptop) is apparently adjusting the mic level... but it is now having absolutely no effect on speaker volume. How do I fix this?

If I go back to the Volume Control, File>ChangeDevice> lists:
0: HDA Intel (Alsa mixer)
1: Realtek ALC268 (OSS Mixer)
2: Playback: ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
3: Capture: Monitor Source of ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)
4: Capture: ALSA PCM on front:0 (ALC268 Analog) via DMA (PulseAudio Mixer)

It's a Toshiba Satellite A205-S5855, running Ubuntu Studio (8.04).

---

### Post by Th3Professor on 2008-05-05
I'm still stuck. Any ideas?
-Mic isn't properly working.
-External (physical) volume control on laptop now adjusts mic level and not speaker level.

(Odd though, it adjusts mic level, yet I cannot record with the mic.)

I'm still hoping to get the mic working properly and to get the physical volume control back to adjusting speaker level and not mic level... not sure how.

---

### Post by cespinal on 2008-05-06
hello to all!!  first post here!! 

I have been using Hardy since yesterday on my HP dv9000 and after some classic tweaking (wireless, screen resolution, etc) I have not been able to get my microphone to work despite some heavy searching on the forums. 

see, alsamixer recognises my soundcard as HDA Nvidia. Alsamixer in this case does not have the same options that appear in this posts so I just enables and maxed out every volume control I found. 

Now, if I try to record something on the sound recorder, I would hear static but nothing else. Im posting my amixer output should it could help: 

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 78 [98%] [4.00dB] Playback [off]
  Front Right: 78 [98%] [4.00dB] Playback [off]
Simple mixer control 'External Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [off]
  Front Right: 80 [100%] [6.00dB] Playback [off]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]

I think this is my last issue before having ubuntu fully running on my pc.. PLEASE HELP!!!

---

### Post by Th3Professor on 2008-05-07
I'm in the same boat (as cespinal).

If anybody can provide some help on getting the mic to work, it'd be greatly appreciated. I, too, have gone through the various past threads in these forums on mic set-up and have tried everything mentioned in them, though still having no luck with the mic. I have the exact same results as cespinal.

---

### Post by cespinal on 2008-05-07
yup... FYI, this is how my alsamixer looks like: 

Now, if I can get to obtain he whole features, maybe I could boost up my mic and hear something... Anyone knows hoy to get alsamixer with all the features?

---

### Post by Th3Professor on 2008-05-07
> **cespinal said:**
> yup... FYI, this is how my alsamixer looks like: 

Now, if I can get to obtain he whole features, maybe I could boost up my mic and hear something... Anyone knows hoy to get alsamixer with all the features?

I'll venture a guess that there would be differences between different systems, all depending on the specific hardware of the specific computer and the actual system (like Ubuntu 7 to 8.04, and default Ubuntu vs Ubuntu Studio). I don't know if Studio makes much of a difference, though who knows.

---

### Post by cespinal on 2008-05-08
bump...i need to enable capture on alsamixer... Nothing happens if I press space on mic!

---

### Post by Th3Professor on 2008-05-09
I 2nd that bump.

---

### Post by Th3Professor on 2008-05-11
bump for some hope for some new help on mics.

---

### Post by cespinal on 2008-05-11
bump again...please :(

---

### Post by Th3Professor on 2008-05-12
bump

---

### Post by cespinal on 2008-05-13
3120383028th BUMP

---

### Post by Th3Professor on 2008-05-15
3120383029th bump

---

### Post by Aremel on 2008-05-23
I don't know if you solved this one or not, but I had the same problem with my volume control panel button controlling the mic.  I don't know how it got that way, but I was able to set it back to controlling the master volume in the Sound Preferences window.  Under Default Mixer Tracks, I changed the device to the Conexant CX20561(Hermosa)(OSS Mixer), then selected "Volume" in the space below.  The "Digital-1" option had been checked.  That corrected the problem.

I have HP dv9715 with 8.04 installed, BTW.

---

### Post by cespinal on 2008-05-23
I just gave it up trying to fix it some time ago... but I'm going to try what you suggest when I get home after work.. 

thanks for your input! I hope it helps..

---

### Post by Th3Professor on 2008-05-23
> **Aremel said:**
> I don't know if you solved this one or not, but I had the same problem with my volume control panel button controlling the mic.  I don't know how it got that way, but I was able to set it back to controlling the master volume in the Sound Preferences window.  Under Default Mixer Tracks, I changed the device to the Conexant CX20561(Hermosa)(OSS Mixer), then selected "Volume" in the space below.  The "Digital-1" option had been checked.  That corrected the problem.

I have HP dv9715 with 8.04 installed, BTW.

Yeah, that fixes the external volume control (switching back to the main speaker volume), though there's still the issue of having a working mic.

---

### Post by cespinal on 2008-05-23
yup.. that was useless for me

---

### Post by markbuntu on 2008-05-24
I used the gnome-alsa mixer and that worked for me. I had to turn on the Mic Boost, uncheck mute and rec in the microphone column and turn it all the way up. 

Even so it was a lot lower level than the other levels so I needed to turn up the volume on my stereo to hear it. (I have my computer line out into my stereo.) If you are running through an external amp this may be your problem. I only noticed a very very low thump when I first thumped the mic. If I had been listening to anything else I would not have noticed it. If you have the recording level monitor it will show up on that but very weakly unless you thump the mic. 

Your results may vary.
I was using an audio technica ATR20 low impedance cardoid microphone, probably not the best choice for this sort of thing.

---

### Post by Aremel on 2008-05-25
I don't know if this would matter, but I was looking at HP's website about my 'puter.  Interestingly it says "HP Pavilion WebCam with Integrated Microphone" as one of the features.  Could it be that somehow the mic is controlled via the webcam and that's confounding Ubuntu's attempt to locate and activate it?  I do know, however, that my webcam can be working with, say, skype and the mic still doesn't work.

Just a thought.

---

### Post by markbuntu on 2008-05-26
On my HP Pavillion an1330n Media Center the mic connector on the back of the machine used to work but doesn't now. I have to use the one on the front and use the mic boost in the mixer and turn it all the way up.

---

### Post by cespinal on 2008-05-26
Aremel could be right on that...

On the other hand, mi alsamixer wont give the mic boost options, It is just different from others I have seen in these forums.

---

### Post by Th3Professor on 2008-05-26
I have a built-in webcam and built-in mic, both, on the laptop and neither seem to have any direct correlation to the functionality of the other. They seem independent of the other. I don't think there's any need to futz around with the webcam.

As far as mic boost goes... I've boosted all of that up all the way and still nothing. At one point I received static (even at various levels, high, mid, low) and at another point I received "pulsed static". Not sure what that was all about.

---

### Post by Iehova on 2008-05-28
I'm in exactly the same boat as cespinal and Th3Professor. I just hear static.

---

### Post by visionofarun on 2008-06-26
Bump! I am on the same boat as well.

---

### Post by Th3Professor on 2008-06-26
at least 4+ people in same boat... hopefully someone will chime in.

---

### Post by cespinal on 2008-06-26
maybe 4+ people is too little?

---

### Post by Th3Professor on 2008-06-26
hopefully not... I'd hope that even 1 person would be enough.

---

### Post by Iehova on 2008-06-26
Still no microphone. :( Interestingly when I booted up a mandriva CD which uses pulseaudio by default, and I went to the alsamixer, I could set the L+R capture like so many guides suggest (although the only capture channel was something like "pulseaudio capture"). Alas this didn't resolve the problem and I still couldn't record.

Having said that, microphone is a lesser problem for me than getting suspend (or hibernate!) to work properly. ;)

---

### Post by cespinal on 2008-06-26
there's a lot of info regarding suspend/hibernate. I personally gave up hibernate after finding out my suspend worked well and the battery consumption is almost zero (I just did not know that). 

Aditionally, my hibernate button disappeared from my log out menu somehow, which is good for me since I feel my OS just gets simpler. 

Regarding mic's, maybe the kernels are a little bit outdated in comparison with the newer pcs or laptops...

---

### Post by Th3Professor on 2008-06-26
I've had probs with both hibernate and suspend... everytime I "wake" the pc after either of those I have no audio. I check the audio settings, it's all the same as before, still no audio. So it requires a reboot, which means no hibernate or suspend for me. I gotta have my audio.

cespinal: the hibernate button is no longer on your logout screen?! Weird! Can you share a screenshot?

Regarding the mic... it can't be due to an old kernel, at least for me... I'm up to date with the kernel:

2.6.24-19-generic

(I'm on ubustu/ubuntu studio... although the default kernel is rt, I prefer generic for normal computer use and only use rt when using particular "studio" applications.)

(Neither the hib/susp nor the mic issues are resolved from using rt instead of generic.)

---

### Post by alsamman on 2008-07-10
when i run vumeter -r &, it hears sound coming from the mic after I did the first method of just checking Mic boost and mic capture, but trying to get the mic working on any other program (ie, sound recorder, aMSN) is unsuccessful

---

### Post by Ms_Angel_D on 2008-07-11
Thanks for this I was wondering why my microphone didn't work turns out the volume was all the way down ;)

---

### Post by Skillachi on 2008-07-13
Well i cant get my mic to work either or hibernate for that matter (but this isnt the thread for hibernate now is it). Anyway I have tried all the above instructions... it still doesnt work. Im working on hardy heron and have a hp dv6700t laptop with all the stuff and my mic and webcam built in. When i tried the vumeter thing, it the top bar just keeps jumping but i cant hear anything at all... no echo's... nothing, but soudn coming out otherwise is fine.

---

### Post by vnieto on 2008-07-16
I have the same Mic problem, I try all the suggest but still don't work.
Some idea?

---

### Post by hallbuzz on 2008-07-16
Spent several days trying to get my mike to work finally succeeded with following settings:
1. Right click on Volume icon (Speaker sign bottom toolbar)
2. Click on Open Volume control
3. Click on Edit -> Preferences
4. Tick the following boxes:
   Master, Mono, Microphone, Microphone capture, Mic Select, Mix Mono.
With the exception of Mic Select these are the boxes I ticked in a vain attempt to get my mike to record.

 When in desperation I ticked Mic Select I was given the option of choosing either Mike 1 or 2.  I chose 2 and hey presto I was able to record using both Audacity and Sound recorder.

---

### Post by ReFuSeD88 on 2008-07-16
ehh,, this is the same as my problem! gonna try! great answers thx

---

### Post by vnieto on 2008-07-16
> **hallbuzz said:**
> Spent several days trying to get my mike to work finally succeeded with following settings:
1. Right click on Volume icon (Speaker sign bottom toolbar)
2. Click on Open Volume control
3. Click on Edit -> Preferences
4. Tick the following boxes:
   Master, Mono, Microphone, Microphone capture, Mic Select, Mix Mono.
With the exception of Mic Select these are the boxes I ticked in a vain attempt to get my mike to record.

 When in desperation I ticked Mic Select I was given the option of choosing either Mike 1 or 2.  I chose 2 and hey presto I was able to record using both Audacity and Sound recorder.

I don't understant your solution. Can You explain more?

---

### Post by cespinal on 2008-07-20
bump

---

### Post by Jescrib2 on 2008-07-23
Thanks. 
The mic on my head set works but I can not get the mic through my web cam to work. Any advice?
Thanks

---

### Post by mad_golfer on 2008-07-23
Thxs my mic work nwo !!!


- Anthony
[Found a great deal on PC Magazines]("http://www.magazinesusa.com/pc-magazine-subscription.cfm") :lolflag::guitar::):KS

---

### Post by coleyman on 2008-07-23
Well, this helped me get my mic setup and working. Actually, I'm going from my home stereo headphone out into the front mic input. Nothing was working and I read this tutorial and changed my capture settings and all and I'm using Audacity and finally got the input signal and meters working. But, when I try to play back what I recorded, I get an error message that says "Error while opening sound device. Please check the output device settings and the project sample rate." Any suggestions on this? Thanks. I'm not just a newbie, I'm a newbie that knows zilch about codes.
Jeff

---

### Post by Fibonacci on 2008-08-26
Try this:

On gnome-volume-control, under the Options tab, change V_REFOUT to 2.25V or 3.7V, whichever works best for you.
See [http://ubuntuforums.org/showthread.php?t=901164](http://ubuntuforums.org/showthread.php?t=901164)

---

### Post by cespinal on 2008-08-26
> **Fibonacci said:**
> Try this:

On gnome-volume-control, under the Options tab, change V_REFOUT to 2.25V or 3.7V, whichever works best for you.
See [http://ubuntuforums.org/showthread.php?t=901164](http://ubuntuforums.org/showthread.php?t=901164)

Thanks for the tip.. but it seems my volume control does not offer the options you are talking about. the only menu available on preferences is volume control preferences. take a look at this screenshot:

---

### Post by UKaDi on 2008-09-01
Here is how I got my Skype Mic to work both as a separate headset as well
as on my IBM T60 LapTop:
SystemSettings >> SoundSystem 2nd tab Hardware: Full duplex ticked;
Than here my KMix settings (I apologoize for the wording in German)
Important for good sound quality on second tab: left mouse click mic mute;
I hope this may help you

---

### Post by ZOOstation on 2008-09-02
First of all, big thanks to Cappy! This is the only useful microphone help on these forums. I did what you said and the mic works great.

Second of all, I didn't look through all six pages of this thread so I apologize if this issue has been addressed.

An interesting new problem arose as a result of tinkering with the volume controls, however. The volume buttons on the computer don't do anything of any value. With the volume control window open, I can see that the buttons on the keyboard (it's a laptop, that's where the speaker controls are) modify the Line-In levels on the Playback tab. However that does absolutely nothing to the sound coming out of the speakers, so even if I turn the volume completely down or on mute (again, I'm talking about using those buttons) I get the same amount of sound. If I use the sliders in the volume control window, however, I can make a difference. Altering either the Master or PCM sliders will actually change the volume of what I'm listening to.

SO, why are the volume buttons suddenly useless and how can I return them to their previously functional state?

---

### Post by -Jimaras- on 2008-09-09
Thank you very much!!! I don't know how exactly I did it but i think that it worked when I went to options and changed the Input Source to front line.I still have a playback problem when I listen to music with Amorok.Sorry about my English.

---

### Post by Liametc on 2008-09-12
IVE FINALLY GOT MY HEADSET MICROPHONE TO WORK!!!!!

ive read almost all of this thread and tbh none of it worked but it was useful.

im running ubuntu studio and here is what i did

firstly i plugged my mic and headset into the back of my computer, NOT the front, it seems to work on the back

secondly i followed the steps of going into volume control ad checking everything, BUT i left out master volume (dont know if this affected it but im not changing what works for me) the input i set to mic, and the capture volume i had to about third the way up, any louder and you get distortion. 

now this is what seemed to get it to work. on playback, set the PCM to max (as well as everything else) hey presto it worked for me, hope it works for you too:)

---

### Post by CATM on 2008-09-16
I can't figure it out for the life of me. I have tried every solution in this post and nothing seems to be working. All I get when I perform the "test" in "system-pref-sound-soundcapture-test" is a static pulsing beeping noise that could wake the dead. I have an HP Pavilion dv6000 with standard equipment. I am open to any alternative solutions. Thanks in advance and by the way, Ubuntu people are by far the most courteous and helpful people on the planet.....I have learned all I know about linux from the knowledge presented in this forum....A huge shoutout to all who contribute...Thanks a ton.

---

### Post by dzrtmn on 2008-10-12
THANK YOU! Although I have an Intel HDA internal card, your instructions enabled me to get the mic working :)

---

### Post by rutz3n on 2008-10-20
I think i got the same problem as TheProfessor and cespinal...

I already tried all sugestions on this thread and in 99999 others... It's not only a VOLUME question.... Mute, unmute....always the same silly things.

It's strange that i can "hear" the internal mic when it is on... but i can record anything neither use skype.

Any ideias? Thanks a lot.

---

### Post by biodiesel-bri on 2009-08-10
I was able to get my hda Nvidia / Conexant Venice external mic working under Kubuntu 9.04 with these gymnastics:

Left click on the volume control of kmix and choose Mixer
Under Settings -> Configure Channels select everything

I muted IEC958 and IEC958 Default PCM and using pavumeter[1] also discovered that my system thought the ext mic was the int mic, so I switched over the capture toggle to the int mic.

I had tried alsamixer as noted in previous posts, you may want to start with that first.

[1] For whatever reason I couldn't find vumeter, but I was able to install pavumeter which seems to do the same thing.  If you want to install pavumeter, do this:
```
sudo apt-get install pavumeter
```

The commands for pavumeter are slightly different, use:
```
pavumeter --record
```

---

### Post by pinkpinkpinkpanther on 2009-08-23
Hi,

I have recently installed kubuntu 9.04 on hp Elitebook 6930p laptop, a very beginer to linux.

1- My speakers work after creating file /etc/modprobe.d/options.conf 
    containing this line:
    options snd-hda-intel model=mobile   
But I cant use my skype even for a test call, it says problem with audio playback.
In settings of multimedia I can see Audio input for which I have one options: HDA Intel(AD 198x Analog) and when I select this, test button is not active! 
Please help me not to escape from linux!

Thanks in advance.

---

### Post by Iehova on 2009-09-01
Hi pinkpinkpinkpanther,

Welcome to Linux! I'm sorry to hear that you're having problems, it sounds very odd that your speakers are giving you problems, but I'm glad you sorted that. With regards the skype problem, i've had that same error on a different laptop. It may be with the problem with the version in the ubuntu repositories, you could try uninstalling it and downloading directly from the skype website (or vice-versa). I'm no expert though, you'd probably receive more help if you started a new topic (probably in the multimedia or beginners forum).

With regards the previously mentioned conexant hermosa microphone issues, i'm pleased to report that [COLOR="red"]the microphone works in the latest daily build of karmic![/COLOR] This may already be widely known in which case I apologise, but it is nonetheless great news.

---

### Post by cespinal on 2009-09-01
those are great news! but im not sure what a daily build is :( would you please clarify a little further? 
thank you!!!!!

---

### Post by Iehova on 2009-09-01
That is the very latest development version of Ubuntu Karmic (ie the next version of ubuntu). You can download it from [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) , burn it to a CD and try it out. Be warned if you install it that it's still very buggy (not released until october) and liable to break at any time. For me the microphone was also muted initially, I had to right click and open the volume control, go to the input tab and slide the volume up to the max, then it worked fine.

---

### Post by Leed on 2009-09-02
Thanks to Biodiesel for the tips on pavumeter...

I'm using the Asus T91, both built in mics don't work, when using mic boost I just get static noise. Pavumeter also shows this noise. I don't believe it's an issue with the sound controls, something must be wrong with the drivers

Volume control states that I have a HDA Intel MID

---

### Post by matricks on 2009-11-15
Just bought a laptop Packard Bell Easynote TJ61 with an internal sound card Conexant CX20561 (Hermosa) and successfully installed Ubuntu 9.10 64-bit. Only problem was that the microphone (internal and external) was not working in all applications (soundrecorder, audacity, skype etc). Output audio (eg- Rythmbox) worked fine with ALSA and PulseAudio. 
Tried a LOT of stuff, but the decisive move was to add: 
options snd-hda-intel position_fix=1 model=laptop
to the file /etc/modprobe.d/alsa-base.conf and reboot.
If hope this helps ... Another thread dealing with the Conexant chip microphone is read-only otherwise I would have posted there.

---

### Post by contrariwise on 2009-12-10
To fellow Googlers: Dear God, I spent two days fiddling with all these settings, reading every thread I could find on the subject, and I have finally found those magic words that make my mic work.

killall pulseaudio

And now it works like a peach!

---

### Post by vnieto on 2009-12-11
My mic now is working on Karmic Koala without problems

---

### Post by La cebolla on 2010-09-04
I just bought a new headset but I can't get the [COLOR=#ff0000]**microphone**[/COLOR] to work properly. The mic actually works fine, since I could record and hear my voice on a friend's computer. Now I've tried fixing settings according to the answers on several forums. Now the recording level seems to be at max but I just can't get any speech recorded. When I use Audacity for recording, I get to see the line jumping up and down whenever I'm speaking. When I listen to the recording, however, I only hear some cracking noise.

I have used the **Alsamixer**, the sound control from System->Settings->**Sounds** and the **PulseAudio** sound control. My current settings are as follows:
**Alsamixer:** Mic Boost(+20dB), Mic Front Input, Mic Select, IEC958, External Amplifier. The mute-boxes that are checked: Surround, Center, CD, Phone, Aux.  The record-boxes that are checked: Mic, Capture. The sliders are on top position where mute isn't checked.
**Sounds:** On the second tab I have chosen Analog Stereo Duplex. On the Recording-tab  I have set the recording to max and selected Analog Microphone / Microphone 1.
**PulseAudio:** On the Input-tab (the 4th tab) both the left and the right front are set to 150%. On the output-tab (the 3rd tab) Port is selected to be Analog Output (LFE) / Amplifier.

My computer currently runs on the Lucid Lynx (10.04). The system's language isn't set to English, so please do forgive any translation errors I may have made.

I would really appreciate if someone could solve this problem.

---

### Post by Iehova on 2010-09-04
Hi La cebolla,

I don't really know anything about anything, but if you go to the sound preferences menu (click on the volume icon then sound preferences - i guess it's the same as system>preferences>sound) and go to the input tab you should see an input volume and an input level. Does the input level show movement when you make sounds into the microphone? Do you have a choice of device for sound input?

If you get a response in the sound preferences then maybe for the time being forget about audacity and open sound and video>sound recorder. Record from capture as CD, lossy and see if that works. There is also a level meter at the bottom that should show movement when you're making sound.

If that works then presumably your Audacity settings aren't right.

---

### Post by La cebolla on 2010-09-04
Thank's for the tips. The input level meters do move when I speak. I tried every single file type on sound recorder and all the possible devices from the sound preferences menu. I thought I had already done it but I must have thought wrong. 

At first I found out that speech, lossy (.spx) could catch something. The background noise was still tremendous. Then I changed the device from Analog Microphone / Microphone 1 to Analog Microphone / Microphone 2. Now every file type records alright. Audacity records ok, too.

Thank you very much, Iehova.

---

### Post by Pictor on 2010-09-08
I still can't get my microphone to work :(

I have used the Upgrade ALSA Script to get the audio work on Ubuntu.
But the Audio Input microphone cannot be used.

In Audio Preferences (right click on the volume icon), under the tab "Input" I justa have "Analog Internal Audio Speaker" but nothing move the Input Level (I don't know if it's the Front Mic or the main Laptop Mic).


None of the above suggestons helped me. Only KMix show me the Front Mic, the Boost Mic, ..... but the volumes are disabled (not settable).

My notebook is a Sony VAIO VPCS12C5E.
Audio devices:
- Intel [HDA Intel], dispositivo 0: ALC275 Analog [ALC275 Analog]
- NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]


Somebody has something to say?

---

### Post by neu5eeCh on 2010-11-08
> Somebody has something to say? 	

Yes.

Give up.

I keep checking in, every now and then to see if there have been any new developments on Linux and microphones, but with all the other challenges confronting linux, the community seems to have written off the microphone. If you have a computer on which they work, lucky you. If not, give it up or set aside lots of time.

---

### Post by peredur on 2011-01-30
> **Iehova said:**
> Hi La cebolla,

I don't really know anything about anything, but if you go to the sound preferences menu (click on the volume icon then sound preferences - i guess it's the same as system>preferences>sound) and go to the input tab you should see an input volume and an input level. Does the input level show movement when you make sounds into the microphone? Do you have a choice of device for sound input?


Sheesh!  Two years, on and off, I've been struggling with this and that's all it was.  The microphone was muted in the Sound Preferences.

:oops:


Peredur

---

### Post by uhurusurfa on 2011-03-07
On a Dell 1721 AMD64 - after install of Ubuntu 10.10 the external jak for the mic did not work. Afer hours of messing about it sems the answer is to install the Alsa mixer GUI front end (Ctk+ version NOT the Gnome one which did nothing at all) then make sure "Capture" buttons are reasonably high up the slider and the £Line Jack Mode" is set to "Mic"

---


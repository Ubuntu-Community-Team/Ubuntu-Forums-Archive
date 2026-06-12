---
title: "[SOLVED] Can't hear sound from Youtube or anything else"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-15
Hello,

I have been trying to make the sound on my laptop work for a while. I have the Dell XPS M1210.

I am able to here the startup and dhutdown sounds, although they are very low in volume. I ran the sound test and I am able to hear the beeps, but they are very low and difficult to hear. I used the hardwre tester as well, it passed every test except for the sound test. I can not hear anything from [www.youtube.com](www.youtube.com) Help!

Testing detected sound card:

U0x46d0x8b1


Can anyone tell me how to make the sound work?

---

### Post by eternalnewbee on 2008-10-15
Try this for youtube:
sudo apt-get install libflashsupport

---

### Post by frankleeee on 2008-10-15
> **GumpTron said:**
> Hello,

I have been trying to make the sound on my laptop work for a while. I have the Dell XPS M1210.

I am able to here the startup and dhutdown sounds, although they are very low in volume. I ran the sound test and I am able to hear the beeps, but they are very low and difficult to hear. I used the hardwre tester as well, it passed every test except for the sound test. Help!

Testing detected sound card:

U0x46d0x8b1

Can anyone tell me how to make the sound work?

You might right click on the volume icon then volume control and turn everything up and make sure nothing is muted. Also you may need to add some preferences with the right click to see if anything else is muted or turned down

---

### Post by GumpTron on 2008-10-15
> **frankleeee said:**
> You might right click on the volume icon then volume control and turn everything up and make sure nothing is muted. Also you may need to add some preferences with the right click to see if anything else is muted or turned down

all i see is Microphone. Everything is turned up and still no sound.

---

### Post by eternalnewbee on 2008-10-15
Might be a hardware problem...

---

### Post by GumpTron on 2008-10-15
> **eternalnewbee said:**
> Might be a hardware problem...

sound works fine for windows XP and I am able to hear some sound with Ubuntu. Are you sure its hardware?

---

### Post by SunnyRabbiera on 2008-10-15
> **GumpTron said:**
> sound works fine for windows XP and I am able to hear some sound with Ubuntu. Are you sure its hardware?

well please keep in mind that ubuntu isnt windows.
Anyhow I suspect this might be a pulseaudio issue, by default hardy uses pulseaudio as its sound server but sadly not everything works on it yet.
To change your sound system go up to system> preferences> sound
if all the boxes say automatic i suggest changing them to alsa by clicking those pulldown menus and selecting ALSA.

---

### Post by patrickballeux on 2008-10-15
Do you have pulseaudio installed?

Install "pavucontrol", this is the tool to control the different settings of Pulseaudio.  (There is another volume control in there...)

As for your Youtube problem, make sure that you set "Pulseaudio" as your sound server in System - Prefenreces - Sounds.


Also, Flash 10 works better than Flash 9 and does not need the libflashsupport package...

I found out that using any software that uses Alsa and it picked up by Pulseaudio is not working really well.

Make sure that you are all pulseaudio or all Alsa (remove pulseaudio for that)

My suggestion:  Switch all to pulseaudio, once properly configured, it works really well...

---

### Post by SunnyRabbiera on 2008-10-15
> **patrickballeux said:**
> Do you have pulseaudio installed?

Install "pavucontrol", this is the tool to control the different settings of Pulseaudio.  (There is another volume control in there...)

As for your Youtube problem, make sure that you set "Pulseaudio" as your sound server in System - Prefenreces - Sounds.


Also, Flash 10 works better than Flash 9 and does not need the libflashsupport package...

I found out that using any software that uses Alsa and it picked up by Pulseaudio is not working really well.

Make sure that you are all pulseaudio or all Alsa (remove pulseaudio for that)

My suggestion:  Switch all to pulseaudio, once properly configured, it works really well...

yeh but for the newcommer though I suggest using alsa as it doesnt need as much tweaking.

---

### Post by GumpTron on 2008-10-15
I decided to reboot Ubuntu and now everything works! Thanks to everyone here, I am sure one of the solutions above solved my problem. I can hear youtube and I can hear everything much louder. Thank you so much.

---

### Post by SunnyRabbiera on 2008-10-15
well if sound gets disabled again hit control-alt-backspace.

---

### Post by patrickballeux on 2008-10-15
> **SunnyRabbiera said:**
> yeh but for the newcommer though I suggest using alsa as it doesnt need as much tweaking.

I was also saying the same thing a few weeks ago.  But if your ALSA sound card does not support a mixer (like mine), you play a video on youtube and your sound card is locked by Flash and no other software can play sound anymore...

This is annoying.  But putting everyting in pulse and installing pavucontrol solves all those little problems.  I don't know why Ubuntu Hardy is not installing by default pavucontrol and setting all sound source to pulse.  This way, no one would have these stupid glitches.

Let's hope that it will be fixed in Ibex...

---

### Post by SunnyRabbiera on 2008-10-15
well pulse was still very fresh with hardy but now its have had some time to develop i think the future looks good for pulse.

---

### Post by eternalnewbee on 2008-10-15
Computers are like people. They all come with different personalities...
Live long & prosper.

---

### Post by blackamel on 2011-10-17
[SIZE=3]Go to
 >Application
>Settings
>System Settings
>Multimedia
>Phonon(Audio Hardware Setup)
Under Hardware section on Profile, try what is offered and check for sound.


It worked for me![/SIZE]

---


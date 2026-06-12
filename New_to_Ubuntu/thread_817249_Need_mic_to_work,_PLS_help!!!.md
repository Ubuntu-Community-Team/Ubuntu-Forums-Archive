---
title: "Need mic to work, PLS help!!!"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by benjamin_linux on 2008-06-03
Hi, 
i'm asking again because i still can't find an answer and i need my microphone to work, i'm a freelance so i really really need my microphone and Skype working.

Everything works just fine except my microphone, i tried almost everything in alsamixer and mix and nothing, i reboot to Vista and there it works, so it must be a config issue.

Plsssssss :)

---

### Post by ruffEdgz on 2008-06-03
Just to clarify the problem more, here is another post he made about this issue:

[http://ubuntuforums.org/showthread.php?t=811742](http://ubuntuforums.org/showthread.php?t=811742)

If the built-in mic isn't working, I would try to see if the input jack works for Ubuntu. Do you have a friend or your own mic that isn't a built-in mic that you can test and plug in.

I don't know if this is the same PC but looking at Compaq's site and I see that they are using for the speakers and mic: Altec Lansing® speakers

If anyone else has any ideas, would love to her them :D

---

### Post by wolfen69 on 2008-06-03
please include some info with your questions. people can not help if they dont know what type of equipment you are using. common sense needs to make a comeback.

---

### Post by benjamin_linux on 2008-06-03
Well,

the equipment is a Compaq Presario f700 (Sempron 3600+, 1gb RAM, nVIDIA 7m), and the audio/mic is Conexant High Definition SmartAudio 2.21. Just to check i just used the oh-my-god-so-completely-useless voice recognition software from Vista and "it works".

---

### Post by benjamin_linux on 2008-06-18
It's been two weeks and nothing, someoneeee pleeeasseeeeeee

---

### Post by soro2005 on 2008-06-18
I guess that's the first thing you've done, but just in case: Have you tried to find out whether there's a specific driver for your soundcard and mic? For instance at [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

In the end, what matters may be your soundcard rather than the microphone model.

---

### Post by benjamin_linux on 2008-06-19
Let's see, i didn't tried those drivers because for what i read they are kind of old, but i updated the Alsa drivers from Synaptic and nothing, still the same... Finally yesterday i bought the cheapest genius microphone (u$s2,90) and well, it works just fine.

Someday i'll see whats wrong with the built-in microphone, or perhaps with II i won't have this problem, because no one seems to know exactly what the problem is.

Thanks for the help!

---

### Post by soro2005 on 2008-06-19
In any case, I guess your best bet is to make a note of the sound card you have and go out into the world wide web to hunt for information. It looks like it might be a rather rare configuration that you have there. Not everything works, though, because some hardware manufacturers don't provide linux drivers for their products, and there's not always a geek interested enough in that particular device to spend the time figuring out how to make it work.

You could send a nagging message to the manufacturer and tell them that you're disappointed by the fact it doesn't work with your operating system. :)

---

### Post by tact on 2008-06-19
hey there   "i have done everything|a million things" in alsa and mixer etc... doesnt really help solve the matter.  :)

Glad you are up and running with the external mic work-around.  Well done - very sensible.

What version of ubuntu are you using?  Is it (u/ku/xu)buntu?
What version (8.04, 7.10, x.xx)?

Version number makes a huge difference as in Hardy (v.8.04) there was a move to a totally new sound architecture (pulseaudio).

Once we get the above answered we can move forward substantially.  :)

---

### Post by benjamin_linux on 2008-06-19
It has been really annoying, being "my first time on Linux". Everything else worked just fine, only this damn microphone... Gladly i find a "solution" for three bucks (nine here in Argentina). Is not a bad idea, to send an e-mail, even just to bother someone else with this problem ;)

I have (U)buntu 8.04, it´s my first time on Linux.

Thanks again!

---

### Post by tact on 2008-06-20
> **benjamin_linux said:**
> It has been really annoying, being "my first time on Linux". Everything else worked just fine, only this damn microphone... Gladly i find a "solution" for three bucks (nine here in Argentina). Is not a bad idea, to send an e-mail, even just to bother someone else with this problem ;)

I have (U)buntu 8.04, it´s my first time on Linux.

Thanks again!


Ok - please remove the external mic...  and reboot your PC.  

Then when booted clean again - look at the notification area at the top right of the screen you will see your volume control - correct?

I know you mentioned doing lots of stuff with alsa and the mixer etc..  but entertain me a little here.  :)

Right click on the volume control and left click on "Open Volume Control".

On the first (Playback) tab is there a slider for "Microphone"?    (While in there you might want to max all the sliders to the top).

Across on the Options tab - do you see a dropdown box labelled "Mic Select"?

What do you see when you click beside "Mic Select"?   Options for one mic?  Two mics?

Do you have a "Switches" tab?   Is there an option there to check a box for extra Mic boost?

If you give a "No" to any of the above....  Click on Edit>Preferences and check the following boxes:
Microphone
Mic Boost
Mic Select

And then check the above out again.  Make sure the mic is enabled and the volume slider maxed out.

Wait for your response.  

Cheers

---

### Post by benjamin_linux on 2008-06-20
On Playback there are three sliders for microphones (external, internal and docking) and all of them are at 100%.
On the other hand, in Preferences i have Master / PCM / IEC958 / Docking, external and internal Mics... there's no mic select or boost!
And in Switches all it shows is IEC958 and is checked.

---

### Post by arochester on 2008-06-20
Try...

Open Skype
Click on the S-button (bottom left) 
Click on Options
Click on Sound Devices
Experiment with Sound In
Click Make a test call

...Mine didn't work until I changed to the option with hw in it.

---

### Post by tact on 2008-06-21
> **benjamin_linux said:**
> On Playback there are three sliders for microphones (external, internal and docking) and all of them are at 100%.
On the other hand, in Preferences i have Master / PCM / IEC958 / Docking, external and internal Mics... there's no mic select or boost!
And in Switches all it shows is IEC958 and is checked.

Ok looks like you have all the bits in place.   Lets look at software...

-  have you made an modifications to your pulseaudio config files?  Followed any of the guides on these forums like "The (almost) perfect Pulseaudio..." guide?   Have you edited /etc/asound.conf etc?

(I hope not... but knowing if you did may help find the problem)

-  Can you open Applications>Sound @ Video>Sound Recorder and record your voice?

-  Open up a terminal and type in 
```
padsp skype
```

Now with skype running and logged in..  check settings, audio device and Sound in, Sound out, and Ringing - should all be "default device".

Try "Make a test sound" and "Make a test call"....

How did all that work?

---

### Post by patil.rr on 2008-06-21
Thanks for starting this thread.. Looks like I have messed-up configurations by installing Pulse audio... I have the same problem as benjamin_linux...

On Playback there are three sliders for microphones (external, internal and docking) and all of them are at 100%.
On the other hand, in Preferences i have Master / PCM / IEC958 / Docking, external and internal Mics... there's no mic select or boost!
And in Switches all it shows is IEC958 and is checked.


[COLOR="Red"]'Now with skype running and logged in.. check settings, audio device and Sound in, Sound out, and Ringing - should all be "default device".'[/COLOR]

I tried it.. but nothing works...
Also please note.. Applications>Sound @ Video>Sound Recorder ---  I am unable to record my voice using this application...
My Notebook configuration:-
HP Pavillion dv6000, AMD Turion 64, NVIDIA graphics, inbuilt microphones... running UBUNTU Hardy Heron.. have not yet tried external Mic

I am completly new to Linux...

Thanks in advance..

---

### Post by soro2005 on 2008-06-21
[Here's somebody who's solved a similar problem]("http://www.linux.ryukent.co.uk/show.php?id=31"), with a different computer, though, and probably also with a different sound card. I insist, the sound card is most likely the key to the problem, not the microphone.

---

### Post by patil.rr on 2008-06-22
Thanks for quick reply.... 
humm... but my sound card works with Vista...
However will try and comeback...

---

### Post by tact on 2008-06-22
According to this thread 
[http://ubuntuforums.org/showthread.php?t=385739](http://ubuntuforums.org/showthread.php?t=385739)

...its a good idea to go into the sound settings (Right click on the sound icon in the notification area, open volume control, then Edit>Preferences and put a check beside EVERY device....

Then max out all the volume controls and make sure none are muted and see if the moc is working.  It may not be seen by the system as "mic" it could be "digital" or other...

If this fails to work then we check all the pulseaudio settings....

---

### Post by WitchCraft on 2008-06-22
The problem you are describing sound very much like a driver problem to me.

There are 3 things you can do when you have problems with a driver on Linux:
1. search sourceforge.net / google.com/ncr for a driver, and install it
2. download the latest alsa source, and compile it
3. download the latest linux kernel, (watch out for patches), and compile & install

These are the 3 ways that you can install new drivers.
Most of them are in the Linux kernel, a few things are in alsa.
And if that doesn't work, then you need a 3rd party driver, if it exists...

---

### Post by Methuselah on 2008-06-22
Is it still not working benjamin?
I had a similar problem.

[EDIT: I just noticed that the external microphone works, so the below might not be relevant!]
[It was my external mic that didn't seem to work]

Try:

Go to add/remove programs and type pulse in the search box.
Select all 'PulseAudio' related packages only and apply.

After this the pulseaudio device chooser should appear under Applications->Sound & Video. Launch it.

It should appear as an icon in the panel in the upper right.
Left click it and select Volume control.

Under input devices make sure it isn't muted (grey) and pull the sliders all the way up. 

That worked for me. 
The problem was that the mic was too low or muted in PulseAudio (the software through which all sound passes in Hardy Heron).
Not sure why it was set that way after installation.

---

### Post by benjamin_linux on 2008-06-24
Sorry, i was at my girlfriend's house this days.
It's not just with Skype i have the problem, the sound recorder doesn't works either. 
(If someone would gave me a dollar for every test call i've made on Skype)... No change of devices works for me there and i haven't modified at all any sound configuration, it's really weird!

Thanks for all the help :D

---

### Post by WitchCraft on 2008-06-24
> **benjamin_linux said:**
> Sorry, i was at my girlfriend's house this days.
It's not just with Skype i have the problem, the sound recorder doesn't work either. 
(If someone would gave me a dollar for every test call i've made on Skype)... No change of devices works for me there and i haven't modified at all any sound configuration, it's really weird!

Thanks for all the help :D

If the device driver doesn't work, then it doesn't work, no matter whether you did or didn't modify anything in your config file.

On the other hand, i would try to increase the record volume and unmute your mic as recommended in the previous post...

---

### Post by benjamin_linux on 2008-06-24
As i mentioned earlier, i did that and nothing changes.

I don't think i should do the things you recommend me to do because i installed HH around a month ago, so nothing (kernel, alsa, drivers) should be out of date, don't you think?

---

### Post by benjamin_linux on 2008-06-28
To give this thing a twist...
I rebooted on Windows and i was bored so i put a Flaming Lips record and WTF, it sounded allot louder/better then on Linux and in stereo... I thouth the soundcard was working well, but i guessed wrong (sorry to those of you that mentioned this possibility, but i thoth it worked fine!).
This open new perspectives, now PLEASE what can i do, i'm just sick of this problem!

---

### Post by marianogedisman on 2008-11-08
Man, I've been going insane trying to figure this out, but hey, it's my first day with this issue.
I felt the duty to register and share the pain of not having the built-in mic working.

Maybe we're asking way too much from Linux? With XP my webcam wouldn't work. Now it does.

It's not Linux's fault, but HP/Compaq for not giving detailed info on the devices!

---


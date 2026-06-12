---
title: "To quiet a dog"
date: 2010-03-07
forum: Programming Talk
---

### Post by Eredeath on 2010-03-07
So my dog barks obsessively when I leave her alone. I've been looking for ways to quiet her down without hurting her (e.g. bark collar) or spending too much money (humane bark collars are pricey). I've come across some products that make a loud sound or something when the dog barks as a way of negative reinforcement.

I want to make one of these.

I have little programming experience (all of it in windows and in the console). But what I would like to do is make a program that will take in a sound via the microphone, measure it, if the sound is loud enough (e.g. her barking) enough play a predetermined sound file.

It's really simple but I'm in need of a jumping off point. Recommendations on which language to use and (the hardest part that I can foresee) how to take input from the microphone and measure it.

Any guidance will be much appreciated. 

And just for fun if anyone wants to see Kelly (my dog) you can visit my [youtube channel.]("http://www.youtube.com/eredeath")

---

### Post by dollarmenunaire on 2010-03-07
Which languages are you comfortable with in Windows?

I would recommend Perl for this. Perl is an interpreted language, so its more scripting however some would argue that. It is similar to C it its syntax.

Take a look through [http://www.cpan.org/](http://www.cpan.org/) and see what modules for audio you can find.

---

### Post by Eredeath on 2010-03-07
> **dollarmenunaire said:**
> Which languages are you comfortable with in Windows?

I would recommend Perl for this. Perl is an interpreted language, so its more scripting however some would argue that. It is similar to C it its syntax.

I've worked with both C++ and Java.

---

### Post by Eredeath on 2010-03-07
I found a Audio::DSP Module that is supposed to read and write to IO audio devices. I'm having trouble using it though. This is the link to the .pm file [http://http://cpansearch.perl.org/src/SETHJ/Audio-DSP-0.02/DSP.pm]("http://http://cpansearch.perl.org/src/SETHJ/Audio-DSP-0.02/DSP.pm") I can't make left or right of it though. This is the code i have thus far: ```
#!/usr/bin/perl -w
require 5.004;

use Audio::DSP;

my $trial = Audio::DSP->dread();
print($trial);
``` But it is giving me a Segmentation fault
I just want to see... something

Okay so i'm realizing i'm an idiot... 
I need to define the device to read from. I want to read from my microphone so I'm trying to find the device name right now. Anyone know how to do this?

---

### Post by Eredeath on 2010-03-07
Okay so I've decided to use python instead of Perl and found this [little gem]("http://ubuntuforums.org/showthread.php?t=500337"). The post by CShadowRun gives me exactly what i need.

---

### Post by Eredeath on 2010-03-07
After scouring the interwebs and the irc's I out together a very rudamentary solution. But non the less it works. Here is the code I used: ```
#!/usr/bin/python

import pygame, alsaaudio, time, audioop

# Open the device in nonblocking capture mode. The last argument could
# just as well have been zero for blocking mode. Then we could have
# left out the sleep call in the bottom of the loop
inp = alsaaudio.PCM(alsaaudio.PCM_CAPTURE,alsaaudio.PCM_NONBLOCK)

# Set attributes: Mono, 8000 Hz, 16 bit little endian samples
inp.setchannels(1)
inp.setrate(8000)
inp.setformat(alsaaudio.PCM_FORMAT_S16_LE)

# The period size controls the internal number of frames per period.
# The significance of this parameter is documented in the ALSA api.
# For our purposes, it is suficcient to know that reads from the device
# will return this many frames. Each frame being 2 bytes long.
# This means that the reads below will return either 320 bytes of data
# or 0 bytes of data. The latter is possible because we are in nonblocking
# mode.
inp.setperiodsize(160)

pygame.init() #initializes pygame
pygame.mixer.music.load("/home/eredeath/Documents/programs/Sounds/highpitchsqueal.wav")
#the above line loads in sound file

while True:
	# Read data from device
	l,data = inp.read()
	if l:
		if audioop.max(data, 2) > 32700:
			pygame.mixer.music.play() #plays soundfile
	time.sleep(.001)
```
I'm hoping to develop it further, but for now it does what I need it to do.... The dog is going to hate this.

---

### Post by dollarmenunaire on 2010-03-08
Awesome! I was considering recommending python but I have little experience using it.

Good job!

---

### Post by Eredeath on 2010-03-08
Thanks. :D
This was (is) my first python program. I used it today and it worked great! The dog barked twice (once when i first left and once a few hours later), both times the sound triggered and both times she silenced herself.
I'm hoping to add web-cam enable to it so when it goes off i can record what happens, start and stop times so i can set it to be on certain times of the day. And maybe even a GUI so it's easily usable by others.

---

### Post by raydeen on 2010-03-08
Oh, this is just screaming to be a practical joke!! I may have to set this up to scare the wife and kid for April Fools Day! :D

---

### Post by themarker0 on 2010-03-08
> **Eredeath said:**
> Thanks. :D
This was (is) my first python program. I used it today and it worked great! The dog barked twice (once when i first left and once a few hours later), both times the sound triggered and both times she silenced herself.
I'm hoping to add web-cam enable to it so when it goes off i can record what happens, start and stop times so i can set it to be on certain times of the day. And maybe even a GUI so it's easily usable by others.

Wow this is quite an interesting project. Can you add UI support? My neighbors and i have been searching for something similar, after getting them to install linux, i have to do all cml for them, so this would be nice. Just a request though. and i will for sure use this!

---

### Post by Eredeath on 2010-03-08
> **themarker0 said:**
> Wow this is quite an interesting project. Can you add UI support? My neighbors and i have been searching for something similar, after getting them to install linux, i have to do all cml for them, so this would be nice. Just a request though. and i will for sure use this!

Sure. Since you're showing interest I'll work on the GUI first. As it is my first project in Python and my first GUI ever, it might be awhile before I have anything useful and it will probably be really buggy. I'll keep updating this thread as I work on it. Just subscribe to get updates. :)

---


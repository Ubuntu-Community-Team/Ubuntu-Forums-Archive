---
title: "Sound problems...please help"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by jukingeo on 2008-06-16
Hello all, 

I have been having major sound problems this week after following a procedure that would fix a problem I had with streaming audio.  

Anyway, I guess I should start at the very beginning and provide as many details as possible.  As it is now I am very new to Ubuntu and I only have been on it for a month now.  While most problems I have managed to solve in a couple of days, my audio problems so far seem never ending.

Ok, first off, my system:

Dell Dimension 4600 (Windows XP and Ubuntu Studio 8.04 dual boot):

2.8ghz CPU 133mhz buss speed
1.5gig of ram
1 IDE 80 gig hard drive (master) for Windows XP only
1 SATA 500gig drive for Ubuntu master and storage purposes
Nvidia 5200 series video card with either 128meg or 256meg ram

and most important:

Sound Blaster X-Fi sound card

After my installation of Ubuntu (standard) version 8.04 my sound didn't work right off the bat.  I searched around and found out that there were many issues with getting the X-Fi to work using the Creative provided drivers which operate through ALSA.  I was right away told to use OSS.

Ok, so I installed OSS and I had sound...but not with everything.

The internet worked but just about none of my games worked. I was also able to play any audio and video files stored on my machine through Totem movie player.  Linux based games such as SuperTux and Neverball DIDN'T work.

In the interim I have installed other games and other programs that I wanted on Linux.

This is what I ended up with at this stage of the game:

Games:

(Linux)

Neverball (no sound)
SuperTux  (no sound)

(emulators)

GENS-Sega Genesis (all no sound)
GFCE-NES
Stella-Atari 2600
DosBox
ZSNES

Audio/Video Applications:

Open Movie Editor (very choppy picture, no sound)
Cinelerra (clear picture AND had sound)
Kino (cannot get to work at all)

Ubuntu system sounds do not work

Internet streaming audio/video (e.g. You Tube) worked fine with some minor crashes every now and then.


After I did a bit of digging within the Ubuntu forums I came across this guide:

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

After following this guide these were the results:

Games:

(Linux)

Neverball (full sound, played beautifully)
SuperTux  (full sound, played beautifully)

(emulators)

GENS-Sega Genesis (played but with very distorted sound (even after altering the games settings as well)).
GFCE-NES (Sound)
Stella-Atari 2600 (Sound, but played at higher than normal pitch, this was corrected within Stella's audio adjustments).
DosBox (Worked, but like GENS, was distorted, but not as severe as GENS)
ZSNES (A minor adjustment in a configuration file got me sound here)

Audio/Video Applications:

Open Movie Editor (very choppy picture, distored sound)
Cinelerra (clear picture AND had sound...no change)
Kino (cannot get to work at all...same, no change (problem turned out to be a codec problem, still unsolved though).
I added Audacity, Ardour and RoseGarden...all but RoseGarden worked.

Ubuntu system sounds still do not work 

The internet and streaming audio in general became very choppy as a result of these changes.  You Tube became so slow it was unwatchable.

Within the same post as the link to the above procedure, I found another guide that would supposedly fix the audio streaming problem.

Here is where that guide starts:

> **psyke83 said:**
> As far as I can see, this guide will break Flash for many users on Hardy, as libflashsupport is required for Flash v9 to work with PulseAudio, and it isn't installed by default. Unfortunately, even if you do install this package, it will cause Firefox to crash regularly on pages with Flash content.

The good news is that there are backported fixes coming to Hardy soon, but I have created a guide that addresses these problems for those that cannot wait. Please see Part A & B of my guide here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Also, people experiencing skipping with PulseAudio may find a solution from Part C.

After I followed this guide, my sound was completely wiped.  
Video had returned to normal on-line, but there is no sound. Nothing worked.  Apparently the procedure was more or less meant for ALSA and not OSS.  Sure enough, I cannot even get into OSS to make sound adjustments.

I figured that perhaps there may have been a Kernel issue and as such I know that I wanted to upgrade to Ubuntu Studio (because I wanted the real time Kernel anyway), so I did so in the hopes of solving some of my problems.  Alas, that wasn't the case.  The author of the above procedure did try to help me fix the problem and in the end the result was to try and uninstall everything we did.  I am not sure that we were successful at that.  I do not still have sound.  He suggested that I look for help elsewhere as he didn't know I OSS and he also didn't know that ALSA doesn't work with my X-Fi sound card.

At any rate, this is what I want to get running again WITH sound:

Games:

(Linux)

Neverball 

(emulators)

GENS-Sega Genesis 
GFCE-NES
Stella-Atari 2600
DosBox
ZSNES
Wine (never tested, but I have installed)

Audio/Video Applications:

Open Movie Editor 
Cinelerra 
Kino 

ALL if the Ubuntu Studio Applications with emphasis on:

Audacity
Ardour
RoseGarden
JACK Rack
Hydrogen


Of course I do want my internet streaming audio/video to be fully functional again as well.

Any assistance would be much appreciated.

Thank You,

Geo

---


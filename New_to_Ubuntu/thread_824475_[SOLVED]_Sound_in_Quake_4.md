---
title: "[SOLVED] Sound in Quake 4"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by kayfes on 2008-06-10
I have a Creative Labs - Sound Blaster Audigy SE Sound Card and I have no sound in Quake 4. 

Everything else works fine except the sound.

---

### Post by kayfes on 2008-06-10
I have searched google up and down does anyone have any advice?

I even found my post from the leisure and games ubuntu forums for this issue.

---

### Post by Kabal on 2008-06-10
Try to lower the sound quality to 11Khz..?

---

### Post by kayfes on 2008-06-10
How would I do that?

---

### Post by Kabal on 2008-06-10
btw are you running Quake4 via Wine?
or running the game native under (K)Ubuntu?

---

### Post by kayfes on 2008-06-10
Native in Ubuntu Hardy.  Tha graphics are great just deaf when I play the game.

Will have to figure out Wine eventually as I have about 15 other games I want to play but I figured I would start with Q4.

---

### Post by Kabal on 2008-06-10
Do you have the latest installer for Quake4?

If not: [http://zerowing.idsoftware.com:6969/](http://zerowing.idsoftware.com:6969/)

And for sound please try the SETTINGS menu ingame..
There you can set the sound quality.

Or popup a console with CRTL + ALT + (~) and do some configging your self.

com_allowConsole 1 is easy to set for allowing console with only the (~)

Most sound settings in Quake4:

s_force22kHz                     "0" or "1"
s_clipVolumes                    "1"
s_constantAmplitude              "-1"
s_decompressionLimit             "2"
s_deviceName                     ""
s_doorDistanceAdd                "150"
s_dotbias2                       "1.1"
s_dotbias6                       "0.8"
s_drawSounds                     "0"
s_force22kHz                     "0"
s_frequencyShift                 "1"
s_globalFraction                 "0.8"
s_loadOpenALFailed               "0"
s_maxChannelsMixed               "63"
s_maxSoundsPerShader             "0"
s_meterTopTime                   "2000"
s_minStereo                      "8"
s_minVolume2                     "0.25"
s_minVolume6                     "0"
s_musicVolume                    "0.5"
s_muteEAXReverb                  "0"
s_noSound                        "0"
s_numberOfSpeakers               "6"
s_playDefaultSound               "1"
s_quadraticFalloff               "0"
s_radioChatterFraction           "0.9"
s_realTimeDecoding               "1"
s_reverbFeedback                 "0.333"
s_reverbTime                     "1000"
s_reverse                        "0"
s_showLevelMeter                 "0"
s_showStartHardware              "0"
s_showStartSound                 "0"
s_singleEmitter                  "-1"
s_skipStartSound                 "0"
s_spatializationDecay            "2"
s_speakerFraction                "0.65"
s_subFraction                    "0.5"
s_useDeferredSettings            "1"
s_useEAXOcclusion                "1"

s_useEAXReverb                   "1"
s_useOcclusion                   "1"
s_useOpenAL                      "0"
s_volume                         "1"

You can check your own values.. and try experimenting with them.

:)

---

### Post by kayfes on 2008-06-10
Useful info will come back an update after I try some of those.

---

### Post by Kabal on 2008-06-10
Good luck! :)

---

### Post by kayfes on 2008-06-17
Stll don't have any sound in Quake 4.  I have reinstalled Hardy wanted a fresh clean copy and Installed Quake 4.  Got it running like I did before but once I have to now sound.  I have gotten my soundblaster audigy to play sound now so thats what I am plugged into.  Any help would be much appreciated.

---

### Post by kayfes on 2008-06-17
Got lucky! Well sort of lucky looked up down and around google and found that worked for someone trying to play Doom 3.  Anyways turns out all I had to do was run: quake4 +set s_driver oss.

---


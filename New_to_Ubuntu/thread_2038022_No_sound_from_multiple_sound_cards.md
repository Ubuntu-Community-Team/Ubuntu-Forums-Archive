---
title: "No sound from multiple sound cards"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by paichkash on 2012-08-05
hi
i have no sound from my sound card i have two sound cards.. both work ok in xp and my speakers are also ok

all that i want is to set the sblive card as default ...

here are some outputs for some commands.. 

```
r@r-desktop:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```
```

r@r-desktop:~$ asoundconf list
Names of available sound cards:
I82801BAICH2
Live
```

i also tried the following command but stil no luck
```
asoundconf set-default-card Live
```

thanks

---

### Post by Hadaka on 2012-08-05
hi, from the launcher click SYSTEM SETTINGS....SOUND....HARDWARE
then choose the card you want as default.
hope this helps.

---

### Post by paichkash on 2012-08-05
i had tried that but had no luck ..
the prefrense is like the device which prodces sound is on top..

i think i am having some succes after i followed the following article
[http://robertbeal.com/644/change-the-default-sound-card-in-ubuntu-karmic](http://robertbeal.com/644/change-the-default-sound-card-in-ubuntu-karmic)

what i want is:
Use my PCI sound card for sound in ubuntu for everything..

after follwing above article now when i play a local .move file in movei player i can hear it ok through the PCI sound card which i what i want...

but when i open youtube i hear it through built in sound card which is not what i want .. i want it to come through PCI card.

my current settings :
when i click the speaker icon next to the shutdown icon the in the Device :its shown as "sb live 5.1 alsa mixer"

I got another related question:
there are three things for controling sound which i assume..
one is the speaker icon next to shutdown icon..
second is the Application..System Settings ,,, Multimedia
third is  system..prefrences... sound

what is the difference betweent them ? 

where can i choose which program to use which device ?
thanks for the prompt respnses.

---

### Post by paichkash on 2012-08-09
its weired.
ubuntu login sound and mplayer is played throug the headphones..
whearas the youtube is played throug the builtin speaker.. 

i want all each and every thing t use only by pci sound card .. right now the only thing not doing so is youtube.. :popcorn:

---


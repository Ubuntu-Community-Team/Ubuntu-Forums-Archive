---
title: "two sound cards, sound in only some programs"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Preserved Killick on 2008-06-07
Hello Ubuntu users,

I hope you will please help me solve this problem.  I ran the latest updates (might have been kernel updates?) and now *sound only works in some applications*.

I DO get sound after login and when I press panel buttons in Gnome.  I can start Juk and play music files from a hard drive.

I get NO sound when playing YouTube videos in the browser or when using bzflag (a game).

Here's what I have under the hood:

HDA Intel integrated board
    00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) High Definition Audio Controller (rev 03)
Audigy Sound blaster card
    06:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
Hardy Heron 8.04
Gnome 2.22.2
Nvidia accelerated graphics driver
grep Codec /proc/asound/card0/codec#*
     Codec: Realtek ALC880

If I open System> Preferences> Sound: Sounds Tab: Enable software sound mixing (ESD) is checked.  Play system sounds is checked.  I can play system sounds.

System> Preferences> Devices: Default Mixer Tracks: CAO106 (Alsa mixer)

When I ran $ alsamixer I saw that my volume was turned up. 

I don't know how sound is supposed to work, but I suspect that various programs are supposed to be able to send output to sound at the same time.  I used to be able to listen to Juk and play bzflag with sound from both at once.

I don't care which soundcard I use.  My speakers are plugged in to the sound blaster card right now, but if using the HDA is going to work better, I'll move the plug or even un-install the sound blaster if that's what it takes.  

Thank you to anyone who tries to help!

-- Killick

---

### Post by orannis on 2008-06-07
For a short time, I had two sound cards and had this same problem, unfortunately, I don't remember how I fixed it. Unless your going to suffer a unnacceptable quality loss by switching to the onboard card, I would just take the discrete sound card out and use the onboard one.Or, if you look around the forums, you may find another thread about it.

---

### Post by markbuntu on 2008-06-07
Sounds like your audio managers defaulted to different cards. Every sound application goes through a sound manager, either alsa or pulseaudio or xmms2 or oss and those control which sound card is used by their default settings.

If you have you System/Preferences/Sound set to automatic the system will try to switch managers depending on what the application needs. This causes problems.

I also have two sound cards and the trick to this is to get everything running through one sound manager and then set that one's default to the card. This will avoid these types of conflicts. There is a pretty terrific sound how-to in the Mutimedia and Video forum. You should give it a try.

---

### Post by Preserved Killick on 2008-06-08
The thread markbuntu directed me to in Multimedia was excellent.

The quick & dirty version is below, but you should **really, really, take a look at the guide by LordRaiden in Multimedia.**

Open a terminal.  $ aplay -l  (gives a list of soundcards installed)

if soundcards installed,

$alsamixer

If you have green boxes under the slide-volume, press M will toggle to un-mute those channels.  To save this change so it will work this way on reboots: 

$ sudo alsactl store n-1 (where n= your number of soundcards.  I have 2, so my n-1=1)

To set one card as the primary card:

$ cat /proc/asound/modules

I had:

0 snd-hda-intel
1 snd-ca0106        but I wanted snd-ca0106 to be my 0 card, so:

$ sudo [editor] /etc/modprobe.d/alsa-base (I used nano but you can use gedit or whatever editor you like)

then add two lines to the end of the file:

options snd-ca0106 index=0
options snd-hda-intel index=1

(use your own card names and put them in the order you want).  After a reboot, sound now worked in YouTube and everything else except for bzflag (a game) but LordRaiden had said some games require alsa-oss to be installed:

$ sudo apt-get install alsa-oss

Then when I want to use it, I start bzflag:

$ aoss bzflag    instead of $ bzflag

This gets me sound.  If anyone knows how to edit a panel launch button to use aoss I'd be happy to hear about it so I wouldn't have to open a terminal to start bzflag.  Also, and this is odd, but if I have a YouTube video paused and I start bzflag without aoss, sound does work.  Dunno why.

Thank you markbuntu and LordRaiden.

-- Killick

---


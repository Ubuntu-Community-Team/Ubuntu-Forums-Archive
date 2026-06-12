---
title: "[SOLVED] Sound nightmares"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by JDVyska on 2008-10-24
Alrighty.  Me and my ubuntu experience with sound has been a bumpy ride.  I got to stable several months back with lots of tweaking to ALSA settings and such.

Then I opened up our little happy relationship to a new partner, a Plantronics USB Gamecompro 1.  Apparently, my Wine, Vent and ALSA didn't take kindly to the old 0.8MM headset getting the heave ho.

I had no problem with Vent (and winecfg) seeing the new USB headset (Followed WoW Related guide, since my only vestigial Windows apps are WoW and Vent: [http://www.wowwiki.com/Linux/Wine/Misc#In-Game_Voice_Chat_with_USB_Headsets](http://www.wowwiki.com/Linux/Wine/Misc#In-Game_Voice_Chat_with_USB_Headsets)).  It even worked.   Briefly.   What was happening was that it would just stop playing sound over the headset, for no clear reason.  I launched vent from command line to see if there were errors when it would cut out... nada.

Well, I'm an experienced ALSA battler, been using Ubuntu for a while... I figure I can sort this mess out pretty good with some forum searching.   I then take what appears to be a horribly wrong turn:  I install PulseAudio.

Come to discover, Wine appears to have a belligerent hatred for PulseAudio (ok, not really, but they *do* say they refuse to  support it (and seem quite irked with Ubuntu for choosing to include it) since they haven't even finished ALSA support).  With PulseAudio installed, everything BUT WoW and Wine continue to work fine.... until I also tried to watch anything Flash.

:(

So, I'm now torn.
[LIST]
[*]Do I uninstall Pulse completely as outlined ( [http://ubuntuforums.org/showthread.php?t=885437&highlight=switch+pulseaudio+alsa](http://ubuntuforums.org/showthread.php?t=885437&highlight=switch+pulseaudio+alsa) ) and try to fix my ALSA situation?
[*]Do I go completely random and try OSS4?
[*]Do I try to install all manner of hacks to fix things (this did NOT fix anything: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) )?
[/LIST]


What do I do?   I'm an avid pro-Ubuntu guy now, but I've never had good experience with sound, and I'm feeling pretty lost.  One of the first times in a year I've missed Windows.  I don't even know what approach to take with this mess.

:frown:


More useful stats:
[LIST]
[*]Ubuntu 8.04 32bit, fully patched up
[*]Sound Card 1: Creative Labs Audigy 1  ( I believe, can look deeper)
[*]USB Headset:  Plantronics USB Gamecompro 1
[/LIST]

---

### Post by Crandom on 2008-10-24
I can only second your point that PulseAudio seems to have killed wine and many other apps. I am interested to see if you can sort this out, because my audio is half broken too :-(

---

### Post by markbuntu on 2008-10-24
You can get wine working with pulseaudio by launching it with 

padsp wine 

and setting wine to use oss. Padsp is the oss wrapper for pulseaudio. 

The problem is that the wine devs made some erroneous assumptions when writing their alsa plugin which they have recently fessed up to and have fixed. This fix is making its way into a release soon we hope.

There is info on getting specific troublesome applications to work with pulseaudio here ( this is mostly due to faulty alsa implementations that need to be worked around):

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

I have two sound cards, a usb headset and a usb webcam with its own mic. The only reasonable way I have ever found to use them all is with pulseaudio.

---

### Post by JDVyska on 2008-10-24
Alright.  That got me further.  I had tried padsp as a prefix to both wow & vent before  (padsp wine [Vent/WoW]), for some reason that broke my wow sound yesterday.  It seems to be fine now, so likely that was some config setting incorrect.

Hopefully you can help a little further.  Ideally, I'd like WoW's sound routed to my soundcard.  Vent, I'd like to go to my headset.

Right now, all wine sound is going straight to the soundcard for output.  It does seem to be pulling input from the headset.

When I run 'psdsp winecfg' and hit the Audio Tab:
```
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM headset
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM headset
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM headset
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM headset

```

Under OSS Driver > Wave Out Devices, I have PulseAudio Virtual OSS and a strange "blank" entry.  Wave In only has Pulse.   Mixer shows both PulseAudio Virtual OSS and USB Mixer.

When I go into Vent, I have output device options of "Default Wave Mapper", "PulseAudio Virtual OSS", and that blank option.  Seems no matter which I set it to, all sound routes to the main sound card.


How do I achieve WoW to sound card and Vent via USB?

---

### Post by markbuntu on 2008-10-24
Do you have pavucontrol which is the pulseaudio volume control. You should be able to route your sound with that now that the applications are using pulseaudio.

I don't use wow or vent or even wine for that matter but there are a number of threads about that in the forums here. There might even be a wow how to in the Tutorials and Tips section of these forums.

---

### Post by JDVyska on 2008-10-24
OK.  Strange thing with pavucontrol:

When using Wine through padsp, it only shows up as a stream to change the setting of where it's going when it's doing sound effects or text to speech - not when someone is talking.

So, I've got my rig doing what it's supposed to be doing now (thanks to some long wav file I made it play).

Thanks bunches guys.  This has been... interesting.  I'll mark solved.

---


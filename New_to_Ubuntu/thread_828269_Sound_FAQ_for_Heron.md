---
title: "Sound FAQ for Heron?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by ofb on 2008-06-13
I'm looking for a FAQ or good thread on sound in Heron.

Move Player (Totem) and VLC don't seem to share the sound card with other apps. You can't get either to play sound if another sound app is running, and other apps are blocked from playing sound if either is already running.

XMMS, SMPlayer, MPlayer, Flash in Firefox, and aplay (email notification) all seem to work fine together. It's just Totem and VLC that block other apps, though they don't block each other.

Sound Preferences shows Autodetect for all playback, ALSA for capture, and "VIA 82C686A/B rev50 (Alsa mixer)" for Default Mixer.

... and now I notice capture doesn't work at all. So yeah, I could use a FAQ. Looks like this is going to take a few evenings to get working as well as Gusty did.

---

### Post by joshsmith on 2008-06-13
[http://ubuntuforums.org/showthread.php?p=4723680](http://ubuntuforums.org/showthread.php?p=4723680)

---

### Post by wolfen69 on 2008-06-13
see [this]("http://ubuntuforums.org/showthread.php?t=776739") to fix your sound.

---

### Post by ofb on 2008-06-13
Great stuff. Thank you.

Question: what does Pulse do for me?

I get the idea it's a management layer that will be good for Linux sound and developers once it has application support, and that right now application support is lacking. It's looking like what I should do for my apps is switch everything to ALSA rather than Autodetect, as Autodetect allows my only two Pulse-compatible apps to block the rest of my sound apps.

It looks like going to pure ALSA would remove all blocking problems. Also I'd avoid the extra CPU hit of running the Pulse layer.

Conversely, not all of my sound apps have Pulse support so I'll never completely solve the blocking problem no matter what I do. (Perhaps this was a real reason XMMS got dropped?)

How's my logic? Is this a bad idea?

---

### Post by markbuntu on 2008-06-13
Alsa has plugins for pulseaudio and jack and oss and gstreamer and xmms2 midi and a wrapper for OSS apps. Here are a few essentials for alsa:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)
gnome-alsamixer (GUI alsa mixer for Gnome)

If you are missing any of these, you should get them.

I tried and tried (for weeks) to get pulseaudio working with everything but it just would not work to my satisfaction. So I gave up on pulseaudio and use alsa for everything because it works for everything. Besides, why put another layer on the sound management, what is the point?

The last thing we need is another layer between a jack app and the sound card.

I read somewhere that pulseaudio helps for upstreaming and network distribution etc, but how many people need to do that on their home desktop?

If you are trapped in pulseaudio hell you can get back to alsa by disabling pulseaudio from starting at boot and reenabling the alsa utils at boot. I used bum (Boot Up Manager) for the former and System/Admin.../Services for the latter.

bum is also great for speeding up the boot process in general by blocking the loading of modules you don't need like bluetooth and laptop stuff.

---

### Post by ofb on 2008-06-14
> **markbuntu said:**
> Besides, why put another layer on the sound management, what is the point?

Well, I'm trying to hold the charitable view that there is one, though I haven't found it yet.

But I'd also like to get things fixed, and I'm afraid Heron has a bit of a laundry list of things that don't work that I need to spend my evenings on.

So to experiment with getting the sound functional quickly, I've changed the Autodetects in the Sound Preferences for playback to ALSA, and unchecked Pulseaudio Session Management in Sessions. Reboot, and I still have the Pulse daemon running. Blocking is reduced, but I can still get some apps to conflict until I kill Pulse. Installed Burn, unchecked Pulse, rebooted, and the daemon is still there and still needs to be killed before I can rid myself of all blocking.

Persistant cuss, isn't it? Do I have to remove it via Synaptic to really stop it from starting?

---

### Post by markbuntu on 2008-06-14
Unchecking the Pulseaudio Session Management does not stop the daemon from loading at boot. In fact I still have that checked in Sessions but the daemon does not run. 

You really need to get bum (Boot Up Manager) from the repos and do it there.

Also make sure that you have the alsa-utils checked in Sys../Admin../Services.

I don't know about removing it with synaptic. There seems to be a lot of stuff it will take down with it when it goes so I didn't try that.

---

### Post by ofb on 2008-06-14
Sorry for the typo above. I did install BUM (not BURN) and unchecked PulseAudio Sound Server.

As described, this did not stop the daemon loading at boot. Did it for you?

Meanwhile I added alsa-utils in Sys>Admin>Services per your latest suggestion, and that makes no difference to any of the above. And yup, I'm doing full reboots, not just restarting the desktop.

I'd suppose we may have slightly different results for required modules due to hardward differences. However stopping the daemon from loading should be the same, and I would have though BUM would take care of that.

As far as I can tell, stopping that daemon is all I need to do to completely fix sound for this machine now.

---

### Post by markbuntu on 2008-06-14
When you used bum did you click on the apply button at the bottom left?

I forgot to do that once and was distraught that pulsaudio was still there after reboot. It was so frustrating....

---

### Post by ofb on 2008-06-15
I used right-click for 'deactivate and apply now', and pulse remained unselected in BUM when I had a look on the next boot. But anyway just went back and hit the apply button now, and rebooted, and yup pulse is still loaded.

---

### Post by ofb on 2008-06-25
The only way I've found to really stop pulse from loading (and thus stop my sound apps from conflicting) is to go System > Preferences > Sessions, then Add a new item with the command 'killall pulseaudio'.

People reading along are advised to follow the links above to where others have the opinion that this is not a solution, and offer detailled explanations about how to make pulse work. 

That might work for some people and those people should probably do it. For the rest of us with apparently unsupported apps by pulse (and gamers, judging by the forum threads) the above is what I had to do to finally get rid of this new layer that does not yet work.

Maybe Ubuntu figures pulse will be fully functional before Heron LTS is expired, and maybe pulse clears up, or will clear up, other troubles I've never had with Linux sound. Presumably there was solid reason for creating and adding it, so probably the first thing you should do is try to make it work.

---

### Post by ofb on 2008-06-26
One more thing for people reading along, the way to use ut2004 without it conflicting with your music player is install alsa-oss.

Then in my case, change the menu item command from 'sh ut2004' to 'aoss sh ut2004'. If your menu item command is just 'ut2004', then you'd just use 'aoss ut2004'.

---


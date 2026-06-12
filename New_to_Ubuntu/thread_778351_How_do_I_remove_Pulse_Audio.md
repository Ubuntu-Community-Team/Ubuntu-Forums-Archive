---
title: "How do I remove Pulse Audio?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-02
Don't ask why, please....  I'd just like my sound system to be the way things were when 7.10 was on here.  Again...DO NOT ask me why.  I've expressed my feelings [elsewhere]("http://ubuntuforums.org/showthread.php?t=754125") already.

---

### Post by rubicon on 2008-05-02
Remove **pulseaudio** packages (better in synaptic), install appropriate alternatives for them (e.g. libsdl1.2debian-alsa instead of libsdl1.2debian-pulseaudio), then remove all unneeded dependencies (sudo apt-get autoremove).

That'll hopefully do it. Though it's a pity for me that one want to remove PA (you asked not to ask why, oh well, ok).

---

### Post by rubicon on 2008-05-02
Oh crap, I forgot! Make sure you inverse-pass (:P) this guide: [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

### Post by diablo75 on 2008-05-02
Are there any details guides out there that show how to properly do this.  The words "should work" are unsettling to me.

---

### Post by rubicon on 2008-05-02
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) , go down to *PulseAudio Removal*

---

### Post by diablo75 on 2008-05-02
> **rubicon said:**
> [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) , go down to *PulseAudio Removal*

Well, the guide asks me to "remove the extra lines in /etc/asound.conf".   Unfortunately, no such file exists.

The next step tells me to go to my System>Preferences>Sound menu, and change everything to ALSA.  But still, for some reason, the Bass/Treble mixers still do nothing (the speaker-looking icon in the top taskbar, that is).

Also, when I tried to remove the "pulse-audio" package via synaptic, it said I would have to also remove the "ubuntu-desktop" package as well, which I will not attempt because I'm not that stupid.

IS IT JUST ME, OR HAVE I JUST BEEN SUBJECTED TO A FORM OF VENDOR LOCKIN?  (Sorry, I have no idea how to express my outrage about this).  I F-ING HATE PULSE AUDIO!!!!  I want it off my system until it's finished and ready to support surround sound cards, and can handle simple stuff like Bass and Treble adjustments out of the box.  Excuse this blunt rant, but if you totally LOVE Pulse audio, you're a blind fanboy who needs to buy a decent sound card that does everything pulse audio TRIES TO DO but does better via hardware.  I have an Audigy that NEVER once had a problem playing sounds from multiple sources.  I DID NOT WANT PULSE AUDIO!

](*,)  <---I wish this little animation was more graphic and disturbing.  Not to express how angry I am right now, but to express the anger that has built up since the release of 8.04 and seeing little done about this sh-t.

---

### Post by forumache on 2008-05-02
Easier solution.

Type in a terminal: pulseaudio -k

This will kill pulseaudio. No need to uninstall anything. When it will be patched, then it will be no need to kill it.

After killing it, you need to restart all sound using applications (like rhythmbox, firefox (flash)), in order for them to pick the default card (instead of pulseaudio virtual card which does not exist anymore).

I think it is a better solution than messing with the package system.

Enjoy,
Dan.

---

### Post by diablo75 on 2008-05-02
> **forumache said:**
> Easier solution.

Type in a terminal: pulseaudio -k

This will kill pulseaudio. No need to uninstall anything. When it will be patched, then it will be no need to kill it.

After killing it, you need to restart all sound using applications (like rhythmbox, firefox (flash)), in order for them to pick the default card (instead of pulseaudio virtual card which does not exist anymore).

I think it is a better solution than messing with the package system.

Enjoy,
Dan.
Edit:  Scratch that...  For some reason, even after trying this command in terminal, the bass and treble is still not adjustable.  Sorry to be such a whinny B$%^&, but this is functionality lost from an "upgrade".  And it wasn't even an actual upgrade.  This is a fresh install.  Should I take back 7.10's sound and slower performance?

---

### Post by rubicon on 2008-05-02
Look. ubuntu-desktop is just a mere meta-package. If you delete it, you won't get automatically updated to *intrepid*, for example. All other packages won't be touched *in any way* by this action and will be upgraded automatically whenever possible. Not even talking about losing them, duh.

Come on, where is your spirit of adventures :D Just uninstall all that, delete asound.conf (if any) and pick ALSA everywhere! Don't forget to share impressions ;) You're on verge of downgrading so why not try this anyway?

---

### Post by diablo75 on 2008-05-02
> **rubicon said:**
> Look. ubuntu-desktop is just a mere meta-package. If you delete it, you won't get automatically updated to *intrepid*, for example. All other packages won't be touched *in any way* by this action and will be upgraded automatically whenever possible. Not even talking about losing them, duh.

Come on, where is your spirit of adventures :D Just uninstall all that, delete asound.conf (if any) and pick ALSA everywhere! Don't forget to share impressions ;) You're on verge of downgrading so why not try this anyway?

My spirit of adventure went out the window after waiting for weeks for Pulse Audio (or the rest of Ubuntu) to catch up with the number of speakers I've had on this computer for years, and have never once had a problem using all of them with joy.

I started to go through Synaptic to remove more pulse audio related packages, and when I saw that it wanted to remove Amarok, I lost my nerve again and what little spirit of adventure is apparently necessary  to reverse these irritating side effects of "upgrading" to 8.04.  Have you ever had more than 2 speakers on your computer and gotten used to it over the years?  All I am trying to say is, you come to take things for granted... like out of the box perfect functionality of your sound card.  It was a reality for me, until Pulse Audio.

---

### Post by rubicon on 2008-05-02
[COLOR="Gray"]You tired of the system and think that all this progress is just a darn step back? Almost gave up squeezing proper video/sound/anything from the system that in the previous release were right here, in your hands? Yeah, i think i know that feeling.

My impressions of the 8.04 aren't the best either, but this is **the progress** in the widest meaning of this word. Through bugs came features :P

If you can, try another distro. Not easy one, for example, Gentoo, Source Mage, install something on PS2/3, then come back on Ubuntu. Something that you've been finding irritating and buggy before &#8212; you'll find great and easy. I tried Arch, and so I came back here. Not anymore I care about PA or bulletproof X.[/COLOR]

Well, back to your problem. I quess it will just be a little bit more tricky than I thought. Removing pulseaudio will remove amarok, because one of links in "PA dependencies chain" is something that Amarok depends on. There should be some way to keep amarok and remove PA at the some time... If not, try just disabling it, and select ALSA everywhere. There are a lot of places for that, so be sure to check them all. Again, that two links will help you finding these places. Anyway, you can always downgrade... 

Well, good luck.

---

### Post by Bastaard on 2008-05-03
I feel you diablo. ALSA worked just fine and now Pulseaudio came to **** things up for everyone.

---

### Post by PC_load_letter on 2008-05-11
Diablo: Any luck in removing PA? I'm still on the fence regarding Heron. Audio quality + Amarok are ESSENTIAL to me. I have a pro sound card installed and I can not compromise sound quality. Would you please update us on what you managed to do?
Thanks.

---

### Post by whitethorn on 2008-05-11
I have a 5.1 surround system running off a USB 24 bit Creative Live card.  I have surround sound using Pulse Audio, but I gotta say I tried out a whole bunch of things b4 it started working, and there's no real ALSA support for my card, I had to use a different asound.conf script. I found a small program written by someone on another thread, which pretty much setup my Pulse audio properly. 

Found here
[http://ubuntuforums.org/showthread.php?p=4790443](http://ubuntuforums.org/showthread.php?p=4790443)

And I changed these lines in the /etc/pulse/daemon.conf 

 default-sample-format = s16le
 default-sample-rate = 48000
 default-sample-channels = 6

If you decide to give this a try, you might want to set the sample rate to 44100 (it's the usually the default sample rate)

---

### Post by diablo75 on 2008-05-11
> **PC_load_letter said:**
> Diablo: Any luck in removing PA? I'm still on the fence regarding Heron. Audio quality + Amarok are ESSENTIAL to me. I have a pro sound card installed and I can not compromise sound quality. Would you please update us on what you managed to do?
Thanks.

I would like to say so, but I've decided to just cave in and wait for the software to work itself out via updates.

I have, however, come across one useful thread that appears to have one simple command that might knock it all out for you, but I've not tried it myself:

[http://ubuntuforums.org/showthread.php?t=782139](http://ubuntuforums.org/showthread.php?t=782139)

---

### Post by abhiroopb on 2008-06-17
May be too late, but just uninstall ALL packages relating to pulse audio (except the one that tells you that it will uninstall amarok, etc). Then in amarok go to settings>configure amarok>engines select alsa in sound device. Restart. Should fix issues. I HATE PA...seems like for every step forward ubuntu takes it takes 2 steps back.

---

### Post by badmotor on 2008-06-18
I'd like to add one more vote about the annoyance of Pulseaudio.  Not that there's a poll running or anything.... or is there?

---

### Post by monkotronic on 2008-06-18
I couldn't agree with  you more about pulse audio.  My card keeps randomly not working anymore.  One time it puts the proper card in as the primary and then another time it puts the second card in which is only for capture and then nothing works.  today it is showing no sound cards and nothing is working.  alsa was great.  always worked.

---

### Post by YaroMan86 on 2008-06-18
I used to have issues with Pulse Audio until it came bundled with Hardy. Then I had no problems. :D

---

### Post by diablo75 on 2008-06-20
I think the phrase "birth pangs" is in order.  Fortunately, I've had time to heal, and so has the code behind Pulse.  On recent fresh installs, it is functioning as I had hoped it would in April.  Treble/Bass controls work, surround sound levels work and don't require me to edit a config file... those were my main complaints.

---

### Post by abhiroopb on 2008-06-20
Sorry to be disrespectful but birth pangs? I mean come on this is version 8.04! This is the point where all the polish is coming into it, where it is (pardon my saying) starting to "just work" like macs (I know i know macs only have to cater for one set of hardware types). Anyway my point is in Gutsy my sound and wifi worked fine, in hardy neither worked well (wifi didn't work at all). Everything else seems great but wifi is ESSENTIAL, and without it working its difficult to  diagnose the problem. Its like Hardy took a step back there.

---

### Post by MillDaKill on 2008-07-29
Has anyone done this successfully.  My pulse audio keeps crashing but getting rid of pulse could be kind of tricky.  If you run gnome desktop, the ESD sound daemon has been replaced with the pulse drop in.  I would love to hear from anyone that has successfully removed PA and is up and running.

---

### Post by Tom--d on 2008-07-29
I just removed it. 
And Changed everything to alsa. 
Works perfectly :)

---

### Post by unebaguettesvp on 2008-08-02
i removed it successfully as well! in synaptic, i did a search for pulseaudio. i removed everything except for libasound2-plugins, libpulse0, and libsdl1.2debian-all. then i reinstalled esound to get my system sounds working again because i uninstalled pulseaudio-esound-compat (which wasn't working 100% to begin with). then i replaced my old .asoundrc and .asoundrc.asoundconf files. and everything worked!!! i had to change somethings back to alsa, like everything in System->Preferences->Sound. i also had to increase the volume on some channels in alsamixer.

i'm so glad i got rid of pulseaudio! none of my emulators worked, neither did audacity!

Edit: be careful of installing esound!!! caused gnome to freeze on another computer!

---

### Post by markbuntu on 2008-08-02
You can completely disable PulseAudio but it is tricky, it seems the PA devs were determined to make it a difficult as possible to keep it from starting up because it is everywhere. You can disable it at boot with Boot Up Manger (bum), and then you can disable it at System/Services and System/Preferences/Sessions. Then you can uncheck Mixing in System/Preferences/Sound and get esound with Synaptic to replace that.

You also should go into /etc/pulse/default.pa and comment out the lines in the entire sections with 

load-module mdule-hal-detect 
load-module module-esound...
load-module module-gconf...
load-module module X11....

and the line with

load-module module-default-device-restore

which I am sure has caused no end of frustrated people who set up their sound perfectly only to find it back the way it was every time they rebooted. Acutually, you could probably comment out the entire file. AN do not forget ~/.pulse.

---

### Post by Ferrat on 2008-08-26
> **unebaguettesvp said:**
> i removed it successfully as well! in synaptic, i did a search for pulseaudio. i removed everything except for libasound2-plugins, libpulse0, and libsdl1.2debian-all. then i reinstalled esound to get my system sounds working again because i uninstalled pulseaudio-esound-compat (which wasn't working 100% to begin with). then i replaced my old .asoundrc and .asoundrc.asoundconf files. and everything worked!!! i had to change somethings back to alsa, like everything in System->Preferences->Sound. i also had to increase the volume on some channels in alsamixer.

i'm so glad i got rid of pulseaudio! none of my emulators worked, neither did audacity!

Edit: be careful of installing esound!!! caused gnome to freeze on another computer!

Yeah that's my problem I want to remove Pulse, pulse messes everything up one way or another but when I remove it and install esound gnome freeze upon startup =/ 
anyone have a solution for this??

---

### Post by unebaguettesvp on 2008-08-28
> **Ferrat said:**
> Yeah that's my problem I want to remove Pulse, pulse messes everything up one way or another but when I remove it and install esound gnome freeze upon startup =/ 
anyone have a solution for this??

i fixed my esound problem by doing this:

[http://ubuntuforums.org/showthread.php?t=855764]("http://ubuntuforums.org/showthread.php?t=855764")

good luck!

---


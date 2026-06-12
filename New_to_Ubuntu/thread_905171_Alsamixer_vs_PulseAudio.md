---
title: "Alsamixer vs PulseAudio"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by fredfelter on 2008-08-30
Thinkpad T22, Ubuntu Hardy

The sound issues in Ubuntu are beyond arcane. For example:

   Terminal > Alsamixer says PulseAudio for card and has only Master for playback and Capture for Capture. However Volume Control (my sound card - Alsamixer) offers a variety of sound options. What is the relationship of those 2 interfaces? Do they need to be coordinated in settings?

   There is no listed PulseAudio in Applications > Sound&Video. Since I cannot record sound in any app (Skype, Sound Recorder, Ekiga, etc.) that I´ve tried to date and since many suggested fixes say to check settings in Sound&Video > PulseAudio I'm stuck.

Thanks in advance.

---

### Post by gmxgeek on 2008-08-30
personally, i configure everything to use alsa, and do a killall of pulseaudio, since for me it creates for problems than it is worth. But, that might just be me.

---

### Post by prshah on 2008-08-30
> **gmxgeek said:**
> personally, i configure everything to use alsa, and do a killall of pulseaudio, since for me it creates for problems than it is worth. But, that might just be me.

I'm the reverse; only pulse and no alsa; but as you said, it's a matter of preference :)

I guess OP needs to go any one way, rather than both. You can select from System-Preferences-Sound.

---

### Post by gmxgeek on 2008-08-30
> **prshah said:**
> I'm the reverse; only pulse and no alsa; but as you said, it's a matter of preference :)

I guess OP needs to go any one way, rather than both. You can select from System-Preferences-Sound.

My main issue is wine compatability, since if i have PA open while launching wine apps, i get silence from everything running off PA. So, if i kill PA, then everything runs on ALSA, and no problems

---

### Post by t0p on 2008-08-30
I used to have problems with pulseaudio - and with flash 9. But then I read the guide [linked to here]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472"), and my problems were solved.  This fix gets pulseaudio working right, and also installs flash 10.  No more sound problems or flash problems.  Well worth trying.

---

### Post by Nepherte on 2008-08-30
In the end pulseaudio will use alsa (or oss) to output sound.

From wikipedia:
In a typical installation scenario under Linux, the user configures ALSA to use a virtual device provided by PulseAudio. Thus, applications using ALSA will output sound to PulseAudio, which then uses ALSA itself to access the real sound card

---

### Post by alexcckll on 2008-08-30
> **t0p said:**
> I used to have problems with pulseaudio - and with flash 9. But then I read the guide [linked to here]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472"), and my problems were solved.  This fix gets pulseaudio working right, and also installs flash 10.  No more sound problems or flash problems.  Well worth trying.
Is this likely to be packaged up for Hardy officially?  I'd rather not muck around with unofficial repos..

---

### Post by Nepherte on 2008-08-30
I doubt it will be officially fixed for hardy. In Intrepid development it is fixed though, that's where he got the packages from. You can fix it by doing it manually (installing from official repositories and edit configuration files yourself) [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) or you can use that unofficial repo (which does exactly the same thing) [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472). I've tried both ways and it always worked.

---

### Post by fredfelter on 2008-08-30
Thanks for the comments and suggestions.

Still no ability to record sound in Sound Recorder or Skype.

I updated PulseAudio according to the link above and I now have something called PulseAudio Device Chooser in Apps > Sound & Video. Do I need to configure it in order to make things work correctly?

In System > Preferences > Sound > Audio Conferencing > Sound Capture there is no Autodetect option as suggested by the PA guide. What should I set it to, Alsa or PA?

In Skype > Options > Sound Device > Sound In > what should my choice be since Default kills the call shortly after it rings and either Pulse or my sound card choices do not record for the test call although they do give a test sound.

Finally it looks like it&#347; necessary to have a functioning Sound Recorder to have Skype work. Any idea how to get Sound Recoder up to speed.

Thanks.

---

### Post by nicedude on 2008-08-30
You can find a deb of flash 10 for hardy with a simple google search. Flash 10 works much better for me than flash 9 did.

I have a question though is there anyway to remove pulse or alsa completely and use the one you keep ? If so I would appreciate someones input since it seems stupid to have both ( I currently use alsa for everything anyway but instead of killing pulse I would like to know if I can remove it, like I do to jockey :-) )


Thanks if anyone knows the repercussions of this.

---

### Post by Nepherte on 2008-08-31
> **nicedude said:**
> I have a question though is there anyway to remove pulse or alsa completely and use the one you keep ? If so I would appreciate someones input since it seems stupid to have both ( I currently use alsa for everything anyway but instead of killing pulse I would like to know if I can remove it, like I do to jockey :-) )
I wouldn't remove alsa, since pulseaudio will not be able to produce sound (unless you install oss instead, see my previous post). You can however safely remove pulseaudio and set everything to use alsa. Just look in synaptic for packages with pulseaudio and remove those.

[QUOTE=fredfelter]Still no ability to record sound in Sound Recorder or Skype.[/QUOTE]
Here is more information on how to make skype work with pulseaudio: [http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype) I hope it helps. I don't use skype, so can't really guide you there.

> In System > Preferences > Sound > Audio Conferencing > Sound Capture there is no Autodetect option as suggested by the PA guide. What should I set it to, Alsa or PA?
Directly taken from that guide: "6. Go to System/Preferences/Sound. Set all "Sound playback" options to "Autodetect", and set "Sound capture" to "ALSA"". In other words, you have to set sound capture to alsa.

---

### Post by billgoldberg on 2008-08-31
> **gmxgeek said:**
> personally, i configure everything to use alsa, and do a killall of pulseaudio, since for me it creates for problems than it is worth. But, that might just be me.

Same here, but I also remove PulseAudio from my system.

I hope PulseAudio will do better in Ibex.

---


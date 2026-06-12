---
title: "Sound requires reboot"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by agobox on 2008-07-22
Hi,  

I have a six speaker surround system which sounds great.  However, after shutting down and starting up the sound doesn't work at all.  If I reboot, the sound does work.  Any ideas on how I can fix this?

I'm completely new to Ubuntu.  I searched the forums but didn't see any answers to this problem.

thanks for any help,
agobox

---

### Post by Dr Small on 2008-07-22
What exactly do you mean, the sound doesn't work?
Do you get any errors when trying to use sound?

---

### Post by agobox on 2008-07-23
Hi Dr.,

well, no sound at all.  When CDs play no sound comes out of the speakers.  The Ubuntu start-up drum roll doesn't play.  No system sounds.  

There are no error messages, and everything else seems to work normally.  But, once I re-boot, all sounds work fine.

One more piece: I have to use the Re-Start to get sound.  If I shut down completely, and boot up again there is still no sound.  

baffled.

thanks for your help,
ago

---

### Post by sydbat on 2008-07-23
I'm having a similar problem, except I have some sounds, but not others.

---

### Post by billgoldberg on 2008-07-23
I don't really have a idea.

Some things you can try:

Switch from pulse audio to alsa or something else  in system-> preferences ->sound (use the test button).

Open up alsamixer (using the terminal) and look if nothing is muted (you could also download and use gnome-alsamixer).

Install "asoundconf-gtk" and open it to make sure you selected the correct card.

Those are the things I would try.

---

### Post by Dr Small on 2008-07-23
If you have a .wav somewhere, try running:
```
aplay /path/to/file.wav
```

And you could see if you got any errors, or you could just launch Totem, VLC, Mplayer from the terminal, and when it doesn't play, look at the output in the terminal too see what the problem could be.

First off though, make sure you are in the 'audio' group:
```
groups
```

If not, then run:
```
sudo adduser $USER audio
```

Dr Small

---

### Post by sydbat on 2008-07-23
The strange thing for me is, I have sound for some things and not others...when I reboot it does not seem to "fix" this. Maybe I broke something with an application install, but Synaptic has no "Broken" applications listed.

When I say some sound, I can visit Youtube and see/hear fine, but when I try Amarok (which was working fine the other day before the last update) I get this:```
xine was unable to initialize any audio drivers
```and yet Rhythmbox is fine. Weird.

---

### Post by agobox on 2008-07-23
Hi,

I'll give the suggested solutions a try.  I assumed (I know, don't assume) that it was something deeper in the system - like it doesn't recognize me as the user.  When I do a fresh start, the sound settings have disappeared.  When I Re-Start, the sound settings are the ones that work.  

I'll post back after I have time to try the solutions mentioned above.

thanks for all the help,
agobox

p.s. When I was on XP, the front left speaker never had sound no matter what I did, so I'm psyched that it works in Ubuntu.

---

### Post by agobox on 2008-07-24
Hi,

I tried a few different things and lost all sound for a while.  I got it back, but with the same problem of having to Re-Start.  Here's the output from the terminal:

sudo asoundconf-gtk
 
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

(there was no card selected; the motherboard soundcard and my Audigy were on the dropdown list and I selected the Audigy)

You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

(I couldn't find asoundconf list, so tried)

sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
V8237
Audigy2

If I re-run asoundconf-gtk there isn't anything selected or highlighted.  I'm not sure what parameter I'm leaving out.

Also, if I run Hardware Testing, only the motherboard soundcard is available, and it produces no sound.

when I try aplay /path/to/file.wav I get the message "no such file or directory".  I do have audio as a group.  I'm playing in SoundJuicer, so I don't know if that effects this.

thanks,
ago

---

### Post by agobox on 2008-08-03
Hi,

I waited a week to make sure things worked consistently before replying.  I've got sound now on every start up.  I uninstalled and removed asoundconf-gtk, then reinstalled it.  I also made sure that alsamixer was on the correct soundcard, and I've had no problems since then.  

I know both asoundconf-gtk and alsamixer were set up correctly before, so I think there must have been something in the newer version that wasn't in the older.  Or maybe it just didn't install correctly the first time.

Anyway, many thanks to all of you who helped.  Is there a protocol for thanking properly?

best regards,
agobox

---


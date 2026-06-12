---
title: "Version 11.10 - sound system no longer recognised"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by harfin on 2011-11-15
Apologies if not correct place!

A short time ago I up-graded to Oneiric Ocelet.

Since that time I have no access to sound controls - I have been unable to get the Pulse Sound programmes to run.

The error given when I try to run (Pulse Audio) is:
'Connection to Pulse Audio failed. In this case this is likely because Pulse_Server in the environment/X11 Root Window Properties or default-server in client.conf is misconfigured. This situation can also arise when Pulse Audio crashed and left stale details in the Root X11 window. If this is the case then Pulse Audio should autospawn again, or if this not cofigured you should run start-pulseaudio-x11 manually'

The Pulse Audio window remains on the desktop, appearing to be attempting to do something (unsuccessfully!).

I have tried removing Pulse Audio and then installing again, that made no difference.

I have no sound icon on the top toolbar (I did have that prior to upgrading to 11.10.

I have tried rebooting several times, again with no positive outcome.

I have a Dell E520 with an on-board Intel Sound system; there is a 1.5Gig memory and a 3.06Mghz processor.

In addition, my system is now slower than a wet week (or the implementation of a politicians promise!). 

Can anyone point me in the right direction please?

Alan A Hart

---

### Post by harfin on 2011-11-16
All is forgiven Ubuntu!  The latest update today (16 Nov) has restored my sound controls and speeded the system up to it's former glory!
Thankyou U!!
Alan

---

### Post by raja.genupula on 2011-11-16
[http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/](http://lkubuntu.wordpress.com/2011/07/20/sound-troubleshooting/)

---

### Post by harfin on 2011-11-18
Despite initial success after the new version of Pulse Audio and system upgrade 2 days ago, I am now back to being unable to open Pulse Audio.

I worked through the page of checks from raja.genupula, and although playing and hearing the playing of sound CD, when I try to open Pulse I get the same error message as before, i.e.
'Connection to Pulse Audio failed. In this case this is likely because  Pulse_Server in the environment/X11 Root Window Properties or  default-server in client.conf is misconfigured. This situation can also  arise when Pulse Audio crashed and left stale details in the Root X11  window. If this is the case then Pulse Audio should autospawn again, or  if this not cofigured you should run start-pulseaudio-x11 manually'

I do note also that when Ubuntu starts (splash screen?) where I am asked for my user password, the sound indicator in the top right is showing at the extreme left point, i.e. I assume no sound.

Help!

Alan

---

### Post by harfin on 2011-11-18
An addition - this afternoon I now can see the sound icon active on the entry screen (splash screen?) - perhaps one of the steps in the the page of checks from raja.genupula did do something!

Still cannot get Pulse Audio to run; still get the same error message.

Any other suggestions?

Alan

---

### Post by harfin on 2011-11-19
Update Saturday 19 Nov
The sound icon on the splash screen has now gone back to extreme left (muted?)
However, I can now access Pulse Audio!
This Pulse Audio on again / off again is very frustrating.
Can anyone point me towards a resolution?

Alan

Update Sat 19 Nov evening
When I switched on this evening, guess what - no sound indication at splash screen stage and unable to open Pulse Audio - same old error message as before.

Please, any one have any ideas?

Alan

---

### Post by Gallando on 2012-08-22
Remove .pulse folder in your home directory and let PulseAudio recreate it by running:

pulseaudio --start

This fixed it 100% for me

---


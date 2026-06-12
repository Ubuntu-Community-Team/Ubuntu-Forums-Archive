---
title: "Lost sound from centre speaker"
date: 2015-06-06
forum: New to Ubuntu
---

### Post by geoff20 on 2015-06-06
Hi,
Running 15.04 and have lost sound from the central speaker of  HDMI 5.1. Have an Intel NUC.
Have eliminated the Amp and speaker as the problem.
Reinstalled pulseaudio, reinstalled unity.
The sound system in Ubuntu shows I'm running through HDMI/Display Port.When I do a test the left and right speakers are fine but I get nothing from the middle speaker.
This happened after Kodi crashed when trying to use  a plugin.Any suggestions would be welcome

---

### Post by geoff20 on 2015-06-07
Update.
Had the problem with a particular video and assumed that it was the case for all.(  what a silly billy)
Have now realised that it is only that video that is effected( so far ).
However, even though I have sound through the centre speaker and all speakers for other videos, I still do not have sound through the centre,the rear and subwoffer when I run a speaker check, only the front left and right.
I can't check for Intel drivers as the Intel Graphics Installer for Linux informs me that The Distribution is not supported.I am assuming that this means 15.04 as I had no problem with 14.10.

---

### Post by geoff20 on 2015-06-08
Still having problems.
Have found that the centre speaker is working but not receiving any dialouge from the video just background.This could explain why the test for the centre speaker does not work under HDMI 5.1 but I'm at a loss to where I go from here.

---

### Post by cariboo on 2015-06-08
Open a terminal, and open alsamixer:

```
alsamixer
```

and check if all the speakers are turned up enough to hear them. Once you have made the changes needed, save the settings using the following command:

```
sudo alsactl store
```

---

### Post by geoff20 on 2015-06-09
Hi 
Thanks for your help
I'm assuming that I should see controls for the speakers.Front, Centre etc
What I see is a Master, PCM, Mic,Mic Boss,Mic Boss,S/PDIF,Beep, Capture.
The card is listed as HDA Intel PCH
Chip Intel Valleyview2 HDMI.

---


---
title: "No audio lubuntu 12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by marmotman on 2012-04-30
Hi everybody, I just installed lubuntu 12.04 on my Asus Eee pc 1015 BXO and I've got an audio issue. 

It simply doesn't work in any way, I tried to install drivers and alsamixer but I still can't ear anything.

SOmebody can help me?

Thanks a lot :)

---

### Post by 00negative on 2012-04-30
> **marmotman said:**
> Hi everybody, I just installed lubuntu 12.04 on my Asus Eee pc 1015 BXO and I've got an audio issue. 

It simply doesn't work in any way, I tried to install drivers and alsamixer but I still can't ear anything.

SOmebody can help me?

Thanks a lot :)

You sure the sound just isnt muted? Dont remember if lxde has the speaker icon in the task bar for sound but I would check your sound settings

---

### Post by marinara on 2012-05-01
try the sound troubleshooting plan on the wiki

---

### Post by NikTh on 2012-05-01
You can also install pavucontrol to check your audio preferences.
```
sudo apt-get install pavucontrol
```

---

### Post by seppalta on 2012-05-01
Be sure that pavucontrol, pulseaudio, pulseaudio-utils and libgtk-3-0  are all installed.  Then play with the different settings in pulseaudio  volume control and the controls in your player until you get sound.    [http://douwil7.100webspace.net/linux/Tuning.html#17](http://douwil7.100webspace.net/linux/Tuning.html#17)[]("http://ubuntuforums.org/Be%20sure%20that%20pavucontrol,%20pulseaudio,%20pulseaudio-utils%20and%20libgtk-3-0%20are%20all%20installed.%20Then%20play%20with%20the%20different%20settings%20in%20pulseaudio%20volume%20control%20and%20the%20controls%20in%20your%20player%20until%20you%20get%20sound.%20http://douwil7.100webspace.net/linux/Tuning.html#17")[]("http://douwil7.100webspace.net/linux/Tuning.html#17")

---

### Post by marmotman on 2012-05-01
I installed pulseaudio and pavucontrol and now it runs! Can't test the headphones but thanks a lot anyway!!

---

### Post by dmmo on 2012-09-26
Hi everybody,
I faced a similar problem, however the pavucontrol program didn't help, my internal speaker keeps silence.

I have ASUS Eee PC R11CX with pre-installed UBUNTU 12.04

Does anyone have an idea what could be the reason and how to solve this difficulty? Headphones work well

---

### Post by shaktiman1234 on 2012-09-26
Can you post the result of following command in the terminal:
```
aplay -l
```

You may also look at [http://ubuntuforums.org/showthread.php?t=1366524#6](http://ubuntuforums.org/showthread.php?t=1366524#6)

---

### Post by dmmo on 2012-09-26
to shaktiman1234:
Here it is:

dmmo@dmmo-X101CH:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dmmo@dmmo-X101CH:~$

---

### Post by Gozhai on 2012-09-27
I had a similar problem.

Updated my Lubuntu yesterday,  and that seemed to kill the sound. 

I came here via google ... 

When I ran pavucontrol though, everything seemed fine.

I was about to give up, and then decided to toggle the MUTE button in the Output Devices tab. Had a DeadBeef playing in the background anyway, and the sound just started coming through just fine.

My sound was working fine pre update though. That said, I have had experiences with Linux in the past where the software had some sound setting or another muted by default. 

Give it a go, and it might just work for you.

GT

---

### Post by Zalmoksis on 2012-09-28
No sound with Lubuntu 12.04 on Asus EEE PC 1225B here.

Gozhai, where have you found the Output Devices tab?

Z.

---

### Post by Zalmoksis on 2012-10-05
It finally helped when I installed pulseaudio, although I cannot say I understand why exactly.

Z.

---

### Post by shaktiman1234 on 2012-10-11
hi dmmo,
Please tell me the model no. of your PC and manufacturer.
Use the output of this command **aplay -l ** to match the right entry from this table given in the post : [http://ubuntuforums.org/showthread.php?t=1366524#6](http://ubuntuforums.org/showthread.php?t=1366524#6)

---

### Post by dmmo on 2012-10-11
> **shaktiman1234 said:**
> hi dmmo,
Please tell me the model no. of your PC and manufacturer.
Use the output of this command **aplay -l ** to match the right entry from this table given in the post : [http://ubuntuforums.org/showthread.php?t=1366524#6](http://ubuntuforums.org/showthread.php?t=1366524#6)

Dear shaktiman,
I should have reported a bit earlier - the problem is solved. I still don't know what was the reason, I just used pre-installed OS (Ubuntu 12.04). About a week ago I simply reinstalled the system from a memory stick (the very same Ubuntu 12.04) and everything works well.

---

### Post by mafi127 on 2012-10-15
Sorry for bumping old theard but I have the same problem. I have sound in my headphones but If I remove headphones then I cant hear nothing. when I look in pavucontroll then its seems working the equalizer line is bumping, but I cant hear nothing, I have allso tryed to mute and unmute but still no sound.

Using lubuntu 12.04. any help plz :(

---

### Post by rdp011t on 2012-11-01
Installed all four - pavucontrol, pulseaudio, pulseaudio-utils and libgtk-3-0 
VLC, rhythmbox, audacity all work fine now.
Thank you
rdp011t 
(running on HP pavillion, yr 2001).

---

### Post by Cincinnatux on 2013-05-28
I realize this is an old thread, but I was just troubleshooting the same problem with my system and found a different option to work for me, so I thought I'd log it here.  In pavucontrol, select the Configuration tab and try different profiles to see if one of them works.  In my case, it was set to Audio Stereo Duplex and changing it to Audio Stereo Output made all the difference.  I'm too ignorant to guess at why that might be, but it's worth trying if you have a similar problem.

---

### Post by fortherush2010 on 2013-10-20
Just wanted to say thanks.  pavucontrol and pulseaudio made my Toshiba Satellite 1905-S277 (super old laptop) audio work.

---

### Post by mikmik on 2013-11-05
Something to add... for SKYPE users.
This cost me a stray on Mint 15 and a reinstall by the way...

So leave the default sound mixer (which sucks, old colour and cursor) and launch SKYPE (installed from repo).
Get to SKYPE sound options and discover a long list of cards/options. Select your fafourite... AND MAKE SURE THE 3 ITEMS HAVE THE SAME SELECT !

Until I tried that I was desperate... now USB headset works better than it ever has.

Hope this helps.

mikmik

---

### Post by secuono on 2014-02-09
Also have this issue.
Installed  pavucontrol, pulseaudio, pulseaudio-utils and libgtk-3-0 and messed with all of the settings, nothing. 
Have an HP desktop, Lubuntu latest version. 
What else can I try?

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by G_Ajith_Kumar on 2014-02-09
Hi, I have an HP laptop. I have similar hardware configuration as yours. The audio works well with 12.04 as well as 13.10. No problems so far.

On the Pulse audio volume control panel (pavucontrol) click the configuration tab and select all the options one by one. My audio works well on both Analog Stereo Duplex and Analog Stereo Output. So please check this out.

You could also try installing another audiovideo software such as vlc player (from the Ubuntu Software centre).

good luck :)

---

### Post by secuono on 2014-02-10
I did go through all the options and no change. 
Online videos have no sound as well. 

 Ubuntu Software centre gets no where, nothing available even w/o a search. Using the Synaptic package manager instead. 
Installed VLC, no change.

---

### Post by rcollins0618 on 2014-04-20
> **mafi127 said:**
> Sorry for bumping old theard but I have the same problem. I have sound in my headphones but If I remove headphones then I cant hear nothing. when I look in pavucontroll then its seems working the equalizer line is bumping, but I cant hear nothing, I have allso tryed to mute and unmute but still no sound.

Using lubuntu 12.04. any help plz :(

Two years later, and I have the exact same exact problem!
Ubuntu 14.04
Acer Aspire V5-122P
aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC282 Analog [ALC282 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

What's going on here? How do I fix this?
And no, my sound is not muted.

---

### Post by futak-eric on 2014-08-31
+1 for pavucontrol; installed, messed around with some settings for a few minutes and sound! beautiful sound! :guitar:

Thanks all

---


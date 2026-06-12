---
title: "Hardy sound problem - alsamixer"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by cairnsww on 2008-06-14
Hardy sound problems - alsamixer
I have no sound at all after upgrading to Hardy.

I have been working through the Comprehensive Sound Problem Solutions Guide at [http://ubuntuforums.org/showthread.p...t=82801G+Sound](http://ubuntuforums.org/showthread.p...t=82801G+Sound) and reached the stage where it advised me to check my alsamixer settings by typing alsamixer in a terminal. When I do this, I get:

ALSA lib control.c:874snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

It seems that this might be THE problem. Any advice on what i do now?

Thanks,
Bill

---

### Post by cairnsww on 2008-06-14
Bump

---

### Post by alienexplorers on 2008-06-14
Do you have ALSA-BASE installed.  Do you also have ALSA-UTILS, GSTREAMER0.10-ALSA installed.

---

### Post by cairnsww on 2008-06-14
Yes - all these are installed

---

### Post by cairnsww on 2008-06-14
Bump - anyone any ideas?

---

### Post by ukripper on 2008-06-14
This may help - [http://ubuntuforums.org/showthread.php?t=337276](http://ubuntuforums.org/showthread.php?t=337276)
try this first if this works -
add your user to the group "plugdev"

---

### Post by cairnsww on 2008-06-14
I don't see a group called "plugdev"

---

### Post by ukripper on 2008-06-14
> **cairnsww said:**
> I don't see a group called "plugdev"

create one and then try

---

### Post by cairnsww on 2008-06-14
I created a "plugdev" group and added myself to it. Still no sound and still the same message from the command 'alsamixer".

No progress so far.

I will work through the thread at
 [http://ubuntuforums.org/showthread.php?t=337276](http://ubuntuforums.org/showthread.php?t=337276)

Thanks so far ...

---

### Post by ukripper on 2008-06-14
> **cairnsww said:**
> I created a "plugdev" group and added myself to it. Still no sound and still the same message from the command 'alsamixer".

No progress so far.

I will work through the thread at
 [http://ubuntuforums.org/showthread.php?t=337276](http://ubuntuforums.org/showthread.php?t=337276)

Thanks so far ...

you can try following from the post:
>  Please execute the asoundconf(1) set-default-card macro in
    a Terminal now to refresh your user's configuration presets. You may
    accomplish this task by executing the following command in a Terminal:
    [B]
asoundconf set-default-card[/B]





Now all is good, alsa works.

Hope this helps someone else.

---

### Post by myromance123 on 2008-06-14
At first this was my problem with hardy too, but with an update the sound worked only,though, it was on my right speaker only ..my left is silent. I have tried the mute unmute and separating the speakers and playing with the volume that others have prescribed but to no avail.

 I am using Realtek ALC880, and i have tested my hardware. all speakers work and ubuntu does recognise the sound card.So I really need help here.


   I have overvome even broken dependencies, but I cant get sound working rite so please help me. I have only used ubuntu for about a day.:confused:

---

### Post by cairnsww on 2008-06-14
bill@Lawrence:~$ asoundconf set-default-card
You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

bill@Lawrence:~$ asoundconf list
Names of available sound cards:
Intel
bill@Lawrence:~$ asoundconf set-default-card intel
bill@Lawrence:~$ 

Looks good so far but still no sound. Itry -

bill@Lawrence:~$ alsamixer
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

Still no progress.

---

### Post by cairnsww on 2008-06-14
I seem to have posted this reply to the wrong thread - apologies.

I tried this and this is what I got:

bill@Lawrence:~$ asoundconf set-default-card
You have omitted a necessary parameter. Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

bill@Lawrence:~$ asoundconf list
Names of available sound cards:
Intel
bill@Lawrence:~$ asoundconf set-default-card intel
bill@Lawrence:~$

Looks good so far but still no sound. Itry -

bill@Lawrence:~$ alsamixer
ALSA lib control.c:874snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

Still no progress.

I am running with a completely standard Intel motherboard with a built in sound card:

bill@Lawrence:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Everything worked perfectly on 7.10 before I upgraded tp 8.04.

Surely this can't be a difficult problem?

---

### Post by markbuntu on 2008-06-14
Sounds like pulseaudio has kluged your sound. This happens to me every time I try to get pulseaudio to work no matter which guide I try. But, I have figured out a way to stop pulseaudio and get back to alsa. If the guides in the multimedia and video section or the Tutorials and Tips sections of the forums don't help, use my Emergency Sound Repair Guide

I wrote this after the second time following those guides. Don't get me wrong, they help a lot of people, just not me.

**Emergency Sound Repair Guide**

1. If you are using jack Kill jackd with system monitor or jack control.

2. Stop pulseaudio from loading at boot with Boot Up Manager (bum). You will have no success just disabling the PulseAudio Manager in Sessions.

3. Make sure alsa-utils runs at boot (System/Admin../Services)

4. Check with Synaptic that these are all installed:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

4. System/Preferences/Default Sound Card, choose the sound card. 

5. Sys../Pref.../Mutimedia Systems Selector, set all to alsa

6. Sys../Pref.../Sound, set all to alsa

7. Reboot

8. Use (your choice) alsamixer, alsamixergui, gnome-alsamixer, to configure the channels, volumes etc. Turn stuff on and put up the sliders. check mix, capture, cd, mic, etc, unmute, mute, blah blah blah...

9. Test with Rythmbox, vlc, totem, xine, gstreamer, etc. configure all preferences to alsa if available/possible.

10. Test Sound Recorder. set capture/mix level, enable record, turn on mic, unmute, mute etc, etc... fool with the mixer( volume control or the mixer itself) until it works right

11. Jack control. set driver to alsa. Make sure jackd is killed when app using it closes.****

good luck!

---

### Post by cairnsww on 2008-06-15
Thanks marcbuntu for your detailed reply. I have followed what I can of your suggestions:

1. How do I know if I am using jack and how do I kill it?

2. Done

3. Done (it was set)

4. All are now intalled

4 (second 4!) Now here's a thing. I click on System>Preferences>Default Sound Card and I get "Starting Default Sound" in the task bar and then it goes away without doing anything. Suspicious?

5. I don't have "Sys../Pref.../Mutimedia Systems Selector"

6. Done

7. I did that and still no sound.

---

### Post by ukripper on 2008-06-15
> **cairnsww said:**
> Thanks marcbuntu for your detailed reply. I have followed what I can of your suggestions:

1. How do I know if I am using jack and how do I kill it?

2. Done

3. Done (it was set)

4. All are now intalled

4 (second 4!) Now here's a thing. I click on System>Preferences>Default Sound Card and I get "Starting Default Sound" in the task bar and then it goes away without doing anything. Suspicious?

5. I don't have "Sys../Pref.../Mutimedia Systems Selector"

6. Done

7. I did that and still no sound.

Updating to latest alsa works for me all the time.
I use this guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by markbuntu on 2008-06-15
> **cairnsww said:**
> 

4 (second 4!) Now here's a thing. I click on System>Preferences>Default Sound Card and I get "Starting Default Sound" in the task bar and then it goes away without doing anything. Suspicious?

5. I don't have "Sys../Pref.../Mutimedia Systems Selector"



If that happens in step 4 then it is a sure sign that pulseaudio still controls the audio.

Put etc/asoundrc in the trash and try rebooting again. Sorry, I forgot that part and it is critical to getting this to work.


Do not worry about not having the Multimedia System Selector. I don't even know where that came from in my system. Setting Sound preferences should be enough.

If this still doesn't help you, try the guide at the top of the multimedia and video section of the forums. There is another extensive how to in the tutorials and tips section that will get you the latest libasound2 and flash 10. 

These did not help me for everything but they have been helpful for a lot of people.

---

### Post by cairnsww on 2008-06-18
Thanks for all who replied to my original query.

It turns out that it was a known bug on the Intel 82801H Audio controller.

The latest set of system updates fixes the problem.

---


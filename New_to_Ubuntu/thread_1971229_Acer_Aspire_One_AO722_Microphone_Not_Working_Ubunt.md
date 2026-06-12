---
title: "Acer Aspire One AO722 Microphone Not Working Ubuntu 12.04LTS"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by rakesh.swapna on 2012-05-02
Acer Aspire One AO722 **Microphone not working**. I have a good sound in speakers.

So far I have tried:-
1. I have downloaded this and installed but it gives an error ask me whether you want to report this, I choose yes, [http://people.canonical.com/~diwic/temp/alsa-hda-dkms-acer3830tg_0.1_all.deb](http://people.canonical.com/~diwic/temp/alsa-hda-dkms-acer3830tg_0.1_all.deb)
(I uninstalled it)

2. I am started with this 

# sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
# sudo apt-get update
# sudo apt-get install linux-alsa-driver-modules-$(uname -r)
# sudo apt-get install pavucontrol

But it gives an error "Unable to locate package linux-alsa-driver-modules-3.2.0.24-generic-pae" "Coudn't find any package by regex 'linux-alsa-driver-modules-3.2.0-24-generic-pae"

---

### Post by kdrainey on 2012-05-02
Me too!  Acer One D260 Ubuntu 12.04 no mike.   Sound settings-->Input  shows no device in the window.

---

### Post by Axxon95 on 2012-05-04
Same issue here with an Acer Aspire One in the D250.

---

### Post by brallan on 2012-05-08
same here, on my AO722. any help would be greatly appreciated.

---

### Post by brallan on 2012-05-08
here is the relevant output of lspci -v:
```
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Acer Incorporated [ALI] Device 0598
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

```

---

### Post by LewisTM on 2012-05-13
Taken from the Acer 522/722 [wiki]("https://help.ubuntu.com/community/AspireOne522")

* Open a terminal window and run "alsamixer"
* press F6 and choose "1 HDA ATI SB" as a sound card to configure by pressing Enter
* to see the mic-related sliders, press F5 and move the cursor keys to the right, only the outermost three sliders need to be set to a level of 56 by pressing the Up key
* then, by pressing the "c" key on each of the three sliders, the volume level of each right channel needs to be put to 0
* finally, quit alsamixer by pressing ESC.

Comments:
1) I set mic boost and capture to 100 and I get no hum. Muting the right channel is key.
2) When everything is set, execute
```
sudo alsactl store
```
3) The settings need to be restored at every boot. Add this command as a startup application
```
alsactl restore
```

Cheers!

---

### Post by brallan on 2012-05-14
that worked for me on my 722, but in testing with soundrecorder the background hum is very loud! are these settings right? Otherwise, sound playback works fine.
[IMG]http://dl.dropbox.com/u/53208596/alsamixer.png[/IMG]tried raising and lowering the volumes of ike boost and capture to no avail, there is always a loud hum. When I plug in an external mike it's still the same hum.

---

### Post by brallan on 2012-05-14
uff in [the community wiki]("https://help.ubuntu.com/community/AspireOne522") it says that there is no way to get rid of the hum, and indeed, even with an external mike I still have hum. What a bummer. [LewisTM]("http://ubuntuforums.org/member.php?u=680986"), do you have a 522 or a 722?

---

### Post by Jazqas on 2012-05-17
Not sure if this a real solution, but I installed qasmixer and played with the settings (mixer device : hw and mic boost)  until it sounded better. 
Hope this helps.

Jazqas.

---

### Post by LewisTM on 2012-05-21
I have a 722 running Xubuntu 12.04
No difference except I have beep set at 100%.
I also have the /etc/asound.conf specified [here]("http://ubuntuforums.org/showpost.php?p=11876897&postcount=5").
Tested on Skype and Sound Recorder and both record and play back fine.

---

### Post by nodjoim on 2012-06-19
Same problem here. Very loud hum and very distorted microphone sound, completely unusable. Running Ubuntu 64 bit 12.04 on Toshiba Tecra laptop.

---

### Post by brallan on 2012-06-20
Jazqas, any chance we can get a screenshot or the configuration you are using? are you using a 522 or 722?

thanks!
> **Jazqas said:**
> Not sure if this a real solution, but I installed qasmixer and played with the settings (mixer device : hw and mic boost)  until it sounded better. 
Hope this helps.

Jazqas.

---

### Post by zooey on 2012-06-23
I have similar problem on Acer Aspire one 722 netbook

i tried setting it like described with alsamixer and alsactrl but this doesn't worked for me. Then i installed the pavucontrol and set in Input left channel to maximum, right to minimum to microphone and also to internal microphone and set it to internal microphone. I also found that you must at every startup do this switching to microphone and than back to internal microphone.
I found that i can do it from command line with amixer utility.

I listed all sound cards with:

```
cat /proc/asound/cards

```
You will see sound cards which you have on machine associated with numbers. I am using card with number 1 -> this number i will use in amixer to select my card -> amixer -c 1

I listed all my sound card controls with

```
amixer -c 1 controls
```

to check my controls, there i saw Capture Switch control

Then i opened .profile file in home directory

```
sudo gedit /home/user/.profile
```

go to the end of file
and add this to lines

```
amixer -c 1 cset name='Capture Switch' off
amixer -c 1 cset name='Capture Switch' on
```

this turns off microphone and turns on,

now it should work out of box, hope it will help to someone ;)

---

### Post by biodojo on 2012-07-24
Hi we have 200 of these for student use running Ubuntu 12.04

I can get the internal mic to work but when on battery power I can't get the mic to be ready on start up. The user has to toggle the mic on and off (either by going to sound settings->chosing input->pressing the mute switch twice) or by clicking on a script that contains

pactl set-source-mute 2 1
pactl set-source-mute 2 0

and choosing Run in terminal.

I have tried adding this script to start up programs and to the .profile file

Additionally once this has been done, if the user stops recording something, does another activity, then reopens an app to record more, the mic needs to be re-toggled.

While this works, since these are for student use I would love for the mic to "just work". I can't 100% verify but it seems that when plugged in the mic stays working, so it might be something involving power saving. Any ideas on what to investigate?

---

### Post by nicolas.bernaerts on 2012-10-30
A complete Ubuntu 12.04 LTS installation procedure is available at
[http://bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722](http://bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722)

It should deal with the microphone problem (at least it has solved the issue for me).

Cheers.

---

### Post by agastly on 2012-11-02
> **brallan said:**
> uff in [the community wiki]("https://help.ubuntu.com/community/AspireOne522") it says that there is no way to get rid of the hum, and indeed, even with an external mike I still have hum. What a bummer. [LewisTM]("http://ubuntuforums.org/member.php?u=680986"), do you have a 522 or a 722?

I've just posted on another thread that I got rid of the noise on an Acer One 722 by leaving the mains adapter plugged in but switched off.  It gets rid of the mains hum.  Unplugging altogether still leaves hum.

---

### Post by appalachian on 2012-11-29
I would hold off on applying the fix found in [http://bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722](http://bernaerts.dyndns.org/linux/251-ubuntu-precise-acer-ao722)

If you are running Ubuntu Studio 12.04 LTS 

I had some issues rebooting after trying to update the kernel on my AO722-0828, the system never loaded.  I had to revert back to my 3.2.0 kernel.

---

### Post by Chew N Tobacca on 2013-02-02
I would like to post my findings on this topic. I have an Acer Aspire One 722-825 and had similar issues running Kubuntu 12.04. Up until today, I tried numerous fixes to get my mic working, from this thread and from [the Aspire One forums]("https://help.ubuntu.com/community/AspireOne522"), and nothing seemed to get my microphone working. When I was able to record anything, it was nothing but static, regardless of settings in alsamixer, pavucontrol, or qasmixer. Finally I just gave up.

Today I installed new updates, and thought I would play with it again. I opened Audacity using the previous settings in alsamixer, etc., and was able to record audio (very quietly, nearly inaudible). Adjusting the 'mic boost' in alsamixer allowed for a better quality recording with minimal background noise.

None of the audio related packages were updated as near as I can tell. I believe the fix was implemented with the kernel update (3.2.0-37-generic-pae).

I hope this helps other users with this model.

---

### Post by kel008 on 2013-06-10
Hi All,

This is my first post ever. I'm a relative newbie to Ubuntu (12 months) but love it -hope it helps someone. 

I had this microphone problem appear after upgrading from 11.10 LTS to 12.04 LTS and I have a Acer Aspire D257 but the problem also affected my HP Pavillion dv6 as well. This solution to seems (and I mean seems because its early days yet) to be hardware independent. After reading the various forums I did the following:
• went to the software centre and installed 'PulseAudio Volume Control' (pavucontrol)
• Once installed I opened it (type 'Pulse' into the Dash (Windows key))
• I selected the 'Input Devices' tab and 'microphone'.
• I then altered the settings to my desired (best) levels.
Note: you may need to have: 'System Settings, 'Sound' open at the same time (they are inter-dependant ie. working with the same hardware).

Cheers.

---


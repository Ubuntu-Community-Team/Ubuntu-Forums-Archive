---
title: "no sound"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by BirkMcGirk on 2008-08-14
so i just installed ubuntu 8.04 onto my desk top, and everything runs great, except for the sound. i have researched for a long time, and can only find the alsa mixer, and no, nothing is muted. so since that is not the problem, does anyone think they know what is? please keep in mind i am only 2 days into ubuntu, and have very little computer knowledge. thanks for your help.

---

### Post by Kevbert on 2008-08-14
Do you know what the audio card is ?  What's the make and model of the PC ?
Please go to Applications-Accessories-Terminal and type in the following:
sudo lshw -C multimedia
Please note that the Ubuntu commands are case sensitive. When prompted enter your log-in password.  Now select the text that is displayed with your mouse and go to the Edit menu and select Copy.  Open a new post here and paste that output using Ctrl+V.

---

### Post by pmlxuser on 2008-08-14
Oh are you listening using external speakers. did you plug at the right jack. or are the speakers turned on?

sometimes you find its just small details that we forget.

does your computer have a mute button (have you tried to change that setting etc)

can you be specific if not as above

---

### Post by BirkMcGirk on 2008-08-14
i have a gateway model no. MFATXPNT ES2 500XL if that helps. and here's the stuff from the terminal window.

 *-multimedia            
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
birk@birk-desktop:~$ 


thanks

---

### Post by BirkMcGirk on 2008-08-14
yeah i already checked, all sound is on, and its in the right jack. but thanks foir the ideas.

---

### Post by Kevbert on 2008-08-19
It looks like you need to modify the alsa-base file.  Go to terminal and enter
```
sudo gedit /etc/modprobe.d/alsa-base
```
Now you need to add a line at the end (this you'll need to experiment with as info is sketchy)
```
options snd-hda-intel model=ref
```
or
```
options snd-hda-intel model=m2-2
```
or
```
options snd-hda-intel model=m6
```
or
```
options snd-hda-intel model=pa6
```
After each change you need to save the file and reboot, then try out the sound.  You will only need one of these lines.  Please let me know which one works (if any).  It seems that this is the configuration file that's causing the problem.

---

### Post by cybrsaylr on 2008-08-19
Sometimes you have to reboot.
I just installed the new banshee version and lost all sound for some reason.
None of the other players would play sound either.
After a reboot all the sound came back for all the audio players I have.

This seems to happen once in awhile.
Don't know why.

---

### Post by BirkMcGirk on 2008-08-19
> **Kevbert said:**
> It looks like you need to modify the alsa-base file.  Go to terminal and enter
```
sudo gedit /etc/modprobe.d/alsa-base
```
Now you need to add a line at the end (this you'll need to experiment with as info is sketchy)
```
options snd-hda-intel model=ref
```
or
```
options snd-hda-intel model=m2-2
```
or
```
options snd-hda-intel model=m6
```
or
```
options snd-hda-intel model=pa6
```
After each change you need to save the file and reboot, then try out the sound.  You will only need one of these lines.  Please let me know which one works (if any).  It seems that this is the configuration file that's causing the problem.

none of these worked, do you have any other ideas?

---

### Post by leepesjee on 2008-08-19
You might be suffering from the Hardy/pulseaudio troubles. Try ```
killall pulseaudio
``` and try again.
If sound works now, you have your diagnosis. Than you can either follow
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
or
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Leo.

---

### Post by BirkMcGirk on 2008-08-19
> **leepesjee said:**
> You might be suffering from the Hardy/pulseaudio troubles. Try ```
killall pulseaudio
``` and try again.
If sound works now, you have your diagnosis. Than you can either follow
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
or
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Leo.

thanks for the help, but it didn't work

---

### Post by vitu on 2008-08-22
I have the same problem](*,),didn' figure out what the problem is. have still no sound- completely lost.

---

### Post by talibanned on 2008-08-22
I have the same problem as well.

been going at this for about 4 days now. getting nowhere.

i have reinstalled hard 4 times, tried intrepid yesterday but no joy.

i am running an ICH8 card.

---

### Post by BirkMcGirk on 2008-08-27
ok so i solved the problem, but i feel like a complete idiot. but maybe this will help you. 

double click on the speaker icon and make sure nothing is muted, then go to the "switches" tab and make sure  "audigy analog/ digital output jack" is unchecked.

---

### Post by EmilyRose on 2008-08-27
Just wanted to say thanks, super easy fix that is - but I had the same problem. Woulda taken me forever to think to check the lousy switches tab!! :D

---


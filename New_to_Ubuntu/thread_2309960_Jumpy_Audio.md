---
title: "Jumpy Audio"
date: 2016-01-14
forum: New to Ubuntu
---

### Post by dimethyl on 2016-01-14
Hi all,
I am running ubuntu 14.04 LTS on a System 76 Gazelle Professional laptop.  I am having a problem with audio output.  When I play an audio file (from any application), the sound sounds a little glitchy.  By glitchy, I mean the audio seems to jump around a little here and there by a few milliseconds or so.  The audio still runs normally besides the glitches, but I do hear some "skipping," almost as if you were listening to a scratched CD.  It happens whether I use headphones or the digital output (S/PDIF)

I ran the only audio test on System Testing and got the following message:

audio/alsa_record_playback_automated FAILED

Comment

INFO:root:Using PulseAudio identifier 2 (alsa_input.pci-0000_00_1b.0.analog-stereo) for input 
INFO:root:Using PulseAudio identifier 0 (alsa_output.pci-0000_01_00.1.hdmi-stereo) for output 
INFO:root: Player: Starting 
INFO:root:Recorder: Starting 
INFO:root:Sampling complete, ending process 
INFO:root: Player: Stopping 
INFO:root:Recorder: Stopping INFO:root:FAIL: 
Test frequency of 5035 is not in one of the bands with magnitude peaks 
INFO:root:WARNING: Microphone seems broken, didn't even record ambient noise

I don't see any info given in the above results that clue me into what I might try next to solve the problem.  What should I try next?

I would appreciate any help you have to offer.
Thanks

---

### Post by T.J. on 2016-01-15
If you are using Pulseaudio - which is likely, it has had a long history of being poorly handling certain audio chipset drivers. You may be able to solve your problem by adjusting the the driver parameters in the file: /etc/pulse/default.pa. You will need to have administrator permission to do this. Be sure to make a backup copy of the file before you make changes, just in case.


Edit the line:
load-module module-udev-detect

and add "tsched=0" so it will be:

load-module module-udev-detect tsched=0

Save it, and then preferably reboot, just to be on the safe side. Don't worry, this parameter should be perfectly safe to use. It will force PulseAudio try to not bulldoze over the sound driver's timing by forcing the scheduler to 0.

Hopefully, that will do it. Let me know if it persists.

---

### Post by dimethyl on 2016-01-16
Thanks for the response, T.J. The problem mysteriously went away after I first posted, but I made the change you suggested anyways to protect any future audial bulldozing.  I will let you know if I hear any problems later.

In case any other new users have this problem who are unfamiliar with the command line (terminal), one can get administrator permissions using terminal by following these steps:

1. Open terminal (you can find it by clicking the ubuntu logo at the top of your "dock" and typing "terminal" into the search bar.  Click the icon and it will open)
2. Type sudo -i
3. Press enter
4. Type in your password when prompted
5. Press enter again.  

If you entered your password correctly, you now have administrator permission

To access the necessary file from the command line, you can:
1. Type "sudo gedit /etc/pulse/default.pa" into the terminal.  
2. Press enter.  The file will open in an application used for editing text - gedit.
3. To find the right line, hold the ctrl key and press f, let go when you see the white search bar at the top of the window.  
4. Enter "[COLOR=#000000]load-module module-udev-detect" into the search bar 
5. Press Enter
6. When you see this line in the text, move your cursor to the end of it.
7. Ass one space after the line and add "[/COLOR][COLOR=#000000]tsched=0" after the previous line.
7. Save and close.[/COLOR]

---


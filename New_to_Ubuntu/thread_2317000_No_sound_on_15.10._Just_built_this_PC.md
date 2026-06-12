---
title: "No sound on 15.10. Just built this PC"
date: 2016-03-12
forum: New to Ubuntu
---

### Post by Skrullknight on 2016-03-12
Theres no sound and I have tried pretty much everything..But also for some reason alsamixer wont save settings.Help

---

### Post by sandyd on 2016-03-12
Hi, can you post the output of the following commands, which will allow us to identify your sound card hardware and help your further.

```

aplay -l
lspci | grep -i audio
lsmod
ps ax | grep -i pulseaudio
cat ~/.asoundrc
cat /etc/asound.conf

```

All commands are to be run as your normal user, not with sudo. 
Please ignore any errors that may be generated and paste the output anyways.

---

### Post by Skrullknight on 2016-03-12
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
skrullknight@Skrull22:~$ lspci | grep -i audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri HDMI/DP Audio Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)

---

### Post by buzzingrobot on 2016-03-12
All the little wires connected to the right places? :)  I've managed that more than once.

---

### Post by Skrullknight on 2016-03-12
Yep..But what wires would you be talking about in specific?

I just built this PC. and yeah about those cabels I checked them and they are all in correctly according to my mobo manual. Im hooked up through HDMI And I have an AMD A8 7600 APU.

---

### Post by sandyd on 2016-03-12
Hmm.

HDMI audio you say?

You might need to switch the sound output to HDMI audio.

Run
```

sudo apt-get install pavucontrol
```

Go to the menu and open "PulseAudio volume control".

Click on "Output Devices", your HDMI output and your computer's standard sound output should be there. If it isn't, go to the "configuration" tab, and enable it there (Change it from "Off" to something that matches your configuration).

Then, in the "Output Devices" tab, go to your computer's sound card (the one that does not say HDMI). Use the third button on the left of the sound card icon (This button looks like a checkbox) to set that sound card to "fallback". Make sure that the HDMI sound card does not have the fallback set. Re-open applications that play sound and try again. If you go to the "Output" tab, you should be able to see the applications using the "HDMI" output now instead of the onboard/sound card

Side note: All this can be done through System Settings -> Sound and changing the output to the correct one, but I prefer a solution that works no matter what GUI is used.

---

### Post by Skrullknight on 2016-03-13
For some reason I do not see the checkbox next to the icon on output settings

i see it now

still shows the default one and  on the pulse audio i switched everything to hdmi and it seems to be working as it shows the application running audio..but no sound

Also it says HDMI(Unplugged) but its plugged in..im using it right now..but still no sound

---

### Post by RobGoss on 2016-03-13
What version of Ubuntu are you running it might help others pin point your probelm

---

### Post by Skrullknight on 2016-03-13
15.10

---

### Post by RobGoss on 2016-03-13
At the top of your right hand screen is there an audio button? If it is click on that and you should see your Audio setting were you can choose and Play Sounds Throught

---

### Post by Skrullknight on 2016-03-13
OK yeah i see it. But before it only said digital output now it says HDMI aswell..so i guess were getting places..now whats next?

---

### Post by RobGoss on 2016-03-13
Are you trying to listen to music of watching videos on YouTube? sometimes people forget to click on little speaker at the bottom of the video to hear it.

---

### Post by Skrullknight on 2016-03-13
Nope.the speaker on youtube is up..and its for sure not youtube because i heard theres a a startup sound? would have never knew that existed lol.Plus i tried the test sound option.

No sound on anything

---

### Post by RobGoss on 2016-03-13
> **Skrullknight said:**
> No sound on anything

I came across this post that might help sort things out [https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html) I think its worth a try..

Play close attention to this section

[COLOR=#333333][FONT=Ubuntu][h=2][FONT=inherit]Check that the sound card was detected properly[/FONT][/h][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]Your sound card may not have been detected properly. If this has happened, your computer will think that it isn't able to play sound. A possible reason for the card not being detected properly is that the drivers for the card are not installed.[/FONT]
[FONT=inherit][FONT=inherit][FONT=inherit]
[LIST]
[*=left][FONT=inherit]Go to the [FONT=inherit][Dash]("https://help.ubuntu.com/stable/ubuntu-help/unity-dash-intro.html")[/FONT] and open the Terminal.[/FONT]

[*=left][FONT=inherit]Type [FONT=monospace]aplay -l[/FONT] and press [FONT=inherit]**Enter**[/FONT].[/FONT]

[*=left][FONT=inherit]A list of devices will be shown. If there are no [COLOR=#808080][FONT=inherit]playback hardware devices[/FONT][/COLOR], your sound card has not been detected.[/FONT]
[/LIST]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Skrullknight on 2016-03-13
Tried everything on there but when i test sound for the HDMI.i hear no sound at all.

It detects my hardware but nothing..IDK why.

---

### Post by RobGoss on 2016-03-13
> **Skrullknight said:**
> It detects my hardware but nothing..IDK why.

If you don't mind me asking is this a new installation? sometimes it's best to just do a reinstall to fixes some problems... That's the great thing about Ubuntu just a sugestion

---

### Post by Skrullknight on 2016-03-13
I reinstalled twice :( but nothing.

What should i do?

---

### Post by RobGoss on 2016-03-13
Did you try another Ubuntu distribution be for this one?

And what operating system did you have on your machine before you install Ubuntu 15.04

---

### Post by Skrullknight on 2016-03-13
No OS..and its 15.10. This is a newly built PC. And I put ubuntu 15.10 on it

Any more ideas?

---

### Post by RobGoss on 2016-03-13
Try a different version of Ubuntu and see how that goes, I'm just trying to figure out if it's something with Ubuntu or maybe the way your machine was build no pun intended

---

### Post by Skrullknight on 2016-03-13
I know I did everything right with hardware according to my mobo manual. But lets say if if it is hardware..what would it be? I plugged in HD audio in the right spot. but im sure i did everything right with Hardware

---

### Post by RobGoss on 2016-03-13
I just wanted to see if another version of Ubuntu would work as far as sound goes

I was reading this post also [http://askubuntu.com/questions/469804/ubuntu-14-04-no-sound](http://askubuntu.com/questions/469804/ubuntu-14-04-no-sound)

---

### Post by sandyd on 2016-03-13
Hmm.

Run
```

alsamixer
```
and go to the sound card by pressing F6.

Is there anything muted?

Also, have you tried the proprietary ATI drivers as well as the open source ones?

To install the proprietary ATI drivers, search for "Additional Drivers" in the Unity Dash. You should then be able to install the drivers from the window that appears. Note that you must have internet for the drivers to appear in the window.

---

### Post by Skrullknight on 2016-03-13
No nothing is muted and I have the catalyst control Center. But also I saw something on the software center and i looked up "ati" and something came up..had 2 stars..but when i attempted to download it, it said are you sure this may screw around with your Computer (it obviously didnt say that but in my terms it did basically) Should i install it?

Anyone?

---

### Post by Geoffrey_Arndt on 2016-03-13
Might be helpful to post a screen pic of your complete Alsamixer settings . . . also, did you say if the Live OS had sound? 

Further, the output from inxi -A will give a precise summary of your sound system (must install inxi first (sudo apt-get install inxi)).

---

### Post by Skrullknight on 2016-03-14
Would buying a sound card and just taking the easy way out fix this problem?

---

### Post by QIII on 2016-03-14
Hello!

That would avoid the problem, not fix it -- although it might allow you to use audio in the interim. :)

Please give the community a bit more time.  We are spread out all across the face of the globe and the person with the very best answer for you may simply not have seen your question yet.  So please don't bump your thread so often.

We ask that you wait 12 hours before bumping.  That puts you question in front of an entirely different population.

Cheers!

---

### Post by tea for one on 2016-03-14
Good evening

I assume that you are still connected via HDMI and you have video on your monitor but no sound?

Can you adjust the sound settings on your monitor?

Failing that, try this shot in the dark.............

Do you have a headphone jack on your monitor?

If you do, can you try to ascertain if you have sound from headphones via your monitor?

---

### Post by Skrullknight on 2016-03-14
Can't adjust sounds on monitor. And no headphone jack.i pretty much tried everything.

Nope no luck with that

Is it my monitor? i dont think my monitor has sound..would i need to buy speakers? If so. then good! :D

---

### Post by Geoffrey_Arndt on 2016-03-14
Have you tried to install "QasMixer" . . ?   It's available in the Ubuntu Software Center.    Might have better luck with it than the CLI version of Alsamixer . . . easier to update and save changes.

I'm fairly sure your sound system is compatible with Ubuntu . . . it's the default in several certified & preinstalled Linux PC's from Dell and Asus in particular.

---

### Post by tea for one on 2016-03-15
> **Skrullknight said:**
> Can't adjust sounds on monitor. And no headphone jack.i pretty much tried everything.

Nope no luck with that

Is it my monitor? i dont think my monitor has sound..would i need to buy speakers? If so. then good! :D

HDMI combines both sound and and video via one cable from your PC to a monitor/TV screen. I do not understand how you can have HDMI input into your monitor without having some sort of control over sound.

Monitors that can receive HDMI input often have other hardware settings for Display, Picture, Audio and Advanced settings?

---

### Post by Skrullknight on 2016-03-15
OK guys.I bought speakers..It shows its plugged in..But Nothing still..I see it in sound settings but im still getting no sound

---

### Post by Skrullknight on 2016-03-15
Finally fixed it!! :D

---

### Post by cariboo on 2016-03-16
> **Skrullknight said:**
> Finally fixed it!! :D

Could you let us know what you did to solve the problem, aside from plugging in a set of speakers, so that others can benefit from your experience.

---

### Post by jondog154 on 2016-03-16
Please tell me your mother board model and cpu model.... Also open a terminal run sudo lshw then post the output :)

---

### Post by Skrullknight on 2016-03-16
I plugged in the speakers than raised the bars on alsamixer.

---

### Post by tea for one on 2016-03-16
> **Skrullknight said:**
> I plugged in the speakers than raised the bars on alsamixer.

I'm pleased that you now have sound from your PC but I imagine that everybody who tried to help you assumed you already had some sort of sound output device.

We live and learn, don't we..............

---

### Post by Skrullknight on 2016-03-16
Yeah XD

---

### Post by RobGoss on 2016-03-16
Glad you see you found what the problem a lesson learned, You should mark this thread as Solved

---


---
title: "skype not working"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by knuti1960 on 2012-04-12
Hello,
 
I´m new to Linux, installed Lubuntu (11.10) on an old Thinkpad with 256 MB RAM, 10GB HD, 800 Mhz Pentium3.
Today I have installed skype, but the testcall wasn´t good: I could hear the voice from the other computer very well,but what I had spoken, was not to hear.
 
In skype I went to audio,mikrofone:
default device sound fusion cs46xx.
 
I have downloaded skype (Beta)version 2.2.0.35
 
Any suggestions what to do now?
 
Knud

---

### Post by Sableyes on 2012-04-12
Silence or bad quality sound?

On my fresh installs of Ubuntu, my mic is always muted. If there's no sound from you at all (or low sound) check your mic volume in the KDE sound manager (should be in settings).

(I interweb DJ and ALWAYS forget to unmute myself on fresh installs >.~) 

^^

---

### Post by E_Sound on 2012-04-12
Open terminal and type "alsamixer". There you can adjust volume level of all sound sources. Or press "m" if your microphone is muted.

---

### Post by na5h on 2012-04-12
You could also use Skype through you web-browser using this awesome site: [imo.im]("https://imo.im/")

---

### Post by Rodney9 on 2012-04-12
Pavucontrol is a great help for using Skype.

```
sudo apt-get install pavucontrol
```

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by pichel30 on 2012-06-16
I found this [https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting), look the step 4

Audio Problems

Selecting Microphone (input device)

Most netbooks/laptops have two input devices, one built into the casing and another one for plugging in an external microphone. In Ubuntu 10.04 (Lucid Lynx) and Skype 2.0+ you might have problems selecting the right input device. The following instructions should solve this issue:

1. Install pavucontrol, a program with which you can select audio devices

Click here to install the pavucontrol package

Synaptic

    Go to Applications &#8594; Add/Remove...

    Set Show: to All available applications

    Search for pavucontrol and install it. 

Or open the Terminal, and execute the following command:

    sudo apt-get install pavucontrol

2. Start Skype and initiate a test call (you can use echo123 Skype testing service).

3. Start pavucontrol while the test call is running: Press Alt-F2 and type pavucontrol, hit return

4. In pavucontrol there is a tab called Recording where you can select the input device for the application Skype

Note: Skype has to be running and Skype needs to use (i.e. make a call) Pulseaudio while you change settings with pavucontrol. 


:guitar:

---

### Post by amac777 on 2012-06-16
Skype for Linux version 4 was recently released so you might want to un-install the old version you have been trying to get working and just install the newest version. The sound quality was much better for me on the new version and it worked out of the box with my mic and cam.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by drpjkurian on 2012-06-16
I am really excted to know about this. I thought microsoft wll scrape skype for linux

---

### Post by Macn on 2012-06-16
Check your microphone operates by performing local recording tests.  Check the volume level for the microphone it may also be muted

---


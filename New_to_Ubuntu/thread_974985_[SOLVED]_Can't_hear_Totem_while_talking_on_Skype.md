---
title: "[SOLVED] Can't hear Totem while talking on Skype"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by djsjbh on 2008-11-08
Hi folks,

I recently upgraded to 8.10 and it went smooth. One of the things I noticed is that I can't talk on Skype and listen to an avi in Totem at the same time through my usb headset. I had a customer on Skype who asked me to watch an avi while we were chatting. I played the avi in Totem but couldn't hear it - I had to boot in to Windows to finish the conversation (embarrassing after just telling him how great Linux is).

also the sound from flash video is gone again. I finally got the sound in youtube videos to work under 8.04 but when I up graded I lost it again.

Any ideas folks?

Thank you

32 bit Ubuntu - Intel duo-core - MSI no-frills motherboard - 2 gb ram - Nvidia Geforce 8500

---

### Post by kostkon on 2008-11-08
> **djsjbh said:**
> Hi folks,

I recently upgraded to 8.10 and it went smooth. One of the things I noticed is that I can't talk on Skype and listen to an avi in Totem at the same time through my usb headset. I had a customer on Skype who asked me to watch an avi while we were chatting. I played the avi in Totem but couldn't hear it - I had to boot in to Windows to finish the conversation (embarrassing after just telling him how great Linux is).

also the sound from flash video is gone again. I finally got the sound in youtube videos to work under 8.04 but when I up graded I lost it again.

Any ideas folks?

Thank you

32 bit Ubuntu - Intel duo-core - MSI no-frills motherboard - 2 gb ram - Nvidia Geforce 8500
Both of problems are related to *PulseAudio*. *PulseAudio* allows you to have concurrent sounds on your desktop.

First of all, you'll have to setup *Skype* accordingly. You'll have to go to *Skype*'s preferences and then select the *Sound Devices* option. There you should see three drop-down menus: *Sound In*, *Sound Out* and *Ringing*.

You will need to change what device is selected for *Sound Out* and *Ringing* to *pulse*. You should have an option *pulse* there, if you don't, then come here for more help.

After this, you will need to install the *PulseAudio Device Chooser* utility using *Synaptic*. The package's name is *padevchooser*. Search for it in *Synaptic* and install it.

This will allow you to select which sound device an application will use to output its sound.

You will need to do this, since you cannot anymore select your headset as the Sound Out device in *Skype*. So you need to do it through *PulseAudio*.

Thus, run the *PulseAudio Device Chooser* (it will have an menu entry in *Applications -> Sound & Video*). You will see its icon appearing in your taskbar.

Afterwards, left-click on *PulseAudio Device Chooser*'s icon and select *Volume Control* from the menu that will appear.

The *Volume Control* window will pop-up. In the *Output Devices* tab you should see your headset(s) and soundcard(s) listed. Select the one you want to have as the default by right clicking on it and enabling the *Default* option.

Do the above for your headset. After doing it, from now on *Skype* and *Totem* will be able have sound at the same time and use your headset to send their sound to.

Using the *PulseAudio Device Chooser* you get the freedom to decide which sound device an application uses to output its sound. You may find this really useful.

For example, if you run *Skype* and Totem, in the *Playback* tab you should see their streams appearing there. Right click on each of them and select *Move Stream...* A list will appear showing your soundcard(s) and your headset(s). Select the one that you want this application to use.

You can set the Device Chooser to start every time you login from its preferences.

Now about Flash. 8.10 offers you *Flash 10*, and this version of *Flash* works well with *PulseAudio*. But since you say that you have upgraded, then maybe you are still using *Flash 9* (which does not work well with it).

Thus, you need to open *Synaptic*, search for the *flashplugin-nonfree* package, left-click on it and select it for *Complete Removal*. Then hit the *Apply* button to remove it.

After removing it select it for installation again (this will make it to redownload Flash from Adobe, this time though the version 10). Afterwards, search for the package *libflashsupport* and check if it is installed (the box next to it will be green). If it is, select it for *Removal*, if it isn't, you don't need to do anything.

Then, press the *Apply* button again and that's it.

Hope that helps you...

For any questions regarding the above, don't hesitate to ask.

And sorry for the long reply...

---

### Post by djsjbh on 2008-11-08
I did what you wrote to the letter and checked it three times. As of now I can talk over Skype but I can't hear the other speaker. I also cannot hear any sound other than the test beeps in Sound Preferences > Devices box. Also, I still cannot hear flash video in youtube.

---

### Post by djsjbh on 2008-11-08
never mind above. I got everything to work, including flash, through pulse. The problem was that the sound was coming through my pc speakers and I had them turned off. thank you for the help. if I can figure out how to switch the sound to the headset I'll mark this as solved.

---


---
title: "Cant record audio"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by nnjond on 2008-07-26
Hi, Can anyone help me?

I can successfully line-in sound and play it out through my pc speakers but my sound editors wont pick it up when I press rec.

---

### Post by eightmillion on 2008-07-26
Which sound editors are you using?

---

### Post by nnjond on 2008-07-26
I've tried several, Audacity worked well in MS Win.

---

### Post by eightmillion on 2008-07-26
Have you tried changing the settings under Edit>Preferences>Audio I/O | Recording?

---

### Post by nnjond on 2008-07-26
I've tried a few of those options in each S editor.

---

### Post by eightmillion on 2008-07-26
Could you run 'alsamixer -V capture' in a terminal and make sure it's set to capture from Ext Mic and that the levels are appropriate?

---

### Post by nnjond on 2008-07-26
Audacity doesnt give you the option to capture from ext mic, Line-in, or anthing else in Ubuntu; unlike MS Win.

---

### Post by eightmillion on 2008-07-26
I should have noted that left and right will select channels and pressing space on the selected channel will enable recording for that channel.

---

### Post by nnjond on 2008-07-26
???

Why would i want it to capture mic when the audio source is line-in.

---

### Post by eightmillion on 2008-07-26
Please install alsamixergui with 'sudo apt-get install alsamixergui'. Run it and see what capture options are available.

---

### Post by nnjond on 2008-07-26
nick@nick-desktop:~$ sudo apt-get install alsamixergui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libfltk1.1
The following NEW packages will be installed
  alsamixergui libfltk1.1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 430kB of archives.
After this operation, 1085kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main libfltk1.1 1.1.7-6 [400kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe alsamixergui 0.9.0rc2-1-9 [30.0kB]
Fetched 430kB in 7s (56.2kB/s)                                                 
Selecting previously deselected package libfltk1.1.
(Reading database ... 125445 files and directories currently installed.)
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.7-6_i386.deb) ...
Selecting previously deselected package alsamixergui.
Unpacking alsamixergui (from .../alsamixergui_0.9.0rc2-1-9_i386.deb) ...
Setting up libfltk1.1 (1.1.7-6) ...

Setting up alsamixergui (0.9.0rc2-1-9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nick@nick-desktop:~$

---

### Post by nnjond on 2008-07-26
Error while opening sound device. Please check the input device settings and the project sample rate.

---

### Post by eightmillion on 2008-07-26
Ok, now run alsamixergui and check what channels are set to capture. There will be two circles above the mixer channels that are capable of capturing audio. Could you post what the names of those channels are and which of them if any has red circles?

---

### Post by nnjond on 2008-07-26
RED: mic

WHite: Line, CD, Phone, Aux,

---

### Post by nnjond on 2008-07-26
Have to go out for a while . Thanks for your help so far.

---

### Post by eightmillion on 2008-07-26
Try changing line to capture. Click the white circles above line. Exit alsamixer and try to record with Audacity. Make sure audacity is set to use alsa in the preferences.

---

### Post by nnjond on 2008-07-26
Thanks for your help. It seems to record now, but Ive lost all my sound.

---

### Post by eightmillion on 2008-07-26
Well that's no good. You might try running alsamixergui again and seeing if anything is muted or the volume turned way down. There are little speakers above each channel that should all be green.

---

### Post by nnjond on 2008-07-26
The little speaker on the Alsa mixer gui are either grey or white and I can't figure out what that means.

---

### Post by eightmillion on 2008-07-26
I'm attaching a screenshot. Note that PCM and Ext Mic are muted on mine (the little speakers are white). To unmute a muted channel, just click on the speakers.

---

### Post by nnjond on 2008-07-26
Maybe the best thing is to show u my gui:

[IMG]file:///home/nick/Desktop/Screenshot.png[/IMG]

---

### Post by eightmillion on 2008-07-26
That didn't quite work.

---

### Post by nnjond on 2008-07-26
Ive taken a scrnsht of my gui but i dont know how to paste it ?

---

### Post by eightmillion on 2008-07-26
Hit the new reply button, and click the little paper clip in the editor. A window will pop up that will allow you to upload your screenshot.

---

### Post by nnjond on 2008-07-26
This should be ok.

---

### Post by eightmillion on 2008-07-26
First, turn up the volume sliders on your master surround channel and then play something with audio and start unmuting channels one by one until you hear something.

---


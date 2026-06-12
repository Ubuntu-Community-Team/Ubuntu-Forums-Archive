---
title: "internal microphone not working"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by jsabina1 on 2013-03-09
Hi everybody,
i've been able after some research to make the internal webcam working, but I still have some problems with the microphone.
My laptop is a HP pavillon dv6000.
I've uninstalled pulse audio and installed alsa.
I am trying on skype.

I can see in the microphone devices

HDA Intel, ALC268

with lspci I have
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

if I do the test call I hear the sound but not my voice recorded.
All muted... (I checked on the mixer that the microphone is enabled).
Only if I choose HDA Intel, ALC268 Analog Direct Sample snooping device
I can hear a noise bzzzz but not my voice..

suggestion?

thanks!

---

### Post by Mark_in_Hollywood on 2013-03-09
If there is a speaker (volume) icon on your panel (mine is on the top panel), right click, open and pull down to Run Audio Mixer. from the pulldown menu for Sound Card:, open them one at a time and see if the microphone icon has an X through it. If you see the X - click it to to remove the X. Sound will work afterwards.

Why did you install Alsa & Pulse? Did your OS installation not do this for you?

---

### Post by jsabina1 on 2013-03-10
> **Mark_in_Hollywood said:**
> If there is a speaker (volume) icon on your panel (mine is on the top panel), right click, open and pull down to Run Audio Mixer. from the pulldown menu for Sound Card:, open them one at a time and see if the microphone icon has an X through it. If you see the X - click it to to remove the X. Sound will work afterwards.

Why did you install Alsa & Pulse? Did your OS installation not do this for you?

I've read somewhere that pulse could give problems with microphone or skype... so I installed Alsa.
The sound works, it's only the microphone not working.
Here the screenshot of my sound mixer.. looks fine no?

thanks!!!

---

### Post by Mark_in_Hollywood on 2013-03-10
See this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/753065](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/753065) 

at post #9 is the following:

The only solution to make microphone work is to install linux-backports-modules-alsa-generic...

Just go to:

Menu / System / Administration / Synaptic Package Manager

And search and mark for installation:

linux-backports-modules-alsa-generic

tip: if you have multiple versions click on the first and read the description which should inform what name to install...

If after the reboot and mic mute is off, still does not work, just go to terminal and type:

sudo nano /etc/modprobe.d/alsa-base.conf

and add or change the following:

options snd-hda-intel model=auto enable=yes

Then Ctrl+X, type Y to write and exit, reboot and mic will work.

---

### Post by jsabina1 on 2013-03-10
> **Mark_in_Hollywood said:**
> See this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/753065](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/753065) 

at post #9 is the following:

The only solution to make microphone work is to install linux-backports-modules-alsa-generic...

Just go to:

Menu / System / Administration / Synaptic Package Manager

And search and mark for installation:

linux-backports-modules-alsa-generic

tip: if you have multiple versions click on the first and read the description which should inform what name to install...

If after the reboot and mic mute is off, still does not work, just go to terminal and type:

sudo nano /etc/modprobe.d/alsa-base.conf

and add or change the following:

options snd-hda-intel model=auto enable=yes

Then Ctrl+X, type Y to write and exit, reboot and mic will work.

Thanks a lot!
Unfortunately I cannot find in synaptic that package, tried also with apt-get but no luck

---

### Post by jsabina1 on 2013-03-10
ok sorry added this

deb [http://*ubuntu.mirror.cambrium.nl/ubuntu/](http://*ubuntu.mirror.cambrium.nl/ubuntu/)* lucid main and could find the package..
I am installing, let's see

---

### Post by jsabina1 on 2013-03-10
not working :(
it added new entries but not working

---

### Post by Mark_in_Hollywood on 2013-03-10
In the terminal type

uname -r

post the result of that here, please. Meanwhile see: [http://ubuntuforums.org/showthread.php?t=1441449](http://ubuntuforums.org/showthread.php?t=1441449)

where the question revolved around the alsa "meta package".

---

### Post by jsabina1 on 2013-03-10
3.5.0-25-generic

---

### Post by Mark_in_Hollywood on 2013-03-11
Open the Ubuntu Software Center and search for:

linux-backports-modules-alsa-3.5.0-25-generic

Install it. Reboot. Call the alsamixer from the terminal and look for a "Mic" section, not "Mic Boost".

---

### Post by jsabina1 on 2013-03-11
cannot find it.. I am doing a search on google..
anyway I am using an external webcam now and it's working, thanks!

---


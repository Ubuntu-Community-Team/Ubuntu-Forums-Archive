---
title: "no sound on bluetooth"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by JSchultheis on 2011-10-07
I have an internal bluetooth adapter, and two different headset options for a2dp, which both work on other devices for streaming music.
I have paired and connected a headset.
I have installed Pulseaudio.

When I click Pulseaudio > Volume Control, I can navigate to ALSA plug-in, ALSA Playback on, then select my headset.

At that point to audio stops (from the speakers) then nothing; on occasion I hear something like static, like the end of a record on the record player or stuck in between stations on an analog AM radio.

[_***[COLOR="Blue"]Static Example Link[/COLOR]***_]("http://www.youtube.com/watch?v=e33yjsT_kSI&feature=related")

Switching back to 'Internal Analog Stereo' brings the music back to the speakers like nothing happened.

Any ideas what I can do? :popcorn:

---

### Post by JSchultheis on 2011-10-07
[[IMG]http://www.granitegrok.com/pix/old_radio_1.jpg[/IMG]]("http://www.youtube.com/watch?v=COx4tpZ6Xc8&feature=related")

for more fun clicky the picture ^___^

---

### Post by JSchultheis on 2011-10-09
bump for bluetooth

---

### Post by JSchultheis on 2011-10-10
Well "Community".... 

here is my update:

I tried several things, ncluding search, search, search, of course I did that before starting the thread lol.

```
dpkg -l|grep asound
```
was useful in finding files that included 'asound' as part of the filename, so that I could determine installation or not.

In fact I used "dpkg -l|grep pulse" for 'pulse' files, and "dpkg -l|grep blue" for.......... that's right, 'blue' files.

Next, I went to several websites and proceeded to 'install' or 'troubleshoot' pulseaudio per the instructions listed. Of course most were for older versions of Ubuntu, but I just went with the newest option. 

[[COLOR="blue"][SIZE="2"][FONT="Times New Roman"]***_example_***[/FONT][/SIZE][/COLOR]]("http://ubuntuforums.org/showthread.php?t=789578")

I did the same thing for 'installing' and troubleshooting' bluetooth.

[[COLOR="Blue"]_***[SIZE="2"][FONT="Times New Roman"]example[/FONT][/SIZE]***_[/COLOR]]("https://help.ubuntu.com/community/BluetoothHeadset")

I think I installed 'hcitools' in 'Synaptics Manager', uncertain where intalled, but definitely installed it.

Then I went to ```
Menu>System Tools>Users and Groups
```
oh did I mention that I am actually using Ubuntu based Peppermint OS? silly me... (I thought it might scare off any help lmfao)

Anyway, in users and groups, I selected "Manage Groups". In the box that opened, I selected 'Bluetooth' then hit 'Properties'.

Under 'Group Members', I put a check in the box of the appropriate group.

After 'Bluetooth', I did the same for 'Audio', ****'pulse-access'***, and was told to do this for 'pulse-rt' but I don't have pulse-rt. In fact I may have selected others that seemed to make sense.

I checked the 'hidden' volume level box, available through terminal:```
alsamixer -Dhw
```
I used the arrow keys to make sure that: 'Master' Headphones' and 'PCM' were all at max.

I created a file of:```
gksudo gedit /etc/asound.conf
```
then entered the following:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

Don't forget when working in terminal to:```
sudo apt-get update
```and```
sudo apt-get upgrade
```


Finally, finally, I right-clicked the bluetooth icon on the panel. 
I highlighted the device of choice.
I selected Device>Audio Profile
I selected A2DP (High Fidelity) etc. 
I instantly heard the music transferred over.

Thank you, me, for all of the help.:biggrin:
I'm welcome, me.:twisted:

---

### Post by JSchultheis on 2011-10-10
So it does look like:

*PulseAudio has to be running

*Right-Click Bluetooth applet, select devices, highlight the device, go to device, go to audio profile, select A2DP

*Click PulseAudio (Device Chooser) Applet, Click Volume Control, Playback Tab, Click Internal Audio and Select (Bluetooth Device that I want to use)

---

### Post by JSchultheis on 2011-10-10
***_[COLOR="Blue"][SIZE="2"][FONT="Times New Roman"][[COLOR="Blue"]link for installing Pandora One[/COLOR]]("http://www.piotrkrzyzek.com/install-pandora-one-desktop-app-on-ubuntu-linux/")[/FONT][/SIZE][/COLOR]_***
---although I used gedit (not vim) to access the Sources.List, then used the search function to find 'canon', then simply removed the hash marks (#). --I also ignored the 'maverick' nonsense.

So now bluetooth is running.
PulseAudio is running.
Pandora is running.
And Peppermint OS is supporting it all like a champ.

---

### Post by JSchultheis on 2011-10-11
[COLOR="Blue"][FONT="Times New Roman"][SIZE="3"]***_[CENTER][[COLOR="Blue"]another good comprehensive link[/COLOR]]("http://dpillay.wordpress.com/2010/09/27/ubuntu-10-04-a2dp-awesome-headset-music/")[/CENTER]_***[/SIZE][/FONT][/COLOR]

although I followed it most of the way through, at the advice of navigating to System>Preferences>Sound, I deterred. The peppermintOS option is Menu>Preferences>Sound, in which "Sound" is absent here. However, going to PulseAudio Volume Control>Configuration

Considering the bluetooth is connecte and paired, there is a drop down option offering A2DP.


:guitar:

---


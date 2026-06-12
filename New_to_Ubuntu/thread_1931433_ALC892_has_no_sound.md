---
title: "ALC892 has no sound"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by herklots on 2012-02-25
Installing lubuntu-11.10-alternate-amd64.iso on AMD A4-3400 on ASUS F1a75-V PRO (alternate used to setup full disk encryption, works very well thanks!) the sound from ALC892 simply doesn't work, though alsamixer etc shows it's there.

So I tried some live USB sticks to test the connections etc:
linuxmint-201109-xfce-dvd-64bit.iso sound works fine instantly (can't use Mint because no FDE)
xubuntu-11.10-desktop-amd64.iso sound works fine instantly

It ain't me, babe.

I suggest this is looked at before releasing 12.04...

---

### Post by Rodney9 on 2012-02-25
These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

sudo apt-get install pavucontrol

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.

---

### Post by Rodney9 on 2012-02-25
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by herklots on 2012-02-25
Thanks for the advice, though my point is that the other distributions work correctly out of the box with the exact same hardware, and the Lubuntu didn't... so it appears to be a Lubuntu install issue.

The live ISO also has same problem (I used the alt ISO with direct install onto encrypted partition).

alsmixer shows default sound card as ATI R6xx HDMI which isn't used on this mobo; card #1 is the Realtek ALC892.

Perhaps it's a simple as Lubuntu install presumes that the A75 chipset audio is used, other distis presume that if an alternative sound chip is found, that should be the default.

Again, my point is that it would be good if Lubuntu worked correctly out of the box in this circumstance since the other distis do.

---

### Post by herklots on 2012-02-25
The working solution is at [http://ubuntuforums.org/showthread.php?t=1348604](http://ubuntuforums.org/showthread.php?t=1348604)

This describes that alsa-utils is broken and the utility asoundconf-gtk won't work as standard to select sound card.

Solution summary:

Grab [http://www.avenard.org/files/ubuntu-repos/bleeding/alsa-utils_1.0.18-1ubuntu11_amd64.deb](http://www.avenard.org/files/ubuntu-repos/bleeding/alsa-utils_1.0.18-1ubuntu11_amd64.deb)
or [http://www.avenard.org/files/ubuntu-repos/bleeding/alsa-utils_1.0.18-1ubuntu11_i386.deb](http://www.avenard.org/files/ubuntu-repos/bleeding/alsa-utils_1.0.18-1ubuntu11_i386.deb)

Use Synaptic (under System Tools) to uninstall any alsa-utils version there already

Use Gdebi (under System Tools) to install alsa-utils_1.0.18-1ubuntu11_amd64.deb or alsa-utils_1.0.18-1ubuntu11_i386.deb that you just downloaded

cd /usr/bin
sudo cp asoundconf /usr/
sudo apt-get install asoundconf-gtk

There will now be a program 'Default Sound Card' in Preferences which allows the sound card to be selected.

---


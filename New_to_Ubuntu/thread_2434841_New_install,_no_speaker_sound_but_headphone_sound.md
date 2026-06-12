---
title: "New install, no speaker sound but headphone sound"
date: 2020-01-11
forum: New to Ubuntu
---

### Post by ievans147 on 2020-01-11
Hi. I’m trying to install Linux for the first time, dual-booting with Windows 10 on my HP laptop. I’ve successfully installed a few times, but I’m having problems with audio. Depending on the distro (I’ve tried Ubntu Gnome, Ubuntu Budgie, Kubuntu and Linux Mint) there is either,
 

[LIST]
[*]no sound
[*]Sound when booting from the usb, but not sound after I install
[*]Sound via headphones, but not via the usb speakers
[/LIST]
 
GUIs seem to think sound is being played. For instance, in Ubuntu Budgie the sound settings GUI showed me the audio for a youtube video, even though I couldn’t hear it.
 
I’ve tried a few things to solve it but I don’t really know what I’m doing. I’ve tried:
 

[LIST]
[*]Force-reloading alsamixer
[*]Switching sound cards in aslamixer
[*]Changing volumes in alsamixer
[*]Switching run=YES to run=NO after running the command
[LIST]
[*]sudo gedit /etc/default/speech-dispatcher
[*]Note: this command opened a blank file, so I think speech-dispatcher didn't previously exist
[/LIST]

[*]Uninstalling and reinstalling alsa-base and pulseaudio with these commands:
[LIST]
[*]sudo apt remove –purge alsa-base pulseaudio
[*]sudo apt install alsa-base pulseaudio
[*]This broke the desktop system on Kubuntu (and didn’t work)
[/LIST]
[/LIST]
 
 
I’m also having trouble booting into GRUB rather than Windows 10, and right-clicking, but I guess those are stories for other days...
 
 Currently I have Ubuntu Budgie installed.

Any help is much appreciated!

---

### Post by NM5TF on 2020-01-13
are you sure it's not muted in ALSA mixer ???  this is a very common & easily fixed problem

here is a little troubleshooting primer  [https://www.maketecheasier.com/fix-no-sound-issue-ubuntu/](https://www.maketecheasier.com/fix-no-sound-issue-ubuntu/)

try it & see if this doesn't fix it.....

here is another tip 

[https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

good luck
tommy

---


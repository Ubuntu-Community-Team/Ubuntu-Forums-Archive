---
title: "No sound in Chrome, update warning &amp; error"
date: 2015-03-08
forum: New to Ubuntu
---

### Post by pkoukoulis-r on 2015-03-08
Hi

I have attempted to follow the instructions available at
[http://askubuntu.com/questions/490995/no-sound-in-chrome-when-playing-youtube-videos-and-mp3s-under-ubuntu-14-04](http://askubuntu.com/questions/490995/no-sound-in-chrome-when-playing-youtube-videos-and-mp3s-under-ubuntu-14-04)

Ubuntu = 14.10 64 bit, Chromium = Version 40.0.2214.111 Ubuntu 14.10 (64-bit)

1 - Update :
$ sudo apt-get update
2 - Reinstall Alsa and Pulse Audio :
$ sudo apt-get remove --purge alsa-base pulseaudio
$ sudo apt-get install alsa-base pulseaudio
3 - Install Ubuntu Audio Dev Team Driver :
$ sudo add-apt-repository ppa:ubuntu-audio-dev

$ sudo apt-get update
$ sudo apt-get dist-upgrade
$ sudo apt-get install chromium-browser
4 - Installing PepperFlashPlayer :
$ sudo apt-get install pepperflashplugin-nonfree
$ sudo update-pepperflashplugin-nonfree --install
$ sudo apt-get dist-upgrade && sudo shutdown -r

The output from the "sudo apt-get update" command under section 3.
is showing up as follows:

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

The warnings and error however did not appear in the first update, "sudo apt-get update".


How can a "sudo apt-get update" be performed without having warnings and an error?

Thanks
Peter

---

### Post by deadflowr on 2015-03-08
Disable the repo, it has no version for utopic.

Edit: The first update command was run before you added the broken ppa for ubuntu-audio-dev.
Which is why it did not produce any errors.
When you added the busted ppa, then the apt-get update command produce the broken errors.

to remove simply add an -r to the add-apt-repository command like so
```
sudo add-apt-repository -r [COLOR=#000000] [/COLOR] ppa:ubuntu-audio-dev
```
then re-run the update command.

---


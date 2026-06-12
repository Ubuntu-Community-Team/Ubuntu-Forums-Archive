---
title: "Can't get sound working on xfce4"
date: 2016-12-04
forum: New to Ubuntu
---

### Post by ross420 on 2016-12-04
Hello, I've been using ubuntu 12.04 for about 2 months now on my Acer chromebook 14, which I downloaded with crouton. The first time I downloaded xfce4 I already couldn't get sound working, Didn't bother my until now. When I want to listen to music I have to put on music from ChromeOS and then start xfce4. Anyways, I've looked up many guides how to get it working. But since, I'm not too techsmart I just don't understand those, and I've already tried to install Pulseaudio - Can't get it to work, When i run xfce4-mixer I get 
*" GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem." *Also I've tried to reset the thingy from xfce4-mixer in settings editor. Still nothing. 
I know that this seems to be a really common issue here, But I really just don't understand all these guides I would really appreciate the help.

Lots of love.

---

### Post by Bucky Ball on 2016-12-04
Welcome. You installed pulse audio and 'couldn't get it to work' doesn't tell us much about why or how. 

Either way, you want pulseaudio volume control. Install that, play an audio track, launch PAVControl and you should see the audio stream bouncing up and down under the 'playback' or 'input' tab. From there it is a matter of experimenting with input and output ports until you get it right. See how you go with that and let us know.

PAVControl is in the official repositories, i.e. Software Centre, Synaptic Package Manager (which I think is default in Xubuntu?) or install using the terminal. You are looking to install 'pavucontrol'.

---

### Post by ross420 on 2016-12-04
Okay so, I wen't to this page [https://apps.ubuntu.com/cat/applications/precise/pavucontrol/](https://apps.ubuntu.com/cat/applications/precise/pavucontrol/)
And clicked the "*Available on the Software centre" *button, and The webpage doesn't exist. 
I don't know how to put this, I really don't understand how to install all that kind of stuff. What other options do I have, do I have to put something in terminal or what?

It transfers me to this page apt://pavucontrol  ... which doesn't have anything but an error message

---

### Post by Autodave on 2016-12-04
I am wondering why you are running that old of a version and whether programs are still available. I would suggest that you d-l 16.04 and start by doing a clean install.

You may want to d-l Xubuntu as it is much less of a memory hog than Ubuntu Unity.

---

### Post by oldos2er on 2016-12-04
See [http://packages.ubuntu.com/precise/pavucontrol](http://packages.ubuntu.com/precise/pavucontrol), pavucontrol is available for 12.04. Do you have the universe repository enabled?
Could you run each of the following commands, and copy/paste the text output here? It'll help us diagnose the problem. ```
lspci | grep Audio
cat /etc/apt/sources.list
ll /etc/apt/sources.list.d/
```

---

### Post by ross420 on 2016-12-04
(precise)evonroossaar@localhost:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation Device 2284 (rev 35)
(precise)evonroossaar@localhost:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
(precise)evonroossaar@localhost:~$ ll /etc/apt/sources.list.d/
total 36
drwxr-xr-x 2 root root 4096 Dec  4 12:43 ./
drwxr-xr-x 6 root root 4096 Dec  4 12:43 ../
-rw-r--r-- 1 root root   67 Dec  4 12:43 google-chrome.list
-rw-r--r-- 1 root root   67 Dec  4 12:43 google-chrome.list.save
-rw-r--r-- 1 root root  172 Dec  4 12:43 hikariknight-unix-runescape-client-precise.list
-rw-r--r-- 1 root root  172 Dec  4 12:43 hikariknight-unix-runescape-client-precise.list.save
-rw-r--r-- 1 root root   67 Dec  4 12:43 runescape.list
-rw-r--r-- 1 root root   67 Dec  4 12:43 runescape.list.save
-rw-r--r-- 1 root root  154 Dec  4 12:43 webupd8team-pulseaudio-eq-precise.list

---

### Post by oldos2er on 2016-12-04
Check Software & Updates ([https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)) to see that universe is enabled, then ```
sudo apt-get update && sudo apt-get dist-upgrade
```, then retry installing pavucontrol.

What happens if you run *alsamixer* in a terminal?

---

### Post by ross420 on 2016-12-04
by running alsamixer in termial I control the sound from ChromeOS. Like I have music running in ChromeOS while using xfce4, but with alsamixer I control the sound volume for the music coming from ChromeOS.
Card and Chip: CRAS

Plus really, you asked me to check software and updates from that website, I don't understand what I have to check. I literally don't understand half of the stuff you're asking me to do. Sorry for being that incompetent.

What am I supposed to download from the *[http://packages.ubuntu.com/en/precise/pavucontrol](http://packages.ubuntu.com/en/precise/pavucontrol)* website?

---

### Post by oldos2er on 2016-12-04
You'll have to forgive me but I don't know how to open the Software tab in 12.04, because I'm running 16.10. You can try Super-R (that is, hold down the "Super" key, also known as the Windows key, then hit R) to open the whisker menu (if you have it enabled, if not, ignore this), type in "software" without the quotes. You're looking for the Software & Updates program to check if you have the universe repository enabled.

Don't download anything from the website yet. I was just checking there to be certain pavucontrol was available for 12.04.

---

### Post by HermanAB on 2016-12-05
Howdy,

Linux sound problems are mostly a thing of the past and in 99% of cases of no sound, all you need to do is run aumix and turn the volume up - really.

---


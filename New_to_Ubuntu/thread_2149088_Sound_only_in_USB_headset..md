---
title: "Sound only in USB headset."
date: 2013-05-27
forum: New to Ubuntu
---

### Post by Fazer4463 on 2013-05-27
After reading online that Alsa was a better sound quality than PulseAudio, I decided (Stupidly) to remove pulse and just run Alsa. I lost all my sound from every output.
I then followed the sound troubleshooting guide on this forum and have my sound back on my USB headset

To cut a long story short I then tried to re-install Pulse only to find that I have lost the ability to change the audio output to anywhere else except my headset....see attached screenshot, there are no entries in the sound control panel anymore.

Please bear with me, I only installed Ubuntu 12.04 LTS less than 2 weeks ago

---

### Post by papibe on 2013-05-27
Hi Fazer4463.

Disconnect your handset and try restart pulseaudio by running these 2 commands one after the other:
```
pulseaudio -k

pulseaudio -D
```
Let us know how it goes.
Regards.

---

### Post by Fazer4463 on 2013-05-27
I tried your first command and got this result:-

richard@ubuntu:~$ pulseaudio -k
The program 'pulseaudio' is currently not installed.  You can install it by typing:
sudo apt-get install pulseaudio


So I did:-
richard@ubuntu:~$ sudo apt-get install pulseaudio

and got this result:-
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

the above means nothing at all to me

---

### Post by papibe on 2013-05-27
Sorry, I think I misunderstood your concern. Those commands are to restart pulseaudio.

I wouldn't know how to manage a system without it.

May be you can install and try the alsa-tools-gui package:
```
sudo apt-get install alsa-tools-gui
```
Just a thought.

Regards.

---

### Post by Fazer4463 on 2013-05-28
You were correct on the first assumption, I am trying to get pulseaudio back on my system but it won't let me, sorry for the misunderstanding

***EDIT*** I just retried the pulseaudio install and it has worked.......EXCELLENT !!!  Thank You

---


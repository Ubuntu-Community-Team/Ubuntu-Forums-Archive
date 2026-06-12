---
title: "Trouble with skype in 11.04"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by L Campbell on 2011-12-21
I'm having trouble finding ' 2.2.0.35-0Lucid1' in Ubuntu Software Center.

All I can find is '2.2.0.35-0natty1' and it isn't working for 11.04.

Your suggestions will be appreciated.

---

### Post by BC59 on 2011-12-21
I don't know if I understood well, but you can download the package you are asking from [here]("https://launchpad.net/ubuntu/+source/skype/2.2.0.35-0lucid1")

---

### Post by L Campbell on 2011-12-21
> **BC59 said:**
> I don't know if I understood well, but you can download the package you are asking from [here]("https://launchpad.net/ubuntu/+source/skype/2.2.0.35-0lucid1")

Thanks for your suggestion.

I went to the link and saw '2.2.0.35-0lucid1'.diff.gz  1.5Kib but I have no idea what to do with it.

Kind regards.

---

### Post by BC59 on 2011-12-21
You just have to download the file **skype_2.2.0.35.orig.tar.gz** Then go to Downloads, double click and extract to Downloads. Then choose your architecture i386 or 64bits and double click on the corresponded file. Ubuntu Center will install it.

---

### Post by L Campbell on 2011-12-22
> **BC59 said:**
> You just have to download the file **skype_2.2.0.35.orig.tar.gz** Then go to Downloads, double click and extract to Downloads. Then choose your architecture i386 or 64bits and double click on the corresponded file. Ubuntu Center will install it.

Well, I believe I followed your instructions properly but still the 'test call' doesn't work.

Thanks anyway.

---

### Post by Sigma1 on 2011-12-22
I had some conflicts between pulseaudio and skype; you can always try ```
killall pulseaudio & skype
``` (I think) from a terminal window.

---

### Post by L Campbell on 2011-12-22
> **Sigma1 said:**
> I had some conflicts between pulseaudio and skype; you can always try ```
killall pulseaudio & skype
``` (I think) from a terminal window.

Thanks, I tried this but now there is NO sound from Skype.

qwer@qwer-P9852A-ABA-753N:~$ killall pulseaudio & skype
[1] 3058
No command 'skype' found, did you mean:
 Command 'skyped' from package 'skyped' (multiverse)
skype: command not found
[1]+  Done                    killall pulseaudio
qwer@qwer-P9852A-ABA-753N:~$

---

### Post by Paqman on 2011-12-22
> **L Campbell said:**
> 
All I can find is '2.2.0.35-0natty1' and it isn't working for 11.04.


11.04 is codenamed Natty Narwhall, so that's the correct one. When you say it "doesn't work", can you be a bit more specific?

---

### Post by L Campbell on 2011-12-22
> **Paqman said:**
> 11.04 is codenamed Natty Narwhall, so that's the correct one. When you say it "doesn't work", can you be a bit more specific?

OK, sorry I didn't make that more clear.

When I go to my account and log on I always try a 'test call'.

I do not hear my voice response after the test call.

---

### Post by Sigma1 on 2011-12-22
Have you looked at your sound preferences? Sometimes the microphone / recording preferences need tweaking. If you're not recording in Skype, chances are you won't record via any other microphones, either.

---

### Post by L Campbell on 2011-12-22
> **Sigma1 said:**
> Have you looked at your sound preferences? Sometimes the microphone / recording preferences need tweaking. If you're not recording in Skype, chances are you won't record via any other microphones, either.

I tried this in Terminal ' killall pulseaudio & skype ' and I'm wondering if I can UNdo that command now?

---

### Post by Sigma1 on 2011-12-22
Try typing ```
pulseaudio
```; it's set to load at each startup, anyway, generally.

---

### Post by L Campbell on 2011-12-22
> **Sigma1 said:**
> Try typing ```
pulseaudio
```; it's set to load at each startup, anyway, generally.

OK, this is what I got from Terminal:-

qwer@qwer-P9852A-ABA-753N:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
qwer@qwer-P9852A-ABA-753N:~$ ^C

---

### Post by Sigma1 on 2011-12-22
OK, well, if you just close your session, then start a new one, you'll get pulseaudio back. Check sound output with skype first, and then check sound input settings on your general sound preferences, via gnome-volume-control. Go to the input tab (third one along) and make sure that, when you speak in the mic, you're getting some reaction in the input level field. It might just be a question of setting the right level (it can be mute, by default), or, failing that, the right device.

---

### Post by L Campbell on 2011-12-22
> **Sigma1 said:**
> OK, well, if you just close your session, then start a new one, you'll get pulseaudio back. Check sound output with skype first, and then check sound input settings on your general sound preferences, via gnome-volume-control. Go to the input tab (third one along) and make sure that, when you speak in the mic, you're getting some reaction in the input level field. It might just be a question of setting the right level (it can be mute, by default), or, failing that, the right device.

Thanks, I'll try that.

In the meantime I went across town to my other computer and by checking Synaptic I see it has 2.2.0.35-Onatty1 and it, too, will not pass the 'test call' test.

---

### Post by Ms. Daisy on 2011-12-23
You may check this thread to see if it will solve your problem.
[http://ubuntuforums.org/showthread.php?t=1893830](http://ubuntuforums.org/showthread.php?t=1893830)
 
I had a similar problem which seemed to stem from the fact that skype does not automatically make your webcam the default sound device.

---

### Post by L Campbell on 2011-12-24
> **Ms. Daisy said:**
> You may check this thread to see if it will solve your problem.
[http://ubuntuforums.org/showthread.php?t=1893830](http://ubuntuforums.org/showthread.php?t=1893830)
 
I had a similar problem which seemed to stem from the fact that skype does not automatically make your webcam the default sound device.

Thanks for your suggestion.

What I have done now is to install 10.04.3 then install Skype from the Software Center and it seems to be working perfectly now.

---


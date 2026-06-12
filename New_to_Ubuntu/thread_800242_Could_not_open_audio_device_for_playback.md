---
title: "Could not open audio device for playback"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by mormor on 2008-05-19
udiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

Heron. Sound worked just fine yesterday. Seen this as a bug-report on the internet after googling, but can not find any fix to it. All help will be apriciated: )

---

### Post by xfceuser on 2008-05-19
Try restarting the computer and see if the problem solved. Indeed maybe "Device is being used by another application." so if you restart, "another application" may leave the sound device free.
Also try closing all other applications that may use sound (sometimes even firefox cam make this problem (flash player uses the sound device))

---

### Post by sdennie on 2008-05-19
Rather than fulling rebooting, you could also log out, hit Ctrl-Alt-F1 and login to a terminal.  Then type:

```

pkill -9 -u your_username
exit

```

Hit Ctrl-Alt-F7 and log back in.

---

### Post by bratliff on 2008-07-17
I am having the same problem. NO sound on video's or youtube. Following these instructions made me lose video sound. 
[http://www.uluga.ubuntuforums.org/showthread.php?t=772632](http://www.uluga.ubuntuforums.org/showthread.php?t=772632)

bratliff



> **mormor said:**
> udiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

Heron. Sound worked just fine yesterday. Seen this as a bug-report on the internet after googling, but can not find any fix to it. All help will be apriciated: )

---

### Post by fabhren on 2008-08-14
Hello all,

I am also a newbie in Ubuntu but what I've found it is that sometimes process become dead but still are living among the process list occupying valuable resources. These are known as "zombie" processes.

What you have to do is to find which application may be grabbing the sound from you.

```
ps -ef
```

This command should list you all the processes the machine is running. Probably that application was launched by your username so you only need to find it and kill it with:
```
kill -9 id_of_the_process
```

My mplayer was blocking my sound so I just killed all instances related to it and my sound was released.

Hope this helps.

---

### Post by Gannon8 on 2008-08-14
1. You cannot kill zombie processes with the kill command. That is why they are called "zombie"
2. You should only get zombie processes if the parent process is behaving badly or if you have killed init. To kill zombie processes, you may want to kill their parent processes and let init kill them.
3. Zombie processes should not take up the audio buffer, but I am not sure about that...

---

### Post by M2_ on 2008-10-05
> **mormor said:**
> udiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.


I've got the same problem. And there is nothing in list of devices, so i can't even choose one.

my /etc/modprobe.d/sound contains:

alias snd-card-0 snd-emu10k1
options snd-emu10k1 index=0
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=1

That's seems to be ok, but it does not work from yesterday. I've even compiled a new reknel, because of another problem, and it does not work in both of them.

---

### Post by billgoldberg on 2008-10-05
Correct me when I am wrong, but this sounds like the famous PulseAudio bug.

In that it can only use one source at the time.

I use ALSA instead of PulseAudio because of this. However it seems this bug has been fixed in Intrepid.

---

### Post by zanknits on 2009-01-29
I'm using Intrepid and I just got the same error message. Is there a way to disable pulseaudio?

---

### Post by Heathtech on 2009-02-04
I don't think the bug was resolved, for I also got the same error message in Intrepid.

I don't know how to disable pulse audio, but I can confirm that killing the pulseaudio process made the error go away and I got my sound back.  Mine was related to flash, I'm sure.  Not sure how safe killing the pulseadio process is, though.

---

### Post by furcino on 2009-03-17
> **sdennie said:**
> Rather than fulling rebooting, you could also log out, hit Ctrl-Alt-F1 and login to a terminal.  Then type:

```

pkill -9 -u your_username
exit

```

Hit Ctrl-Alt-F7 and log back in.

Thank you, great advice. **Brought the sound back immediately.**

However, why is there the need to log out or reboot when fixing most problems? I'm still not that sure how the system is build, but I really don't like rebooting or logging off, because then there is no real point in having a Linux OS. I feel like I'm cheating every time I push the reset button :) Isn't there a magic 'reset just the flashy Desktop programs' thing..?

---

### Post by click4851 on 2009-03-17
I've had good luck with this guide you could start there...

[http://ubuntuforums.org/showthread.php?t=789578&highlight=logitech+headset](http://ubuntuforums.org/showthread.php?t=789578&highlight=logitech+headset)

---

### Post by sdennie on 2009-03-17
> **furcino said:**
> Thank you, great advice. **Brought the sound back immediately.**

However, why is there the need to log out or reboot when fixing most problems? I'm still not that sure how the system is build, but I really don't like rebooting or logging off, because then there is no real point in having a Linux OS. I feel like I'm cheating every time I push the reset button :) Isn't there a magic 'reset just the flashy Desktop programs' thing..?

There isn't usually a reason to reboot or logout for fixing problems.  However, for the purposes of a support forum, it's much easier to say, "Logout and pkill everything" or "Reboot" than it is to give the detailed instructions on how to do it without logging out/rebooting.  

It's the same reason people give cryptic commandline solutions rather than attempting to give language dependent GUI instructions along the lines of "Click this, click this, click this".

Still, logging out is not very onerous in linux.  Sure, you have to restart your apps but, they will all be cached and so it's a MUCH lighter weight thing to do than rebooting.

---

### Post by alexebird on 2009-03-25
I had this error come up when I tried testing my sound in sound settings and was able to get my sound back.  I was trying to watch a flash video in Firefox, and that's when I noticed the sound wasn't working.  I started Amarok to verify it really wasn't working and I got the "xine was unable to initialize any audio drivers" error.  I was just messing around, but here is what I did.
[LIST=1]
[*]```
prompt > killall pulseaudio
```
[*]Quit Firefox cleanly.
[*]```
prompt > pulseaudio
``` (This command may not even need to be run, because I closed the terminal which I ran it in and the sound was still working.)
[/LIST]
After this, Amarok worked fine without even restarting it, and the video worked in Firefox when I retried it.

Hope this helps!

---

### Post by tenmilez on 2009-04-28
> **Heathtech said:**
> I don't think the bug was resolved, for I also got the same error message in Intrepid.

I don't know how to disable pulse audio, but I can confirm that killing the pulseaudio process made the error go away and I got my sound back.  Mine was related to flash, I'm sure.  Not sure how safe killing the pulseadio process is, though.

Not sure why this works, but thank you :)

---

### Post by hellboi on 2010-07-13
I was having a similar issue. In my case it turned out to be Google Chrome that was causing the issue.

I just have to shut Chrome, start the audio player, then re-start Chrome.
I have a hunch that the problem is flash related, it's still pretty buggy in Chrome.   

I realise most of the issues above are unrelated to this, but I thought it might help someone.

---


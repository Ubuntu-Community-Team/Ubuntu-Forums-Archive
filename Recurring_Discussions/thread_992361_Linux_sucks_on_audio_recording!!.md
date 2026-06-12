---
title: "Linux sucks on audio recording!!"
date: 2008-11-24
forum: Recurring Discussions
---

### Post by superoptimo on 2008-11-24
For me, Linux sucks on audio recording. Why?

[LIST=1]
[*]Audacity. I used to edit audio with audacity on windows, Great software, so I was expecting that it will works on linux in the same way. Guess what?? it crashes!! with Alsa drivers it just get blocked. OSS driver (With alsa emulation) doesn't work. Ironically, the wine emulation of Audacity for windows works fine... Why??
[*]Ardour?? it requires jack, so I do install jack and configure it with qjackctl. It just make things worse!!  How I can configure the correct latency and buffer parameters for my laptop?? With every configuration it just play audio very noisy, I've tried every configuration that i saw in many forums, and the result is the same. 
[*] Jockosher. A very unstable software, it is capable of open the audio devices, and records from mic, but eventually crashes without any advice.
[*] Sweep. As same as jokosher, with a better interface. But crashes.
[*] Rezound?? crashes.
[/LIST]

I hope to make audacity working fine on linux, but none of the existing sound servers work well. ALSA just crash the app, Jack always sounds awful with noises and eventually crashes. OSS just can't open the device.

The audio device works fine, because Skype runs fine, also audacious and LMMS runs wonderfully. So I can't figure out what's happening!! I have a descent laptop dell 1420 2G ram core 2 duo. Its audio driver is Intel 8280.

It's sad, but after this issue I have to say that the only aspect, the core only one aspect,  where Windows rules is on audio edition. because in every other aspects windows totally sucks every time. (2000,xp,vista every version all of them are the same ****!!)

---

### Post by cmay on 2008-11-24
[http://64studio.com/](http://64studio.com/)

it seems that proff does use linux also.
 i use this distro myself and it works out of the box with all things needed to make music. 

there is a live cd so you  can test it out first,

---

### Post by poebae on 2008-11-24
Unfortunately it's true, and there's very little defence for it.

Windows requires very little fiddling to get the sound working perfectly across applications. Sure, there's always going to be the crowd who says that Windows dumbs it down too much and isn't very flexible, but 99% of users don't want to know what Alsa, Pulse and OSS are.

Audio is one of the areas in which Linux doesn't "just work". There are threads in the forums with polls asking what needs to be done about the audio situation, and the last time I checked, the concensus was that it pretty much needs to be re-done, because the audio situation is unfortunately quite awful.

---

### Post by DirtDawg on 2008-11-24
> **superoptimo said:**
> For me, Linux sucks on audio recording. Why?

[LIST=1]
[*]Audacity. I used to edit audio with audacity on windows, Great software, so I was expecting that it will works on linux in the same way. Guess what?? it crashes!! with Alsa drivers it just get blocked. OSS driver (With alsa emulation) doesn't work. Ironically, the wine emulation of Audacity for windows works fine... Why??
[*]Ardour?? it requires jack, so I do install jack and configure it with qjackctl. It just make things worse!!  How I can configure the correct latency and buffer parameters for my laptop?? With every configuration it just play audio very noisy, I've tried every configuration that i saw in many forums, and the result is the same. 
[*] Jockosher. A very unstable software, it is capable of open the audio devices, and records from mic, but eventually crashes without any advice.
[*] Sweep. As same as jokosher, with a better interface. But crashes.
[*] Rezound?? crashes.
[/LIST]

I hope to make audacity working fine on linux, but none of the existing sound servers work well. ALSA just crash the app, Jack always sounds awful with noises and eventually crashes. OSS just can't open the device.

The audio device works fine, because Skype runs fine, also audacious and LMMS runs wonderfully. So I can't figure out what's happening!! I have a descent laptop dell 1420 2G ram core 2 duo. Its audio driver is Intel 8280.

It's sad, but after this issue I have to say that the only aspect, the core only one aspect,  where Windows rules is on audio edition. because in every other aspects windows totally sucks every time. (2000,xp,vista every version all of them are the same ****!!)

Audacity is a great piece of software. If you want to use Linux, it sounds like you may have to do some tweaking to get it to work correctly. My understanding is the Audacity developers have some modifications to make concerning the Linux audio setup and haven't got around to it yet. If you don't feel like tweaking is worth your time, use Windows. 

conversely, try the advance search function of this forum to search thread titles for the word 'audacity' and you will come up with [plenty of hits]("http://ubuntuforums.org/search.php?searchid=52129481"). Spend a little time looking through these and you will probably find some useful information.

Or use Windows. Up to you.

---

### Post by markbuntu on 2008-11-24
It would probably be in your interest to read a few how tos:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

Audacity is a big piece of crap when compared to what you can do with ardour. A lot of professionals and big studios use ardour/jack/linux because it works great and is very reliable and is free.

Audacity is OK as a free alternative to the money you would have to spend to get a really good windows application but there is really no point to using something that the developers have no interest in keeping up in linux. The audacity devs are not putting much effort into this so if you are having problems with audacity in linux you should be complaining to the audacity developers.

---

### Post by mbsullivan on 2008-11-24
> 
[http://64studio.com/](http://64studio.com/)

it seems that proff does use linux also.
i use this distro myself and it works out of the box with all things needed to make music. 

I've never used this distro, but I second the suggestion to try it out. It seems to be solid, from what I've heard.

In any case, if you're going to do any serious recording you'll want to use a realtime kernel.

Mike

PS -- If you want something more Ubuntu-like, you could try [Ubuntu Studio]("http://ubuntustudio.org/").

---

### Post by superoptimo on 2008-11-25
Ok. At first, please forgive me about my rude and offensive language. I don't want to blame to anybody.

The fact is that I want to get running Jack on my box. It is my last hope for getting running audio recording software. 
But Jack isn't running well. Why?? every configuration that I've tried gives me errors or a noisy distorted sound. How I could deal with this??

Facts:
-My sound card doesn't support realtime.
-My sound card doesn't support more than 2 buffers.
-My sound card doesn't support more than 1024 Frames/buffer.

Does Jack support my mediocre sound card? (Intel 82801H)
I've saw all those examples that are configured for a Creative labs or a sound blaster chip. Yes, those are the proper hardware for audio production indeed.

But I'm not pretending building my own production studio with my laptop. I simply want to record some audiologs for post them on internet. So I need it basic.

If jack doesn't work, what am I just supposed to do?

---

### Post by cmay on 2008-11-25
i provided a link for a live cd which can do this simple stuff. you can also install it and use as a perfectly good hobby studio.
picture of my current setup of 64studio which runs perfect attached.. 
as you can see the studio is very hardware based. its easy for me to switch a usb plug on linux and put in another and i have not to worry about the drivers needing to be reinstalled as i did on windows. always when ever i pulled a usb plug it could not find the drivers for the new hardware. i use many different kinds of usb devises like drum machines and keyboards.  which is why i would recommend you to try this live cd first and see what you think. 
good luck.

---

### Post by semitone36 on 2008-11-25
> **cmay said:**
> [http://64studio.com/](http://64studio.com/)


This looks like it could be exactly what I am looking for! What is 64studio like compared to Ubuntu Studio?

---

### Post by cmay on 2008-11-26
it works better overall i think. its stable and its build only with the purpose of  making music. programs like audacity works in this right out of the box since its build around the concept that it is a studio set up.there is very little programs (no games) that has nothing to do with music like firefox. it is very stable.

---

### Post by zettberlin on 2008-12-05
> **superoptimo said:**
> Ok. At first, please forgive me about my rude and offensive language. I don't want to blame to anybody.

I understand your anger, sometimes one needs to vent some steam and I am sure there is no offence meant :-)

> **superoptimo said:**
> 


Facts:
-My sound card doesn't support realtime.
-My sound card doesn't support more than 2 buffers.
-My sound card doesn't support more than 1024 Frames/buffer.



To be perfectly honest: these are no facts.

> -My sound card doesn't support realtime.

RT-capabilities have nothing to do with the device, its a kernel-thing only. To make the kernel ready for jacks RT-mode you need to have 3 lines in the file /etc/scurity/limits.conf

```
@audio          -       rtprio          99

@audio - memlock 1894774

@audio - nice -20
```

You do NOT need the special RT-kernel for that, every modern kernel supports jacks RT-Mode it limits.conf is set up OK. The RT-Kernel is tuned some more for the task though...


>-My sound card doesn't support more than 2 buffers.
>-My sound card doesn't support more than 1024 Frames/buffer.

Wrong also, the buffersize is handeled by jack as well, regardless, what device is being used. For your card try:

3 periods/buffer
48000 Hz Rate (very important, 44100 will not do good)
512 frames or 1024 if needed.

I have got jackd/Ardour/Rosegarden etc. running on very similar soundchips with a Toshiba Tecra with 256MB RAM and a Pentium III/933HZ with 1024 Frames and on a MSI cheapo notebook with 512 to edit Ardour Sessions with 40+ tracks and dozens of plugins.

If really everything fails, get a cheap USB-Soundcard (Behringer UControll for abour 25 Euros / 30 USD). with such a piece everything wents OK...

> **superoptimo said:**
> 
I've saw all those examples that are configured for a Creative labs or a sound blaster chip. Yes, those are the proper hardware for audio production indeed.


Soundblaster? Ha! I run my Workstation in my little Studio with a Presonus Firebox and with a MAudio Audiophile - both barely acceptable hardware for music production...

;-) ;-)

good luck

HZN/Berlin

---

### Post by saturninus on 2008-12-30
Agreed.  I've been using Ubuntu Studio and I can only get one synth to work.  The rest crash out or are too archaic to start using right away.

---


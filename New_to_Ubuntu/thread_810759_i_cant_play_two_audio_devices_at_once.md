---
title: "i cant play two audio devices at once"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by moose4204l on 2008-05-28
why cant i play two audio devices at once. if i am watching a youtube vid and then i leave the page open and i try mplayer on a wav or mp3, it wont work, i have to close the website. or if i want an hydrogen .h2song to play as i mess with zynaddsubfx, i cant do that either.

is there a way to fix this?

---

### Post by sayakb on 2008-05-28
Open the audio mixer from panel (double click on the volume control icon) and goto File->Change device->Change it to ALSA

---

### Post by moose4204l on 2008-05-28
that didnt work, am i supposed to do somethng else after i click them, i tried re-loading hydrogen but i cant get it to play...here is a screen shot of the options for me


[[IMG]http://img129.imagevenue.com/loc1026/th_02940_screenshot_122_1026lo.jpg[/IMG]](http://img129.imagevenue.com/img.php?image=02940_screenshot_122_1026lo.jpg)

---

### Post by moose4204l on 2008-05-28
anyone else know what to do?

---

### Post by spiderbatdad on 2008-05-28
```
asoundconf unset-pulseaudio
asoundconf set-default-card I82801DBICH4
```

---

### Post by moose4204l on 2008-05-28
still no good. i have hydrogen open and im playing my thing, and i am trying to play mplayer for the piano/keyboard sounds an i cant.

this is what i get when i try to run mplayer

> MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing song4.wav.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 50.0 (50.0) ??,?% 


---

### Post by spiderbatdad on 2008-05-28
Ah. you needed to reboot after the asoundconf commands...sorry.

---

### Post by moose4204l on 2008-05-28
still no good,  i rebooted then i opened terminal and hydrogen and play a .wav and while that was on i opened another terminal and mplayer <file> and it still didnt work. i dont think anything changed but i got this 

> MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing song1.wav.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 63.0 (01:03.0) ??,?% 


---

### Post by adobrakic on 2008-05-28
I'm also having this problem. If i have Banshee open, my youtube videos don't have any sound.

Moose, if you find out how to fix is, could you please post your solution?

---

### Post by adobrakic on 2008-05-28
anyone find this out?

---

### Post by moose4204l on 2008-05-28
i think they are giving up on me

---

### Post by llama320 on 2008-05-28
First off, I'm assuming you're using Hardy, otherwise everything below probably doesn't apply. anyways...

I had the same problem..the way I fixed this was to embrace pulseaudio instead of trying to use ALSA..okay so here's what I did:

Go to System > Preferences > Sound: change all "Sound Playback" options to PulseAudio

Now, to get youtube working..this is a problem with pulseaudio and flash non playing nice. After you've changed everything to pulseaudio

```

sudo apt-get purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

Now restart and it will (hopefully) work

if this doesn't work, you may want to set your audio settings on your audio player to pulseaudio (I did this with amarok..mplayer should have this option, but I'm not sure)

Good Luck

---

### Post by markbuntu on 2008-05-28
I think your problem is with jackd since hydrogen uses jackd for audio and mplayer uses pulseaudio. You need jackctrl or jackcontrol I think it is called. Anyway, you can use it to configure jack to run through alsa instead of taking control of your sound card and locking out other applications. I never saw an option in jackctrl to choose pulseaudio so you may be stuck with alsa.

If you don't have them you should get the alsa wrappers for pulseaudio and xmms and any other sound manager one of your programs uses. Then you can set Sound to alsa instead of automatic and everything will run through alsa instead of them fighting for control of your sound card.

If you set everything to run through alsa you can avoid these problems except with flash. What I have found with my configuration is that flash will play together with anything already running but will not let another application that starts while flash is running use any sound. Once flash is finished the other apps can be opened and used.

Flash does not play nice with any other sound app in my experience no matter if it uses pulseaudio or alsa or xmms. It does not seem to matter. 

If anyone has figured this out please let us know.

---

### Post by SunnyRabbiera on 2008-05-28
> **moose4204l said:**
> i think they are giving up on me

Well the truth is that this is still an issue for some people in linux, right now linux in general does have issues playing two audio streams at once.
Its because how sound is relayed in linux, its not the same as windows and the kernel can only do so much on its own.
this issues has been around for years, its improving yes but its not quite there yet.

---

### Post by moose4204l on 2008-05-28
> **SunnyRabbiera said:**
> Well the truth is that this is still an issue for some people in linux, right now linux in general does have issues playing two audio streams at once.
Its because how sound is relayed in linux, its not the same as windows and the kernel can only do so much on its own.
this issues has been around for years, its improving yes but its not quite there yet.

well thanks for the heads...not to sound to negetive but you said its an issue for some and its improving so send that info my way to improve my stuff the best i can. people are giving me ideas on how to fix it but nothing is working so am i chasing a ghost with these method or no?

---

### Post by SunnyRabbiera on 2008-05-28
> **moose4204l said:**
> well thanks for the heads...not to sound to negetive but you said its an issue for some and its improving so send that info my way to improve my stuff the best i can. people are giving me ideas on how to fix it but nothing is working so am i chasing a ghost with these method or no?

well yes you might be on a wild goose chase, but its worth trying.
Please keep in mind that Linux/ Ubuntu is a community developed OS, so dont expect everything to work like it does in windows.
but keep trying none the less, and dont give up... you wont regret it :D

---

### Post by michaelzap on 2008-05-28
I'm having what is posibly a similar problem (fresh Hardy install, Flash 10 beta, on a Core2Duo desktop).

If I try to watch a web video (e.g., YouTube) while playing music in Amarok, my sound output dies and I can no longer hear anything in any program until I log out and back in. This also seems to happen with other programs playing at the same time (VLC, Totem), but mostly I've seen it happen in the case described above. What might cause that?

I'm going to set all my playback options to PulseAudio now and see if that helps.

---

### Post by markbuntu on 2008-05-28
I have everything set up to alsa and everything works for me except flash won't let other apps use the sound card while it is playing but once it stops everything is fine. ALL my sound inputs work all the time and all at once if I let them, line, cd, dvd, mic, pcm, aux, etc.

This is what I did:
1. get the alsa plugins/wrappers for pulseaudio and xmms and OSS and the gnomeALSAmixer and the alsa default sound card app.
2. set everything in System/Preferences/Sound to ALSA instead of automatic
3. Open default alsa sound card and choose my sound card instead of pulseaudio
3. use the gnomeAlsamixer to set the levels (it offers more choices than alsamixer and lives in my menu)

I tried to get everything to go through pulseaudio but it just didn't seem to work out so I tried ALSA and that works for me. If you use jack, pulseaudio is just a headache but then again, jack can be a headache too.

good luck.

---

### Post by moose4204l on 2008-05-28
ok, how do i get the alsa plugins/wrappers...i followed the section called "Getting the ALSA drivers from a *fresh* kernel" from [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=alsa+plugins%2Fwrappers") but i dont know if that solved what your directions is trying to accomplish.

also, i am able to get two mplayers to run side by side now with two songs going. I still have the problem where if I load up ZynAddSubFx and i have the keyboard out, and then i go to load mplayer, mplayer does not play. i get that same error message i posted before from mplayer

---

### Post by llama320 on 2008-05-28
> **michaelzap said:**
> I'm having what is posibly a similar problem (fresh Hardy install, Flash 10 beta, on a Core2Duo desktop).

If I try to watch a web video (e.g., YouTube) while playing music in Amarok, my sound output dies and I can no longer hear anything in any program until I log out and back in. This also seems to happen with other programs playing at the same time (VLC, Totem), but mostly I've seen it happen in the case described above. What might cause that?

I'm going to set all my playback options to PulseAudio now and see if that helps.

Michael,

Your problem was *exactly* the same as mine
I posted my solution above, try it out :)

---

### Post by michaelzap on 2008-05-31
> **llama320 said:**
> Michael,

Your problem was *exactly* the same as mine
I posted my solution above, try it out :)

Well, I did try it, but it didn't fix the problem. I am using Flash 10 beta, but I don't think that's related actually. Audio output stops if I play (or even open) two non-Flash videos in any video app (e.g., VLC).

I find that if I kill the pulseaudio process my audio comes back. If I don't do that, Ubuntu hangs on logout until I do a Ctrl-Alt-Backspace. That kills the process, so sound is restored again at the login screen.

I've seen a few threads on resolving pulseaudio bugs, but I think I'm going to wait for an update from the official repos since it's not a difficult situation to live with.

---

### Post by llama320 on 2008-05-31
> **michaelzap said:**
> Well, I did try it, but it didn't fix the problem. I am using Flash 10 beta, but I don't think that's related actually. Audio output stops if I play (or even open) two non-Flash videos in any video app (e.g., VLC).

I find that if I kill the pulseaudio process my audio comes back. If I don't do that, Ubuntu hangs on logout until I do a Ctrl-Alt-Backspace. That kills the process, so sound is restored again at the login screen.

I've seen a few threads on resolving pulseaudio bugs, but I think I'm going to wait for an update from the official repos since it's not a difficult situation to live with.

sorry I couldn't help :)

---

### Post by michaelzap on 2008-05-31
> **llama320 said:**
> sorry I couldn't help :)

I appreciate any advice from a llama, whether or not it ultimately solves my problem. ;)

---

### Post by markbuntu on 2008-06-01
Alsa plugins are in the repositories. Just open synaptic and do a search for alsa and you will find them.

Flash has problems all of its own that do not let other audio play when it is playing no matter if you are using pulseaudio or alsa or oss or xmms or jack. What I found is that at least with alsa flash returns control of the audio device when it is finished so other apps can use sound. Pulseaudio was not so consistent in this.

---

### Post by frankstrudel on 2008-06-03
ditto, but with amarok... everything plays fine by themselves, but a second one won't play.

---

### Post by Orestez on 2008-06-03
I have the same problem as you do.

This worked for me, and I think I read it somewhere else... 

Make sure to put all your sound playback settings to pulsedriver server.
Close all apps that play sound.
Do Alt+F2 and write "killall pulseaudio".

After I do that, everything plays simultaneously  . 

What I dont get is how this can be a problem of Flash, when its solvable by killing pulseaudio... Oh well, annoying. Its little things like these that are cannonfodder for windows advocates tho.

---


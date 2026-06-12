---
title: "Audio problems with Python"
date: 2007-05-01
forum: Programming Talk
---

### Post by Andrew Pape on 2007-05-01
Hi,

I have decided to try game programming with Python, using Pygame, which in turns uses SDL (Simple DirectMedia Layer) for audio and video.

I have run a few of the demo programs for Pygame, and found the same problem: the audio crackles. In each case, the audio is an Ogg file or else a wave sound effect. It first seemed like I might have a problem with my speakers or audio cables or connections, but when I play the same audio file with the Totem music player, just by simply clicking on the audio file, it plays perfectly. It seems that the programming call to the pygame mixer is the problem.

I've sent many messages to the pygame mailing list, and have had several replies. They have mostly suggested slight changes to the pygame mixer calls, for example to allocate a larger sound buffer, but such changes have not stopped the crackling. So it seems the problem is due to my OS setup. I'm using Feisty Fawn. Someone on the pygame mailing list said that he's had trouble with the combination of ALSA and SDL. I am reluctant to post more to the pygame mailing list because I'm getting more convinced that the problem isn't related to pygame itself. So I thought I'd try this forum.

I've tried experimenting with the sound options on the preferences menu, but with no luck. From what I've read about SDL, it should work with OSS or ALSA. But I'm out of my depth here. I hope someone can help.

Thanks in advance.

Cheers,

Andrew.

---

### Post by Andrew Pape on 2007-05-02
I've heard back from the Pygame mailing list today and a Linux guru solved the problem for me.
Before running the game, it's necessary for me to type the following line (or put it in a script):

export SDL_AUDIODRIVER=dsp

His general info was:

>You could try using the OSS emulation provided by ALSA:
>$ export SDL_AUDIODRIVER=dsp
>or:
>$ export SDL_AUDIODRIVER=dma
>then:
>$ python program-name.py

>or forcing ALSA:

>$ export SDL_AUDIODRIVER=alsa

>In my travels I've encountered stories of the ALSA OSS emulation working
>"better" than the native ALSA drivers, I can't verify that though,

I've read that SDL (Simple DirectMedia Layer, used for gaming) can use either ALSA or OSS. I don't have much technical knowledge about either of them, but hopefully the advice above will help any linux users of Pygame (which uses SDL) play audio properly.


Andrew.

---


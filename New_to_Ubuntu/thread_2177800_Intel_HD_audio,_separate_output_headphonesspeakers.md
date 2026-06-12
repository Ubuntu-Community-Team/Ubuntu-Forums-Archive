---
title: "Intel HD audio, separate output headphones/speakers"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by iamgrief on 2013-09-30
Hello, I am not pretty new with linux, but previously I was always stuck at some moment with different issues, so no one linux distro could change the windows in the meaning of primary OS for me for a long time. Recently I tried ubuntu 13.04 and (surprise!) almost everything was working right after installation automatically. The only thing I cannot fix is the sound. It works. Not perfect (some glithes appear during cpu heavy load), but acceptable for me. Even skype works right after apt-get install. But every time **I plug headphones, sound disappears from the speakers**. Is it possible to separate headphones and speakers as sound output devices? I just **want to hear my companion in the headphones, leaving all other sounds in speakers**. I have intel HD soundcard integrated to MSI 440-c75 (HDAUDIO\FUNC_01&VEN_10EC&DEV_0888&SUBSYS_14627599&REV_1002). Please do not ask me for different configs. I just want to know the theory - is it even possible or it isn't. If yes - should I configure ALSA directly or it can be reached with editing PulseAudio configs only? Should I find somewhere a new driver for the sound? Etc, etc... If you have a good article - welcome, I didn't find anything good using google. Thanks in advance.

---

### Post by theDaveTheRave on 2013-09-30
iamgrief,

the long and short answer to your question is... it depends...

Are you on a laptop or a desktop.

If you are on a desktop you can have 2 sound cards, one on the main board, and an extra sound card, you should be able to run different applications out through different cards ~ but you'll need to look into the setting in each application.

If you are on a laptop the same thing applies, with the added dificulty that it can be difficult to add an extra soundcard. and the hardware will disconnect the 'speaker' when you plug in a headset.

Other than that it sounds like you may need to look more deeply into pulse audo or ASLA, along with playing around with your settings.

David

---


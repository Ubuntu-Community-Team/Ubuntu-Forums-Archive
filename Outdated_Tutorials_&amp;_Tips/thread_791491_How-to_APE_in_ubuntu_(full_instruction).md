---
title: "How-to APE in ubuntu (full instruction)"
date: 2008-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by presston on 2008-05-12
Most of new users know that Ubuntu cannot play losess files as APE (+cue). That's why i decided to make short instruction how to make it works in audacious and beep player.

--------------------------------------------

1.(optional)Go to synaptic. Make search by word "audacious". And install audacious-extra

2.download 
[http://www.netswarm.net/misc/audacious-mac-0.3.10.tar.gz](http://www.netswarm.net/misc/audacious-mac-0.3.10.tar.gz)
and
[http://supermmx.org/resources/linux/mac/mac-3.99-u4-b5.tar.gz](http://supermmx.org/resources/linux/mac/mac-3.99-u4-b5.tar.gz)

3.unpack them

4. in terminal
> cd mac-3.99-u4-b5(mac-x.xx-ux-bx in other versions)
> ./configure
> make
> make install
> cd ~

5.> cd audacious-mac-0.3.10
> ./configure
> make
> make install

6. close terminal
7. start audacious and go preference-modules-audio.

maqke sure that all positions checked up.

that's all. have fun with losses music:)

PS. don't forget about > audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE, AAC, and WMA files. 
here: [http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/)

---


---
title: "Sound stuttering in Ubuntu"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by EllieDragonfly on 2011-10-14
Okay, I just upgraded to 11.10, and my sound stutters, and works really badly. My computer is Acer Aspire One, AO751h. It really bugs me, please help me.
PS: I am not that good with linux, so please be patient and keep it simple.
Yeah and my mic doesn't work either, pretty annoying, should I install Ubuntu 11.04? I have all my files on Ubuntu One so I don't mind.

---

### Post by fjblanco on 2011-11-02
Hi, I've the same problem in my AO751h. Once I installed (fresh) the 11.10 version, the mic didn't work and the sound was intermitent. I tried to update the ALSA driver and now ubuntu doesn't detect the audio (the aplay utility doesn't play any sound...).
Please... help!!
Thanks!

---

### Post by MRA2011 on 2011-11-06
Hi guys,

I've joined specially to post what worked for me (fix for choppy audio, don't know about the other bits!). I too have an Acer Aspire One 751h and have spend several hours searching and trying different fixes. I cannot say 100% that it was not down to a combination of things I tried, but nothing else seemed to have any effect and then this one fix just worked:

Press Ctrl+Alt+T to open the Terminal window

Copy & Paste (Ctrl+C then Ctrl+Shift+V)/type in the following text:

**> gedit /etc/pulse/default.pa**

Now find the line which says load-module module-udev-detect

change it to read **> load-module module-udev-detect tsched=0**

save and close the text editor

In the terminal window type:

**> pulseaudio -k**

to restart Pulse Audio. Now run your sound/video file and it should all be working ok. If not then post again and I'll tell you all the other stuff I tried!:KS

Taken from - [http://www.st4ck.com/it/post/ubuntu-11-04-vlc-out-of-sync/#Runtime](http://www.st4ck.com/it/post/ubuntu-11-04-vlc-out-of-sync/#Runtime)

---

### Post by ns7815 on 2012-03-18
Thank you, MRA2011.

I was having problems with stuttering audio on my Acer Aspire 5755G with Ubuntu 11.10.

I tried your fix above and it worked flawlessly.

Now all I need is for someone to make linux drivers for my 2GB GeForce GT 630M graphics card... :cry:

---

### Post by martesmartes on 2012-07-04
@MRA2011 Thanks--I was having the same problem with Linux Mint13 Mate, and this seems to have fixed it perfectly.

---

### Post by e8hffff on 2013-02-20
Fixed my stuttering too on 12.10 Kubuntu.  Many thanks.

Crazy how this isn't fixed in mainstream

---

### Post by ntoprint on 2013-02-20
I have an HP Touchsmart Laptop/Tablet that I recently just put Ubuntu 12.10 on. I have sound when play with things on my computer and when watching YouTube and other basic videos. But, when I try to play games like Lord Of Ultima and Command and Conquer: Tiberium Alliances, there is no sound. I have no sounds for any parts of the game: sound effects or music. I have checked the settings on the games themselves and everything should work based on those settings. I have gone into my sound settings on my OS and tested everything and it checks out. Any ideas or help available would be great. Thanks.

---


---
title: "Sound Suddenly Stopped"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by tprzepiorka on 2008-08-13
Since I've installed ubuntu (7.04) my audio has worked perfectly without any tweaking. This includes the time after I upgraded to Hardy. However the other day I restarted my computer and no sound was coming from my speakers. I booted to vista and it worked, so it doesn't look like a hardware problem. Also when I double click on the volume icon I only get one selection for changing the volume. In the past I got many different ones.

I can post any information that can help fixing this issue. But not sure if there is an easy way to get my sound card model info by using a command. That would help. I didn't change any hardware or anything to do with sound/audio when it stopped working so I'm not sure of the cause.
Thanks in advance for any help :)

---

### Post by billgoldberg on 2008-08-13
> **tprzepiorka said:**
> Since I've installed ubuntu (7.04) my audio has worked perfectly without any tweaking. This includes the time after I upgraded to Hardy. However the other day I restarted my computer and no sound was coming from my speakers. I booted to vista and it worked, so it doesn't look like a hardware problem. Also when I double click on the volume icon I only get one selection for changing the volume. In the past I got many different ones.

I can post any information that can help fixing this issue. But not sure if there is an easy way to get my sound card model info by using a command. That would help. I didn't change any hardware or anything to do with sound/audio when it stopped working so I'm not sure of the cause.
Thanks in advance for any help :)

The command you are looking for is "lspci".

Try switching your sound to ALSA in system -> preferences -> sound (could be administration) and select ALSA instead of default.

Or try another one and see what works.

Then install gnome-alsamixer

```
sudo apt-get install gnome-alsamixer
```

and launch it from applications -> sound and videos -> gnome-alsamixer

once opened, max everything.

---

### Post by Crafty Kisses on 2008-08-13
Have you tried this?

1. Right Click on speaker icon on panel
2. Click "Open Volume Control" in the resulting menu
3. Select the "Switches" tab
4. Make sure "Line In as Output" is checked.

Then to make sure also, you can open "alsamixer" do the following in Terminal:
```
alsamixer
```
Look at the volumes.

---

### Post by tprzepiorka on 2008-08-13
Great! Thanks for the tips. Tried going into the sound preferences but that didn't fix it. I opened up the volume control and then went to File>Select Device and picked one that wasn't selected, until I got one that worked. 

Don't know if there is anyway to report how it changed as a bug or anything. It seems very odd that it would change the device itself and then mute my audio option.

Thanks again for the speedy replies. :)

---

### Post by nicedude on 2008-08-13
I hate to say this one as its a tag line from one of my favorite shows "IT Crowd" on BBC, but "have you tried turning it on and off again" :-)

On one of my Ubuntu boxes sound conks out say once a week and I have to reboot to get it back, Haven't taken the time to troubleshoot it though as it is fixed by a reboot and I don't watch to much media on that box anyway so I don't know why. But most likely that a video player that was supposed to be closed still had its hooks in my sound system.

So try a reboot if you haven't already

Edit
oops I see you got it working while I was typiing and it was Alsamixer after all, good deal that you got it going.

---

### Post by tprzepiorka on 2008-08-13
Haha, don't worry I always try a reboot before looking for help. Fixes about 90% of problems :D

---


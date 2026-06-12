---
title: "no full screen for video files"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by bijelivuk on 2008-07-19
hi...
i have a problem with playing any kind of video files
i can't make it fullscreen.....when i watch it in window mode it works ok but when i transfer it to fullscreen i have same size picture and black frame around it

is there any chance to see it fullscreen???

i tried to change programs...vlc, kaffeine, noautn....same problem everywhere

i have fujitsu siemens v5515 laptop with sis mirage 3 graphic....can that be a problem??

---

### Post by nikgare on 2008-07-19
If possible, can you try in Xine?

---

### Post by bijelivuk on 2008-07-19
tried it...
same thing...

---

### Post by Joergen Marmalade on 2008-07-21
Same problem here.

---

### Post by billgoldberg on 2008-07-21
Could it be related to the video card or compiz?

Go to "system -> administration -> hardware drivers" and install them.

If nothings there, google for "ubuntu envy". Download it and use it.


---

It could also be compiz related.

Go to applications -> add/remove and search for "compiz icon".

Install it, use it and select metacity instead of compiz as window manager.

Then try watching the video.

--

This is the first time I heard of a problem like this, so I don't know it this has something to do with it, but it seems likely.

---

### Post by Joergen Marmalade on 2008-07-22
Thanks for you help, although it didn't do much good.

Compiz Icon didn't do any difference at all.

As for Envy, I haven't tried it as it only supports ATI and Nvidia graphics cards and *bijelivuk* and I both have SIS Mirage 3 graphics cards.

Any suggestions?

---

### Post by RomeReactor on 2008-07-22
Hi. Maybe this [solution at UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback") can be of help.

---

### Post by SunnyRabbiera on 2008-07-22
Some low end video cards have side effects like this I am afraid, heck even if it was a intel it might have been better...

---

### Post by sisco311 on 2008-07-22
try:
```
mplayer -zoom -vo x11 file.avi
```

---

### Post by tech0007 on 2008-07-22
> **sisco311 said:**
> try:
```
mplayer -zoom -vo x11 file.avi
```

x11 video ouput does not allow fullscreen.  you should use -xv or -gl/gl2.

---

### Post by sujoy on 2008-07-22
yes x11 doesn't allow fullscreen thats why the -zoom option was given

either mplayer -vo xv file.avi or mplayer -zoom -vo x11 file.avi ought to work

---

### Post by Joergen Marmalade on 2008-07-22
As a matter of fact, boys and girls, I have solved the problem.

I changed to X11 under preferences=>preferences=>video=>output modules in VLC. That seems to work for me!

Thanks to everyone!

---

### Post by bijelivuk on 2008-07-25
thank you all for help

that setting in vlc preferences has done a job for me to

again, thanks

---


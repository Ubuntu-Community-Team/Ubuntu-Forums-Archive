---
title: "divx to xvid convertor"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by sitka on 2008-04-28
How can you convert divx files to xvid?????

---

### Post by anewguy on 2008-04-28
I know there are several tools around for working with video - I use on called Kino.  I also had to install ffmpeg and it's associated stuff.  Kino imports the videos from my camera and then I can export them to another flavor - not sure if xvid is one of those or not.  You may want to try it just to see.

:)

EDIT:  Just checked, when you export there are some tabs across the screen - choose "other" then you can select XVID mpeg4 as the output type.

---

### Post by joshrobinson on 2008-04-28
> **sitka said:**
> How can you convert divx files to xvid?????

avidemux is also an option

---

### Post by little_penguin on 2008-05-24
Actually all you need to do is to change the fourcc code from divx to xvid. There is a program called gfourcc that does this which is a GUI for cfourcc. You can install both of these via Synaptic or via the command line, whichever you prefer. Then just open the avi in gfourcc and change from divx to xvid, or whatever options are available.
No conversion necessary, just change the fourcc code, really fast and easy.

---

### Post by micro_mx on 2008-05-25
avifix -F DX50 movie.avi 
I think avifix its in transcode

---

### Post by skippycostin on 2011-07-25
> **little_penguin said:**
> Actually all you need to do is to change the fourcc code from divx to xvid. There is a program called gfourcc that does this which is a GUI for cfourcc. You can install both of these via Synaptic or via the command line, whichever you prefer. Then just open the avi in gfourcc and change from divx to xvid, or whatever options are available.
No conversion necessary, just change the fourcc code, really fast and easy.

Thank you :)

---


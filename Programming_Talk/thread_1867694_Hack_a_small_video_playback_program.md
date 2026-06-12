---
title: "Hack a small video playback program"
date: 2011-10-23
forum: Programming Talk
---

### Post by cap10Ibraim on 2011-10-23
is there a simple program that I can use to play a video file that keep growing in size 
I'm capturing a video using cheese 
wrote small code that send the file while recording to another host 
the file received keep growing in size as it should be but I have to open Totem again to play the extra received packets 
If you can point me to small app that use C , so I can implement select() while opening the media file

---

### Post by DarkAmbient on 2011-10-23
If I understood correctly, you want to record a video while you watch what's being recorded? Doesn't most (all?) video-capturing software let you do that?

---

### Post by cap10Ibraim on 2011-10-23
I'm capturing video through a cam 
while recording i'm sending the file through a network to hosts 
the file keep assembling correctly while received , but the playback program open a fixed size file in other words it only play   the bytes received by the time the playback program is opened , even though more packets are being added to the file

---

### Post by Ms. Daisy on 2011-10-23
> **cap10Ibraim said:**
> I'm capturing video through a cam 
while recording i'm sending the file through a network to hosts 
the file keep assembling correctly while received , but the playback program open a fixed size file in other words it only play   the bytes received by the time the playback program is opened , even though more packets are being added to the file Why can't you stream it to the hosts and capture the recording separately?

---


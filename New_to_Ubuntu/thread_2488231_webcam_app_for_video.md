---
title: "webcam app for video"
date: 2023-06-27
forum: New to Ubuntu
---

### Post by mjp292 on 2023-06-27
What's a good webcam app for video?

---

### Post by ActionParsnip on 2023-06-28
Cheese ....?

---

### Post by mjp292 on 2023-06-28
should I smile?

lol

thanks
'
p.s. but seriously, i tried it, and it won't record audio for some reason - >???

---

### Post by mIk3_08 on 2023-06-28
audio? It should be coming from your mic. Try to check your sound  settings "input devices." see the input volumes or just see image below.  Regards and cheers.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292428&stc=1[/IMG]

---

### Post by Autodave on 2023-06-28
guvcview is anither to try.  Works great for me.

---

### Post by TheFu on 2023-06-28
Cheese never worked well for me.  
GuvcView did.  
When I need more than trivial recording, I use OBS, but that is a complex application for video muxing and production.
Sometimes, just using SimpleScreenRecorder works.

When it comes to screen/video recording, the display server matters.  I use X11, not Wayland. That could be important, but may not be. IDK.

---

### Post by MAFoElffen on 2023-06-28
+1 --- Another vote for GuvcView.

Another note is that guvcview is the only Linux webcam app that I've been able to get to work dependably on MAC hardware, for my MAC customers.

---

### Post by mIk3_08 on 2023-06-29
Thanks for sharing guys. I have search GuvcView via apt and its positive its in the repository and I have already tried and installed it and works so smoothly to my Ubuntu 22.04 LTS system. Regards and cheers.

---

### Post by mjp292 on 2023-07-11
I can't for the life of me get the video to deliver audiol.
I made every setting right in sound and pulse audio.
On my hp desktop AND hp laptop the same damn problem!

help!

This is a movie I uploaded - no audio!

---

### Post by jimmyrus on 2023-09-15
> **mjp292 said:**
> I can't for the life of me get the video to deliver audiol.
I made every setting right in sound and pulse audio.
On my hp desktop AND hp laptop the same damn problem!

help!

This is a movie I uploaded - no audio! 
This guy has the same problem  [https://ubuntuforums.org/showthread.php?t=2487377](https://ubuntuforums.org/showthread.php?t=2487377)   [https://ubuntuforums.org/showthread.php?t=2487268&p=14144881](https://ubuntuforums.org/showthread.php?t=2487268&p=14144881) 

[FONT=monospace]Lots seem to have this problem too if you do a google search. Some of the smarter ones tell about their hardware and check sound levels in pavucontrol for the app, but they've been linux users for a good while. May wanna try it.
[COLOR=#000000][/COLOR][/FONT]

---

### Post by SeijiSensei on 2023-09-16
If the file is a normal video format like .mp4, you should open it with a video player like VLC. Then you'll have audio.

If not, what format is the file? What extension does the file have?

---


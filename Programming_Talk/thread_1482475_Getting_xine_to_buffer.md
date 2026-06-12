---
title: "Getting xine to buffer"
date: 2010-05-13
forum: Programming Talk
---

### Post by PaulM1985 on 2010-05-13
Hi

I'm still working on my media player and having more trouble.  I am almost there with it but for one small thing.  

I am streaming video from an apache server on one computer to another computer which is using xine as the media playing component.

When I set the player to start playing a video, it manages to buffer to about 21% then the xine lib starts playing the video.  Because of this I get really jumpy frames and no sound.  I have noticed that if I start xine at the command line passing in the url of the video, eg [http://xxx.xxx.x.xx:8080/myVid.avi](http://xxx.xxx.x.xx:8080/myVid.avi) the player buffers to 100% then plays.

When I say starting from command line, I mean on the actual xine component, not what I have written.

Does anyone know much about xine?  Does anyone have any idea I on how I can get it to wait until it has completed buffering before getting the player to start?

Paul

---

### Post by PaulM1985 on 2010-05-14
bump

---


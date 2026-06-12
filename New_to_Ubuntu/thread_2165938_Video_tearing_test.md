---
title: "Video tearing test?"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by vasa1 on 2013-08-07
There are several mentions of video tearing in this thread: [Xubuntu 13.10 XMir ISO Available For Testing]("http://ubuntuforums.org/showthread.php?t=2165540").

I came across this video, [http://www.youtube.com/watch?v=ceX18O9pvLs](http://www.youtube.com/watch?v=ceX18O9pvLs), but there's no explanation of what we're supposed to see.

---

### Post by moltenicee on 2013-08-07
If you have screen tearing, the bar will not be solid. It will have breaks in it and be jagged with v-sync off. If you don't notice anything wrong with the video, then you are fine and have no screen tearing! :)

---

### Post by XG4GRhE on 2013-08-07
> **moltenicee said:**
> If you have screen tearing, the bar will not be solid. It will have breaks in it and be jagged with v-sync off. If you don't notice anything wrong with the video, then you are fine and have no screen tearing! :)

how do u fix it on ubuntu 12.04? i am 100% sure i have this

---

### Post by Rob Sayer on 2013-08-07
> **XG4GRhE said:**
> how do u fix it on ubuntu 12.04? i am 100% sure i have this

This is a bit off topic ... the OP is talking about a pre official release ubuntu version with a possible bug.  Not 12.04.

Tearing in general can be caused by plenty of things, from playing software to slow hardware.  But it's not really a ubuntu issue per se.

My torture test video is a 16Gb 1080p file.  Definitely over 10Kb/s bit rate.  And it's h.264 codec video with CABAC enabled, which is the hardest to play.  On my laptop with an i3 and 4Gb RAM (ie. middle of the road), running kubuntu 12.04 with no compositing on full screen, on external screen with both screens active, it plays flawlessly at about 20% CPU usage.  

So, on second thought, tearing is definitely not a ubuntu issue really.  However, ubuntu with unity does *not* perform as well as kubuntu on the same machine.

That's using smplayer with the local file stream cache set to a healthy number and cache pre fill enabled.

I'd try different video players ... smplayer performs the best IME.  If you're running ubuntu/unity, install the utility that enables you to turn off compositing full screen.  It doesn't work for video rendering as well as kde but it's better.

---

### Post by The Cog on 2013-08-07
Tearing is when the screen is updated partway through a vertical scan. When that happens, for a moment the screen is broken into two parts, containing parts of two consecutive frames. This is invisible when there is no movement, but obvious when there is a lot of movement, visible as lots of horizonal breaks (tears). That tear test on youtube shows the moving bar being broken into two parts quite often on my PC. Tearing can't happen if the screen is always updated exactly as the screen starts a new scan from top to bottom.

---

### Post by vasa1 on 2013-08-07
> **moltenicee said:**
> If you have screen tearing, the bar will not be solid. It will have breaks in it and be jagged with v-sync off. If you don't notice anything wrong with the video, then you are fine and have no screen tearing! :)
Thanks for explaining but could you clarify a couple more points? If there is no tearing then the white bar should be intact all through the video. I downloaded the video and played it using GNOME Mplayer, Vlc, Firefox and Chrome. The white bar was intact while moving for the first two but with both browsers I saw very obvious tearing. So it seems this is dependent on the video player? People in the post I linked to didn't mention what they were viewing the videos on.

The second point is that, with the first two players, even though the white bar was intact, the horizontal movement wasn't smooth but somewhat "stuttery". Is that also tearing?

---


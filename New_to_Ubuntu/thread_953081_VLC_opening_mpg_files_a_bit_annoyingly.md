---
title: "VLC opening mpg files a bit annoyingly"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by kingdonerkebab on 2008-10-19
Hi. Little problem I'm having with VLC. Trying to make it my default program for all videos, mainly cos it plays everything. I'm using Hardy. I've set it to open mpgs by right clicking one, then properties>open with the selecting vlc. It's selected automatically the other mpgs on my drive too so that's all good. When I double click an mpg now though it gives me an error message:

The following errors occurred. More details might be available in the error message below;
Unable to open 'file:///media/Data/video1%20-%20B%20Day%20%5B2006%5D%5BCD+2%20video1%20Vu%20%5BFt.%20%5B2006%5D.mpg'

or something that looks vaguely like that anyway. If I open up VLC first and use open file, then browse to the file and open it works, but not when I double click or right click then 'open with vlc' over the icon.

Thanks

---

### Post by patrickballeux on 2008-10-19
Could be related to the path where your video is...

Just for a quick test, copy the video on your desktop, and double-click on it.  If it works, you know that it is something in the path that VLC is not able to translate/follow...
It happened to me with another software because my path was /home/patrick/Vidéos". The "é" prevented the loading with a full URL.

---

### Post by kingdonerkebab on 2008-10-19
Thanks for answering so quickly!

You are right. Tried moving it around and renaming the subfolder it was in. I think it was because the subfolder had []s in it.

---


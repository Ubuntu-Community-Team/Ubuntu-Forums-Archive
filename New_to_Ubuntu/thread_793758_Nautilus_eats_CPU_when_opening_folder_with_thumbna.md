---
title: "Nautilus eats CPU when opening folder with thumbnails"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by El Lance-O on 2008-05-14
The title wraps it up.

When I enter a folder with video files or pictures, especially when there are a lot of them, my CPU jumps up quite high (60-80%) and sometimes causes nautilus to hang.

Hardy overall just eats the hell out of my CPU :(

And I have a dual-core, what's up with that?

---

### Post by seetho on 2008-05-14
Nautilus generates previews (thumbnails) of all files - not just pics.  If you have folder with lots of large files it will take a long time to generate the thumbnails.  You can go to Nautilus prefences and change the preview behaviour, or even turn it off.

As for your dual core CPU, run "top" in terminal and press "1" to see if you really are using both CPUs (or you can run System->Administration->System Monitor to see you CPU load.  If you only see one cpu then you are running the wrong kernel.

---

### Post by balagosa on 2008-05-14
experienced the same thing. i dont know Nautilus that much but maybe you can disable the preview option for pictures?

---

### Post by El Lance-O on 2008-05-14
Nope, the two CPU's are correctly detected.

But Firefox (2, 3 just died on me) eats CPU REALLLY REALLY bad, especially when flash is in play.

And overall, it just seems like my laptop should be "faster".

Anyways, the thumbnail problem happens more often with videos than pictures, and it seems to go away once I minimize the window or change viewports.

I just want to know why it spikes so high, as it didn't before.

---

### Post by seetho on 2008-05-14
Nautilus previews videos as well.  It will try to decode the video and create a thumbnail out of a frame of the video.  If you have many videos in a folder then it will chew up your cpu time.  However it will only do this once.  The next time you browse into the folder it should be quick.

I have a 1.4Ghz single core cpu notebook and it runs fine with max file size to preview set to the default 5MB.

Perhaps you can try disabling the preview feature to see if it is the source of the problem.

---


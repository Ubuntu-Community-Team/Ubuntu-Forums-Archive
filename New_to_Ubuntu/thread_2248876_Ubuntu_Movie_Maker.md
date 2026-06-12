---
title: "Ubuntu Movie Maker"
date: 2014-10-17
forum: New to Ubuntu
---

### Post by dcraiglong on 2014-10-17
As a hobby I make audio books and load them to youtube, usually short poems or short stories. In Windows I would record the audio and combine WAV/MP3 with a static picture in Windows Movie Maker and then simply export them as a WAV. Is there any program in Ubuntu I can use to do this same thing (doesn't have to be WAV but anything youtube would pick up as a video.)? It seems such a simple thing but I'm having the hardest time. Thank you so much friends.

---

### Post by TheFu on 2014-10-17
ffmpeg or avconv?

```
ffmpeg -i <audio file> -loop 1 -i <image file> -shortest <output video file>
```

avconv will be slightly different.

IMHO, much easier than all that GUI stuff.

---

### Post by papibe on 2014-10-17
Hi dcraiglong. Welcome to the forum ):P

There are several alternatives, all available for installation on the 'Software Center'. Search for 'video editor'.

I'd recommend taking a look at 'Openshot'.

Hope it helps. Let us know if that works for you.
Come here often, and have fun.
Regards.

---

### Post by haplorrhine on 2014-10-17
OpenShot is pretty intuitive and will allow you to do that much.

---

### Post by jeehyun on 2014-10-18
Openshot is best option. Avidemux is also good. Commercial sw for consumers is not available.

---

### Post by Rob Sayer on 2014-10-18
I'd recommend openshot and avidemux too.  They both have a very good balance between ease of use and power.

---

### Post by MartyBuntu on 2014-10-18
Kdenlive.

---

### Post by 3rdalbum on 2014-10-19
I did exactly this recently in Openshot. I dragged the audio file onto one of the audio tracks in Openshot and dragged the picture into the Video track, then lengthened the picture's duration to match the audio duration. I applied a fade in and fade out on the picture. Then I exported the video using the "YouTube" setting and I uploaded the file to YouTube.

Easy. Openshot.

---

### Post by FakeOutdoorsman on 2014-10-19
Several simple examples using ffmpeg are here: [https://trac.ffmpeg.org/wiki/Encode/YouTube](https://trac.ffmpeg.org/wiki/Encode/YouTube)
Also a fancy example using various visualization filters.

It has the advantage of being able to re-mux your audio, so you don't have to re-encode it; therefore preserving quality and less of a wait for the output to be made. I don't know if any of the other mentioned tools can do that.

To get ffmpeg you can: [download](http://johnvansickle.com/ffmpeg/), [use a PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media), or [compile](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

---


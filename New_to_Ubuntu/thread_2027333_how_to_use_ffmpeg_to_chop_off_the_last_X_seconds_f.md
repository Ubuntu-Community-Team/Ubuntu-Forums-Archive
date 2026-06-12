---
title: "how to use ffmpeg to chop off the last X seconds from an mpeg-4 video"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by palawanbeach on 2012-07-16
According to [http://ubuntuforums.org/showpost.php?p=12102310&postcount=2](http://ubuntuforums.org/showpost.php?p=12102310&postcount=2), I can use ffmpeg to chop off portions of an mpeg-4 if I know exactly where I want to chop.

I can figure out what portion to chop by first playing the video file in VLC.

Let's say an MPEG-4 video file goes for 2 minutes, 15 seconds. And let's say I want to remove the last 3 seconds, so that all that remains is 2:12. what command do i run in terminal to accomplish this?

Bonus question: What if I want to keep 2minutes:12seconds:**20microseconds**?

---

### Post by evilsoup on 2012-07-16
From the manpage:

```
-t duration (output)
           Stop writing the output after its duration reaches duration.  duration may be a number in seconds, or in
           "hh:mm:ss[.xxx]" form.

```

I'm pretty sure ffmpeg will have to re-encode after this, though, so you will lose quality.

---

### Post by palawanbeach on 2012-07-16
> **evilsoup said:**
> From the manpage:
```
-t duration (output)         
```
I'm pretty sure ffmpeg will have to re-encode after this, though, so you will lose quality.

thanks, evilsoup, for your response.

I would like to retain the quality for this my simple "chopping" operation. What should I do? If ffmpeg produces a lower-quality video, what programs keep the same level of quality?

---

### Post by FakeOutdoorsman on 2012-07-19
> **palawanbeach said:**
> I would like to retain the quality for this my simple "chopping" operation. What should I do?

You can copy streams instead of re-encoding:
```
ffmpeg -i input -t 5 -ss 15 -vcodec copy -acodec copy output
```
or newer syntax:
```
ffmpeg -i input -t 5 -ss 15 -c copy output
```
I added *-ss 15* in the examples to show how to also cut off the first 15 seconds.

---

### Post by palawanbeach on 2012-07-19
thanks, fakeoutdoorsman.

---


---
title: "nuvexport to DVD with mythtv 0.19"
date: 2006-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by irwand on 2006-05-17
After getting mythtv 0.19 from
deb [http://deb.thehunter.ws/](http://deb.thehunter.ws/) breezy mythtv-stable
I found that nuvexport 0.2 no longer works well with it.

Fortunately, the latest nuvexport (currently 0.3) works pretty well..
Although, at least to export myth recordings to DVD, you need to answer "no" to "Enable noise reduction" question. Apparently ffmpeg that is on breezy needs some work on the yuvdenoise. If you answer "yes" to that question, the transcode fails. This costed me a lot of hours, until I read:
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
(read the ffmpeg part)

---


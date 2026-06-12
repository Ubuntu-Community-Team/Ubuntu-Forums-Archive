---
title: "Constantly monitoring file for change"
date: 2006-01-08
forum: Programming Talk
---

### Post by harisund on 2006-01-08
I think the title is pretty much obvious. There is a file that I want constantly monitored. Every time it changes I want something to run. 

By changes, I mean the content. Basically it is a target file for wget. Everytime I enter a url into it I want wget to start in the background using the contents of the file as the download url. 

Is there a way to put it as a script? 

Thansks !

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=harisund]I think the title is pretty much obvious. There is a file that I want constantly monitored. Every time it changes I want something to run. 

By changes, I mean the content. Basically it is a target file for wget. Everytime I enter a url into it I want wget to start in the background using the contents of the file as the download url. 

Is there a way to put it as a script? 

Thansks ![/QUOTE]
what I would do is wget the page to some file that I could compare it to and then maybe set up a cron job to wget the same page periodically.  You could compare them with diff --brief.  If diff reports any changes, you can run your script.

---

### Post by harisund on 2006-01-08
hmm...diff was something I hadn't known about.. thanks ..

---

### Post by Lews Therin on 2006-01-08
When I ran Gentoo, I used [inotify](http://www.edoceo.com/creo/inotify/) for things like this. Ubuntu doesn't seem to include that patch (no /dev/inotify file), but when the kernel package is updated to 2.6.13 you should be able to use it.

---


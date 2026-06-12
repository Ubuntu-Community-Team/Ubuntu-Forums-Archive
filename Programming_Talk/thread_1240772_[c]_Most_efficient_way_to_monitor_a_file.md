---
title: "[c] Most efficient way to monitor a file"
date: 2009-08-15
forum: Programming Talk
---

### Post by Xaero252 on 2009-08-15
Okay, heres the situation, an application logs to a file, this file is only 1 line long, and it is just updated periodically. What I want to do is use system("notify-send 'Example' 'Message'"); to use the gnome notification daemon to send me the status & message from that file, but obviously only when it has changed.
The primitive solution was to just use a while loop at always read from the file, and see if its changed by comparing the string result. However, this is obviously TERRIBLY inefficient. Is there a better way to wait for this file to change? it probably won't be updated too frequenty (avg is more than 2 minutes, but there are times when it can change several times in a single minute)

---

### Post by scourge on 2009-08-15
It's probably not as trivial as it sounds. Inotify should do the job, although I haven't used it personally:
[http://en.wikipedia.org/wiki/Inotify](http://en.wikipedia.org/wiki/Inotify)
[http://www.linuxjournal.com/article/8478](http://www.linuxjournal.com/article/8478)

---

### Post by uljanow on 2009-08-15
There are basically two options, i) get notified ii) use polling (check only file properties instead of the content).

---


---
title: "Linux API Reference [urgent]"
date: 2008-08-28
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-08-28
Hi, Any one knows how to delete a file and folder in linux with c++ ? I did it in windows but linux is really annoying me ? :(
Why there isn't any API reference ? Linux is really really really JUST working with files. Is that always good ? I have to read a file (wtmp or utmp) and get current loggedon username !!! It can slow down  my program :( Really there isn't other way ?

---

### Post by Joeb454 on 2008-08-28
Moved to Programming Talk.

---

### Post by mike_g on 2008-08-28
This was already answered in another thread: [Linux API Reference Urgent](http://ubuntuforums.org/showthread.php?t=901133&page=2). Cross posting is annoying because you end up wasting peoples time; I almost answered this :(

---

### Post by signifer123 on 2008-08-28
> **hosseinyounesi said:**
> Hi, Any one knows how to delete a file and folder in linux with c++ ? I did it in windows but linux is really annoying me ? :(
Why there isn't any API reference ? Linux is really really really JUST working with files. Is that always good ? I have to read a file (wtmp or utmp) and get current loggedon username !!! It can slow down  my program :( Really there isn't other way ?

As was stated before in the other thread( please stop making them ) you could have just read the output of the `who` command.

Why do you think reading files this slows down your system so much?


I timed the attached program that reads the utmp 1000 times, with opening, read all the lines, and closing each time. Timed it with the time command, resulting in the following times.

real	0 min 0.033 sec
user	0 min 0.008 sec
sys	0 min 0.028 sec

Just writing the value of i to the console each time, raised it to:

real	0 min 0.061 sec
user	0 min 0.028 sec
sys	0 min 0.020 sec

In conclusion, reading those files arn't killing you. if you can read utmp 30000 times in a second.

Source code attached.

---


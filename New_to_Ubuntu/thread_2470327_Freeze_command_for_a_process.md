---
title: "Freeze command for a process?"
date: 2021-12-26
forum: New to Ubuntu
---

### Post by gfl3 on 2021-12-26
Hi, 

Is there a way to freeze a running process? If so, what's the command syntax?

---

### Post by KBar on 2021-12-26
It depends on your definition of the words *freeze* and *process*.

In bash, by default, ^Z is the suspend character that sends **TSTP** signal. Job control should be enabled (default). See this answer: [https://superuser.com/questions/485884/can-a-process-be-frozen-temporarily-in-linux](https://superuser.com/questions/485884/can-a-process-be-frozen-temporarily-in-linux)

---

### Post by ActionParsnip on 2021-12-26
[https://ostechnix.com/suspend-process-resume-later-linux/#:~:text=First%2C%20find%20the%20pid%20of,kill%20%2DCONT%20](https://ostechnix.com/suspend-process-resume-later-linux/#:~:text=First%2C%20find%20the%20pid%20of,kill%20%2DCONT%20).

---

### Post by yetimon_64 on 2021-12-28
> **ActionParsnip said:**
> [https://ostechnix.com/suspend-process-resume-later-linux/#:~:text=First%2C%20find%20the%20pid%20of,kill%20%2DCONT%20](https://ostechnix.com/suspend-process-resume-later-linux/#:~:text=First%2C%20find%20the%20pid%20of,kill%20%2DCONT%20).

@ OP, ActionParsnip's link is probably the best/safest info for your needs.

If I have a process running (eg. mpv) and want to pause it I use ...
```
killall -s STOP mpv
```
To restart it ...
```
killall -s CONT mpv
```
If your process has many instances running then using "kill" with the process id number is the best option as per ActionParsnip's link. Only use killall with the process name if you are sure only one instance is running; I only use the above commands with applications I start like video players or music players, which I know are single instances.

---

### Post by TheFu on 2021-12-28
> **gfl3 said:**
> Hi, 

Is there a way to freeze a running process? If so, what's the command syntax?

Read this, annually. [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  Every year, you'll understand more and stuff that didn't make sense last year will make sense this year or the next or the next or the next ... 

Basic Unix job control stuff works on Linux the same.

---


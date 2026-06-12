---
title: "gnu screen &quot;stuff&quot; ?"
date: 2013-04-21
forum: Programming Talk
---

### Post by Merrattic on 2013-04-21
What am I doing wrong?

I have setup a crontab job to quit the running instance of screen (terminate it). From reading the man and googling, it appears I can use a "stuff" command to do this with an octal code to create a return:

```
screen -X stuff "exit\015"
```
or
```
screen -X stuff "exit^M"
```

All this does is place the complete line of text on the command line in screen, the "false" return code doesn't work as expected?

If I type exit at the command line in screen, and press return, screen terminates as intended.

killall -9 screen works, but it isn't as pretty.....:(

Any help appreciated....

---

### Post by schragge on 2013-04-21
Why not just ```
screen -X quit
```:?:

---

### Post by Merrattic on 2013-04-21
I thought I had tried that but will give it a go. Thanks :)

---

### Post by Merrattic on 2013-04-21
It works :)

---


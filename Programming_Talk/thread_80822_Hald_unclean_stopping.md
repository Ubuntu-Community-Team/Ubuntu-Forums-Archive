---
title: "Hald unclean stopping"
date: 2005-10-23
forum: Programming Talk
---

### Post by paddyg on 2005-10-23
Have you noticed an unclean stopping for hald when shutting down your system?
Here's the message on screen:
```
Stopping Hardware Abstract Layer:
/etc/dbus-1/event.d/20hal: line 49: /var/run/hal/hald.pid: no such file or directory
Kill usage......
```

But there is an OK in the end all the same, as if hald stopped anyhow.

Here are the lines in 20hal that cause the message:
```
if [ -e $PIDFILE ]; then
kill -9 $(< $PIDFILE) || true
rm -f $PIDFILE
fi
```
So, my guess is hald stops correctly and then the block is evaluated. But i wonder why the THEN part is evaluated if there is no pid!

I commented the block and the message has vanished.

Now, why those lines? are they really necessary? No such block in Hoary, and it worked great all the same. Am i missing something?

---

### Post by blackant on 2006-02-27
I am getting this, notice this after I connect and disconnect my mp3 player via USB.

---

### Post by blackant on 2006-03-17
I think I fixed it by reinstalling hal...

---

### Post by blackant on 2006-03-17
The problem seems to come back after a reboot...anyone can help?
Thanks.

---


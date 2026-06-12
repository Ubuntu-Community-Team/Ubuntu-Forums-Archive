---
title: "tty over tcp"
date: 2010-05-02
forum: Programming Talk
---

### Post by lpm11 on 2010-05-02
Hello everyone!

I need something, to link tcp connection with character device.
So if I write sth to it, driver sends it to remote client.
When remote client sends me something, it appears on output of tty device.

Generally.. what can a kernel module do and what can't?
I guess it can't make thread and set a TCP server.

I suppose, I have to write my own device driver and application(as TCP server). I'm absolute begginer in writing device drivers, but I'm ready to learn it:)

I have read this: [http://www.linuxjournal.com/article/2476](http://www.linuxjournal.com/article/2476) and don't know:
If I have my own device /dev/ttyotcp, and write sth. by: echo "gtbtg" >/dev/ttyotcp ), how can I receive this in application(in user-mode)?
And another direction: how can application send data, that would appear when I type  cat /dev/ttyotcp ?

Here is my example code: [http://pastebin.org/197831](http://pastebin.org/197831)
But I don't know what to do next.

Could you give me some information or links?:)

---

### Post by km0r3 on 2010-05-02
I'm not literate at Linux Device Driver programming, but I do can recommend you a free collection on lecture on that.

Educate yourself: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

:-)

---


---
title: "Linux Script"
date: 2009-02-18
forum: Programming Talk
---

### Post by applebananafruit on 2009-02-18
Hi. I should have asked this a long time ago. I have a linux server which constantly crashes. Not a lot we can do about it. I need to find a script we can use on a cron job but I can't find any. There all not suitable. Some are close.

Are they hard to make? Could I get one here. It only needs to check if a process is running if not reset.

---

### Post by monkeyking on 2009-02-18
Hi,
I don't quite get what you want.
If you know some commandline tools this should be easy.

you can do something like
```

ps -aux | grep YOUR_PROG

```

---

### Post by geirha on 2009-02-18
Try stopping the process on purpose, then run ```
pidof */usr/local/bin/myprocess* && echo running || echo not running
```
It should print «not running». If you start the process, it should print the pid of the process and «running».

If the above holds true, then you can make a script that looks like:
```
#!/bin/sh
if ! pidof */usr/local/bin/myprocess* >/dev/null; then
    */usr/local/bin/myprocess*
fi

```

---

### Post by applebananafruit on 2009-02-18
Thank you very much. I'll try these and see how they go.

---

### Post by applebananafruit on 2009-02-18
Sorry to be a pain. But is there one I can punch into the cron job to do it for me. I'm a little confused. I've very new to this. I got the idea when I read about it you need a tiny script which you would tell the cron to run every couple of minutes. Then if down or process is not running then start.

---

### Post by geirha on 2009-02-18
Let's say you've created your script and saved it with the filename *thescript*, then make it executable, and move it out of your homedir. /usr/local/bin/ is a good place to put it

```
chmod -v +x *thescript*
sudo mv -v *thescript* /usr/local/bin/
```

Now add it to the crontab by running ```
sudo crontab -e
``` The syntax of the file is explained in crontab(5) which you read by running ```
man 5 crontab
``` The manual page contains examples as well.

Make sure your provide the full path to the script (/usr/local/bin/*thescript*), not just *thescript*.

---

### Post by applebananafruit on 2009-02-18
And the script I use. If it works.
```
#!/bin/sh
if ! pidof */usr/local/bin/myprocess* >/dev/null; then
    */usr/local/bin/myprocess*
fi

```

---


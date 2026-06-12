---
title: "using scheduled tasks program"
date: 2016-06-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-06-08
using the program to run a backup. only problem it runs in the background and i want it to run in foreground. any ideas?

---

### Post by TheFu on 2016-06-08
Replying because nobody else has.
I don´t think this is possible due to the design of cron - assuming ¨scheduled tasks¨ uses cron - on the back-end.You could try setting the DISPLAY environment variable correctly inside the *scheduled task* and if the .Xauth file allows it, it might work. I dunno.  Everything that interacts with the desktop needs the DISPLAY set. This is an X/Windows thing.

---

### Post by rburkartjo on 2016-06-09
fu  thanks thought that might be the problem

---

### Post by TheFu on 2016-06-10
> **rburkartjo said:**
> fu  thanks thought that might be the problem

I tested this yesterday by setting up a tool to change the wallpaper/background on a laptop. I set the DISPLAY.  It didn´t work from the crontab.  On 14.04, it used to work, so something appears to have changed (probably a security thing) since that time.  It always felt like a security hole to me that it worked, so fixing it is appreciated, at least by me.

Know that doesn´t help you.  If you want some GUI to work in the foreground, manually run it.  You can setup a keyboard chord to do it.  These are usually dependent on the DE or WM used.

---


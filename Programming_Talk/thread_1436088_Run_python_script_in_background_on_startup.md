---
title: "Run python script in background on startup"
date: 2010-03-22
forum: Programming Talk
---

### Post by yabune on 2010-03-22
Hi,

I'm new to python and I did a small script that I would like to start when I login. This script has an infinite loop and I would like that it would to keep running when I'm logged in.

Now I have 2 questions:
1) How can I start it in the background? I add this line to .basrc:
```
python myscript.py
```
but the problem is that when I open a terminal window, the bash is locked in the script loop. I have to press CTRL+C to be able to write in the console window.

2) What's the best way to create an infinite loop in python? I did like this:
```

while True:
  do_something();
  time.sleep(0.1);

```
Is this the best way? To have a sleep function?

Thank you!

---

### Post by wmcbrine on 2010-03-22
1. Same way as you start anything in the background -- "&":

```
python yourscript.py &
```

2. What's best depends on what you're trying to do.

---

### Post by yabune on 2010-03-22
Thanks!

I want to check each x minutes if a session is idle or not.
If the session is idle, I want to write on a file.

Could it be something like this?

```

while True:
  idle_time = session.get_idle()
  if idle_time > 0
    do_something()
  time.sleep(60)

```

---

### Post by kostkon on 2010-03-22
What type of session do you mean?

---

### Post by yabune on 2010-03-22
> **kostkon said:**
> What type of session do you mean?

it's the computer idle time.
I have that already working.
I just would like to check if this is the right way to create an infinite loop in python.

Thank you!

---


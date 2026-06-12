---
title: "[Python] capturing terminal output into string"
date: 2011-06-21
forum: Programming Talk
---

### Post by ki4jgt on 2011-06-21
How does one capture stdout (of a command) to a string (in 2.7)? I found this, but it's for 3.0

[http://stackoverflow.com/questions/923079/how-can-i-capture-the-stdout-output-of-a-child-process/923108#923108](http://stackoverflow.com/questions/923079/how-can-i-capture-the-stdout-output-of-a-child-process/923108#923108)

---

### Post by unknownPoster on 2011-06-21
You know, you should try it before you say it doesn't work...

It runs under python 2.6.6 so I see no reason why it wouldn't work under 2.7.x

---

### Post by ki4jgt on 2011-06-21
> **unknownPoster said:**
> You know, you should try it before you say it doesn't work...

It runs under python 2.6.6 so I see no reason why it wouldn't work under 2.7.x

I did try it:

```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/subprocess.py", line 672, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1213, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

The second line, I put "iwlist wlan0 scanning" for my command. I got this returned.

---

### Post by unknownPoster on 2011-06-21
> **ki4jgt said:**
> I did try it:

```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/subprocess.py", line 672, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1213, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```The second line, I put "iwlist wlan0 scanning" for my command. I got this returned.

You should consult the python documentation, it clearly states what you're doing wrong.

[http://docs.python.org/library/subprocess.html](http://docs.python.org/library/subprocess.html)

It has absolutely nothing to do with python 3.0.

You're calling the function wrong, in your case it would be:

```

process = subprocess.Popen(["iwlist", "wlan0", "scanning"], stdout=subprocess.PIPE)

```

---


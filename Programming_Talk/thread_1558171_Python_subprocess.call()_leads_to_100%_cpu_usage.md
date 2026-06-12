---
title: "Python: subprocess.call() leads to 100% cpu usage"
date: 2010-08-21
forum: Programming Talk
---

### Post by kyleabaker on 2010-08-21
I'm trying to debug GM-Notify and am having trouble finding a solution for when the python program uses subprocess.call which leads to 100% cpu usage and never quits until I kill GM-Notify.

The line of code that causes the problem is:
```
subprocess.call([get_executable_path("xdg-open"), url])
```

get_executable_path() simply returns a string of the path to xdg-open and is not the problem. Opening anything via subprocess.call() leads to 100% cpu.

Is there a way to make sure this subprocess is terminated almost immediately after its executed since it is only launching a new page in a web browser?

Thanks in advanced!

---

### Post by ssam on 2010-08-22
```
sam@oberon:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import subprocess
>>> subprocess.call(["xdg-open", "http://www.google.com"])
0
>>>

```
its working fine for me. a new tabs is opened in firefox, and the python function returns.

---

### Post by kyleabaker on 2010-08-22
> **ssam said:**
> ```
sam@oberon:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import subprocess
>>> subprocess.call(["xdg-open", "http://www.google.com"])
0
>>>

```
its working fine for me. a new tabs is opened in firefox, and the python function returns.

It may be a problem only for Ubuntu 10.10 testers, I'm not sure, but I'm trying to find some sort of cpu limiting solution like:
[http://stackoverflow.com/questions/1689505/python-ulimit-and-nice-for-subprocess-call-subprocess-popen](http://stackoverflow.com/questions/1689505/python-ulimit-and-nice-for-subprocess-call-subprocess-popen)

Here is the bug report:
[https://bugs.launchpad.net/gm-notify/+bug/620299](https://bugs.launchpad.net/gm-notify/+bug/620299)

I'm also wondering if it might be a problem specifically for multicore platform, or x86_64, or both.

---


---
title: "Python: Executing command"
date: 2008-10-21
forum: Programming Talk
---

### Post by lixeno on 2008-10-21
Hello,

i'm trying to start a new process / execute a command from within a python script and return the exit code as well as the output..

In windows i use the following code to do this, but when i run it on a Ubuntu server it displays the output without me printing it to the screen.

```

command = "curl http://www.google.com"
pipe = os.popen(command)
output = pipe.read()
status = pipe.close()

```

I tried googling for help but i guess i'm using wrong keywords cause i'm not getting anywhere..

So how do i do this without printing the output to the screen?

---

### Post by ghostdog74 on 2008-10-21
if you want to call external command from Python, you might as well use a shell script. Make use of Python's libraries to do what you want. urllib and urllib2 libraries can do what you want
```

import urllib2
url="http://www.google.com"
page = urllib2.urlopen(url)
print page.read()

```

---

### Post by lixeno on 2008-10-21
Ah, yeah of course..

But this was a simplified example.. And I'm going to use a socks proxy to get the page and as far as i know neither urllib or urllib2 supports this? And i don't really feel like using pycurl..

So the question remains, how do i do what i want to do?

---

### Post by Majorix on 2008-10-21
You might want to look at this:
[http://www.python.org/doc/2.5.2/lib/os-process.html](http://www.python.org/doc/2.5.2/lib/os-process.html)

---

### Post by ghostdog74 on 2008-10-21
> **lixeno said:**
> Ah, yeah of course..

But this was a simplified example.. And I'm going to use a socks proxy to get the page and as far as i know neither urllib or urllib2 supports this? And i don't really feel like using pycurl..

So the question remains, how do i do what i want to do?

[socks proxy](http://pypi.python.org/pypi/SocksiPy/1.00)

---

### Post by geirha on 2008-10-21
And the reason output got printed from the curl command is most likely because os.popen only catches stdout, not stderr.

---


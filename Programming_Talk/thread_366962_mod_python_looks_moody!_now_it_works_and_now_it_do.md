---
title: "mod_python looks moody! now it works and now it doesn't"
date: 2007-02-21
forum: Programming Talk
---

### Post by Isoss on 2007-02-21
I am a web developer and new to python, I installed mod_python and configured it and then I created test.py in the /var/www folder with the script:

```
def index(req):
  return "Test successful";
```

Now [http://localhost/test.py](http://localhost/test.py) prints "Test successful" which means that it's working!

in test.py, I tried using some other scripts which when are erroneous it prints python errors! but when it seems to be right it prints: 

Not Found

The requested URL /test.py was not found on this server.
Apache/2.0.55 (Ubuntu) mod_fastcgi/2.4.2 mod_python/3.2.8 Python/2.4.4c1 PHP/5.1.6 Server at localhost Port 80

What I actually wrote in the file is 

```
print "The sum of %d and %d is: %d" % (2,5,2 + 5)
```
That's all!

Any idea why it isn't working?

---

### Post by Mirrorball on 2007-02-21
mod_python keeps your Python scripts in memory. Whatever changes you make won't have any effect until they are reloaded (and meanwhile things often appear to be broken). mod_python is good for production servers, but for development you might want to try something else. For instance, Django comes with its own server that reloads everything at each request. You can also restart Apache at each change you make, but it's not going to be fun.

---

### Post by Isoss on 2007-02-22
hmmm! I downloaded Djungo yesterday, but I still have to read the documentations to figure out how this works! I need to keep the files in the www directory that apache uses! I also wonder if the same mysql installation that I have will be used! Will there be a different installation with a different data directory specified by Djungo? hope not!

Thanks anyway!

---

### Post by pmasiar on 2007-02-22
> **Isoss said:**
> I am a web developer and new to python, I installed mod_python .... and then django ....

If you are new in Python, maybe more sense will be to start with simple cgi first, as I advised you on your previous question. When you feel you understand what is going on in Python, you may move up to more powerfull and more complicated ways to do things, like mod_python, django, turbogears, pylons etc.

It might be just me, but I prefer smaller number of moving parts - if anything goes wrong, is easier to tweak it and fix it. Make one change at a time: new language, then templating, then framework. IMHO, YMMV.

---

### Post by Mirrorball on 2007-02-22
> **Isoss said:**
> I need to keep the files in the www directory that apache uses!
You can do that, but it's not recommended for security reasons.
> **Isoss said:**
> I also wonder if the same mysql installation that I have will be used!
Yes.

---

### Post by MadMan2k on 2007-02-22
> **Mirrorball said:**
> mod_python keeps your Python scripts in memory.
you can change that:
[http://www.modpython.org/live/current/doc-html/dir-other-par.html](http://www.modpython.org/live/current/doc-html/dir-other-par.html)

---

### Post by Mirrorball on 2007-02-22
Thanks! I didn't know you could do that.

---

### Post by mvaranda on 2007-02-23
Hi,

I am also new using python as CGI. It seems that stdio output do not go to the web client;
It seems you need to send whatever you want using return code.

So instead or print you can appent what you want into a string:

myDesiredOutput = "The sum of %d and %d is: %d" % (2,5,2 + 5)
return myDesiredOutput

I had the same question/problem.

I hope it helps,
Cheers

---


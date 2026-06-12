---
title: "Python-based website very slow"
date: 2012-10-09
forum: Programming Talk
---

### Post by NautiusMaximus on 2012-10-09
Hi All

I'm trying to create a website using python and wsgi. I've been following instructions such as [these]("http://www.linuxforu.com/2009/02/python-on-the-net-using-cgi-and-wsgi/").

This works brilliantly as long as I'm accessing the website on the same computer on which it's hosted. However, if I try to access it from a different computer on the same internal network (so there's no firewall in between), then I run into problems.

To start with, it wouldn't work at all from a different computer. It seemed as if port 8080 (the port I'm using to run the website was blocked). So then I changed the line:

```
httpd = make_server('localhost', 8080, application)
```

to

```
httpd = make_server('0.0.0.0', 8080, application)
```

Having done this, the website does run on another computer, but it's very slow. If I look at a web page on the same computer on which I'm running the website, it loads pretty much instantaneously, but if I look at it on another computer, it takes about 5-10 seconds to load. It's not a problem with a slow network: if I load a standard website with no python via port 80 (even if it has some PHP code in it) then it loads pretty much instantaneously on the other computer.

So the slowness only happens if I'm looking at the python and wsgi based website on port 8080 on a different computer to the one on which it's running.

Any ideas what could be slowing things down, or at least where I might start looking?

I'm using python 3, Ubuntu 12.04, and apache 2.

Many thanks

NM

---

### Post by NautiusMaximus on 2012-10-10
And now a little more information:

I've also tried creating a python based web page using cgi instead of wsgi. This is pleasingly fast. So the problem seems to be to do specifically with wsgi (or maybe something about using port 8080) rather than anything to do with python.

Odd this, as I'd read all about the pros and cons of cgi vs wsgi, and everyone seemed to say that wsgi was better and faster, which is why I started down that route. I guess my backup plan is just to use cgi instead if I can't get the speed issues with wsgi sorted out.

---

### Post by Tony Flury on 2012-10-10
I would start with a very simple web page - with some very simple puthon code - maybe the web equivalent of Hello world.

If that is still very slow - then try a similar web page - with something like plain HTML and simple PHP.

That will at least help you narrow it down somewhat.

---

### Post by NautiusMaximus on 2012-10-10
Thanks for that, Tony. Actually, the page in question is very simple (slightly more than just 'hello world', but really not much: just a simple static web page). But I might try stripping it right back to see if that makes any difference.

I already have tried simple web pages served without any wsgi over apache's normal port 80. They work just fine.

I've been doing some more googling about this. It looks like the way of serving up the page I've been following ([here's the example]("http://www.linuxforu.com/2009/02/python-on-the-net-using-cgi-and-wsgi/") I mentioned in my original post again), which creates a python script with the "make_server" command in it, may be just a simple method used for testing purposes and not really intended for real-life use. I gather that a more robust way of doing it is to edit my apache configuration files so that I don't have to manually run any python script, and the python code is just called from within apache.

So maybe the way to go is to delve into my apache configuration files and see if I can get it to work that way, yes?

---

### Post by NautiusMaximus on 2012-10-11
Yes, it turns out the "make_server" thing was indeed the problem. There are many website out there explaining how to get wsgi working that tell you to use "make_server" to get it running, but rather fewer that tell you that it's not really the right way to do it.

So once I'd figured that out, ditched "make_server", and configured my apache server following [these instructions]("http://code.google.com/p/modwsgi/wiki/QuickConfigurationGuide"), then everything worked just fine.

---


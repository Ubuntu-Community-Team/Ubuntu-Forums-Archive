---
title: "'dpkg-deb --build' in Python"
date: 2010-05-15
forum: Programming Talk
---

### Post by mac9416 on 2010-05-15
Hello, all!

I am writing a Python app to create metapackages. Creating a metapackage involves creating a control file, putting it in a certain directory structure, and running 'dpkg-deb --build <directory>'. The trouble is that I want the app to be cross-platform: therefore it can't depend on dpkg-deb. So I have several options:


[LIST=1]
[*] Compile dpkg-deb on Windows and ship it with my app.
Problem: I doubt the dpkg-deb code is written to be cross-platform.
[*]Translate the dpkg-deb source to Python, making sure it's cross-platform as I go.
Problem: I don't know C. And the code (according to the code's own comments) is messy.
[*]Write my own code to build a deb.
Problem: Well, I'll get to that.
[/LIST]
So, I've decided to go with #3. The job seems fairly simple. Create a control.tar.gz dir containing my control file, create a data.tar.gz containing nothing, and create a debian-binary file containing "2.0." Then tar.gz the whole thing up and call it a .deb.

Here's the problem:
Looking at a deb to find the directory structure of the control and data tar.gzs, I find directories called "." How does one create such a directory? Python says I can't:

```
>>> os.mkdir('/home/mac9416/.')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
OSError: [Errno 17] File exists: '/home/mac9416/.'
```So the question in a nutshell is: how can I make directories called "." to go in my debs?

Thanks!

---


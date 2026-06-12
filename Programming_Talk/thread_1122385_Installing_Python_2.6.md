---
title: "Installing Python 2.6"
date: 2009-04-11
forum: Programming Talk
---

### Post by Sinkingships7 on 2009-04-11
Hi. I'm about to start development on a small project of mine. It's going to be an image converter (converting between jpeg, png, etc., as well as resizing) using the ImageMagick library. I want to do this in Python, but the ImageMagick library requires Python 2.6 or greater.

I've heard of overlapping Python installations messing up dependencies, and have witnessed it myself before when two games of mine didn't work afterward.

What can I do to avoid any issues I may encounter when installing Python 2.6? Or is it unavoidable?

---

### Post by casevh on 2009-04-11
If you plan to install Python 2.6 (or any other Python version) from source, just make sure to use the command "make altinstall" instead of "make install". This will leave the system version of Python along. Your new version will be called "python2.6" instead of "python".

casevh

---

### Post by pmasiar on 2009-04-11
You did not mentioned your OS.

If ubuntu, can you upgrade to version which supports 2.6? Having two different versions on Python might give you problems.

Also, Try PIL for image manipulation. IIRC it comes included in core Py2.6.

---

### Post by Sinkingships7 on 2009-04-11
> **pmasiar said:**
> You did not mentioned your OS.

If ubuntu, can you upgrade to version which supports 2.6? Having two different versions on Python might give you problems.

Also, Try PIL for image manipulation. IIRC it comes included in core Py2.6.

I am using Ubuntu 8.10, 32-bit. I didn't know any version of Ubuntu came included with anything above Python 2.5.2.

---


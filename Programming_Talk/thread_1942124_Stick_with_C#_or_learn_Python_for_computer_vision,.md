---
title: "Stick with C# or learn Python for computer vision,A.I?"
date: 2012-03-16
forum: Programming Talk
---

### Post by cyb3r_sn4k3 on 2012-03-16
Hey guys I have an upcoming project, where I have to use a webcam to detect objects, so right now C# is what I am good at and have experience with. I know a bit of python here and there but havent gone into it much. But since I wanted to run this project on a Linux box and also C# is not exactly meant for this kinda stuff (even though there are stuff like AForge.Net). And also I saw a HackaDay post saying that Python was what they recommended for A.I (Which I would be working on soon....). So what do you think should I move to Python or stick with C#?

---

### Post by Tony Flury on 2012-03-19
Maybe you should prototype your algorithms in python - and then convert to C# if you find you need the speed.

---

### Post by ve4cib on 2012-03-19
Python is nice for quickly banging out prototype AI/computer vision problems.  Unfortunately such programs often require large amounts of computation, and therefore sometimes run slowly when written in an interpreted language like Python.  Often what I'll do is write a quick test program in Python, and once I know the algorithms will work I'll translate that into C++ (for the improved performance).

Ultimately the choice of language is largely irrelevant though; if the algorithm works it works.  It may be slightly slower or faster in one language or another, but that really just amounts to a slightly higher/lower framerate when working with video.

And depending on what (if any) image processing libraries you use there may not even be too big a speed difference between an interpreted and a compiled language.  OpenCV for instance runs at very comparable speeds when used with Python or C++ (largely because the Python library simply wraps around the C++ binaries).

If you know C#, and know how to grab frames from a webcam with it, then there's nothing wrong with working in C#.

---

### Post by cyb3r_sn4k3 on 2012-03-19
But the thing is I just cant seem to get around the GUI in C# for Linux. And most OpenCV functions are dependent on GUI.

---


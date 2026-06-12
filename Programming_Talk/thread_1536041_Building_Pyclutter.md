---
title: "Building Pyclutter"
date: 2010-07-21
forum: Programming Talk
---

### Post by Vids on 2010-07-21
[SIZE=2]Hello  all,

I am trying to build pyclutter modules on ubuntu 10.04

I want to import cluttergst in my program and hence I installed  clutter-gst-1.0.0 from [[FONT=Liberation Serif]http://source.clutter-project.org/sources/clutter-gst/1.0/[/FONT]]("http://source.clutter-project.org/sources/clutter-gst/1.0/").  I also installed pyclutter-gst. I cloned the latest source from [/SIZE][FONT=Liberation Serif][SIZE=3][SIZE=2]git clone   git://git.clutter-project.org/bindings/pyclutter-gst.

Then when I try to run my program it gives the following error:

vidya@vidya-laptop:~/my_sources$ python test_video.py 
Traceback (most recent call last):
  File "test_video.py", line 1, in <module>
    import clutter, gst, cluttergst
  File "/usr/local/lib/python2.6/dist-packages/cluttergst/__init__.py",  line 35, in <module>
    from cluttergst import _cluttergst
ImportError: libclutter-gst-1.0.so.0: cannot open shared object file: No  such file or directory


But actually I see this 'libclutter-gst-1.0.so.0' in /usr/local/lib

Any help please!!

Thanks!
Vidya.

[/SIZE][/SIZE][/FONT]

---

### Post by Iowan on 2010-07-21
Closed.
Duplicate: [http://ubuntuforums.org/showthread.php?p=9619037#post9619037]("http://ubuntuforums.org/showthread.php?p=9619037#post9619037")

From Code of Conduct:> Please do not cross post, or post the same thing in multiple locations.

---


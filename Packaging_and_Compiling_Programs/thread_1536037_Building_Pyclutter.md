---
title: "Building Pyclutter"
date: 2010-07-21
forum: Packaging and Compiling Programs
---

### Post by Vids on 2010-07-21
Hello all,

I am trying to build pyclutter modules on ubuntu 10.04

I want to import cluttergst in my program and hence I installed clutter-gst-1.0.0 from [http://source.clutter-project.org/sources/clutter-gst/1.0/](http://source.clutter-project.org/sources/clutter-gst/1.0/). I also installed pyclutter-gst. I cloned the latest source from git clone  git://git.clutter-project.org/bindings/pyclutter-gst.

Then when I try to run my program it gives the following error:

[COLOR=DarkRed]vidya@vidya-laptop:~/my_sources$ python test_video.py 
Traceback (most recent call last):
  File "test_video.py", line 1, in <module>
    import clutter, gst, cluttergst
  File "/usr/local/lib/python2.6/dist-packages/cluttergst/__init__.py", line 35, in <module>
    from cluttergst import _cluttergst
ImportError: libclutter-gst-1.0.so.0: cannot open shared object file: No such file or directory[/COLOR]


But actually I see this 'libclutter-gst-1.0.so.0' in /usr/local/lib

Any help please!!

Thanks!
Vidya.

---

### Post by Iowan on 2010-07-21
From Code of Conduct: > Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.:D

---

### Post by SevenMachines on 2010-07-22
/usr/local/lib isn't on the default ld library paths. You could temporarily use the environmental variables LD_LIBRARY_PATH or LD_PRELOAD when running ([see 3.3 - Environmental variables]("http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html")). Or add /usr/local/lib to the executable search path when building, although i don't know if python does this or not.

---

### Post by Vids on 2010-07-22
@SevenMachines.. 

Thanks! It worked with  LD_LIBRARY_PATH=.:/usr/local/lib python test_video.py.
But how do I add this path to the library path permanently?

---

### Post by SevenMachines on 2010-07-22
you can put the path in /etc/ld.so.conf.d/ and run ldconfig but I'd suggest leaving the paths as they are and instead using it the way you are, or adding it to a short shell script if you like. maybe its just me but i don't tend to favour /usr/local being used unless i explicitly decide to.

---

### Post by Vids on 2010-07-22
Ok. Thanks for letting me know though.

---


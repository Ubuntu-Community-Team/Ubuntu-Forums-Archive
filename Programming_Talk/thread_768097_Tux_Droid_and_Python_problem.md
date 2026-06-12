---
title: "Tux Droid and Python problem"
date: 2008-04-26
forum: Programming Talk
---

### Post by midnightray on 2008-04-26
Hello all,

I recently purchased the Tux Droid for the reason of learning python. However I am running 8.04 and python seems to be different to the version that the software was writen in.

I get the following errors when I try to run it. (I have installed all python xml related packages I could see and still nothing)
```

phil@phil-laptop:~$ tuxgdg
Traceback (most recent call last):
  File "/opt/tuxdroid/apps/tux_framework/TFW.py", line 12, in <module>
    from FWObject import GdgFramework
  File "/opt/tuxdroid/apps/tux_framework/libs/FWObject.py", line 35, in <module>
    from GdgObject import *
  File "/opt/tuxdroid/apps/tux_framework/libs/GdgObject.py", line 38, in <module>
    from TGFormat import *
  File "/opt/tuxdroid/apps/tux_framework/libs/TGFormat.py", line 30, in <module>
    from TGFXml import *
  File "/opt/tuxdroid/apps/tux_framework/libs/TGFXml.py", line 26, in <module>
    import xml.dom.ext
ImportError: No module named ext
```

Any help would be great. Really want to get my Tux reading the news etc using python.

---

### Post by pmasiar on 2008-04-26
check which version of Python Tux Droid supports. It looks in some inconsistent libraries. xml.dom.ext was not found on your system for whatever reason. There are many ways to do it wrong.

In general, using the most recent Ubuntu might be problem with some programs not in Universe. You might need to learn more about administration, or install exactly the distro  what developers used to run Tux Droid (whatever Droid is, I never used it).

---

### Post by LaRoza on 2008-04-26
> **pmasiar said:**
> check which version of Python Tux Droid supports. It looks in some inconsistent libraries. xml.dom.ext was not found on your system for whatever reason. There are many ways to do it wrong.

In general, using the most recent Ubuntu might be problem with some programs not in Universe. You might need to learn more about administration, or install exactly the distro  what developers used to run Tux Droid (whatever Droid is, I never used it).

Tux Droid is a droid of Tux: [http://www.tuxisalive.com/](http://www.tuxisalive.com/)

---

### Post by midnightray on 2008-04-27
Thanks for the advice,

In Java you can have many versions and switch between them easily.

Is there a version of python before this change and how does one make it the selected / used one rather than the newer broken one.

(Java JDK switching, but for python?)

---

### Post by pmasiar on 2008-04-27
I re-read first post again.

Before you start changing versions of Python find out what exactly is going on (or what version on which distro they tested). Maybe your environment is not set up properly (or they have some custom tricks). If their goal is teach you Python, and charge money for that, they should provide some support.

But if your goal is to learn Python you don't have to pay for it, there are many free online tutorials which will just run. See wiki in my sig for links.

---

### Post by midnightray on 2008-04-27
The problem is the changes to python between 7.10 and 8.04. Confirmed to work properly on 7.10 but 8.04 is a no go.

Its the python-xml package as I have said.

---

### Post by pmasiar on 2008-04-27
Then simplest solution is to downgrade to 7.10 until the issue is fixed, or double boot.

I always envied determination of pioneers to go into unknown lands, face unknown problems.  I wait with upgrade for a month, let others to find and solve problems, then upgrade. You know how you can tell someone is a pioneer? He has arrows deep in his back.

---

### Post by LaRoza on 2008-04-27
> **pmasiar said:**
> 
I always envied determination of pioneers to go into unknown lands, face unknown problems.  I wait with upgrade for a month, let others to find and solve problems, then upgrade. You know how you can tell someone is a pioneer? He has arrows deep in his back.

I install Hardy a month or so ago on my laptop. I installed it (next to my other OS's) and worked on getting it ready without forsaking my 7.10. (Easy to do, just copy the configuration files you want.) I installed everything and 8.04 is ready with no hassle.

Now, where do I get Intrepid Ibex?

---

### Post by midnightray on 2008-04-28
> **LaRoza said:**
> I install Hardy a month or so ago on my laptop. I installed it (next to my other OS's) and worked on getting it ready without forsaking my 7.10. (Easy to do, just copy the configuration files you want.) I installed everything and 8.04 is ready with no hassle.

Now, where do I get Intrepid Ibex?

Guess I'll wait for either side to fix this problem, annoying but I could send it back...

---


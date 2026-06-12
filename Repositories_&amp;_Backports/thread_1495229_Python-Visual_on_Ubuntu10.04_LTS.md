---
title: "Python-Visual on Ubuntu10.04 LTS"
date: 2010-05-27
forum: Repositories &amp; Backports
---

### Post by Tyson D on 2010-05-27
Ok I've seen a few people having a problem with Vpython on Lucid but none seem to be having my problem. When ever i type

python filename.py

i get this error message

#################################################################
(<unknown>:3594): GdkGLExt-WARNING **: Cannot open \xf0\u0016 
L.so

(<unknown>:3594): GdkGLExt-WARNING **: Cannot open \xf0\u0016 
L.so

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: Unable to get extension function: glCreateProgramObjectARB even though the extension is advertised.

aborting...
Aborted
#################################################################


and apt-get policy visual-python gives me this

#################################################################
python-visual:
  Installed: 1:5.12-1.1
  Candidate: 1:5.12-1.1
  Version table:
 *** 1:5.12-1.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Packages
        100 /var/lib/dpkg/status
#################################################################


i obviously have no clue what this means, any help would be great

---

### Post by diesch on 2010-05-27
> **Tyson D said:**
> Ok I've seen a few people having a problem with Vpython on Lucid but none seem to be having my problem. When ever i type

python filename.py

i get this error message

#################################################################
(<unknown>:3594): GdkGLExt-WARNING **: Cannot open \xf0\u0016 
L.so

(<unknown>:3594): GdkGLExt-WARNING **: Cannot open \xf0\u0016 
L.so

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: Unable to get extension function: glCreateProgramObjectARB even though the extension is advertised.

aborting...
Aborted
#################################################################


What does filename.py contain? What does 
```
  python -c 'import  visual'
```print?


> **Tyson D said:**
> 
and apt-get policy visual-python gives me this


I guess you mean  
```
apt-cache policy python-visual
```The version installed is fine.

---

### Post by Tyson D on 2010-05-27
the file usually contains 

from visual import*
ball = sphere()

the cmd you suggested:

python -c 'import  visual'

does nothing at all.

Ive also tried IDLE but when i write the above code it will simply crash.

---

### Post by diesch on 2010-05-27
I guess if you run the commands line by line using the python shell the error is thrown when you run
```
 ball = sphere()
```

That looks like python-visual is fine but there are some problems with your graphic card using OpenGL.

---

### Post by Tyson D on 2010-05-27
But in the past ive had 9.04 and Vpython worked just fine(now im running 9.04 through a VM and it supports Vpython).

and yes when i run the code through python it gives me the same error message.

---

### Post by krisztian_andre on 2010-06-23
I get the same behaviour on my acer spire one and a nice grey sphere on my desktop so its definitely a videocard issue

---

### Post by krisztian_andre on 2010-06-23
Ignore my last comment, there is a package dependency bug. You need to install libgtkglextmm-x11-1.2-dev

---

### Post by hopla on 2010-06-29
Thanks man, I had the same problem and installing libgtkglextmm-x11-1.2-dev fixed it!

---

### Post by shawakaze on 2012-09-15
Thanks, i just installed libgtkglextmm-x11-1.2-dev and it worked.

---


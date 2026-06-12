---
title: "hplip3.12.11 not running"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by linux spartan on 2013-01-04
i cant find a way to make hplip work on ubuntu 12.04 .it says theres an unexpected error with toolbox.py am using a 32 bit machine .tried to reinstall the corrupted .py file using package manager bt i did not find it in the synaptic package manager and i also tried to re-install hplip again bt no avail.the printer is a hp deskjet 2050 j510

---

### Post by ajgreeny on 2013-01-04
That all-in-one printer should be supported by the version of hplip that is in the repos of most supported versions of Ubuntu, so unless you are using Lucid 10.04, why are you installing  the version that you have?  12.04 has version 3.12.2, well above the 3.10.6 needed by that printer, so why not use the repo version.

How are you installing; presumably you are running the **hplip3.12.11.run** file in terminal as shown on the hplip site?  What exactly are the error messages you see?

---

### Post by rburkartjo on 2013-01-04
lin this might help

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by linux spartan on 2013-01-04
i did exactly as the installation instructions said bt i noticed an error in this line saying-  /usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: runtimewarning: Py set_interactive(1)

---

### Post by rburkartjo on 2013-01-04
lin lets try this let me know the results

open a terminal ctrl+alt+t

then enter this
hp-toolbox &
 then hit enter key

---

### Post by linux spartan on 2013-01-04
thanks rbur,its worked via terminal method.first it had a connection problem after accessing it via terminal but i have reinstalled hplip and its worked

---

### Post by rburkartjo on 2013-01-04
glad you got it to work. dont 4get to mark your thread as solved

---


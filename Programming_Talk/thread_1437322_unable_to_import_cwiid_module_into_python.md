---
title: "unable to import cwiid module into python"
date: 2010-03-23
forum: Programming Talk
---

### Post by Rustin Jowe on 2010-03-23
Hello all,
     I am working on a project that will (hopefully) take signals from a wiimote as inputs. I used the synaptic package manager to pick up a promising module called python-cwiid, but when I try to import the module into python (using "import cwiid") the interpreter tells me that there is no module with that name. I want to check whether the synaptic package manager actually put everything in the right place, but I have no idea where the right place is.  If any of you know where modules are supposed to ge, please let me know. Also, if you have any idea why the synaptic package manager didn't work I would love to hear about that as well.
thanks in advance

---

### Post by Rustin Jowe on 2010-03-23
I just wasted about 3 hours of my life ...  oh well. In case anyone looks at this I will post the solution. Synaptic package manager put the module in the directory for python 2.6. the interpreter I was using still used python 2.5. importing the module in python 2.6 worked fine.

---


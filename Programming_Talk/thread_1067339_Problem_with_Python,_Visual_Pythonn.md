---
title: "Problem with Python, Visual Pythonn"
date: 2009-02-11
forum: Programming Talk
---

### Post by paris.mb on 2009-02-11
When I check the version of Python in IDLE on Ubuntu 8.10 it gives me:  2.5.2.

When I check the version in the Terminal I get 2.5.4.

I am having serious trouble getting VisualPython to work.  I have tried using the Synaptic Program Manager to no avail.  I have tried manually installing.  Nothing seems to work.  I have even tried this entire thread:

[http://ubuntuforums.org/showthread.php?t=50468](http://ubuntuforums.org/showthread.php?t=50468)

this also did not work.

What do I do now.  Can I uninstall one version to see if that is the problem, and if so, how? as only one is listed under my manager.  When I try to import visual it gives me an error of not being able to find cvisual.py.

Any and all help would be greatly appreciated.

Thank you,
-Paris

---

### Post by paris.mb on 2009-02-11
I have been successful at install Python 2.6.1, but still cannot get VPython to work.

I am trying to install VPython 5.03.  However it gives me an error when I do an

"import visual"

of:
"Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python2.6/site-packages/visual/__init__.py", line 59, in <module>
    import cvisual
ImportError: /usr/lib/libboost_python-gcc42-1_34_1-py25.so.1.34.1: undefined symbol: PyUnicodeUCS4_FromEncodedObject"

I have looked this up but found no clues on the internet.  I have boost_1_38_0 installed as well.

Any help would be appreciated...
-Paris

---

### Post by aeacides on 2009-02-12
Since you installed python 2.6, it became the default python install. So maybe trying to install libboost for python 2.6, or define the default python install to 2.5.

Is boost_1_38_0 for python 2.6 ?

Your error message (/usr/lib/libboost_python-gcc42-1_34_1-py25.so.1.34.1:) seems to look at the boost_1_34_1 precisely ... maybe trying to install that version could do the trick?

Also, your 2.6 install won't go inside your 2.5 libs.


Cheers :)

---

### Post by paris.mb on 2009-02-12
I re-installed Ubuntu because I thought this was an un-recoverable error and then used the synaptic program manager to update python with the requisite components, and now it is working.  I was thinking along similar lines as to your post, but thanks for helping.  Python simply seems best installed/updated not from the terminal.

Thanks,
-Paris

---


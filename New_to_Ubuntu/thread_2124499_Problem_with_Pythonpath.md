---
title: "Problem with Pythonpath"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by Nigel Hewlett on 2013-03-11
I would be very grateful if anyone could help me with a problem with setting a path to a folder in Python 2.7.3 on Ubuntu 12.04.  I have some txt files in a folder called Vgest in my directory to which I want to apply some Python scripts.  I have tried to use sys.path.append and sys.path.insert but these didn't work.  The relevant path (/home/nhewlett/Documents/Ultrasound/Vgest) was recorded as being in the sys.path but the folder wasn't accessible.  Then I tried adding the path in the bashrc folder.  That didn't work either. Now the relevant path seems to be permanently in sys.path but for some reason it is not accessible.

I have pasted in below the output of some terminal commands.  These show:
A failed attempt to access a file, which is in Vgest.
The printout of sys.path showing that the relevant path is in there, as the third item.
Proof that the relevant file exists at the end of the relevant path, in the form of a command which includes the entire path (after /home/nhewlett/), from which I get a positive result.  It may be just a stupid mistake of mine, but I just can't see it!

Nigel Hewlett

nhewlett@dell:~$ python
Python 2.7.3 (default, Aug  1 2012, 05:16:07) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> open('A2SHA1mV1.txt')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IOError: [Errno 2] No such file or directory: 'A2SHA1mV1.txt'
>>> import sys
>>> print sys.path
['', '/home/nhewlett', '/home/nhewlett/Documents/Ultrasound/Vgest', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-linux2', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PIL', '/usr/lib/python2.7/dist-packages/gst-0.10', '/usr/lib/python2.7/dist-packages/gtk-2.0', '/usr/lib/pymodules/python2.7', '/usr/lib/python2.7/dist-packages/ubuntu-sso-client', '/usr/lib/python2.7/dist-packages/ubuntuone-client', '/usr/lib/python2.7/dist-packages/ubuntuone-control-panel', '/usr/lib/python2.7/dist-packages/ubuntuone-couch', '/usr/lib/python2.7/dist-packages/ubuntuone-installer', '/usr/lib/python2.7/dist-packages/ubuntuone-storage-protocol']
>>> open('Documents/Ultrasound/Vgest/A2SHA1mV1.txt')
<open file 'Documents/Ultrasound/Vgest/A2SHA1mV1.txt', mode 'r' at 0x959ad30>

---


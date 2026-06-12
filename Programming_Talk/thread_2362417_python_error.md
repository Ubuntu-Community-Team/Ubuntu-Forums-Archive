---
title: "python error"
date: 2017-05-28
forum: Programming Talk
---

### Post by claudedjones on 2017-05-28
I've installed a simple music editor called Songpress which uses python. My Ubuntu version is 16.04. The program runs, and seems to work fine, but when I exit I get the following error:
```

#---- System Information ----#
Songpress Version: 1.6
Operating System: Linux 4.10.0-21-lowlatency x86_64
Python Version: 2.7.13 (default, Jan 19 2017, 14:48:08) 
[GCC 6.3.0 20170118]
wxPython Version: 3.0.2.0 gtk2 (classic)
wxPython Info: (__WXGTK__, wxGTK, unicode, gtk2, wx-assertions-on, SWIG-1.3.29)
Python Encoding: Default=ascii  File=UTF-8
wxPython Encoding: UTF-8
System Architecture: 64bit x86_64
Byte order: little
Frozen: False
#---- End System Information ----#


#---- Traceback Info ----#
*** Sun May 28 02:32:56 2017 ***
Traceback (most recent call last):
  File "/home/cjones/Bin/songpress-1.6/songpress-1.6/src/SongpressFrame.py", line 687, in OnFontSelected
    self.SetFont(True)
  File "/home/cjones/Bin/songpress-1.6/songpress-1.6/src/SongpressFrame.py", line 884, in SetFont
    self.menuBar.Check(ids[self.pref.format.showChords], True)
  File "/usr/lib/python2.7/dist-packages/wx-3.0-gtk2/wx/_core.py", line 16710, in __getattr__
    raise PyDeadObjectError(self.attrStr % self._name)
PyDeadObjectError: The C++ part of the MenuBar object has been deleted, attribute access no longer allowed.

```
In that third to last line it refers to a line in _core.py in the package wx-3.0-gtk2 having a deprecated command "no longer allowed"
How do I fix this?

---

### Post by oldos2er on 2017-05-28
Moved to Programming Talk where there's a better chance of receiving an answer.

---

### Post by norobro on 2017-05-28
I've never used Songpress but I like to try out different software. A web search led me to the github repo linked below and it did not produce the error on close that you see. Tried the version from the project website and got the same error as you. 

Investigating a little further I found his patch. 
[https://github.com/lallulli/songpress/commit/20ce977639672ec7abf900cbdc3453ab8647224d](https://github.com/lallulli/songpress/commit/20ce977639672ec7abf900cbdc3453ab8647224d)

So you can either clone the repo and use it, or try applying the patch.

HTH

---

### Post by claudedjones on 2017-05-28
Thank you norobro for your research and discovery. I'm afraid my skills are insufficient to really understand how to proceed with your suggestions, though I can see that they directly apply to the issue I have. I wouldn't know where to begin to clone the repo, or, how to apply the patch. I'll do some research and see if I can figure it out.

---


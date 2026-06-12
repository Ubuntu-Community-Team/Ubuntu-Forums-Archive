---
title: "Error after update"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by themalt on 2012-03-05
Hello 
I got a no entry red sign on the icons bar right hand side after using update manager on drop down I tried following instructions by you tube to report a bug but cannot get it to work: any help please.Below is what I got in Terminal It does not mean anything to me.
james@james-VGN-FE31H:~$ ubuntu-bug unity
Error processing line 1 of /usr/lib/python2.7/dist-packages/ubuntuone-couch.pth:

  Traceback (most recent call last):
    File "/usr/lib/python2.7/site.py", line 161, in addpackage
      if not dircase in known_paths and os.path.exists(dir):
    File "/usr/lib/python2.7/genericpath.py", line 18, in exists
      os.stat(path)
  TypeError: must be encoded string without NULL bytes, not str

Remainder of file ignored
ERROR: Could not import module, is a package upgrade in progress? Error: No module named iri2uri

---

### Post by MG&amp;TL on 2012-03-05
Lol, a bug in a bug-reporting program.

Anyways, there is two ways of reporting bugs-apport (ubuntu-bug) which automatically attaches information and checks for duplicates, or a manual bug report. In your case, apport is not available, so my suggestion is a manual bug. To report a bug, head here:

[https://bugs.launchpad.net/ubuntu/+source/unity/+filebug](https://bugs.launchpad.net/ubuntu/+source/unity/+filebug)

and fill out the form.

Thanks for reporting bugs, it really does help. :)

---


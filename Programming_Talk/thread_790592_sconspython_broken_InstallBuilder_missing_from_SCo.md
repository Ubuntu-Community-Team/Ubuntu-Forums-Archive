---
title: "scons/python broken: InstallBuilder missing from SCons.Environment in Ubuntu 8.04"
date: 2008-05-11
forum: Programming Talk
---

### Post by g0l3m on 2008-05-11
Hello all,

I've had some build scripts (from ages ago) that were working fine under 7.10 (and previous versions) but suddenly stopped working under 8.04. This is using scons (and python).

Here's what I'm getting on 8.04

ImportError: cannot import name InstallBuilder:
  File "/lab/proj/mage/SConstruct", line 11:
    from myDataBuild import *
  File "../../myTools/myDataBuild/__init__.py", line 19:
    from SCons.Environment import Environment, InstallBuilder

This last line (i.e. import InstallBuilder from SCons.Environment used to work fine under 7.10 but InstallBuilder is now missing... I appreciate that this has nothing to do with Ubuntu and is probably to do with the latest version of scons, but does anyone have any ideas what is causing this?

cheers,
g.

---


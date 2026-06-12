---
title: "quickly package"
date: 2012-07-06
forum: Packaging and Compiling Programs
---

### Post by Mike Kroger on 2012-07-06
Hi,

A few days ago I followed Jono Bacon's video on YouTube. I've put together a little app, but I'm having trouble packaging it.

Well, the package is created just fine, but after I install it and try to run it, I get the following error message: -

AttributeError: 'module' object has no attribute 'main'

Strange, because if I go into Python, after installation, import the library and run main(), it works.

Another thing: Couch DB dependencies aren't included in the package. I tested my package on another Ubuntu PC, but it wouldn't run because various Couch DB stuff was missing. After installing the Couch DB package, it worked. Kinda strange that the Couch DB dependencies wouldn't be included in the distribution package, seeing that the default boilerplate created by quickly used Couch DB to store prefs.

A few more things: -

1. How do I add a screenshot to the package?
2. How do I give the package a nice name? If I change the name in setup.py, quickly package fails.
3. How do I get a reference to the installation directory from my code (without hard coding it)?
4. There might be one or two more, but I think that's enough for the moment :)

---

### Post by Mike Kroger on 2012-07-06
Well it doesn't look as if much help is going to be forthcoming. Anyway, for anyone who might be having the same problem, I managed to sort out the "AttributeError: 'module' object has no attribute 'main'"

In the project directory structure, there is a folder called po. In that folder I found a file called POTFILES.in (God knows what it's for). In POTFILES.in I found an entry for bin/my_module_name.py. When I looked in bin, I found that my_module_name.py was actually a link to my_module_name. So I hacked POTFILES.in, changing bin/my_module_name.py to bin/my_module_name. I deleted the link in bin, and ran quickly package again. Viola!

Maybe I need to smoke a few POTFILES.in?

---


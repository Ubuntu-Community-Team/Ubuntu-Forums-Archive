---
title: "Issues with python"
date: 2007-05-12
forum: Programming Talk
---

### Post by JTorres176 on 2007-05-12
I recently upgraded from 6-06 to 7-04 and I'm having massive problems with python.  I can't seem to import any of the modules I normally use in programming.  I've tried using apt-get to resolve the problem by reinstalling python-dev and such, however it blows up telling me that it can't import the modules I'm trying to repair by reinstalling.  Can anyone help out with a solution?  I really want to stay with packages and avoid custom compiling.

Here's an example of what I get when I try to import modules.

```
[joe@sandy] ~> python -v
# installing zipimport hook
import zipimport # builtin
# installed zipimport hook
'import site' failed; traceback:
ImportError: No module named site
Python 2.5.1c1 (release25-maint, Apr 12 2007, 21:00:25) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import time
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named time
>>> import os
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named os
>>> import string
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named string
>>> 

```

Anyone have any ideas?  (besides reinstalling 6-06 that is)

---

### Post by jamescox84 on 2007-05-12
Perhaps try reinstalling python from Synaptic.

---

### Post by JTorres176 on 2007-05-12
Well, I just tried that and I'm still getting the same error.  I went through the python section and reinstalled everything that was listed as installed.

---

### Post by Tenicus on 2007-05-12
What python version?
Nevermind, I see.
Huh.  We have the same version, mine works fine.
Edit- what do you have in sys.modules?

---

### Post by JTorres176 on 2007-05-12
> **Tenicus said:**
> What python version?

I've tried the python link which goes to python2.5, I tried python2.5 directly and python2.4.  They all give me the same issues of not being able to import libraries.

```

[joe@sandy] ~> python2.4
'import site' failed; use -v for traceback
Python 2.4.4 (#2, Apr 12 2007, 21:03:11) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
[joe@sandy] ~> python2.5
'import site' failed; use -v for traceback
Python 2.5.1c1 (release25-maint, Apr 12 2007, 21:00:25) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
[joe@sandy] ~> python
'import site' failed; use -v for traceback
Python 2.5.1c1 (release25-maint, Apr 12 2007, 21:00:25) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.

```

these are my versions, sorry

---

### Post by JTorres176 on 2007-05-12
Okay, after doing a complete reinstall of the entire os and one update using just standard repositories, I opened a gnome-terminal, ran python and got this.

```
[joe@sandy] ~> python
'import site' failed; use -v for traceback
Python 2.5.1c1 (release25-maint, Apr 12 2007, 21:00:25) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named os
>>> 

```

Is anyone else having this problem with their python on the same version?

---

### Post by dwblas on 2007-05-12
Python should be installed in the /usr/lib directory.  Check for that first.  Then check /usr/bin for the python symlink.  It should point to python2.5, or try "python2.5" on the command line.  If you get anything workable, print sys.path which will tell you where python thinks everything should be.  You could also try active state's version of python, but I don't think it would install differently.

---

### Post by JTorres176 on 2007-05-12
This was my own stupidity, I had my pythonhome set in my .bashrc file for compatibility on a program I was using written for FreeBSD.  I yanked the line and reloaded .bash_profile and it's working fine now.

That line's been in my .bashrc for at least 18 months now and never caused a problem, not sure why this suddenly popped up.

---

### Post by dwblas on 2007-05-12
> This was my own stupidityIt's only stupid once we know what's wrong.  Evidently, you were adding to the already existing PYTHONHOME dir, but the reinstall used that exclusively.

---


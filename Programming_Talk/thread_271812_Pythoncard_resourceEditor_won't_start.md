---
title: "Pythoncard resourceEditor won't start"
date: 2006-10-05
forum: Programming Talk
---

### Post by 3rdalbum on 2006-10-05
I've installed the Pythoncard packages:

python2.4-pythoncard
pythoncard
pythoncard-doc
pythoncard-tools
python-pythoncard

But when I try to start the Resource Editor (resourceEditor), it immediately tells me "Unable to find PythonCard installation.". As far as I can see in the documentation, everything should be alright. I'm using Dapper with a stock Python 2.4, and the codeEditor program starts up without any troubles. Any ideas?

---

### Post by l33t_3lv3n_g33k on 2006-11-03
I just installed PythonCard myself and ran into the same issue.  I managed to get the resouceEditor to run by modifying the file '/usr/bin/resourceEditor'.  The original file is:

```
#!/bin/sh

# A simple command-line wrapper for PythonCard's resourceEditor tool.
# Copyright (c) Kenneth J. Pronovici <pronovic@debian.org>; use as you wish.

if [ -d /usr/lib/python2.3/site-packages/PythonCard ]; then
   exec /usr/bin/python2.3 \
   /usr/lib/python2.3/site-packages/PythonCard/tools/resourceEditor/resourceEdit
or.py "$@"
else
   echo "Unable to find PythonCard installation."
fi

```

Note the references to python2.3

You have Python 2.4 installed, so try modifying /usr/bin/resourceEditor to this:

```
#!/bin/sh

# A simple command-line wrapper for PythonCard's resourceEditor tool.
# Copyright (c) Kenneth J. Pronovici <pronovic@debian.org>; use as you wish.

if [ -d /usr/lib/python2.4/site-packages/PythonCard ]; then
   exec /usr/bin/python2.4 \
   /usr/lib/python2.4/site-packages/PythonCard/tools/resourceEditor/resourceEdit
or.py "$@"
else
   echo "Unable to find PythonCard installation."
fi

```

Mine ran just fine after that.

---

### Post by nagius on 2007-08-19
Done exactly what is said but pythoncard still does not run, is there another way? also reinstalled 2 times with synaptic and apt-get.

---


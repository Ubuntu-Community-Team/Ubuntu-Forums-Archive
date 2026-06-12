---
title: "Pythoncard insatallation"
date: 2007-08-19
forum: Programming Talk
---

### Post by nagius on 2007-08-19
I am still getting error message ' Unable to find PythonCard installation' when I type either codeEditor or resourceEditor, changed /usr/bin/resourceEditor as follows:

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

This is from an old post still getting same problems after fix, reinstalled program 2 times via synaptic and change /usr/bin file again.

---


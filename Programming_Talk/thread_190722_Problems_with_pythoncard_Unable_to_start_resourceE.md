---
title: "Problems with pythoncard: Unable to start resourceEditor"
date: 2006-06-06
forum: Programming Talk
---

### Post by arejensen on 2006-06-06
Hi.

I've just installed Ubuntu (6.06), and thought of using it as a platform to learn some Python programming. I thought of using Pythoncard as my GUI toolkit, so I fired up synaptic and told it to download the pythoncard package.

Since it was a metapackage it downloaded and installed these packages:
python2.4-pythoncard
pythoncard
pythoncard-doc
pythoncard-tools
python-pythoncard

My python install is the stock one:
~$ python
Python 2.4.3 (#2, Apr 27 2006, 14:43:58)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from PythonCard import model
>>>
And when I try to import the PythonCard module all seems fine.

The problem occurs when I try to open the resourceEditor. I get this error message:
~$resourceEditor
Unable to find PythonCard installation.
~$

The resourceEditor file seems to stem from pythoncard-tools. I have reinstalled the package without any results.

So my question is this: Am I missing something that you can help me with, or is this a bug?
Any pointers would be welcome. I have tried searching pythoncard's mailinglist and google, but I didnt get anything out of either.

---

### Post by rmr on 2006-06-27
Hmmm. I've the same problem when trying to run resourceEditor although the codeEditor seems to work fine... :-k

---

### Post by rmr on 2006-06-27
Hi!

I've found the problem - the shell script:  /usr/bin/resourceEditor tries to open the resourceEditor.py file residing  in a sub-directory of /usr/lib/python2.3/site-packages/PythonCard and also it tries to use  /usr/bin/python2.3. Both  these files does not exist as we are using python2.4 in Ubuntu 6.06.

But since we are using python2.4, all we have to do is to change 'python2.3' to 'python2.4' in the file: /usr/bin/resourceEditor [Remember to use sudo to edit the file]  ```
sudo nano /usr/bin/resourceEditor
```

The updated contents of the file should be :

```

#!/bin/sh

# A simple command-line wrapper for PythonCard's resourceEditor tool.
# Copyright (c) Kenneth J. Pronovici <pronovic@debian.org>; use as you wish.

if [ -d /usr/lib/python2.4/site-packages/PythonCard ]; then
   exec /usr/bin/python2.4 \
   /usr/lib/python2.4/site-packages/PythonCard/tools/resourceEditor/resourceEditor.py "$@"
else
   echo "Unable to find PythonCard installation."
fi


```

That did the trick for me...

Hope that helps!

Cheers,
rmr

---

### Post by arejensen on 2006-06-27
I know about the fix, I [posted it on the bugtracker]("https://launchpad.net/distros/ubuntu/+source/pythoncard/+bug/48961") when I found out about it, but I havnt gotten any reply from the maintainer yet. Thanks for sharing though. :-)

Thought I had posted the solution to the board, but it was late and I must have forgotten about it. Late nights and no coffee does that to me. ;-)

Maybe you should chip in on the "complaint" on the bugtracker so that it'll get more priority. It's an easy one to fix after all.

---

### Post by Stromham on 2006-06-27
yea we will, but please dont spam it we have lots of important bugs a little bigger than this one.

---

### Post by arejensen on 2006-06-27
Wasn't thinking about spamming it, just letting you know that it wasn't a usererror made by a clueless n00b.

Thanks for your work Stromham. Highly appreciated! :-)

---


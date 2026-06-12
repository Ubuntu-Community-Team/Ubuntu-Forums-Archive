---
title: "beginner Python question"
date: 2011-02-21
forum: Programming Talk
---

### Post by jadedcritic on 2011-02-21
OK, I realize this is probably a newbie question. Long story short, I'm trying to get out of the habit of wistfully reading books on Python and start actually WRITING IT, even if we're talking about painfully simple/basic/beginner scripts.

What I'm looking for is a way to successfully execute bash within python, I'm just trying to have it check for the presence of a file, if the file exists, move on, if it doesn't create it, which, in bash terms, if I'm not mistaken is 


if [ -f /foo/bar ]
then
function
elif
(body of program)

from rooting around in the forums, I gather I need to import os module. Looking at the Python docs, I see allot of options, but no conditional if then loops.  Hopefully I'm looking right through it!

---

### Post by thornmastr on 2011-02-21
from os path import exists

    if exists('Xxx100926.csv'):
      do somehing
    else:
      do something else


Watch your indentation.

 HTH

Thorny:D

---

### Post by Tony Flury on 2011-02-21
> 
Looking at the Python docs, I see allot of options, but no conditional if then loops. Hopefully I'm looking right through it!

What do you mean conditional if then loops ??

If you just mean if/then - you have not been looking in the right place 

```

import os

if os.path.exists("/foo/bar"):
    # Do stuff
else:
    # Do other stuff

```

Python Documentation : [http://docs.python.org/index.html](http://docs.python.org/index.html)

Python Flow Control (loops/conditionals) : [http://docs.python.org/tutorial/controlflow.html](http://docs.python.org/tutorial/controlflow.html)

---

### Post by jadedcritic on 2011-02-21
I spoke poorly.  The python docs are understandably deep, I was scratching the wrong tunnels.  A little more fussing and I came up with thornmastr's approach.

import os, os.path

if os.path.exists("/home/mbean/foobar.py"):
    print ("true")
else:
    print ("false")

It works elegantly enough, but it concerns me a little bit in the sense that I see some semi-reliable information that os.path.exists would return True if a file/link had EVER existed, not currently exists...

Some testing on my own has confirmed that false. :)
I'm good, thank you!

---

### Post by wmcbrine on 2011-02-21
> **jadedcritic said:**
> semi-reliable information that os.path.exists would return True if a file/link had EVER existed, not currently existsThat makes no sense at all. Where are you reading this?

---


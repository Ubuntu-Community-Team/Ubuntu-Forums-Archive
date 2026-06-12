---
title: "Problems Appending an Instance of an Object to a List in Python"
date: 2009-05-02
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-02
Yo guys I am having a problem appending an object to a list. Yes i have google around for the result for a good while but didn't find anything that really helped me. Here is my code:
```

#!/usr/bin/python

import random, cmath

global MAXBUFFER
MAXBUFFER = 0

def event(eventType, eventTime):
	print "GOT HERE!"
	def __init__(self, eventType = None, eventTime = None):
		print eventType
		print eventTime
		self.eType = eventType
		self.eTime = eventTime


lam = 0.9
GEL=[1]
t = ((-1/lam)*cmath.log10(1-random.random()))
e = event("arrival",t)
GEL.append(e)
#GEL.append(4)
print GEL
exit

```
And here is the result I get:
```

$ python projPT1.py 
GOT HERE!
[1, None]
$

```
Thanks in advance.

---

### Post by delfick on 2009-05-02
hello.

you need to do "class event():" rather than "def event(eventType, eventTime):"

(also, the brackets at this point indicate other classes to inherit from)

:)

---

### Post by StunnerAlpha on 2009-05-02
> **delfick said:**
> hello.

you need to do "class event():" rather than "def event(eventType, eventTime):"

(also, the brackets at this point indicate other classes to inherit from)

:)
OMG IM AN IDIOT! Please excuse me while I bang my head on the wall...

---

### Post by delfick on 2009-05-02
> **StunnerAlpha said:**
> OMG IM AN IDIOT! Please excuse me while I bang my head on the wall...

hehehehe :)

I know the feeling :p

---


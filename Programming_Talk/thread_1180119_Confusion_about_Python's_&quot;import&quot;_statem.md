---
title: "Confusion about Python's &quot;import&quot; statement"
date: 2009-06-06
forum: Programming Talk
---

### Post by Volt9000 on 2009-06-06
I'm a bit confused about how Python's "import" statement works.

Let's say I have two files, as follows.

class1.py:
```

class Foo:
	def __init__(self):
		print "Class Foo initialized."

```

class2.py:
```

import class1
c = Foo()

```

When I execute class2.py, I get the error that "Foo" is not defined. But I imported class1, which contains the definition for Foo, so why doesn't this work?

---

### Post by matmatmat on 2009-06-06
```

import class1
c = class1.Foo()

```

---

### Post by unutbu on 2009-06-06
An alternative to matmatmat's solution is 

```
from class1 import Foo
c = Foo()
```

---

### Post by StunnerAlpha on 2009-06-06
> **unutbu said:**
> An alternative to matmatmat's solution is 

```
from class1 import Foo
c = Foo()
```
Couldn't you also do something like:
```

from class1 import *
c = Foo()

```

And that would import everything from that file, correct?

---

### Post by unutbu on 2009-06-06
Yes, but I read somewhere that 
```

from class1 import *
```

is not recommended because it makes it hard to track down where objects are defined.
It is recommended that you explicitly list all objects that you import into the current namespace.

---

### Post by Volt9000 on 2009-06-06
Thanks for your replies, everyone.

I was confused because I come from a C/C# background, and in C# when you say something like

```

using Some.Namespace;

```

that automatically imports everything defined in the namespace; no need to explicitly specify namespaces.

---


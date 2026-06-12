---
title: "Quick question about java imports"
date: 2008-03-08
forum: Programming Talk
---

### Post by mike_g on 2008-03-08
When I include stuff in java I usually use a * to include a set of stuff. EG:
```
import java.io.*;
```
Is there any benefit to only importing the stuff that you use. Say, maybe:
```
import java.io.File;
import java.io.FileWriter;
```
Will it make the exe smaller, or is all that stuff all stored in the java runtime thing?

---

### Post by Acglaphotis on 2008-03-08
In python it's recommended to only import what you'r going to use so it doesn't load in memory.

Both of them run with VMs so i think it wouldn't hurt to try which one uses less memory/has a smaller "exe" size.

---

### Post by smartbei on 2008-03-08
In python it actually loads the whole module but doesn't place it in your namespace. When you do:
```

from math import sqrt

```
you can see in sys.modules that the module math is actually imported, but if you do:
```

dir(math)

```
It will raise an exception because the module object isn't in your namespace. 

So memory-wise it doesn't matter. The real reason you would do:
```

from M import x, y, x

```
and not:
```

from M import *

```
is to not clutter up your namespace.

Not sure how it is in Java.

---

### Post by LaRoza on 2008-03-08
> **mike_g said:**
> When I include stuff in java I usually use a * to include a set of stuff. EG:
```
import java.io.*;
```
Is there any benefit to only importing the stuff that you use. Say, maybe:
```
import java.io.File;
import java.io.FileWriter;
```
Will it make the exe smaller, or is all that stuff all stored in the java runtime thing?

What exe?

No, it most likely won't make a size difference. Of course, it would be easy to test...

Try it.

The biggest thing is cluttering the namespace. I don't know what is in java.io.* so I don't know if it is a cluttering issue with that.

---

### Post by DougB1958 on 2008-03-08
> **smartbei said:**
> ... The real reason you would do:
```

from M import x, y, x

```
and not:
```

from M import *

```
is to not clutter up your namespace.

Not sure how it is in Java.

I'm pretty sure Java's the same:
```
import foo.someName;
```
tells the Java compiler that it should understand later references to "someName" as meaning the "someName" that is defined in package "foo".
```
import foo.*;
```
tells the compiler to understand _any_ name that is the same as one publicly defined in package "foo" as being the one from "foo".

In both cases, "import" only affects how the compiler interprets names, and doesn't actually cause anything to be loaded into memory.

---

### Post by xlinuks on 2008-03-08
It has no impact upon the size of the final executable, either on the execution speed, be it a class file or a packed .jar file.
One uses, say, 
```

import java.io.File;
import java.io.FileInputStream;

```
instead of
```

import java.io.*;

```
just to let the others know that this class uses only the corresponding two classes from the java.io package, nothing more.
Thus it's a matter of style and personal taste.

---

### Post by Asham on 2008-03-08
I think I've read somewhere that import java.io.* is slower to compile compared to explicit class references (import java.io.File) but I'm not sure. Also, it's not that big of a deal with the performance of most computer setups nowadays. :-)

---

### Post by mike_g on 2008-03-08
Thanks for the replies, so it seems its pretty much just a namespace thing.

I know it would be easy to test file size, memory use, etc, but I'm lazy. So i figured I'd ask instead.

---

### Post by pmasiar on 2008-03-09
I dislike Java's "import java.io.*;" imports - and it is not about application's memory - it is about **my** memory. Yes, you can be lazy and import all - then you have to remember which class comes from where to read docs. Or the poor shmo what will maintain that code after you are gone - and is not as expert in java libraries as you are. So IMHO "import java.io.*;" is unprofessional. 
Explicit import shows you what exactly is happening. Isn't static typing all about control? Not mentioning that what will happen if two libraries happen to define class with same name.

---


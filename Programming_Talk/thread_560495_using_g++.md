---
title: "using g++"
date: 2007-09-26
forum: Programming Talk
---

### Post by diamantis13 on 2007-09-26
Hi everybody!

I have a very simple (and a bit silly) question. I have a main function in a file **test.cpp** and a couple of classes in files **class.h** and **class.cpp**
before writing the classes in separate files i just did:
**$ g++ test.cpp -o test.exe**
what should I do?

Thank you very much

---

### Post by LaRoza on 2007-09-26
You can include them:

```

#include "class.cpp"

```

class.cpp should include the headers. Use inclusion guards!

You compile as normal, the preprocessor will do the rest.

---

### Post by hod139 on 2007-09-26
g++ test.cpp class.cpp -o test

Alternatively, you can learn about makefiles. 


Also, in linux, you do not need the .exe extension, that is a dos thing.

---

### Post by hod139 on 2007-09-26
> **LaRoza said:**
> You can include them:

```

#include "class.cpp"

```class.cpp should include the headers. Use inclusion guards!

You compile as normal, the preprocessor will do the rest.

You should not get into the habit of including cpp files in other cpp files.  Except for very esoteric situations, you only want to include header files.  (This is why include guard exist only in headers, cpp file are not usually included).  You compile each cpp file separately, and let the linker worry about putting it all together at the end.  This is not the compiler's/programmer's job to do that by playing with the includes.

---

### Post by diamantis13 on 2007-09-26
I used:

g++ test.cpp class.cpp -o test

and it worked :lolflag:

Thank you very much

---


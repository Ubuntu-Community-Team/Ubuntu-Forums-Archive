---
title: "my simple vallgrind front-end"
date: 2009-04-12
forum: Programming Talk
---

### Post by napsy on 2009-04-12
Hello.

I've written a very small gtk+ front-end for valgrind XML output using python.

- supports multiple threads
- colored tree
- can open backtrace source in integrate vim

Here's an example session:

[[IMG]http://img136.imageshack.us/img136/7932/screenshot1jts.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshot1jts.png)

You can get the script source [here]("http://napotnik.info/valhalla.py").

Note that this is version 0.0.2 and some output messages are not yet supported.

---

### Post by v.cecchetto on 2009-05-14
Hello,
thanks for your work.

I'm trying to use your tool without success for now.

I compiled a simple test.c code.

..................................................
#include <stdio.h>

int main(int argc , char *argv[])

{
	printf("OK! \n");
	return 0;
}
..................................................

gcc test.c -o test 

I execute this command to produce valgrind xml output:

valgrind --xml=yes test 2> test.xml

is it correct? When i open test.xml i see all the usual valgrind output in xml format.

Then i execute your tool and select this file (test.xml) but nothing appens.

Some suggestions?

---

### Post by Zugzwang on 2009-05-14
> **v.cecchetto said:**
> 
I execute this command to produce valgrind xml output:

valgrind --xml=yes test 2> test.xml

is it correct? 

Not quite. You have to reference the executable correctly:
```

valgrind --xml=yes ./test 2> test.xml

```

If it still does not work, try looking at the output in the xml-file with "cat":
```

cat test.xml

```
It might contain errors that the GUI cannot handle.

---

### Post by v.cecchetto on 2009-05-15
Thx for the reply, 

but same results as before. Nothing appens. 

Doh...

---

### Post by Zugzwang on 2009-05-15
> **v.cecchetto said:**
> 
but same results as before. Nothing appens. 


So what's in the XML file?

---


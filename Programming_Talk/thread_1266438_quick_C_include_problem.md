---
title: "quick C include problem"
date: 2009-09-14
forum: Programming Talk
---

### Post by heamaster on 2009-09-14
Hi! This code gives me an error message, why?
"incTest.h"
[PHP]
void testf();
[/PHP]
"incTest.c"
[PHP]
#include "incTest.h"

void testf()
{
}
[/PHP]

"test.c"
[PHP]
#include "incTest.h"

int main()
{
	testf();
	return 0;
}
[/PHP]

Error message:
[PHP]
test.c:(.text+0x7): undefined reference to `testf'
[/PHP]

---

### Post by januzi on 2009-09-14
Could You post makefile or paste compilation command ?
(You forgot to link incTest.obj with test.obj)

---

### Post by heamaster on 2009-09-14
Thank you!
That helped!
You remembered me that I was only compiling test.c, not incTest.c :lolflag:

---


---
title: "Seg-faults on the heap"
date: 2010-01-16
forum: Programming Talk
---

### Post by Saxcore on 2010-01-16
Hi there, just a quick question;

Why does the following code NOT produce a segmentation fault:

```
int main()
{
	int *cat = new int [3];
	cat[0] = 1;
	cat[1] = 2;
	cat[2] = 3;
	cat[3] = 4;
	cat[4] = 5;

	// print them out, to test them...
	std::cout << "cat[0] = " << cat[0] << std::endl;
	std::cout << "cat[1] = " << cat[1] << std::endl;
	std::cout << "cat[2] = " << cat[2] << std::endl;

	// this shouldn't work, but does, for some reason...
	std::cout << "no-existant cat[3] = " << cat[3] << std::endl;
	std::cout << "no-existant cat[4] = " << cat[4] << std::endl;

	delete [] cat;
	return 0;
}
```

...do segmentation faults not occur on the heap?
...or, more likely, have I missed something and/or being really stupid.

Thanks in advance, Sam.

---

### Post by MadCow108 on 2010-01-16
a segfault occurs when a process tries to modify memory which it does not own.
in this case the bit of memory your writing to does still belong to the process (maybe allocated by the new due to memory alignment) so you can write to it without crashing the process immediately.

cat[-100] = 0 or cat[100000] = 0 is more likely to produce a segfault.

although it does not crash its still a bug, and may segfault or do other weird stuff under other circumstances.
it will show up with valgrind as invalid read/write

---

### Post by Saxcore on 2010-01-16
Ah OK. That makes sense. Thanks for your help, MadCow!

---


---
title: "Intentionally forcing a program to cause Bus-Error"
date: 2010-09-12
forum: Programming Talk
---

### Post by sharathcshekhar on 2010-09-12
Hi, 
I was learning about the difference between Segmentation fault and Bus Error in Linux and learned that Bus Error is caused by a mis aligned memory detected at the CPU level or a non existent memory.
Now, I want to stimulate this condition and check it. My question is how can I write a simple C program that will cause a Bus Error? Following the examples in a few books, I wrote this program :
```

int main()
{
	union dummy_u {
		char a[10];
		int i;
	}dummy;
	int *p = (int*) &(dummy.a[1]);
	*p = 10;
	return 0;
}

```
According to the book, it should raise a Bus Error at accessing "*p =10", as the alignment for integer would be wrong. But this is not creating any problems for me! The program is just running fine.
Is the memory alignment problem not applicable for newer processors? Wha am I doing wrong?

---

### Post by gmargo on 2010-09-12
In the **x86** architecture, unaligned memory accesses just work; the processor transparently takes care of the overhead.

Check out the "Bus error example" in this Wikipedia article; it caused a bus error for me: [http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

---

### Post by sharathcshekhar on 2010-09-14
Hi Gmargo,
Thank you very much for the reply. That was very informative and the Wikipedia Link you sent, worked as well. Thanks a lot!

---


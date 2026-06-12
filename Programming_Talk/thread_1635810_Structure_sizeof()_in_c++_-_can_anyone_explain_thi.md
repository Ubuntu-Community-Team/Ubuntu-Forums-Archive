---
title: "Structure sizeof() in c++ - can anyone explain this"
date: 2010-12-02
forum: Programming Talk
---

### Post by akvino on 2010-12-02
Here is the description of the problem - 

Current Structure:

[PHP]//declaration
typedef struct
{
	long int num1;
	int num2;
	double long num3;
	int num4;
	double long num5;
} BIN_TEST;

//in main
	BIN_TEST 	bt1 = { 1, 2, 3, 4, 5};
	BIN_TEST * 	p_bt = & bt1;

	cout<<"\nSizes: \nsizeof(p_bt) \t"<<sizeof(p_bt);
	cout<<"\nsizeof(p_bt->num1) \t"<<sizeof(p_bt->num1);
	cout<<"\nsizeof(p_bt->num2) \t"<<sizeof(p_bt->num2);
	cout<<"\nsizeof(p_bt->num3) \t"<<sizeof(p_bt->num3);
	cout<<"\nsizeof(p_bt->num4) \t"<<sizeof(p_bt->num4);
	cout<<"\nsizeof(p_bt->num5) \t"<<sizeof(p_bt->num5);
	cout<<"\nsizeof(*p_bt) \t"<<sizeof(*p_bt);
	cout<<"\nsizeof(bt1) \t"<<sizeof(bt1);

[/PHP]

the output is:
Sizes: 
sizeof(p_bt)    8
sizeof(p_bt->num1)      8
sizeof(p_bt->num2)      4
sizeof(p_bt->num3)      16
sizeof(p_bt->num4)      4
sizeof(p_bt->num5)      16
sizeof(*p_bt)   64
sizeof(bt1)     64


NOTICE that 8+4+16+4+16 = 48 and not 64;
If I change it to just equal int's in declaration:

typedef struct
{
	int num1;
	int num2;
	int num3;
	int num4;
	int num5;
} BIN_TEST;

the output is:
Sizes: 
sizeof(p_bt)    8
sizeof(p_bt->num1)      4
sizeof(p_bt->num2)      4
sizeof(p_bt->num3)      4
sizeof(p_bt->num4)      4
sizeof(p_bt->num5)      4
sizeof(*p_bt)   20
sizeof(bt1)     20

20 as it should be since 4*5 = 20;

---

### Post by DZ* on 2010-12-02
[http://en.wikipedia.org/wiki/Sizeof#Structure_padding](http://en.wikipedia.org/wiki/Sizeof#Structure_padding)

---

### Post by amauk on 2010-12-02
This is to do with how data gets stored in a struct

It's a little beyond my understanding, but sometimes padding will be added between the data so that each element within a struct is located on some common boundary

see here
[http://en.wikipedia.org/wiki/Data_structure_alignment](http://en.wikipedia.org/wiki/Data_structure_alignment)

*edit*
rearrange the struct so that the 2 doubles are at the beginning and see if the overall size changes
Ie. 16+16+8+4+4

---

### Post by matt_symes on 2010-12-02
Hi

Yes it's padding. You can specify no padding if you want then you will get the answer you are expecting.

Kind regards

---

### Post by C0derBear on 2010-12-02
> **matt_symes said:**
> You can specify no padding if you want then you will get the answer you are expecting.

There are potential down-sides to doing this though, it depends upon the platform and the data what those specific down sides are.

For example, you can force the packing to 1-byte alignment but then accessing a multi-byte element on some systems can cause a segfault. Not usually desired.

By rearranging your declarations you may also minimize this, in a more safe and cross-platform way. For example - grouping same-sized elements together and starting with largest-first. This would minimize the automatic padding that is generated.

---

### Post by matt_symes on 2010-12-02
Hi

> **C0derBear said:**
> There are potential down-sides to doing this though, it depends upon the platform and the data what those specific down sides are.

For example, you can force the packing to 1-byte alignment but then accessing a multi-byte element on some systems can cause a segfault. Not usually desired.

By rearranging your declarations you may also minimize this, in a more safe and cross-platform way. For example - grouping same-sized elements together and starting with largest-first. This would minimize the automatic padding that is generated.

Very true. I was mentioning it more for elucidation.

Kind regards

---

### Post by worksofcraft on 2010-12-02
If you have a 64 bit computer the data-bus is 64 bits wide and it can read or write an 8 byte quantity in a single memory cycle...
provided that memory quantity resides at an address that is aligned to an 8 byte boundary.

If the quantity straddles said 8 byte boundary then the processor must perform two memory cycles, shift the two parts into the correct positions then "or" them together to reconstitute the value you want.

Evidently the latter will be less efficient, so in this case the compiler has optimized for performance rather than reduced memory footprint.

---


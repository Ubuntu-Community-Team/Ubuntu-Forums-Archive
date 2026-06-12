---
title: "size of object in case of virtual pointers"
date: 2011-07-06
forum: Programming Talk
---

### Post by c2tarun on 2011-07-06
```



#include <iostream>
using namespace std;

class B
{
	int a, b;
	public:
		B()
		{
		}
};

class C: virtual public B
{
	int a;
	public:
	C()
	{
	}
	
	virtual void show()
	{
	}
};

int main()
{
	//B b1;
	C c1;
	cout<<sizeof(c1)<<" "<<sizeof(int);
	return 0;
}

```

Can anyone please explain me why I am getting size of c1 as 24?
According to me it should be 8+4+4(vptr)

---

### Post by c2tarun on 2011-07-06
I fiddled a bit and found that size of my virtual pointer is 12 Bytes why so?

---

### Post by Blackbug on 2011-07-06
I believe your processor architechture is 64 bit. The size of one word is 8.
Since there are three INT included in size of class C ( and size of int is 4 ), 
out of 8 bytes only 4 are filled for 1 interger in the word.
4 x 3 = 12, thus two 8 byte words are created ( total size 16 )
and 8 bytes for the vptr
total: 24
 
this is my preassumption in case any better opinion would love to hear

---

### Post by c2tarun on 2011-07-06
oh.... I never thought of that. :)
Thanks a lot
I am marking this thread solved.

---


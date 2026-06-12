---
title: "pointer and gcc"
date: 2008-07-13
forum: Programming Talk
---

### Post by elgoog on 2008-07-13
Hi, Is there something strange when pointers are being used in gcc. 
I am learning about pointers and the book I am referring to has this example.
```

#include<stdio.h>
int main()
{
	int arr[]={10,20,30,45,67,56,74};
	int *i,*j;
	
	i=&arr[1];
	i=&arr[5];
	printf("%d %d\n",j-i,*j-*i);

	return 0;
}

```

And the Output is
10 -1074789232
Can someone explain me please.

---

### Post by boblemur on 2008-07-13
i could be wrong but...

the first is the values in the pointers ( derefrencing the point)

to the value 20 and then minusing 10 from it...

however the second is taking the address of j and minusing the address of i

i obviously having a greater address hence the negative...

correct me if im wrong...

---

### Post by elgoog on 2008-07-13
> **boblemur said:**
> i could be wrong but...

the first is the values in the pointers ( derefrencing the point)

to the value 20 and then minusing 10 from it...

however the second is taking the address of j and minusing the address of i

i obviously having a greater address hence the negative...

correct me if im wrong...

correct you if you are wrong??? 

I just started learning about pointers and arrays from the book "Let us C" by Yashwant Kanetkar.  How do I correct ya if me hardly knows anything. LOL.

Anyhooo. If you are right about the second thing "*j-*i", so if j is stored in a lesser location value than i, then does linux store values in backward locations.???

---

### Post by liability on 2008-07-13
You assigned two different addresses to *i*, but you didn't assign anything to *j*.

---

### Post by elgoog on 2008-07-13
Ya, Gcc does store values in location backwards. Tried this:
```

#include<stdio.h>
int main()
{
	unsigned long int i=7,k=7;
	unsigned long int *j;
	j=&i;
	printf("%u\n",j);
	
	j=&k;
	printf("%u\n",j);

	return 0;
}

```

And the output is 
3219522512
3219522508

So 'i' is stored in 3219522512, and 'k' is stored in 3219522508. 
Thanks Buddy.

---

### Post by Canis familiaris on 2008-07-13
Replace 
i=&arr[5]; by j=&arr[5];

It should work.

To explain:

You have created pointer to type int called i and j.
i and j store the pointer to the address of variables arr[1], arr[5] (assuiming you made the change)

*i, *j are the values stored at the the adresses at which the pointer i, j respectively which would correspond to value of arr[1], arr[5]

*j - *i would give you arr[5] - arr[1] = 56 - 20 = 36

j - i would give you the the difference in addresses of j and i i.e. 4.

The correct output will be:

4 36

---

### Post by boblemur on 2008-07-13
lol i ment someone else correct me :P not you.... ohh right :P didnt see the typo

---

### Post by Canis familiaris on 2008-07-13
> **elgoog said:**
> Ya, Gcc does store values in location backwards. Tried this:
```

#include<stdio.h>
int main()
{
	unsigned long int i=7,k=7;
	unsigned long int *j;
	j=&i;
	printf("%u\n",j);
	
	j=&k;
	printf("%u\n",j);

	return 0;
}

```

And the output is 
3219522512
3219522508

So 'i' is stored in 3219522512, and 'k' is stored in 3219522508. 
Thanks Buddy.

No not always, 
And NEVER it stores backwards in arrays.
You have to correct your code in the original post. 
You have not initialized j.

My corresponding output in the second program:
2682484376
2682484368

---

### Post by elgoog on 2008-07-13
Ya you are right. NEVER in arrays.
I tried this.
```

#include<stdio.h>
int main()
{
	unsigned long int a[]={1,2,3,4,5,6};
	unsigned long int *j;
	int i,x,y;
	printf("Storing of Variables in memory location by an array.\n");	
	printf("\n\n");
	for(i=0;i<6;i++)
	{
		j=0;
		j=&a[i];
		printf("%u\n",j);
	}


	printf("Storing of Variables in memory location directly.\n\n\n");
	scanf("%d%d",&x,&y);
	j=0;
	j=&x;
	printf("%u\n",j);

	j=0;
	j=&y;
	printf("%u\n",j);
	return 0;
}

```
OUTPUT:
Storing of Variables in memory location by an array.


3217666524
3217666528
3217666532
3217666536
3217666540
3217666544
Storing of Variables in memory location directly.


1
2
3217666552
3217666548
..

Does someone know anykind of tutorial or link which explains about this whole storing variables in memory location in linux when using gcc?

---

### Post by Canis familiaris on 2008-07-13
To explain even more properly:

When you declare a variable i.e. one single variable like k then the system looks for free space enough to store that variable. i.e An integer takes 2 bytes so it will look for free 2 bytes.
Now if you declare another variable of type int then it will do the same. Many times it places the new variable next backwards to the previous one but not not nessecarily.

But in arrays it stores in sequential form and NOT backwards.

---

### Post by lisati on 2008-07-13
> **elgoog said:**
> Hi, Is there something strange when pointers are being used in gcc. 
I am learning about pointers and the book I am referring to has this example.
```

#include<stdio.h>
int main()
{
    int arr[]={10,20,30,45,67,56,74};
    int *i,*j;
    
    i=&arr[1];
    i=&arr[5];
    printf("%d %d\n",j-i,*j-*i);

    return 0;
}

```And the Output is
10 -1074789232
Can someone explain me please.
Huh? i=&arr[1] followed by i=&arr[5]? Was this intentional?

EDIT: Just noticed that someone else had commented on this

---

### Post by Canis familiaris on 2008-07-13
> **elgoog said:**
> 
Does someone know anykind of tutorial or link which explains about this whole storing variables in memory location in linux when using gcc?
Most systems whether DOS, Linux, or Windows use similar basic memory management. So any tutorial will do. See my previous post for a better idea.
Another suggestion I give that the book "Let us C" is not very good in explaining Pointers.
I actually learnt pointers in C++, so I dont know what book you need for C for learning pointers.

---

### Post by elgoog on 2008-07-13
> **lisati said:**
> Huh? i=&arr[1] followed by i=&arr[5]? Was this intentional?

EDIT: Just noticed that someone else had commented on this

Ah! A typo. The second ont has to be j. j=&arr[5];
Thanks. Everyone.

---

### Post by Canis familiaris on 2008-07-13
> **elgoog said:**
> Ah! A typo. The second ont has to be j. j=&arr[5];
Thanks. Everyone.

You realised that a bit late. :lolflag:

---


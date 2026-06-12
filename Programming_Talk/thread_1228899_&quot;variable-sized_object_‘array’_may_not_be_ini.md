---
title: "&quot;variable-sized object ‘array’ may not be initialized&quot;"
date: 2009-08-01
forum: Programming Talk
---

### Post by dE_logics on 2009-08-01
Hello.
I'm an absolutely new to programing and I'm getting the messages as quoted above when I try and compile the program with gcc.

---

### Post by Sockerdrickan on 2009-08-01
And my name is Robin.

Now could you post some code?

---

### Post by dE_logics on 2009-08-01
I'm still developing this...I was just trying to run and see how it was working till now.
```
#include<stdio.h>
main()
{
	//This places variable will take in the number of places.
	int places;
	printf("Enter the total number of places \n");
	scanf("%d", &places);
	//Declairing an array with capacity=number of places.
	int array[places];
	//The flag to count the number of combinations
	int f = 0;
	int temparray [places];
	int temp;
	int i;
	//Filling up the array
	for(i=0;i<=places-1;i++)
	{
	int array[i] = i;
	printf("%d \n", array[i]);
	}
	while(f != 2)
	{	//Replacing the third and fourth last places.
		temp = array[places-4];
		array[places-4] = array[places-3];
		array[places-3] = temp;
		f++;
		//Reverting the whole array and printing the results.
		if(f=2)
		{
			for(i=0;i<=places-1;i++)
			temparray[i] = array[(places-1)-i];
			for(i=0;i<=places-1;i++)
				{
					array[i] = temparray[i];
					printf("%d \n", array[i]);
				}
		}
		//swap process for the last 3 places.
		for (i=0;i<=2;i++)
		{
			temp = array[places-1];
			array[places-1] = array[places-2];
			array[places-2] = temp;
			for(int i=0;i<=places-1;i++)
			printf("%d \n", array[i]);
			temp = array[places-2];
			array[places-2] = array[places-3];
			array[places-3] = temp;
			for(int i=0;i<=places-1;i++)
			printf("%d \n", array[i]);
		}
		
	}
}
```

---

### Post by Mirge on 2009-08-01
int array[places];

can't do that... C has to know the size of the array at compile-time. Same with the other occurrences...

---

### Post by dE_logics on 2009-08-01
hummm...yeah I was wondering about that.

Thanks.

---

### Post by dwhitney67 on 2009-08-01
Consider the following:
```

#include <stdlib.h>

...

scanf("%d", &places);

int* array = malloc(places * sizeof(int));

...

free(array);

```

---

### Post by MadCow108 on 2009-08-01
no the C99 standard allows variable size array's, also c89 only gives a warning (the gnu extensions handle that in that case so far I know, so you may to lose portability if you need C89 standard)

the problem is this:
```

int array[places];
(...)
for(i=0;i<=places-1;i++)
	{
	int array[i] = i;
	printf("%d \n", array[i]);
	}

```
you redeclare the array and do not properly initialise it.
just drop the *int* before array in the loop
also you redeclare i in a few for loops later
just drop the int's again

---

### Post by Mirge on 2009-08-01
> **MadCow108 said:**
> no the C99 standard allows variable size array's, also c89 only gives a warning (the gnu extensions handle that in that case so far I know, so you may to lose portability if you need C89 standard)

the problem is this:
```

int array[places];
(...)
for(i=0;i<=places-1;i++)
    {
    int array[i] = i;
    printf("%d \n", array[i]);
    }

```you redeclare the array and do not properly initialise it.
just drop the *int* before array in the loop
also you redeclare i in a few for loops later
just drop the int's again

I stand corrected, thanks!

[http://gcc.gnu.org/onlinedocs/gcc/Variable-Length.html](http://gcc.gnu.org/onlinedocs/gcc/Variable-Length.html)

---


---
title: "segmentation fault in simple C prog"
date: 2008-11-10
forum: Programming Talk
---

### Post by bilol on 2008-11-10
Hi,
  The following code is running fine in windows but giving **segmentation fault in Linux**
#include<stdio.h>
#include<stdlib.h>


```
main()
{
    int **a,i,j,m=5,n=4;
    // Creating a 2D array a[][] of size mXn
    a=(int **)malloc( m*sizeof(int));
    for(i=0;i<m;i++)
	  *(a+i)=(int *)malloc( n*sizeof(int) );
    
    // Making all the elements of a=88
    for(i=0;i<m;i++)
		for(j=0;j<n;j++)
			*(*(a+i)+j)=88;

    // Printing a[][] in matrix format
    for(i=0;i<m;i++)
    {
		for(j=0;j<n;j++)
			printf("%d ",*(*(a+i)+j));
	printf("\n");
    }
	

   
    
    printf("\n\n\n\n");
    return 0;
}


```
Output:
```
88 88 88 88
88 88 88 88
88 88 88 88
88 88 88 88
88 88 88 88
```


What to do? Please suggest.
Thanks in advance.

---

### Post by WW on 2008-11-10
Change this
```

    a=(int **)malloc( m*sizeof(int));

```
to this
```

    a=(int **)malloc( m*sizeof(int *));

```

And, for educational purposes, run this on each of your machines:
```

#include <stdio.h>

int main()
{
    printf("sizeof(int)=%d    sizeof(int *)=%d\n",sizeof(int),sizeof(int *));
    return 0;
}

```

---

### Post by geirha on 2008-11-10
Also, there's no need to cast the return value of malloc. E.g use
```
a=malloc( m*sizeof(int *));
```
instead of 
```
a=(int **)malloc( m*sizeof(int *));
```
Makes it easier to read imo.

And don't forget to free()!

---

### Post by Zugzwang on 2008-11-10
Also, read the [Valgrind HOWTO]("http://http://tldp.org/HOWTO/Valgrind-HOWTO/closerview.html") on how to use valgrind. This tools helps checking for memory leaks and illegal read and write operations which cause these segmentation violations.

---

### Post by WW on 2008-11-10
> **geirha said:**
> Also, there's no need to cast the return value of malloc. E.g use
```
a=malloc( m*sizeof(int *));
```
instead of 
```
a=(int **)malloc( m*sizeof(int *));
```
Makes it easier to read imo.

Personally, I think properly casting the result is better style.

---

### Post by nvteighen on 2008-11-10
> **WW said:**
> Personally, I think properly casting the result is better style.
It's actually completely useless, as those functions return (void *), but casting is a good way to make things explicit and avoid relying on C's implicit casts. I always cast them, but knowing that it's only for readability issues... What never should happen is you coding things without being able to explain what you're doing. (i.e. casting without knowing it's just style or not casting without knowing that malloc() return (void *))

---

### Post by bilol on 2008-11-11
Hi Friends,
Thank you all .....The problem is gone...code is working.
Thanks again for your comments regarding void pointers issue.

---


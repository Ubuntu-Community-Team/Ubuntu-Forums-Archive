---
title: "Number of elements in an array (C)"
date: 2011-11-25
forum: Programming Talk
---

### Post by jacksonyoyo on 2011-11-25
Hi everyone. 
I have defined and INT array in C, and its malloc()-ed. 
```
int* array= malloc(200* sizeof(int));
```Even though memory is allocated to the array, however, the array may not have 200 elements, the number of elements changes in each round of a loop. 

this array needs to then be passed to a qsort() function which requires the number of elements in the array in order to work. 
```
 void qsort( void *buf, size_t num, size_t size, int (*compare)(const void *, const void *) );
```So my question is, how can I get the number of elements in the array?
I have searched online, and the closest thing that I have got so far is :
```
sizeof(array)/sizeof(int)
```this just gives me the size of array, which is not what i want.

Please help, 
thanks for everything in advance.

PS: thank you for the people who helped me with my last post :)

---

### Post by Vaphell on 2011-11-25
how do you fill the array in each round? can't you store the index of the last modified element?

---

### Post by 11jmb on 2011-11-25
There is no built-in array like in java, but in practical use, you can always pass through the number of elements you allocated anyway

---

### Post by Arndt on 2011-11-25
> **jacksonyoyo said:**
> Hi everyone. 
I have defined and INT array in C, and its malloc()-ed. 
```
int* array= malloc(200* sizeof(int));
```

Even though memory is allocated to the array, however, the array may not have 200 elements, the number of elements changes in each round of a loop. 

this array needs to then be passed to a qsort() function which requires the number of elements in the array in order to work. 
```
 void qsort( void *buf, size_t num, size_t size, int (*compare)(const void *, const void *) );
```

So my question is, how can I get the number of elements in the array?
I have searched online, and the closest thing that I have got so far is :
```
sizeof(array)/sizeof(int)
```
this just gives me the size of array, which is not what i want.

Please help, 
thanks for everything in advance.

PS: thank you for the people who helped me with my last post :)

You will have to keep track of it yourself.

---

### Post by jacksonyoyo on 2011-11-26
> **Vaphell said:**
> how do you fill the array in each round? can't you store the index of the last modified element?

O YEA! OF COURSE! 
sorry, my bad!
this thread only appear because of me being stupid... :KS

thanks everyone above!:D

---


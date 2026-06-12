---
title: "C programming - need help with arrays"
date: 2008-12-30
forum: Programming Talk
---

### Post by Tasma on 2008-12-30
I am new to c programming and having trouble with arrays. I've spent a couple of hours researching how these work in c, but haven't found a way to solve the problem, I got, yet:

I need to program a method which generates arrays from random numbers and returns the array. The idea put into code would be something like this:

```
int generate_array(int n, int max) {
	int my_array[n];
	int i;
	for (i=0; i<n; i++) {
		my_array[i] = random_number_generating_method(0, max);
	}
	return my_array;
}
```

As much as I've read and understood solving this isn't quite as simple in c and I need to use pointers? I've tried some ideas, but so far without success(need to work with the created arrays in other methods which call this method).

Help and suggestions with how to put this idea into c code greatly appreciated.

---

### Post by monkeyking on 2008-12-30
Hi,
There are a billion ways of doing this.

This is the way I would do it.

first of all you should make a simple function that simply returns a random number given a certain range like
[PHP]int my_random_int(int lower, int upper);[/PHP]

Then your function type should be different
[PHP]int *generate_array(int n, int max);[/PHP]

Then you should allocate memory with the malloc function and return this instead.

something like

[PHP]
int *return_array=malloc(n*sizeof(int))
for(int i=0;i<n;i++)
return_array[i]=my_random_int(0,max)
[/PHP]

good luck

I haven't checked this code, but it should give you an idea

---

### Post by Tasma on 2008-12-30
Tried that, but I couldn't find a way to access the created array in other methods(tried printing it out in the main method without success for example).

---

### Post by nsche on 2008-12-30
Your code looks ok except for the memory management part.  You are allocating an array on the stack and trying to return it.  It doesn't work that way.  You could allocate the array outside of the function and then it would be in the data segment and could be accessable by the function and its caller (as a global).  The normal c way of doing it would be like this:
```

int *generate_array(int n, int max) {
	int i;
        my_array = malloc(n*sizeof(int));
	for (i=0; i<n; i++) {
		my_array[i] = random_number_generating_method(0, max);
	}
	return my_array;
}

```
As you see pointers and arrays are pretty much the same in c.  In this case the basic difference is that you are returning a pointer to an area in the heap which contains your array.  You could then treat the pointer like an array or do pointer arithmetic with it.

Norm

---

### Post by PandaGoat on 2008-12-30
Another popular way is to pass a pointer to an array to modify instead of returning an array.  You would do something like this:

[PHP]
void generate_array(int n, int max, int* buff) 
{
	int i;
	for (i=0; i<n; i++) 
        {
		buff[i] = random_number_generating_method(0, max);
	}
}
int array[20]
generate_array(20, 1234, array)
[/PHP]

---

### Post by Tasma on 2009-01-01
Thanks =) Got a better overview of arrays now and could get my program working too.

---

### Post by creek23 on 2009-01-01
> **Tasma said:**
> Thanks =) Got a better overview of arrays now and could get my program working too.

mark this, **[SOLVED]**.

---


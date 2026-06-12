---
title: "[SOLVED] Initialising an array AFTER declaration (C++)"
date: 2008-08-24
forum: Programming Talk
---

### Post by Caged on 2008-08-24
Hopefully this will be a simple yes or no question.

The situation is this: An array has been declared with size 100 but it sits in a header file I am not allowed to touch. I need to assign values to this array so is there any way to do this in one or two lines instead of assigning values one by one on each line?

---

### Post by dwhitney67 on 2008-08-24
Here are some ways to initialize an array:
[PHP]int array[10] = {0};    // initialize to all zeroes[/PHP]
or
[PHP]int array[10] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };  // manual init[/PHP]
or
[PHP]int array[10];
memset( array, 0, sizeof(array) );  // initialize to all zeroes[/PHP]
Lastly (not what you really want to see):
[php]array[0] = array[1] = array[2] = array[3] = array[4] = array[5] = array[6] = array[8] = array[9] = 0;[/php]
or
[php]
for ( size_t i = 0; i < sizeof(array)/sizeof(int); ++i )
{
  array[i] = 0;
}
[/php]

---

### Post by Caged on 2008-08-24
Looks like I can't do this:
```
int array[10];
// Everything above cannot be edited by me.
array[] = {1,2,3,....}
```

But I can do this:
```
int array[10];
// Everything above cannot be edited by me.
anotherArray[10] = {1,2,3,....}
for(int i = 0; i < 10; i++)
   array[i] = anotherArray[i]
```

I am all ears for something better.

@dwhitney67: As you can see, I am looking to use values other than 0 and are unique to each other.

---

### Post by dwhitney67 on 2008-08-24
I think you know the answer already.

There are not that many choices... actually there's only one... if you require unique values within each slot of the array.

P.S.  The answer (which I hope) you derive applies to C, C++, Java, C#, Python, etc.  Hint.. you will need to initialize each slot in the array with the particular value you are interested in.

---

### Post by Caged on 2008-08-24
Ok. Thanks anyway. I guess this is solved too.

---

### Post by mujambee on 2008-08-24
If your main concern is clean initialization code and don't mind adding a new function, you could also create a variable length argument function.

```

array_init( int *dst, int count, ... )

```then, to initialize your array you only need to

```

array_init( array, 10, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 );

```

---


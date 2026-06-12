---
title: "Add value to BEGINNING of Array"
date: 2010-01-17
forum: Programming Talk
---

### Post by qwertyuiop96 on 2010-01-17
How do you add a value to the beginning of an array in Objective-C?  (Or C++, I hear that Obj-C accepts C syntax).  In Java, you can just do this:

```

//New integer arrayList
arrayList<int> array = new arrayList<int>();
//Load array with initial values
for (int i=1, i<4, i++) {
    array.add(i);
}
//Add 0 to beginning of array
array.add(0, 0);
```

If you printed the Array, you would get:

```

0
1
2
3
```

But if you do the equivalent in C++:

```

//New array
int intArray[] = [1,2,3];
// Add 0 to beginning of array
intArray[0] = 0;
```

You get:

```
0
2
3
```

How do I use Obj-C (Or C++, if they are compatible), to get the first result?

---

### Post by schauerlich on 2010-01-17
You would have to 
1) possibly increase the size of the array 
2) copy every value up one in index
3) assign ar[0] to the value you want

EDIT: found this looking through some old code.

[php]#include <stdio.h>

#define SIZE 10

int main(int argc, char * argv[])
{
  int ar[SIZE] = {10, 8, 7, 6, 4, 5, 2, 3, 9};
  int i, k, atpos, value;

  // print out the current contents of the array
  for (k = 0; k < SIZE; k++)
  {
    printf("%3d ", ar[k]);
  }
  
  puts("");
  
  printf("What? ");
  scanf("%d", &value);
  
  printf("Where? ");
  scanf("%d", &atpos);
  
  // shift everything up
  for (i = SIZE - 2; i >= atpos; i--)
    ar[i + 1] = ar[i];
    
  // insert desired value at desired position
  ar[atpos] = value;
  
  // print out new array
  for (k = 0; k < SIZE; k++)
  {
    printf("%3d ", ar[k]);
  }
  
  puts("");

  return 0;
}[/php]

Note that this does NOT increase the size of the array before copying each value up. the last value will be lost.

---

### Post by MadCow108 on 2010-01-17
an array is no data structure to add in the beginning.
Its possible of course, but very slow because you have to move all elements (memmove comes in handy)

if you repeatedly need to do so, don't use an array.
A deque or a list are a better structures for those operations.

---

### Post by Senesence on 2010-01-17
This is one way to do it:

[PHP]
#include <stdlib.h>
#include <stdio.h>

int addToStart(int *array, int array_len, int new_entry)
{
	int new_len = array_len + 1;
	array = (int*)realloc(array, sizeof(int)*new_len);
	
	int i;
	for (i = array_len; i > 0; i--)
	{
		array[i] = array[i-1];
	}
	array[0] = new_entry;

	return new_len;
}

void printMyArray(int *array, int array_len)
{
	int i;
	for (i = 0; i < array_len; i++)
	{
		printf("index %d: %d\n", i, array[i]);
	}
}

int main(void)
{
	
	
	// Make your array
	int array_len = 3;
	int *array = (int*)malloc(sizeof(int)*array_len);
    
    // Populate it
    int i;
	for (i = 0; i < array_len; i++)
	{
		array[i] = i+1;
	}
	
	// Show it
	printf("Original array:\n");
	printMyArray(array, array_len);
	
	// Insert new int at the beginning
	int my_new_addition = 0;
	array_len = addToStart(array, array_len, my_new_addition);
	
	// Show it again to see changes
	printf("\nNew array:\n");
	printMyArray(array, array_len);	

	return 0;
}
[/PHP]

Assuming you're using C, that is.

---


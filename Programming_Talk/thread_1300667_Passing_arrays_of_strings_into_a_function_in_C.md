---
title: "Passing arrays of strings into a function in C"
date: 2009-10-25
forum: Programming Talk
---

### Post by exutable on 2009-10-25
Hey guys,

I'm trying to learn some C and can't figure out how to pass an array of strings into a function, I was told that there is a way to pass the strings into a function without specifying the size.  I got this to work but had to pass the size in.

```

#include <stdio.h>
#include <stdlib.h>

char array_a[4][100] = {"@ The mean is the average value of the data set.\n",
					"@ It is computed as the sum of all the elements\n",
					"@ in the data set divided by the number of elements\n",
					"@ in the set.\n\n"};


char array_b[6][100] = {"@ The median is the 'middle' element of the sorted\n",
					"@ data set, i.e., the median is the value for which\n",
					"@ there are as many elements in the set that are\n",
					"@ smaller than or equal to the median as there are\n",
					"@ elements greater than or equal to the median.\n\n", 0x00};

char array_c[3][100] = {"@ The mode is the most often encountered element in\n",
					"@ the data set.\n\n", 0x00};

int main(void) {

	printInstructions(array_a, 4);

	/* Exit gracefully */
	return OK;
}

void printInstructions(char array_test[4][100], int size)
{
	int i;
	for(i = 0; i < size; i++)
	{
		printf("%s", &array_test[i][0]);
	}
}



```


Is it possible or is C really that limited?

Thanks

---

### Post by MadCow108 on 2009-10-25
it is possible by terminating the array appropriately (similar to how normal cstrings work).
In that case you can only determine the size by looping over the array searching for the terminator, just like strlen works. but for functions that just iterating on the array its fine.

Another way is putting the array into a struct which saves the size and pass a pointer to the struct (or whole struct) into the function
This has the advantage of a real random access array without having to search for the size first.

example:
[php]
#include <stdio.h>
#include <stdlib.h>
#define MAX_SIZE 10
typedef struct char_array {
  const char * data[MAX_SIZE];
  size_t size;
} char_array;

// null termianted
void printInstructions(const char **array_test)
{
  for (const char ** it = array_test; *it != 0; ++it)
  {
    const char * str = *it;
    printf("%s\n", str);
  }
}

// struct
void printInstructions2(char_array * ar)
{
  for (int i=0; i<ar->size; i+=1)
  {
    printf("%s\n",ar->data[i]);
  }
}

int main(void) {
  const char * ar[5] = {"str1","str2","str3","str4",0};
  printInstructions(ar);

  printf("\n");

  char_array ar2 = {{"str1","str2","str3","str4"},4};
  printInstructions2(&ar2);
  return 1;
}[/php]

---

### Post by froggyswamp on 2009-10-25
> **MadCow108 said:**
> it is possible by terminating the array appropriately (similar to how normal cstrings work).
In that case you can only determine the size by looping over the array searching for the terminator, just like strlen works. but for functions that just iterating on the array its fine.

Another way is putting the array into a struct which saves the size and pass a pointer to the struct (or whole struct) into the function
This has the advantage of a real random access array without having to search for the size first.


Thanks, I've been wondering about this!

---

### Post by exutable on 2009-10-28
I get this error:

```
Error: 'for' loop initial declaration used outside c99 mode
```

I found out that it's because you declare a variable inside a for loop. It was easy to fix in the second for loop but I have no idea how to fix it in the first one.


Exutable

---

### Post by Arndt on 2009-10-28
> **exutable said:**
> I get this error:

```
Error: 'for' loop initial declaration used outside c99 mode
```

I found out that it's because you declare a variable inside a for loop. It was easy to fix in the second for loop but I have no idea how to fix it in the first one.




The type declaration outside, and the assignment left inside. What did you try?

---

### Post by MadCow108 on 2009-10-28
edit: fixed some confusion, thx arndt)
the reasons is this:
for (**int i** = 0...
this is not allowed in gcc default C standard (I think gnu89)
for that standard you have to write this:
```

int i;
for (i = 0...

```
the first loop is fixed the same way:
```

const char ** it;
for (it = array_test; *it != 0; ++it) 

```

I find that annoying and usually compile with C99 standard or gnu99 extensions which allows the shortcut
gcc --std=c99 or gcc --std=gnu99
note that in that case the loop variable is only in scope inside the loop

---

### Post by Arndt on 2009-10-28
> **MadCow108 said:**
> the reasons is this:
for (**int i** = 0...
this is not allowed in C99
you have to write this:
```

int i;
for (i = 0...

```

I find that annoying and usually compile with gnu99 standard extensions which allows the shortcut
gcc --std=gnu99

Is that correct? It seems to be allowed in c99, but not in earlier versions (for example c89), among them the default one for gcc.

---

### Post by MadCow108 on 2009-10-28
sorry somehow expected that c99 was gcc's default. I was wrong
--std=c99 is enough then

---

### Post by djurny on 2009-10-28
well, c++ is just c at the end of the day, so its not about limitations on c ;)

what about the following example:
[PHP]
#include <stdio.h>

int printarr(char* arr[]) {
        char** p;
        for (p = arr; *p; ++p) {
                printf("%s\n", *p);
        }
        return 0;
}

int main(int argc, char* argv[]) {
        char* msg[] = { "at the end",
                        "of the day",
                        "c++",
                        "is still",
                        "just plain ol' c",
                        0 };

        return printarr(msg);           
}
[/PHP]
only addition is to add a 'terminating string' in the array of strings and check for that while iterating the array..

---

### Post by fct on 2009-10-28
Consider the way it's done in main():

```

int main(int argc, char **argv){

```
or 
```

int main (int argc, char *argv[]){

```

So you can pass arrays of strings like that, only you need to know how many strings are there. You can get the length of each string with strlen().

The problem with the "for (p = arr; *p; ++p) {" approach is that you count on memory after the arrays being NULL, which doesn't always happen (as far as I know).

Edit: noticed the workaround by making the last content of the array 0, that works in this case too.

---


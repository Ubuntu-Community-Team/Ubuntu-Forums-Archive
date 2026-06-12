---
title: "What Am I Doing Wrong With This ARRAY?"
date: 2011-05-04
forum: Programming Talk
---

### Post by KAISER91 on 2011-05-04
The program should allow the user to enter 10 values into an array. Then it should display the highest and lowest values stored in the array. 

Here is my attempt. 

```
#include <iostream>
using namespace std;

int main ()


{
	int highest, lowest;
	int x[10];
	cout << "Enter 10 Values: ";
	for (int i=0; i<10; i++)
	{
		cout << "\nEnter Value: ";
		cin >> x[i];
	}

	lowest=x[0];
	highest=x[0];
	for (int x=1; x<10; i++)
	{
		if(lowest>x[i])
		{
			lowest=x[i];
		}
		else if(highest<x[i])
		{
			highest=x[i];
		}
	}

	cout << "Highest number is: " << highest << endl;
	cout << "Lowest number is: " << lowest << endl;

	return 0;
}

```

---

### Post by KAISER91 on 2011-05-04
lowest=x[0];
	highest=x[0];
	for (int x=1; x<10; **i**++)

The error I'm getting is for the bold (i). 

Why is that?

---

### Post by simeon87 on 2011-05-04
> **KAISER91 said:**
> lowest=x[0];
	highest=x[0];
	for (int x=1; x<10; **i**++)

The error I'm getting is for the bold (i). 

Why is that?

Because you presumably meant to do this: ```
for (int i=1; i<10; **i**++)
```

As it is right now, i is not defined for this particular for-loop.

---

### Post by schauerlich on 2011-05-04
> **simeon87 said:**
> Because you presumably meant to do this: ```
for (int i=1; i<10; **i**++)
```

As it is right now, i is not defined for this particular for-loop.

Not to mention he declares x as an integer in that loop (overshadowing the x he uses as an array), and then tries to dereference it. I haven't run it myself, but presumably it segfaults.

---

### Post by KAISER91 on 2011-05-04
Oh, silly mistake. It's working now, thanks.

---

### Post by KAISER91 on 2011-05-04
> **schauerlich said:**
> Not to mention he declares x as an integer in that loop (overshadowing the x he uses as an array), and then tries to dereference it. I haven't run it myself, but presumably it segfaults.
It's working, dude. 

What do you mean by dereference ?

---

### Post by Jay_E on 2011-05-04
Hi,
two things to ask yourself:
Where is a variable defined?
Is the value the correct type?

"i" needs to be defined as an int.

Also, take a look at your include file.
Are you sure you don't want to use stdio.h?

Then...
when you read SOMETHING from input, it is usually a character - since that is what you usually type on a keyboard.
These have to be converted to integers - or whatever.

Then..
When converting, if you use a function from a standard library, tou need to check error status.
Typos happen.
A significant portion of good code is checking for errors and providing a good bail-out path.

Have fun,
Jay


PS you might try scanf
here is an example (without error-checking):
```
/* scanf example */
#include <stdio.h>
int main ()
{
  char str [80];
  int i;

  printf ("Enter your family name: ");
  scanf ("%s",str);  
  printf ("Enter your age: ");
  scanf ("%d",&i);
  printf ("Mr. %s , %d years old.\n",str,i);
  printf ("Enter a hexadecimal number: ");
  scanf ("%x",&i);
  printf ("You have entered %#x (%d).\n",i,i);
  
  return 0;
}
```

---

### Post by schauerlich on 2011-05-04
> **KAISER91 said:**
> It's working, dude. 

"Dude", it doesn't even compile for me.

```
schauerlich@inara:~$ g++ -Wall -Wextra -pedantic -o foo.out foo.cpp
foo.cpp: In function ‘int main()’:
foo.cpp:19: error: name lookup of ‘i’ changed for new ISO ‘for’ scoping // <-- the error simeon87 mentioned
foo.cpp:11: error:   using obsolete binding at ‘i’
foo.cpp:21: error: invalid types ‘int[int]’ for array subscript // <-- the error I mentioned
foo.cpp:23: error: invalid types ‘int[int]’ for array subscript // again
foo.cpp:25: error: invalid types ‘int[int]’ for array subscript // again
foo.cpp:27: error: invalid types ‘int[int]’ for array subscript // again

```

> What do you mean by dereference ?

When you have a pointer, it "refers" to a certain area of memory. When you try to get at the data a pointer is pointing to, it's called "dereferencing" it. An array is a pointer to the beginning of that chunk of memory. In order to get at the data in the array, you have to dereference a pointer to the element you want. This is usually done by calculating how far away it is from the start (ie, the index of the element in the array) and then dereferencing the pointer made from adding the address of the beginning of the array to the offset your calculated.

---

### Post by heyandy889 on 2011-05-04
Here's a thought. Your code looks good to me. Just one part looks questionable. Inside your primary "comparison" loop, you have this
```

lowest=x[0];
    highest=x[0];
    for (int x=1; x<10; i++)
    {
        if(lowest>x[i])
        {
            lowest=x[i];
        }
        else if(highest<x[i])
        {
            highest=x[i];
        }
    }

```
I would probably recommend this
```

lowest=x[0];
    highest=x[0];
    for (int x=1; x<10; i++)
    {
        if(lowest>x[i])
        {
            lowest=x[i];
        }
        //else if(highest<x[i])
        [SIZE=3]**if(highest<x[i])**[/SIZE]
        {
            highest=x[i];
        }
    }

```
I dunno if the "lowest" and "highest" are mutually exclusive conditions, so you might not want to dive in with if-else if, and instead opt for if-if.

$0.02

---

### Post by Arndt on 2011-05-05
> **heyandy889 said:**
> Here's a thought. Your code looks good to me. Just one part looks questionable. Inside your primary "comparison" loop, you have this
```

lowest=x[0];
    highest=x[0];
    for (int x=1; x<10; i++)
    {
        if(lowest>x[i])
        {
            lowest=x[i];
        }
        else if(highest<x[i])
        {
            highest=x[i];
        }
    }

```
I would probably recommend this
```

lowest=x[0];
    highest=x[0];
    for (int x=1; x<10; i++)
    {
        if(lowest>x[i])
        {
            lowest=x[i];
        }
        //else if(highest<x[i])
        [SIZE=3]**if(highest<x[i])**[/SIZE]
        {
            highest=x[i];
        }
    }

```
I dunno if the "lowest" and "highest" are mutually exclusive conditions, so you might not want to dive in with if-else if, and instead opt for if-if.

$0.02

I can stand on both sides of the fence here. It's good to write code that's "obviously" correct, and pay the price of the occasional unnecessary test or calculation. This means that I like your idea.

It's also good to have a good grasp of the invariants of the entities during a calculation. Here one such invariant is highest>=lowest. It starts out true, it's supposed to be true at the end, so it may be convenient to know that it is true all through the calculation (imagine the calculation to be ten times as complex). Then, from this simple invariant, it follows trivially that the two conditions in the loop cannot be true at the same time. Would it be proper to add a comment to that effect in the code? Here, yes, no, maybe. In more complex code, yes, definitely.

In cases where one plays safe (in the sense that code will not be skipped that should be run) and leaves out the else, one has to be sure that it is not harmful if both blocks are actually run.

---


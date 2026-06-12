---
title: "C++ Problem: My pointer is being set to NULL without my permission"
date: 2008-02-24
forum: Programming Talk
---

### Post by Amurko on 2008-02-24
I can't post the entire contents of my code here but I'll try to summarize the scope of the problem.
[I]
Say I have code of the following format:


[FONT="Arial"]

#include <iostream.h>

int main(int argc, char *argv[]){

n = atoi(argv[1]);
int *A = new int[n];
A[0] = 5;
A[1] = 7;

cout << A << endl;  //Tell me where in memory is the array located

(here's some code in between completely unrelated to the the array A I just made)

cout << A << endl;  // Tell me where array A is located again.

cout << A[0] << endl;  //This now causes a Seg Fault
delete A;
return 0;
}
[/FONT][/I]

When I run my program, the output I get is as follows:

0x8054370* (or some other memory address)*
0
Segmentation fault (core dumped)

I'm a fairly newbie C++ programmer but I've encountered problems of this sort with my code very often.  

To put in layman's terms of what seems to be happening:

- I declare an array of numbers in memory and then set the contents of the array.
- I verify the contents of the array and they indeed are the numbers I previously set.
- I perform a series of operations that DO NOT involve the previous array.
- Now that array has disappeared from memory without my consent.  I get a seg fault when I try to access it even though I never explicitly deleted it or set the corresponding pointer to NULL

So how should I go about debugging a problem in your program where your pointers are set to NULL randomly and without your permission?

---

### Post by aks44 on 2008-02-24
First off, C++ doesn't change your program's variables "without your permission". It *is* definitely an error you made. ;)

Now, with so little code it is difficult to say where the problem lies.

Looks like that you somehow overwrite your pointer's content in your *apparently* unrelated code (the part that is missing).


Please post more code, we won't be able to help much without it.

Another option is to use a debugger (eg. kdbg) and watch for your pointer variable to be changed. From there you should be able to find where lies the problem.

---

### Post by scourge on 2008-02-24
A couple of notes:
- Use <iostream> instead of <iostream.h>
- n needs a type (int)

Here's a bit better version of your code:
```

#include <iostream>

int main(int argc, char *argv[]) {
	int n;
	int *A;

	if (argc <= 1) {
		std::cout << "A parameter is needed" << std::endl;
		return 0;
	}
	n = atoi(argv[1]);
	if (n < 2) {
		std::cout << "A value of at least 2 is needed" << std::endl;
		return 0;
	}

	A = new int[n];
	A[0] = 5;
	A[1] = 7;

	std::cout << A << std::endl;
	std::cout << A << std::endl;
	
	std::cout << A[0] << std::endl;

	delete [] A;
	return 0;
}

```

I can't figure out how you manage to set A to NULL without even touching it.

---

### Post by aks44 on 2008-02-24
> **scourge said:**
> I can't figure out how you manage to set A to NULL without even touching it.
Well, the pointer is on the stack... and buffer overflows (IMO that's what happening) are not that hard to write. ;)

---

### Post by Wybiral on 2008-02-24
> **scourge said:**
> I can't figure out how you manage to set A to NULL without even touching it.

Probably very similar to this (please excuse my C)...

```
#include <stdio.h>

int main(int argc, char *argv[])
{
    char array[2], x;
    x = '1';

    /* unrelated code... ;) */
    array[2] = '0';
    array[3] = '0';

    printf("%c\n", x);
    return 0;
}
```

---

### Post by Zugzwang on 2008-02-25
As already suggested, it might be best to use a debugger for watching for changes in A. Also you might consider to use valgrind/callgrind for checking if your code writes to places it shouldn't. If for example you're using KDevelop, that tool is only one click away.

For both cases, please make sure that you include debugging symbols in your executable ("-g3" switch for the G++ compiler)

---


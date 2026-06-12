---
title: "adding values to struct array"
date: 2008-10-12
forum: Programming Talk
---

### Post by nathanqh on 2008-10-12
Hello there.  I'm written the following code in C and in theory I want rank[] to store a char and an int.  When I run the program though, this is what I get:

Employee: hello
Employee number: 1234
hello1234
hello1234
add another (y/n)?
y
Employee: asdfg
Employee number: 5678
asdfg1234
asdfg5678
add another (y/n)?

instead of printing 
asdfg1234
asdfg5678

shouldn't it output
hello1234
asdfg5678 ?

I'm just wondering why I'm getting asdfg instead of hello?  Thanks!

```
#include <stdio.h>

#include <stdlib.h>


typedef struct {
	const char *emp;
	int num;
} InfoT;

int main () {

	char* employee;
	int number;
	InfoT rank[20];
	int size = 0;

	if((employee = calloc(21, sizeof(char))) == NULL) {
		return EXIT_FAILURE;
	}
	while(1) {
		printf("Employee: ");
		while (1) {
			if (scanf("%s", employee) != 0)
				break;
			getchar();
		}
		printf("Employee number: ");
		while (1) {
			if (scanf("%d", &number) != 0)
				break;
			getchar();
		}
		rank[size].emp = employee;
		rank[size].num = number;


		printf("%s%d\n", rank[0].emp, rank[0].num);
		printf("%s%d\n", rank[size].emp, rank[size].num);

		printf("add another (y/n)?\n");
		
		while (getchar() != '\n')
			;
		if (getchar() == 'n')
			break;
		size++;
	}
	

	return EXIT_SUCCESS;

}
```

---

### Post by WW on 2008-10-12
> **nathanqh said:**
> 
instead of printing 
asdfg1234
asdfg5678

shouldn't it output
hello1234
asdfg5678 ?

I'm just wondering why I'm getting asdfg instead of hello?  Thanks!

You allocate memory for the employee variable once, before the while loop.  So when you read in the employee name, it overwrites the previous value.  The assignment 'rank[size].emp = employee;' just points rank[size].emp to this block of memory; it doesn't allocate new memory and copy the contents of the memory.  So, as you add new employee records, all the emp fields point to the same string, which contains the name of the most recently added employee.

---

### Post by sillv0r on 2008-10-12
The items in rank:

rank[0].emp and rank[1].emp

are pointing to the same block of memory.

This causes the first employee name to be over written by the second.

[EDIT: WW is right.  I'm not quick enough. =D ]

---

### Post by nvteighen on 2008-10-12
Also, you're not free()'ing the memory allocated by calloc(). Of course, of you follow the WW's advice, you'll have to free memory not once, but exactly the same amount of times you've allocated.

Besides that, nice logic and a nice code.

---

### Post by nathanqh on 2008-10-12
oooh, that makes sense!  so i just changed employee to an array too:
```
char* employee[20]
```
and put 
```
if((employee[size] = calloc(21, sizeof(char))) == NULL) {
	return EXIT_FAILURE;
```
into the while loop and it seems to be working!

thanks a lot for the help, i appreciate it!

---

### Post by dwhitney67 on 2008-10-12
> **nathanqh said:**
> oooh, that makes sense!  so i just changed employee to an array too:
```
char* employee[20]
```
and put 
```
if((employee[size] = calloc(21, sizeof(char))) == NULL) {
	return EXIT_FAILURE;
```
into the while loop and it seems to be working!

thanks a lot for the help, i appreciate it!
WW was correct with his assessment.

However, I think your modification is probably not the best.  You should allocate only _one_ employee string at a time _within_ the while-loop.  Then with each iteration of the loop, assign it to your InfoT 'emp' field.

And btw, _never_ use scanf() to read in a string; always use fgets().  Many books and reference materials have not been updated to explain that scanf() and string input can lead to buffer overflows.  This can compromise an application.

Another thing you could focus on is on handling a situation where say, more than 20 employees needed to be added to the ranks.  It would be nice if your program would handle this during runtime, as opposed to hard-coding the size-20 limit on "rank".

To solve this issue, you would have to declare "rank" as an array of pointers to InfoT objects.  You would also have to keep track of how many pointers are in this array, and lastly keep track of how many employees have been added to the ranks (which for this last part, I believe you are already doing it).

Anyhow, read up on realloc(), because this is the critical function that would be needed if you decide to implement my suggestion.

Let me know if you require any further assistance.

---


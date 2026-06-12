---
title: "seems like array of integers is cut in half after being passed to function"
date: 2013-12-25
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-25
```
#include <stdio.h>
void iterateThroughArrays(char *arguments[], int numbers[]);




int main(int argc, char *argv[])
{
	char *names[] = {"Ron", "Jen", "Jazlyn", "Reid"};
	int ages[] = {30, 30, 3, 40};
	printf("%ld is the size of actual ages", sizeof(ages));
	getchar();
	
	iterateThroughArrays(names, ages);
	
	
	
	
	return 0;
}


void iterateThroughArrays(char *arguments[], int numbers[])
{
	int i = 0;
	printf("%ld is the size of numbers (ages) ", sizeof(numbers));
	getchar();
	printf("%ld is the size of an integer", sizeof(int));
	getchar();
	
	int total_ages = sizeof(numbers) / sizeof(int);
	
	for(i = 0; i < total_ages; i++){
		printf("%s is %d years old", arguments[i], numbers[i]);
		getchar();
	}
}

```

Thats my code.  Now check out the output

```
16 is the size of actual ages
8 is the size of numbers (ages) 
4 is the size of an integer
Ron is 30 years old
Jen is 30 years old

```

After ages[] gets passed into iterateThroughArrays, the number of items in "ages" gets cut in half.  Why is that?

---

### Post by nidzo732 on 2013-12-26
You can't use sizeof for that. 
Sizeof is used to get the size of an object that is known at compile time (integers are fixed size so it knows their size). Your arrays are static (their contents are defined in the code) so the compiler knows their size and because of that, sizeof(ages) works well in main(). 
But  [COLOR=#000000][FONT=Ubuntu Mono]iterateThroughArrays[/FONT][/COLOR] gets pointers, not static arrays. Your second call to sizeof actually calculates the size of a pointer which is 8 bytes (you are probably using a 64bit computer?).
When you give a pointer to sizeof, there is no way for it to get the size of the thing it points to.

---

### Post by wingnut2626 on 2013-12-26
Ok, that makes perfect sense!  Here is my ammended code:

```
#include <stdio.h>
void iterateThroughArrays(char *arguments[], int numbers[], int totals);




int main(int argc, char *argv[])
{
	char *names[] = {"Ron", "Jen", "Jazlyn", "Reid"};
	int ages[] = {30, 30, 3, 40};
	printf("%ld is the size of actual ages", sizeof(ages));
	getchar();
	int total_ages = sizeof(ages) / sizeof(int);
	
	iterateThroughArrays(names, ages, total_ages);
	
	
	
	
	return 0;
}


void iterateThroughArrays(char *arguments[], int numbers[], int totals)
{
	int i = 0;
	printf("%ld is the size of numbers (ages) ", sizeof(numbers));
	getchar();
	printf("%ld is the size of an integer", sizeof(int));
	getchar();
	
	
	
	for(i = 0; i < totals; i++){
		printf("%s is %d years old", arguments[i], numbers[i]);
		getchar();
	}
}

```

And here is my output:

```
16 is the size of actual ages
8 is the size of numbers (ages) 
4 is the size of an integer
Ron is 30 years old
Jen is 30 years old
Jazlyn is 3 years old
Reid is 40 years old

```
Are there any other improvements I can make? Thanks for your help.

---


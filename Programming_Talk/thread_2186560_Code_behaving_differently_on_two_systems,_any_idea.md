---
title: "Code behaving differently on two systems, any idea why?"
date: 2013-11-07
forum: Programming Talk
---

### Post by jerome1232 on 2013-11-07
So I wrote this program for class, compiled under Ubuntu using gcc 4.6.3, and for windows I compiled using mingw gcc 4.8.1, I have it working correctly and submitted, but I'm wondering why it isn't 100% in place portable as I would expect?

I'm having a for loop count differently on XP than it counts on Ubuntu, under xp I have to subtract one from count to get a correct count, under Ubuntu (as I would expect) I have to add one.

Here's the code, along with compile commands.

```
/* Reads from stdin and prints the c code to create a typedef struct header file
 *
 * @author 	Jeremy Jones
 * Course: 	COMS B25
 * Created: 	Nov 7, 2013
 * Source File:	createStruct.c
 */

#include<stdio.h>
#include<stdlib.h>

int main(void) {

	char str1[1100][64], str2[1100][64];
	double num[1100];
	int numElem = 0;
	
	puts("typedef struct {");
	puts("\tchar *sender, *reciever;");
	puts("\tdouble amount;");
	puts("} Transaction;");
	puts("");
	puts("Transaction transactions[] = {");

	int i = 0;
	while ( EOF != scanf("%64s%64s%lf", str1[i], str2[i], &num[i]) ) {
		numElem = i + 1;
		i++;
	}

	for ( i = 0; i < (numElem - 1); i++ ) {
		printf("{\"%s\", \"%s\", %f},\n", str1[i], str2[i], num[i]);
	}
	printf("{\"%s\", \"%s\", %f}\n", str1[numElem - 1], str2[numElem - 1], 
			num[numElem - 1]);
	puts("};");
}
```
This one performs as expected on both OS's compiled and ran via a simple:
```
gcc createStruct.c -o createStruct
./createStruct < transactions.txt > transactions.h

```

```
/* Searches a structure for names and computes change
 *
 * @author 	Jeremy Jones
 * Course: 	COMS B25
 * Created: 	Nov 7, 2013
 * Source File:	processTransactions.c
 */
#include "transactions.h"
#include <stdio.h>
#include <string.h>

int main(void) {
	char name[64];
	double netChange = 0;
	int count = 0;
	for (int i = 0; (transactions[i].reciever); ++i) {
		count = i + 1; // on windows I have to use i - 1 to get correct count
	}
	printf("Number of transactions = %d\n", count);
	printf("%s", "Enter name: ");
	scanf("%63s", name);
	for (int i = 0; i < count; i++) {
		if (!strcmp(name, transactions[i].sender)) {
			netChange -= transactions[i].amount; 
		} else if (!strcmp(name, transactions[i].reciever)) {
			netChange += transactions[i].amount;
		}
	}
	printf("Net change for %s is %.2f\n", name, netChange);
}
```
This one counts the elements in the structure differently depending on os. Compiled and ran
```
gcc -std=c11 processTransactions.c -o processTransactions
./processTransactions
```

Any idea *why* they run differently? Is it something I'm doing?

---

### Post by tgalati4 on 2013-11-07
gcc compilers are a black box.  It could be that the NSA likes to sniff a loop every now and then.

The only thing I can think of is an extra return or line feed when going from linux to Windows, which the compiler interprets as a different instruction.  Do a careful comparison of the code between the two operating systems and look at the end-of-line characters.

I would research and summarize the differences between gcc 4.6.3 and 4.8.1 and see if that gives a clue as to what to examine next.

Finally, are there optimization differences between the two compilers?  Perhaps there is a default optimization level for each compiler that is causing different executions.

---

### Post by jerome1232 on 2013-11-08
I did install gcc 4.8.1 for Ubuntu and compiled with that, still the same results. I'll have to do more poking tomorrow, the only difference between the generated header files is the line endings.

```
**Windows**
cat -v -e transactions.h | tail
{"Isabella", "Emma", 628.280000},^M$
{"Abigail", "Sophia", 852.930000},^M$
{"Anthony", "Alexander", 264.010000},^M$
{"Mia", "Emily", 36.110000},^M$
{"Ethan", "Jacob", 767.720000},^M$
{"Ethan", "Noah", 782.250000},^M$
{"Daniel", "Mia", 839.960000},^M$
{"Jayden", "Daniel", 233.540000},^M$
{"Anthony", "Emma", 603.880000}^M$
};^M$

**Ubuntu**
cat -v -e transactions.h | tail
{"Isabella", "Emma", 628.280000},$
{"Abigail", "Sophia", 852.930000},$
{"Anthony", "Alexander", 264.010000},$
{"Mia", "Emily", 36.110000},$
{"Ethan", "Jacob", 767.720000},$
{"Ethan", "Noah", 782.250000},$
{"Daniel", "Mia", 839.960000},$
{"Jayden", "Daniel", 233.540000},$
{"Anthony", "Emma", 603.880000}$
};$

```

I converted the line endings on each operating system and I still get the same results. (it's a header file so I don't see how line endings would affect it anyways)

---

### Post by spjackson on 2013-11-08
I could be wrong here because I haven't seen enough of transactions.h, but my best guess is that
> 
```


    for (int i = 0; (transactions[i].reciever); ++i) {


```

reads beyond the bounds of the transactions array because there does not exist a declared element for which reciever [sic] is 0. In that case, you have undefined behaviour.

---

### Post by ofnuts on 2013-11-08
I'm with spjackson's here. I put more trust in the compiler than in my code (or yours:)). So it's not really a Linux/Windows problem but more a problem with your code, and you just happen to be lucky on one of the two platforms.

---

### Post by trent.josephsen on 2013-11-08
Incidentally, you usually[*] shouldn't put data (or code) in header files, because you may run into linking problems if you #include "transactions.h" in more than one location. I would put "extern Transaction transactions[];" in the header file, and have your createStruct write a .c file that #includes it. This may not be important for your current project, but it's something to be aware of.

[*] Essentially always. I can't think of a counterexample but that might be lack of creativity on my part.

---

### Post by jerome1232 on 2013-11-08
Well that was the assignment (to print to a header file then use the header file in a second program) and I couldn't think of any other way to count the elements of the array. That's the data we are given and we can't stick our own zero in to use as a terminator. We can't modify the structure so that it tracks it's own size. I think you are correct and I just happen to be hitting a zero in memory after the array. Data has come out correct on every run however (with the OS specific adjustment).

---

### Post by spjackson on 2013-11-08
Well I don't know what is and isn't allowed by your assignment, but there are at least 3 ways you can do this.

1. Count the records while generating the header file and print a line like "static const int array_size %d;" (or #define if you prefer).
2. When generating the header file, write a sentinel record at the end (after EOF) "{ NULL, NULL, 0.0 }".
3. Use the well-worn sizeof(transactions) / sizeof(transactions[0]) to limit your loop. In fact you don't need to loop through counting them because you know how many there are before you start, i.e. replace your counting loop with: count = sizeof(transactions) / sizeof(transactions[0]);

---

### Post by jerome1232 on 2013-11-08
I should've thought of number 3. Ah well, I shouldn't get dinged too bad for the mistake. That clears it up. The mistake was me as I suspected :D

---

### Post by trent.josephsen on 2013-11-08
If that's what the instructor expects you to do, that explains why it has to be in a header file -- you can't use sizeof to learn the size of an array defined in a different file (because sizeof is evaluated at compile time, while the data may not be available until link time).

That doesn't make it a sensible idea. A realistic C program would use a sentinel value or store the length separately. Fortunately for your instructor, academics don't need to concern themselves with such mundane trivialities as modularity and robustness.

(Me? Why no, I'm not bitter at all. Why do you ask?)

---

### Post by Bachstelze on 2013-11-08
You should learn to use Valgrind and to not consider a solution correct until it comes out clean in memcheck. It would have told you about your out-of-bouds read.

Doing *if (!strcmp(...))* is also poor practice, as is using *scanf()*.

---

### Post by trent.josephsen on 2013-11-08
scanf definitely has its problems, but what do you object to about !strcmp(...)?

---

### Post by Bachstelze on 2013-11-08
It is of course technically correct, but I consider it poor style. To me, *if (foo)* and its counterpart *if (!foo)* sould only ever be used when *foo* semantically represents a boolean (*i.e.*, something which represents whether some condition is true or false). This is not the case for *strcmp(...)*, which can take three values. If we had a hypothetical function *streq()*, then *if (streq(...))* would be the correct way to use it.

---

### Post by trent.josephsen on 2013-11-08
Fair enough. IMO it's hardly worse than strcmp(...) == 0 (or 0 == strcmp(...) for those who prefer Yoda conditions). But I see where you're coming from.

---

### Post by jerome1232 on 2013-11-08
scanf is what we are using at this stage of learning (this is an intro to c class), we talk about it, talked about the problems it has, but it's what we are using in class. 

I get what you mean about the comparison, to make it more obvious to see what it is I'm checking for. I guess I should be practicing as good of a form as I know how. Thanks. I've heard of valgrind before, I've been using gdb to debug but I haven't used valgrind before, I'll have to try it out.

---


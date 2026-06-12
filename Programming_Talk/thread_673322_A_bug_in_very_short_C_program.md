---
title: "A bug in very short C program"
date: 2008-01-20
forum: Programming Talk
---

### Post by xlinuks on 2008-01-20
Hi,
today I started learning C, and decided to create a very simple app, the one below. Would somebody please take a look at it and tell me why the "for" loop prints blank details about persons instead of what I actually entered..
The most weird thing is that the values are actually stored, the "printf" function confirms that every time I enter some detail about a given person. But when I enter the "for" loop (which is at the end of the code) - as if the records vanished!
Any hint would be appreciated, I've tried to figure lots of things, nothing actually helped..

```

#include <stdio.h>
#include <string.h>

#define STR_SIZE 256

struct Employee {
	
	char sFirstName[STR_SIZE];
	char sLastName[STR_SIZE];
	char sTitle[STR_SIZE];
	int iAge;
	int iSalary;
};

struct EmpRecord {
	
	int iEmployeeIndex;
	struct Employee employees[];
};

int main() {
	
	puts( "Type the number of employees we're gonna create:" );
	int iNum;
	scanf( "%d", &iNum );
	
	if( iNum < 1 ) {
		puts( "quitting, wrong number" );
		return 0;
	} else if( iNum > 10 ) {
		puts( "number too large, quitting" );
		return 0;
	}
	
	struct EmpRecord records;
	records.iEmployeeIndex = 0;

	while( records.iEmployeeIndex < iNum ) {
		
		struct Employee person = records.employees[ records.iEmployeeIndex ];
		
		printf( "Name of employee #%d:\n", records.iEmployeeIndex );
		scanf( "%s", person.sFirstName );
		printf( "CHOSEN FIRST NAME: %s\n", person.sFirstName );
		
		printf( "Last name:\n" );
		scanf( "%s", person.sLastName );
		printf( "CHOSEN LAST NAME: %s\n", person.sLastName );
		
		printf( "Title:\n" );
		scanf( "%s", person.sTitle );
		printf( "CHOSEN TITLE: %s\n", person.sTitle );
		
		printf( "Age:\n" );
		scanf( "%d", &person.iAge );
		printf( "CHOSEN AGE: %d\n", person.iAge );
		
		printf( "Salary:\n" );
		scanf( "%d", &person.iSalary );
		printf( "CHOSEN SALARY: %d\n", person.iSalary );
		
		records.iEmployeeIndex = records.iEmployeeIndex + 1;
		
	}
	
	puts( "\nPrinting out the info about all persons:" );
	int iCount = records.iEmployeeIndex;
	int i;
	
	for( i=0; i<iCount; i++ ) {
		struct Employee nextPerson = records.employees[ i ];
		printf( "Employee #%d\n", i );
		printf( "First Name: %s\n", nextPerson.sFirstName );
		printf( "Last Name: %s\n", nextPerson.sLastName );
		printf( "Title: %s\n", nextPerson.sTitle );
		printf( "Age: %d\n", nextPerson.iAge );
		printf( "Salary: %d\n", nextPerson.iSalary );
		puts( "-----------------\n" );
	}
	
	return 0;
}


```

---

### Post by melopsittacus on 2008-01-20
Hello xlinuks!

You need to allocate memory for records.employees.

Here is how you have to modify your code:

```

	struct EmpRecord records;
	records.iEmployeeIndex = 0;

       records.employees = (struct Employee *)malloc(sizeof(struct Employee) * iNum);

        if (records.employees == NULL) {
           printf("error, could not allocate memory");
           return -1;
        }

	while( records.iEmployeeIndex < iNum ) {
		
		struct Employee person = records.employees[ records.iEmployeeIndex ];




```

You also have to include stdlib.h at the beginning.
For details about malloc, see here: [http://www.cppreference.com/stdmem/malloc.html](http://www.cppreference.com/stdmem/malloc.html)

(warning: I have not tested this code, so it might contain bugs, but the principle is this)

---

### Post by Lster on 2008-01-20
Hello xlinuks

I managed to find the problem(s) with the code (I think) and it runs fine now. I can post the details if you need but if this is work you need to learn from it might be better if you look at some links on "structs" and "allocation/ deallocation".

I will say that even when I fixed it I noticed that if I entered enough characters for the "First Name" I could cause a buffer overflow. Look at this:

> Printing out the info about all persons:
Employee #0
First Name: GGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGmylastname
Last Name: mylastname
Title: CEO
Age: 20
Salary: 1000
-----------------


The "hello" at the end of the Gs is actually the "Last Name". See Wikipedia:

[http://en.wikipedia.org/wiki/Buffer_overflow](http://en.wikipedia.org/wiki/Buffer_overflow)

---

### Post by xlinuks on 2008-01-20
Hi melopsittacus
Unfortunately this doesn't seem to compile, gcc says:
test.c: In function &#8216;main&#8217;:
test.c:38: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
test.c:38: error: invalid use of flexible array member

---

### Post by xlinuks on 2008-01-20
Hi Lster
If you managed to compile and run it successfully please post the code, I will look at the link you gave, however I'm asking you to post the code cause I understand better from live code..

---

### Post by stroyan on 2008-01-20
The complaint about```
test.c:38: warning: incompatible implicit declaration of built-in function ‘malloc’
``` will occur when you call malloc before including a header file to declare it.  You need this line near the top of the file- ```
 #include <stdlib.h>
```
In general you can find the necessary header files for each library function by looking at that function's man page- "man malloc".

---

### Post by fyplinux on 2008-01-20
memory allocation is always the case, I am struggling with this.

---

### Post by wolfbone on 2008-01-21
> **xlinuks said:**
> Hi melopsittacus
Unfortunately this doesn't seem to compile, gcc says:
test.c: In function &#8216;main&#8217;:
test.c:38: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
test.c:38: error: invalid use of flexible array member

As already pointed out: you do need to allocate your dynamic storage, you will need the header for that, and you probably need to exercise more control over the lengths of the scanf'd strings.

Hoiwever, you also appear to be 1) making a copy (struct Employee person) of each (empty) Employee in the employees array in line 40 so that the assignments from scanf aren't actually made into the Employee elements in the array. 2) using a struct (the EmpRecord) with a fancy device called a "flexible array member". I'd guess that was an accident but if you really did want to use it, a patch for a minimally modified version would look something like this:

```
--- xlinuks.c	2008-01-21 04:16:00.000000000 +0000
+++ xlinuks1.c	2008-01-21 04:12:56.000000000 +0000
@@ -1,6 +1,6 @@
 #include <stdio.h>
 #include <string.h>
-
+#include <stdlib.h>
 #define STR_SIZE 256
 
 struct Employee {
@@ -32,43 +32,45 @@
 		return 0;
 	}
 	
-	struct EmpRecord records;
-	records.iEmployeeIndex = 0;
+	struct EmpRecord * records;
+	records = (struct EmpRecord *)					\
+	  malloc(sizeof(struct EmpRecord) + (iNum * sizeof(struct Employee)));
+	records->iEmployeeIndex = 0;
 
-	while( records.iEmployeeIndex < iNum ) {
+	while( records->iEmployeeIndex < iNum ) {
 		
-		struct Employee person = records.employees[ records.iEmployeeIndex ];
+		struct Employee * person = &records->employees[ records->iEmployeeIndex ];
 		
-		printf( "Name of employee #%d:\n", records.iEmployeeIndex );
-		scanf( "%s", person.sFirstName );
-		printf( "CHOSEN FIRST NAME: %s\n", person.sFirstName );
+		printf( "Name of employee #%d:\n", records->iEmployeeIndex );
+		scanf( "%s", person->sFirstName );
+		printf( "CHOSEN FIRST NAME: %s\n", person->sFirstName );
 		
 		printf( "Last name:\n" );
-		scanf( "%s", person.sLastName );
-		printf( "CHOSEN LAST NAME: %s\n", person.sLastName );
+		scanf( "%s", person->sLastName );
+		printf( "CHOSEN LAST NAME: %s\n", person->sLastName );
 		
 		printf( "Title:\n" );
-		scanf( "%s", person.sTitle );
-		printf( "CHOSEN TITLE: %s\n", person.sTitle );
+		scanf( "%s", person->sTitle );
+		printf( "CHOSEN TITLE: %s\n", person->sTitle );
 		
 		printf( "Age:\n" );
-		scanf( "%d", &person.iAge );
-		printf( "CHOSEN AGE: %d\n", person.iAge );
+		scanf( "%d", &(person->iAge) );
+		printf( "CHOSEN AGE: %d\n", person->iAge );
 		
 		printf( "Salary:\n" );
-		scanf( "%d", &person.iSalary );
-		printf( "CHOSEN SALARY: %d\n", person.iSalary );
+		scanf( "%d", &(person->iSalary) );
+		printf( "CHOSEN SALARY: %d\n", person->iSalary );
 		
-		records.iEmployeeIndex = records.iEmployeeIndex + 1;
+		records->iEmployeeIndex = records->iEmployeeIndex + 1;
 		
 	}
 	
 	puts( "\nPrinting out the info about all persons:" );
-	int iCount = records.iEmployeeIndex;
+	int iCount = records->iEmployeeIndex;
 	int i;
 	
 	for( i=0; i<iCount; i++ ) {
-		struct Employee nextPerson = records.employees[ i ];
+		struct Employee nextPerson = records->employees[ i ];
 		printf( "Employee #%d\n", i );
 		printf( "First Name: %s\n", nextPerson.sFirstName );
 		printf( "Last Name: %s\n", nextPerson.sLastName );

```

Note the awkward way you have to allocate the memory for a struct containing a flexible array member. Really though, I think you should just rewrite the whole thing to use ordinary structs and make more economic use of your storage with pointers and pointer arithmetic.

---


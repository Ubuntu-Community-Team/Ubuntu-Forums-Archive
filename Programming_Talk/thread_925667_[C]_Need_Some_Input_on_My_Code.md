---
title: "[C] Need Some Input on My Code"
date: 2008-09-20
forum: Programming Talk
---

### Post by loganwm on 2008-09-20
I'm working on a program that is (for lack of a better term) a "dumb ai."

It basically will convert typed input into crude commands into a small interpreter I'm writing.

Right now I've designed a tiny basis for the interpreter and some basic functions for the short-term memory.

Any input on my organization and any issues is appreciated.

I've also add a small Makefile, just type "make default" to compile the way I've set it up.


I've only documented some scant pieces showing implemented functions in main, but I'll probably do the rest soon.

I'm also adding some real commands, but I just wanted to get this code up and have some "peer editing" of sorts and constructive criticism.

---

### Post by scourge on 2008-09-21
- main() should return an int
- always turn compiler warnings to the max
- use the "extern" keyword for declaring external functions
- if you can remove an #include from a header file and put it in the source file instead, you often should
- Why does Command() take a struct node* parameter, but doesn't do anything with it?
- You're using strncmp() to compare only one character, why?

Here's a patch for you, so you can see what I was aiming for:

```

diff -u a/main.c b/main.c
--- a/main.c	2008-09-21 04:29:37.000000000 +0300
+++ b/main.c	2008-09-21 19:11:07.000000000 +0300
@@ -6,9 +6,9 @@
 
 #include <stdlib.h>
 #include <stdio.h>
-#include <string.h>
 #include "text.h"
 #include "memory.h"
+#include "process.h"
 
 
 
@@ -25,6 +25,7 @@
 		inputArr = GetWordsFromString(input,BASIC_DELIMS); //format string using delims to string array
 		Command(inputArr,root); //
 	}
+	
+	return EXIT_SUCCESS;
 }
 
-
diff -u a/Makefile b/Makefile
--- a/Makefile	2008-09-21 04:28:17.000000000 +0300
+++ b/Makefile	2008-09-21 19:03:58.000000000 +0300
@@ -1,4 +1,5 @@
-cc = gcc
+CC = gcc
 
 make default:
-	$(cc) main.c process.c text.c memory.c -o program
+	$(CC) -Wall -pedantic -std=gnu99 main.c process.c text.c memory.c -o program
+
diff -u a/memory.c b/memory.c
--- a/memory.c	2008-09-20 17:48:57.000000000 +0300
+++ b/memory.c	2008-09-21 19:14:02.000000000 +0300
@@ -1,3 +1,5 @@
+#include <stdlib.h>
+#include <string.h>
 #include "memory.h"
 
 struct node *AddNodeToEnd(struct node *root_, char *name_, char *owner_, char *value_) {
@@ -23,7 +25,7 @@
 
 struct node *FindNodeByName(struct node *root_, char *name_) {
 	struct node *traverse;
-	char nameKey[32];
+	//char nameKey[32];
 	traverse = root_;
 
 	while (traverse->next != NULL) {
diff -u a/memory.h b/memory.h
--- a/memory.h	2008-09-20 17:44:54.000000000 +0300
+++ b/memory.h	2008-09-21 19:07:43.000000000 +0300
@@ -1,6 +1,5 @@
-#include <stdlib.h>
-#include <stdio.h>
-
+#ifndef MEMORY_H
+#define MEMORY_H
 
 struct node {
 	char* name;
@@ -9,6 +8,9 @@
 	struct node *next;
 };
 
-struct node *AddNodeToEnd(struct node*, char*, char*, char*);
+extern struct node *AddNodeToEnd(struct node*, char*, char*, char*);
+
+extern struct node *FindNodeByName(struct node*, char*);
+
+#endif // MEMORY_H
 
-struct node *FindNodeByName(struct node*, char*);
diff -u a/process.c b/process.c
--- a/process.c	2008-09-21 04:15:49.000000000 +0300
+++ b/process.c	2008-09-21 19:12:15.000000000 +0300
@@ -1,3 +1,6 @@
+#include <stdio.h>
+#include <stdlib.h>
+#include <string.h>
 #include "process.h"
 
 void Command(char** string, struct node* root) {
diff -u a/process.h b/process.h
--- a/process.h	2008-09-21 00:00:30.000000000 +0300
+++ b/process.h	2008-09-21 19:07:20.000000000 +0300
@@ -1,7 +1,9 @@
-#include <stdlib.h>
-#include <stdio.h>
-#include <string.h>
+#ifndef PROCESS_H
+#define PROCESS_H
 
-#include "memory.h"
+struct node;
+
+extern void Command(char**, struct node*);
+
+#endif // PROCESS_H
 
-void Command(char**, struct node*);
diff -u a/text.c b/text.c
--- a/text.c	2008-09-19 05:11:20.000000000 +0300
+++ b/text.c	2008-09-21 19:12:49.000000000 +0300
@@ -1,3 +1,5 @@
+#include <stdlib.h>
+#include <string.h>
 #include "text.h"
 
 char **GetWordsFromString(char* string, char* delims) {
diff -u a/text.h b/text.h
--- a/text.h	2008-09-21 04:26:15.000000000 +0300
+++ b/text.h	2008-09-21 19:08:38.000000000 +0300
@@ -1,7 +1,9 @@
-#include <stdlib.h>
-#include <string.h>
+#ifndef TEXT_H
+#define TEXT_H
 
 #define BASIC_DELIMS " ,'\n"
 
-char **GetWordsFromString(char*, char*);
+extern char **GetWordsFromString(char*, char*);
+
+#endif // TEXT_H

```

---

### Post by cb951303 on 2008-09-21
First thing I noticed: you need to protect your headers from being included more than one time.

add something like this to all your header files

```

#ifndef HEADER_FILE_NAME_H //You should use a unique name here such as the name of the header file
#define HEADER_FILE_NAME_H

/* Header file contents goes here */

#endif
```

EDIT1: I see you use a lot of malloc() but not one free()
that's a bad practice. even though your application doesn't need any memory freeing right now because it terminates before you have to free them, in future you may regret this as it will get harder to keep track of allocated memory blocks since C doesn't have garbage collection. My advice is free always all the the allocated memories even though you don't need it.

EDIT2: memory.c and memory.h are not used?

EDIT3: concerning EDIT1: actually you have a memory leak ```
 inputArr = GetWordsFromString(input,BASIC_DELIMS); 
```and it took me 2-3 minutes to notice it. now imagine you have hundreds lines of code ... :)

---

### Post by loganwm on 2008-09-21
I'll probably set to work tearing this apart and fixing the horrible organization and such.

So, what you're saying is adding that line at the beginning of the header allows it to only be included once? and What about a standard header, like sdtlib.h and stdio.h, should a similar trick be used?


And can you help me spot that memory leak? Or at least describe it?

---

### Post by Sockerdrickan on 2008-09-21
> **loganwm said:**
> And can you help me spot that memory leak? Or at least describe it?
[http://bootloop.blogspot.com/2008/09/c-memory-deallocation.html](http://bootloop.blogspot.com/2008/09/c-memory-deallocation.html) :)

---

### Post by cb951303 on 2008-09-21
> **loganwm said:**
> I'll probably set to work tearing this apart and fixing the horrible organization and such.

So, what you're saying is adding that line at the beginning of the header allows it to only be included once? and What about a standard header, like sdtlib.h and stdio.h, should a similar trick be used?


And can you help me spot that memory leak? Or at least describe it?

standard libraries already have that protection. It's a very simple conditional protection actually. If that string is already defined, compiler skips whatever stated between "#ifndef" and "#endif" in other words your header file is not included.

in the function "GetWordsFromString(input,BASIC_DELIMS)" you allocate memory for the variable "output". Than the address of that memory block is passed to "inputArr". But every time the loop iterates the function "GetWordsFromString(input,BASIC_DELIMS)" is recalled thus it creates a new memory block. Then its address is passed to "inputArr". So you lose the old memory address meaning you can't free that block never since you don't know its address. What you should do is to add "free(inputArr);" to the end of the for loop.

---

### Post by monkeyking on 2008-09-21
> **loganwm said:**
> 
And can you help me spot that memory leak? Or at least describe it?

You can use 2 programs for testing the memory correctness of your program.
Run your program through gdb, or run it through valgrind.

good luck

---


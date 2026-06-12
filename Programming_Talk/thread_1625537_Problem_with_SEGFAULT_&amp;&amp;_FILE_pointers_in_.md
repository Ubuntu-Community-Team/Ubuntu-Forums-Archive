---
title: "Problem with SEGFAULT &amp;&amp; FILE pointers in C"
date: 2010-11-19
forum: Programming Talk
---

### Post by mimiteto on 2010-11-19
Hello all!
I am learning C programming language and last night I wrote some code... that seems to be broken in line 91 !
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define NUM 150

typedef struct llist_s{
	int Data;
	int Number;
	struct llist_s *Next;
} llist;

llist *create_node(llist *prev){
	llist *node = malloc(sizeof(node));
	
	if (prev == 0){
		node->Next = 0;
		node->Number = 0;
		return node;
	} else {
		prev->Next = node;
		node->Number = prev->Number + 1;
		node->Next = 0;
		return node;
	}	
}

FILE* generate_ifile(unsigned int num){
	FILE *int_file = fopen("int_file", "wt");
	int i;
	int k;
	
	if (!(int_file)){
		fprintf(stderr, "No file created!!!\n");
	}
	srand(time(0));
	for  ( i = 0, k = 0 ; i != num ; i++ , k++ ){
		fprintf(int_file, "%d ", rand());
// 		fprintf(int_file, "%d ", i);
		if (!(k%10)){
			printf("File successfuly created!!!\n");
			fflush(NULL);
		}
	}
	return int_file;
}

int fill_node(llist *node, FILE *fp){
	return fscanf(fp, "%d", &node->Data);
}

void out(llist *node, FILE *fp){
	fprintf(fp, "%d", node->Data);
	if (!(node->Number%10)){
		fprintf(fp, "\n");
	}
	if (!(node->Next)){
		free(node);
	} else {
		fprintf(stderr, "GENERAL LOGIC FAILURE!!!\n");
		exit (-1);
	}
	return ;
}

void even_odd(llist *node, FILE *even, FILE *odd){
	if (!(node->Data)){
		even_odd(node->Next, even, odd);
		return ;
	}
	if ((node->Data)%2){
		even_odd(node->Next, even, odd);
		out(node, odd);
		return ;
	} else {
		even_odd(node->Next, even, odd);
		out(node, even);
		return ;
	}
}

int main(int argc, char **argv){
	llist *node = create_node(0);
	FILE *odd;
	FILE *even;
	FILE *intfile;
	
	if (argv[3]){
		intfile = fopen(argv[1], "rt");
		even = fopen(argv[2], "w+t");
		odd = fopen(argv[3], "w+t");
	} else {
		intfile = generate_ifile(NUM);
		odd = fopen("~/odd", "w+t");
		even = fopen("~/even", "w+t");
		printf("Check your user directory for outputed files!!!\n");
	}
	fprintf(odd, "Odd numbers are: \n\t");
	fprintf(even, "Even numbers are \n\t");
// 	fclose(intfile);
	return 0;
}
```
Can somebody explain what is wrong from theoretical point of view at least? Thank you in advance.

---

### Post by Arndt on 2010-11-19
> **mimiteto said:**
> Hello all!
I am learning C programming language and last night I wrote some code... that seems to be broken in line 91 !
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define NUM 150

typedef struct llist_s{
	int Data;
	int Number;
	struct llist_s *Next;
} llist;

llist *create_node(llist *prev){
	llist *node = malloc(sizeof(node));
	
	if (prev == 0){
		node->Next = 0;
		node->Number = 0;
		return node;
	} else {
		prev->Next = node;
		node->Number = prev->Number + 1;
		node->Next = 0;
		return node;
	}	
}

FILE* generate_ifile(unsigned int num){
	FILE *int_file = fopen("int_file", "wt");
	int i;
	int k;
	
	if (!(int_file)){
		fprintf(stderr, "No file created!!!\n");
	}
	srand(time(0));
	for  ( i = 0, k = 0 ; i != num ; i++ , k++ ){
		fprintf(int_file, "%d ", rand());
// 		fprintf(int_file, "%d ", i);
		if (!(k%10)){
			printf("File successfuly created!!!\n");
			fflush(NULL);
		}
	}
	return int_file;
}

int fill_node(llist *node, FILE *fp){
	return fscanf(fp, "%d", &node->Data);
}

void out(llist *node, FILE *fp){
	fprintf(fp, "%d", node->Data);
	if (!(node->Number%10)){
		fprintf(fp, "\n");
	}
	if (!(node->Next)){
		free(node);
	} else {
		fprintf(stderr, "GENERAL LOGIC FAILURE!!!\n");
		exit (-1);
	}
	return ;
}

void even_odd(llist *node, FILE *even, FILE *odd){
	if (!(node->Data)){
		even_odd(node->Next, even, odd);
		return ;
	}
	if ((node->Data)%2){
		even_odd(node->Next, even, odd);
		out(node, odd);
		return ;
	} else {
		even_odd(node->Next, even, odd);
		out(node, even);
		return ;
	}
}

int main(int argc, char **argv){
	llist *node = create_node(0);
	FILE *odd;
	FILE *even;
	FILE *intfile;
	
	if (argv[3]){
		intfile = fopen(argv[1], "rt");
		even = fopen(argv[2], "w+t");
		odd = fopen(argv[3], "w+t");
	} else {
		intfile = generate_ifile(NUM);
		odd = fopen("~/odd", "w+t");
		even = fopen("~/even", "w+t");
		printf("Check your user directory for outputed files!!!\n");
	}
	fprintf(odd, "Odd numbers are: \n\t");
	fprintf(even, "Even numbers are \n\t");
// 	fclose(intfile);
	return 0;
}
```
Can somebody explain what is wrong from theoretical point of view at least? Thank you in advance.

How do you know it's on line 91? How do you invoke the program, what are its indata and what happens?

Have you tried the debugger?

Another good tool is 'valgrind'.

---

### Post by spjackson on 2010-11-19
```

    if (argv[3]){

```Wrong test. If there are no command line arguments, this test may be true. You mean:
```

    if (argc > 3){

``````

        odd = fopen("~/odd", "w+t");
        even = fopen("~/even", "w+t");

```fopen does not expand ~. The shell does this. These fopens will fail unless you have a subdirectory called ~ in your current working directory. You are not handling errors if fopen fails. What is that t supposed to do in the open mode?

That's enough for now.

---

### Post by mimiteto on 2010-11-19
Thank you!!! That 't' is for text mode. I didn't know about argv[3] can be logical true, even if no arguments are passed(I use it that way, because that was the way described in some tutorial, and by the way, that was the buggy part)!!! So, THANK YOU gys ;)

---

### Post by gmargo on 2010-11-19
Where's your error checking?  I count seven system calls that should never be written without checking the return values.

---


---
title: "C function help"
date: 2008-06-01
forum: Programming Talk
---

### Post by gorded on 2008-06-01
Hey im trying to make a function that convert a char array to a float array
the string is split by commas like so   1,2,3,4,5,6,7,8   etc.
this is the function so far but i seem to be getting a segmentation fault that i cant quite track down.

```
GLfloat *strarray(char *string) {
	int size = strcount(string, ',') + 1;
	GLfloat *data = (GLfloat*) malloc(size * sizeof(GLfloat));
	char *token = strtok(string, (const char *)',');
	for (int i = 0; i < size; i++) {
		data[i] = (GLfloat) atoi(token);
		token = strtok(NULL,(const char *)',');
	}
	return data;
}
```

strcount is my own method that just count the occurances of a character in a string, it works the way it supposed to. Any help is greatly appreciated.

---

### Post by Can+~ on 2008-06-01
Wait, what is:

```
char *token = strtok(string, (const char *)',');
```

Why are you casting an already constant char, into a pointer?

It should be:

```
char *token = strtok(string, ",");
```

---

### Post by issih on 2008-06-01
Also atoi converts to an integer, the compiler will then probably do an implicit conversion to a float from there in order to store data into your array, assuming it knows how to convert an integer to GLFloat. However if any of your data is e.g. 5.78, you will lose the .78 completely with this method. Look at using atof instead. Not 100% sure thats in the ansi c standard however

---

### Post by Can+~ on 2008-06-01
Ok, I had to invent a "strcount" function, and change everything to floats. My guess is that the size you were getting with the strcount function wasn't all that right.

My version of the counter is more a la K&R, with a pointer over the string, until it gets to the end (char 0).

[PHP]int strcount(char *string)
{
	char *ptr=string;
	int count=0;
	
	while(*ptr != 0)
	{
		if (*ptr == ',')
			count++;
		
		ptr++;
	}
			
	return count+1;
}

float *strarray(char *string) 
{
	int size, i;
	float *data;
	char *token;

	size = strcount(string);
	data = (float*)malloc(size * sizeof(float));
	token = strtok(string, ",");

	for (i = 0; i < size; i++)
	{
		data[i] = atof(token);
		token = strtok(NULL,",");
	}
	return data;
}

int main()
{
	char a[] = "1,2,3,4,5,6";
	float *farray;
	int i;
	
	farray = strarray(a);
	
	for (i=0; i<6; i++)
		printf("%f, ", farray[i]);
	
	return 0;
}[/PHP]

My only wonder, is that this goes over the same array twice, once to get the total length to malloc it, and then again to add the values (O(n)) (Thanks for the correction).

*edit* Made using a list:

[PHP]#include <string.h>
#include <stdio.h>
#include <stdlib.h>

typedef struct FNODE
{
	float value;
	struct FNODE *__next__;
}fnode;

fnode *newNode(const float value)
{
	/*
	 * Allocates and returns a new node with the specified value.
	 * */
	
	fnode *nnode = (fnode*)malloc(sizeof(fnode));
	nnode->value = value;
	nnode->__next__ = NULL;
	
	return nnode;
}

fnode *strList(char *string) 
{
	/*
	 * Creates a List and returns the pointer to the first element.
	 * If the string is empty, the pointer will be NULL.
	 * 
	 * */
	const char sep[2] = ","; // String with separators (for later change)
	char  *token = strtok(string, sep);
	fnode *iter=NULL, *root=NULL;
	
	// Make sure it's not empty.
	if (token != NULL)
	{
		// Make the first one, call it root.
		root = iter = newNode(atof(token));
		
		// Do another step.
		token = strtok(NULL,sep);
		
		// Loop until it ends.
		while(token != NULL)
		{
			iter->__next__ = newNode(atof(token));
			iter = iter->__next__;
			
			token = strtok(NULL,sep);
		}
	}
	
	return root;
}

void printList(fnode *root)
{
	/*
	 * Prints list in format:
	 * [ value, value, value, value ]
	 * 
	 * If root is null, it prints "List is empty".
	 * */
	
	fnode *iter = root;
	
	if (root)
	{
		printf("[ %.2f", iter->value);
		while(iter->__next__)
		{
			iter = iter->__next__;
			printf(", %.2f", iter->value);
		}
		printf(" ]");
	}else{
		printf("List is empty.");
	}
}

int main()
{
	char a[] = "1,2,3,-4, 123, 23";
	fnode *root;
	
	root = strList(a);
	printList(root);
	
	return 0;
}[/PHP]

The insertion is O(n), it creates a new object and connect it to the list each time a new integer (passed to float with atof) is found.

---

### Post by geirha on 2008-06-01
> **Can+~ said:**
> 
My only wonder, is that this goes over the same array twice, once to get the total length to malloc it, and then again to add the values (O(n^2)) (the last for I made, just was an example to check the values). It would be far easier with a list structure, making the transition to O(n).


O(n^2) is when for each element you operate on every other element of the list, which you do not do in the example above. You iterate through the string twice, which is 2n, which gives O(n).

Your first solution is perfectly fine, though don't forget to free()! ;)

---

### Post by Can+~ on 2008-06-01
> **geirha said:**
> O(n^2) is when for each element you operate on every other element of the list, which you do not do in the example above. You iterate through the string twice, which is 2n, which gives O(n).

Your first solution is perfectly fine, though don't forget to free()! ;)

Corrected, a minor brain fart.

---


---
title: "[SOLVED] Something strange on memory allocation with gnu c"
date: 2008-01-21
forum: Programming Talk
---

### Post by fyplinux on 2008-01-21
Hello, I am using "gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)"

I spend hours to debug my program, and find a strange behavior when allocating memory. I don't know whether it is my fault or the compiler's.

I have a list in the sturcture:
```
struct hostlist{
	char **list;
	int index;
	int length;
};
```

Hope these code are enough for you to understand my design:
```

struct hostlist hlst = {0,-1,0};//index is less than length
hlst.list = malloc(sizeof(char **));

        char *buf = calloc(47,1);
	if(buf == 0){
		perror("malloc");
	}
	buf = calloc(47,1);
	if(buf == 0){
		perror("malloc");
	}
	while(readline(flist,buf) ==0){//read one line from a file

		(hlst.index)++;
		(hlst.length)++;

		printf("index %d\n",hlst.index);
		hlst.list[hlst.index] = buf;
		printf("read from file:%s\n",hlst.list[hlst.index]);//------------------
		buf = calloc(17,1);
		if(buf == 0){
			perror("calloc");
		}
	}	
	if(hlst.length>0){
		hlst.index = 0;
		while(hlst.index<hlst.length){
			printf("%s\n",hlst.list[hlst.index]);//===========
			(hlst.index)++;
		}
	}


```

This piece of code works well, the result indicated by ---------------and ===========are the same. 

But, the buf is allocated twice, if it is only allocated once, at ------------------, it's fine, at ================, the first element of the list will be some strange symbols.

what is going on here?

---

### Post by fyplinux on 2008-01-21
if (char **)malloc(A BIG ENOUGH SIZE), the problem solved

---

### Post by hod139 on 2008-01-21
> **fyplinux said:**
> I don't know whether it is my fault or the compiler's.

Not the compilers fault, and almost never is. 

> 
```

struct hostlist hlst = {0,-1,0};//index is less than length
hlst.list = malloc(sizeof(char **));

```this will allocate the outer array (pointer) to be size 1.  It also does not allocate the inner char* To do that, you would do
```

hlst.list[0] = malloc(N*sizeof(char))
}

```where N is the length of the array.

This is why all of your 
```

hlst.list[hlst.index] = buf;

```calls are failing.  hlst.list is allocated to be an array of size 1, with the inner array not allocated!  So, when hlst.index = 0, the first access is legal, but setting it equal to buf is illegal, since it is unallocated.  When hlst.index > 0, the array access is out of bounds.

> 
    char *buf = calloc(47,1);
    if(buf == 0){
        perror("malloc");
    }
    buf = calloc(47,1);
    if(buf == 0){
        perror("malloc");
    }
This is really confusing.  First, you are not guaranteed that a char will always be one byte.  You are safer writing 
```

char *buf = calloc(47,sizeof(char));

```Second, why are you allocating the buffer twice?  The second call to calloc just leaked the memory allocated by the first calloc.  

Lastly, you never free this buffer in the code posted.

> 
```

    while(readline(flist,buf) ==0){//read one line from a file

```What is readline?

> 
```

        (hlst.index)++;
        (hlst.length)++;

        printf("index %d\n",hlst.index);
        hlst.list[hlst.index] = buf;
        printf("read from file:%s\n",hlst.list[hlst.index]);//------------------
        buf = calloc(17,1);
        if(buf == 0){
            perror("calloc");
        }
    } 

```Here, the hlst.list[hlst.index] = buf; line is causing an array index out of bounds error.  You never allocated memory for hlst.list[i].

Again, you reallocate buf, which will cause another memory leak from the above allocations.  Why are you reallocating it again?

---

### Post by fyplinux on 2008-01-21
> 

Second, why are you allocating the buffer twice? The second call to calloc just leaked the memory allocated by the first calloc.

I happened to input these statements twice, and the problem disappeared, that's why I think it's strange.


> 
Lastly, you never free this buffer in the code posted.

Quote:
Code:

    while(readline(flist,buf) ==0){//read one line from a file

...

Here, the hlst.list[hlst.index] = buf; line is causing an array index out of bounds error. You never allocated memory for hlst.list[i].


buf is assigned to be a list element: hlst.list[i] = buf. this is why the inner space is never allocated directly.
on the other hand, buf is re-allocated each time the old one is assigned to hlst.list[i]

The really confusing thing is 

> 

```

struct hostlist hlst = {0,-1,0};//index is less than length
hlst.list = malloc(sizeof(char **));
```

this will allocate the outer array (pointer) to be size 1. 

although the outer array is size one, most of the elements except the first few ones, whose index is greater than 1 could still be accessed.




> What is readline?

read a line from a file, suppose the line ends with '\n', which is not regarded as a character of a line.

---

### Post by Wybiral on 2008-01-21
> **hod139 said:**
> Not the compilers fault, and almost never is.

Quoted for truth!

---

### Post by stroyan on 2008-01-21
I don't know where you got your readline function from.
The way it is called is very likely to overrun the allocated buffer.
You only calloc 17 bytes for buf in the loop.
And the way readline is called does not indicate how much buffer is available.
(The readline from libreadline5-dev allocates a buffer and returns that.)

The gnu glibc version of scanf has a nice feature for safely reading strings by allocating a buffer for the string.
A format of "%as" or "%a[^\n]" will allocate a buffer and assign the address to a pointer variable.
Install the glibc-doc package and have a look at file:///usr/share/doc/glibc-doc/html/libc_12.html#SEC215
Here is a small example.[PHP]
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    FILE *f;
    int i;
    char *line;

    for (i=1; i<argc; i++) {
        f = fopen(argv[i], "r");
        if (f == NULL) return 1;
        while (fscanf(f, "%a[^\n]\n", &line) == 1) {
            printf("line is '%s'\n", line);
            free(line);
        }
        fclose(f);
    }
    return 0;
}[/PHP]

---

### Post by c174 on 2008-01-21
> **fyplinux said:**
> I happened to input these statements twice, and the problem disappeared, that's why I think it's strange.


That is a common thing. Allocating a little extra and it "works". You can experience the same thing with output to the terminal - removing an output makes the program suddenly crash.

These kinds of strange behavior is a sign that you are using unassociated pointers or have other similar mistakes.

---

### Post by hod139 on 2008-01-21
I rewrote some of your code, please read my comments.

Since I have no idea what readline is, this is untested.
```

struct hostlist{
    char **list;
    int index; // don't need length, can be determined from index
};

``````

    // lets define some array sizes
    int MAX_NUM_LINES = 100;
    int BUFFER_SIZE = 47;

    int i = 0;

    struct hostlist hlst = {0,0};

    // allocate an array of MAX_NUM_LINES char pointers
    hlst.list = malloc(MAX_NUM_LINES*sizeof(char *));
    if(hlst.list == 0)
    {
        perror("malloc outer array");
    }
    for(i = 0; i < MAX_NUM_LINES; ++i){
       hlst.list[i] = malloc(BUFFER_SIZE * sizeof(char)); // allocate the inner array to contain BUFFER_SIZE chars
       if(hlst.list[i] == 0){
          perror("malloc inner array");
       }
    }

    // allocate a buffer to hold BUFFER_SIZE chars, initialized to '0'
    char *buf = calloc(BUFFER_SIZE, sizeof(char));
    if(buf == 0){
        perror("malloc");
    }
    
    //I don't know what readline is, so I don't know if you are using it correctly
    // It looks like it probably can easily cause a buffer overflow of buf
   // please see the other posts in this thread about alternatives
    //while(readline(flist,buf) ==0)
    {//read one line from a file
 
        printf("index %d\n",hlst.index); 
 
        if(hlst.index >= MAX_NUM_LINES){
           // not enough memory allocated, break out or reallocate more
        }
        hlst.list[hlst.index] = buf; // lets hope buf was not overflowed in the readline
        printf("read from file:%s\n",hlst.list[hlst.index]);//------------------

        (hlst.index)++; // increments index after we use it        
        
    }
    free(buf); // free the buffer
    
    // I'm not sure why you use two variables to keep track of the array size, one is enough.
    // you don't need length
    for(i = 0; i < hlst.index; ++i){
        printf("%s\n",hlst.list[i]);//===========
    }


   // please free hlst.list somewhere when you are done with it!!!

```

---

### Post by fyplinux on 2008-01-21
My readline function:
```

/*
* read a line from file to buf
* return value:
* 0, succeed,
* 1, end of file
* 2, error
*/
int readline(int file,char *buf){
	int err;
	while((err =read(file,buf,1))!=-1&&err != 0 &&buf[0] != '\n'){
		buf++;
	}
	if(err == -1){
		perror("read line:\n");
		return 2;
	}
	else if(err == 0){
		return 1;
	}
	buf[0] = '\0';
	return 0;
}

```

and the content of the file is an ip address at each line, e.g.:

123.23.55.198
198.168.1.1

---

### Post by hod139 on 2008-01-22
Your readline function could easily overflow the buffer.  You need to look at the code stroyan posted for safer file IO.

---

### Post by wolfbone on 2008-01-22
> **hod139 said:**
> Your readline function could easily overflow the buffer.  You need to look at the code stroyan posted for safer file IO.

And for *safest* file i/o I would suggest reading some more of the glibc documentation. The part in which i/o is covered in depth and where getline(...) is recommended for reading lines from streams might be of particular interest.

---


---
title: "segmentation fault"
date: 2010-10-23
forum: Programming Talk
---

### Post by c2tarun on 2010-10-23
hi friends i am trying to get the ASCII value of a character by the following program.

```

#include<stdio.h>

int main(void)
{
char* exp;
int num;
size_t* n;
*n=100;
getline(&exp,n,stdin);

num=exp[3];
printf("%d",num);
}

```

but i am getting segmentation fault.
this program is working fine in windows turbo c compiler.
can anyone please explain me what is segmentation fault and why is it coming in ubuntu.

---

### Post by worksofcraft on 2010-10-23
> **c2tarun said:**
> hi friends i am trying to get the ASCII value of a character by the following program.

```

#include<stdio.h>

int main(void)
{
char* exp;
int num;
size_t* n;
*n=100;
getline(&exp,n,stdin);

num=exp[3];
printf("%d",num);
}

```

but i am getting segmentation fault.
this program is working fine in windows turbo c compiler.
can anyone please explain me what is segmentation fault and why is it coming in ubuntu.


Segmentation fault means that your program tried to access memory that is not allocated to it. In your program it is trying to store the line where exp points to and it is trying to store 100 where n points to.

Neither of these pointers have been initialized.
Try the following:


[php]
/* gcc -o getline getline.c */
#include<stdio.h>

int main() {
	char * exp = NULL;
	int num;
	size_t n;

	printf("please enter expression:");
	getline(&exp,&n,stdin);
	printf("got line=%s\n", exp);

	/* this reads ASCII value of 4th character in string! */
	num=exp[3];
	printf("exp[3]=%d\n",num);
}
[/php]

---

### Post by Some Penguin on 2010-10-23
*sigh*

What is the value of 'n' when you're attempting to shove bytes using 'n' as a memory address?  And likewise for 'exp'?  Do you know what pointers are?

The existence of a forum is not an excuse to ignore the need to do basic preparation like reading an introductory programming book.

---

### Post by c2tarun on 2010-10-23
hey i am not getting what you are explaining.
exp is a pointer, so it is pointing to the input buffer.
can't we use the characters from that buffer???
i m also not getting last line also about the memory allocation.
please explain a bit.

---

### Post by worksofcraft on 2010-10-23
> **c2tarun said:**
> hey i am not getting what you are explaining.
exp is a pointer, so it is pointing to the input buffer.
can't we use the characters from that buffer???
i m also not getting last line also about the memory allocation.
please explain a bit.

soz, my bad... I updated it now :)

The real input buffer is somewhere in a keyboard device driver, so your program cannot get access to that.

Getline actually wants to copy the characters into a buffer inside your own program. After reading the description of getline I see that when I set that pointer to NULL, getline will allocate the necessary memory for me, but if it is not set to point anywhere in particular then getline tries to use wherever it happens to point. That is most likely outside your application's memory space and hence you get segmentation fault!

---

### Post by Some Penguin on 2010-10-23
The input buffer *DOESN'T EXIST*.

```

size_t *n;

```

leaves n with an UNDEFINED value.  Therefore, interpreting it as ANYTHING, including a memory address, is incorrect.  Hence,

```

*n = 100;

```

is already doomed.

---

### Post by worksofcraft on 2010-10-23
to get an idea of uninitialized pointers you can try running this program a few times:
[php]
/* gcc -o point point.c */
#include<stdio.h>

int main() {
	{
		int x = 1;
	}
	{
		char * exp; // exp is an uninitialized pointer.
		printf("exp points to address %p\n", exp);
	}
	return 0;
}
[/php]
I got:
```


$> ./point
exp points to address 0x7fff3b0a0dc0
$> ./point
exp points to address 0x7fff4cb96290
$> ./point
exp points to address 0x7fffa20c2390

```
it's just random garbage that happened to be in that memory location :shock:

---

### Post by c2tarun on 2010-10-23
> **worksofcraft said:**
> soz, my bad... I updated it now :)

The real input buffer is somewhere in a keyboard device driver, so your program cannot get access to that.

Getline actually wants to copy the characters into a buffer inside your own program. After reading the description of getline I see that when I set that pointer to NULL, getline will allocate the necessary memory for me, but if it is not set to point anywhere in particular then getline tries to use wherever it happens to point. That is most likely outside your application's memory space and hence you get segmentation fault!

:KS thanx a lot worksofcraft. :)

```
to: SOME PENGUINE
```

thanx to you to for replying. and as per your suggestion i'll do my side of reading work from next time ;)

---

### Post by c2tarun on 2010-10-23
hey can you please tell me how to do the step by step execution of the program.
the same way as done by F7 in turbo c in windows.
thanx

---

### Post by worksofcraft on 2010-10-23
> **c2tarun said:**
> hey can you please tell me how to do the step by step execution of the program.
the same way as done by F7 in turbo c in windows.
thanx

when you compile your program you must add the -g switch so it will include debug info. Then you run the debugger gdb and you set break points and can inspect variables with the print command. e.g.
```


$>gcc -g point.c
$>gdb ./a.out
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3...
(gdb) break main
Breakpoint 1 at 0x40052c: file point.c, line 6.
(gdb) run
Starting program: /home/cjs/Desktop/examples/a.out 

Breakpoint 1, main () at point.c:6
6			int x = 1;
(gdb) print x
$1 = 0
(gdb) s
10			printf("exp points to address %p\n", exp);
(gdb) print exp
$2 = 0x7fffffffe850 "\001"
... etc...

```

I know that 15 years ago Borland and Symantec and Watcom had full visual debuggers for C++ on Windows but IDK how to do that on Linux :(

---

### Post by c2tarun on 2010-10-23
i was trying to run the following program

[PHP]
#include<stdio.h>

int main(void)
{
  char* str;
  size_t n;
  int i,count;
  n=100;
  scanf("%d",&count);
  for(i=0;i<count;i++)
    {
      getline(&str,&n,stdin);
      printf("%s\n",str);
    }
}
[/PHP]

it was not running as i expected.
what i expected is that it accepts a number and then accepts that number of strings and print them.
but it is accepting one less string plus printing a large gap between the number input and first string input.???
why so??

---

### Post by GeneralZod on 2010-10-23
"str" is not initialised anywhere.

Edit:

Also, I guess  scanf("%d", &count) doesn't eat the carriage return on that line.

Edit2:

The strings you read in will have a carriage return at the end, so the \n in printf("%s\n",str) will make the number of carriage returns printed equal to two.

---

### Post by c2tarun on 2010-10-23
> **GeneralZod said:**
> "str" is not initialised anywhere.

Edit:

Also, I guess  scanf("%d", &count) doesn't eat the carriage return on that line.

Edit2:

The strings you read in will have a carriage return at the end, so the \n in printf("%s\n",str) will make the number of carriage returns printed equal to two.



sir it is giving long gap before entering the string, not after entering.

---

### Post by GeneralZod on 2010-10-23
> **c2tarun said:**
> sir it is giving long gap before entering the string, not after entering.

Yes, that is because the first "string" read is just the carriage return from when you entered the number, because:

> **GeneralZod said:**
> scanf("%d", &count) doesn't eat the carriage return on that line.


---

### Post by c2tarun on 2010-10-23
> **GeneralZod said:**
> Yes, that is because the first "string" read is just the carriage return from when you entered the number, because:


sir i think this never happened before.
in c integers and strings have different iinput methods. integer variable can't store carriage return.
plus when we press return after entering a string it takes NULL as its last character, as far as i know C, C++ and Java do this way, don't know about other languages....
sorry.
can anyone explain me my problem

---

### Post by dwhitney67 on 2010-10-23
You need to be more vigilant when using scanf() to read input.

If you enter the following characters. "10<enter>" in response to a query to input an integer, the 1 and 0 will be used to satisfy the input.  The <enter> (or should I say newline-character) is still sitting in the input-stream (stdin).

When you proceed to use getline() in the next set of input queries, the first query is immediately satisfied because a newline-character is available in the input-stream.

Consider using getline() for all of you inputs, even if it is an integer.  You can always use atoi() to convert string input to an integer, or even consider using sscanf() for parsing a string with multiple values.

---

### Post by worksofcraft on 2010-10-23
> **c2tarun said:**
> sir i think this never happened before.
in c integers and strings have different iinput methods. integer variable can't store carriage return.
plus when we press return after entering a string it takes NULL as its last character, as far as i know C, C++ and Java do this way, don't know about other languages....
sorry.
can anyone explain me my problem

Yes GeneralZod is correct:

After you have typed the value for count you press the enter key, but scanf is only reading all the digits that it needs to get the value of count and leaves that <Enter> sitting there in your input stream;

Next you ask it to getline and so the first thing it finds is that yet unprocessed <enter> and it assumes that must be your first line. You can test that this is so by typing some garbage after your count:
```


$> gcc rd.c
$> ./a.out
3 hello
 hello

one
one

two
two

```

the gap between the lines is because getline evidently does include the new line character.

p.s. you can fix it like so:
[php]
#include<stdio.h>

int main(void)
{
  char* str = NULL;
  size_t n;
  int i,count;
  getline(&str,&n,stdin);
  sscanf(str, "%d",&count);
  for(i=0;i<count;i++)
    {
      getline(&str,&n,stdin);
      printf("%s\n",str);
    }
  free(str); // release the allocated memory block
} 
[/php]

---

### Post by c2tarun on 2010-10-23
> **worksofcraft said:**
> Yes GeneralZod is correct:

After you have typed the value for count you press the enter key, but scanf is only reading all the digits that it needs to get the value of count and leaves that <Enter> sitting there in your input stream;

Next you ask it to getline and so the first thing it finds is that yet unprocessed <enter> and it assumes that must be your first line. You can test that this is so by typing some garbage after your count:
```


$> gcc rd.c
$> ./a.out
3 hello
 hello

one
one

two
two

```the gap between the lines is because getline evidently does include the new line character.

p.s. you can fix it like so:
[php]
#include<stdio.h>

int main(void)
{
  char* str;
  size_t n;
  int i,count;
  n=100;
  getline(&str,&n,stdin);
  sscanf(str, "%d",&count);
  for(i=0;i<count;i++)
    {
      getline(&str,&n,stdin);
      printf("%s\n",str);
    }
} 
[/php]


thanx :)
i was not knowing that after entering a number there also exists a unprocessed return, which getline can process. thanx a lot

---

### Post by StephenF on 2010-10-23
> **worksofcraft said:**
> 
p.s. you can fix it like so:
[php]
#include<stdio.h>

int main(void)
{
  char* str;
  size_t n;
  int i,count;
  n=100;
  getline(&str,&n,stdin);
  sscanf(str, "%d",&count);
  for(i=0;i<count;i++)
    {
      getline(&str,&n,stdin);
      printf("%s\n",str);
    }
} 
[/php]
This is still incorrect. Either allocate str with malloc and set n to be the size allocated or set str to NULL in which case the value of n is ignored. Leaving str set to some random value will cause undefined behaviour. Read the man page.

Also when done call free on str.

---

### Post by worksofcraft on 2010-10-23
> **StephenF said:**
> This is still incorrect. Either allocate str with malloc and set n to be the size allocated or set str to NULL in which case the value of n is ignored. Leaving str set to some random value will cause undefined behaviour. Read the man page.

Also when done call free on str.

lol - yes I must remember not to cut and paste from other people's posts at 2am... the issue of uninitialized pointers was however addressed earlier... but I'll go back and fix my other post now ;)

---


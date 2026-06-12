---
title: "strings and C"
date: 2008-10-30
forum: Programming Talk
---

### Post by swappo1 on 2008-10-30
Hello,

I am trying to enter a string in C and have each character stored as an element of an array.  I then print each element of the array starting from the first element to the length - 1 element.  I am not sure why I am getting the following results.

Here is my code:
[PHP]#include <stdio.h>
#include <string.h>

main()
{
	char string[80];
	int length, count;
	
	printf("Enter a string: ");
	for(count=0; (string[count] = getchar()) != '\n'; count++);		// input the string into an array
	
	length = strlen(string) - 1;	// get the number of elements in the array
	printf("length = %d\n", length);
	
	printf("The string you entered: ");
	for(count=0; count < length; count++)	// print each element of string
		printf("%c", string[count]);
	return;
}[/PHP]

Here is my result:
> Enter a string: This is a test.
length = 21
The string you entered: This is a test.
&#65533;1&#65533;scott@scott-laptop:~$ 


The length should be 15 and what's with the characters before the prompt?
Thanks for any help.

---

### Post by nvteighen on 2008-10-30
Er... it works perfectly for me.

Btw, always write **int main(void)** and make main return an integer (usually 0 when you consider no error ocurred).

---

### Post by nvteighen on 2008-10-30
Wait a bit. You're not initializing the string variable to anything, so you're leaving it to have space full with random stuff. You better make all characters in the string equal to 0 ('\0') before anything.

That way it will always work everywhere.

---

### Post by skirkpatrick on 2008-10-30
Yes, you can either do a **memset(string, 0, sizeof(string))** at the very beginning or even better:

```

    printf("Enter a string: ");
    int exitFlag = 0;
    while(!exitFlag)
    {
        char ch = getchar();
        switch (ch)
        {
            case '\n':
                exitFlag = 1;
                break;

            default:
                string[count++] = ch;
                string[count] = '\0';
                if (count >= sizeof(string))
                {
                    exitFlag = 1;
                }
                break;
        }
    }

```

Is it longer?  Yes it is.  But it allows you to test for more than just one special character and the important thing it does is to prevent someone from entering data that is longer than the storage space allocated (known as buffer overflow).

---

### Post by swappo1 on 2008-10-30
Okay, when I initialize string[80] to:
```
char string[80]= '\0';
```
I get an error: invalid initializer.  If I use "\0" the program works and prints 15 for the length of the string.  Do I need to use"" for characters? and '' for integers?  Thanks for the help.

---

### Post by slavik on 2008-10-30
should be { '\0' } ... there is no string string C, only char array string and that is how you assign a single value to an array.

---

### Post by rnodal on 2008-10-30
> **swappo1 said:**
> Okay, when I initialize string[80] to:
```
char string[80]= '\0';
```
I get an error: invalid initializer.  If I use "\0" the program works and prints 15 for the length of the string.  Do I need to use"" for characters? and '' for integers?  Thanks for the help.

You can't say string[80] = '\0';. You can not initialize an char array to a character. Instead either do:

> 
char string[] = "Some constant string that can not be modified";
char string* = "Some constant string again";


Or

> 
for(int i = 0; i < 80; i++)
{
     string[i] = '\0';
}


I have not done C in a while so I may be off.

-r

---

### Post by jimi_hendrix on 2008-10-30
i am no C pro but cant you malloc(sizeof(pointer-to-string));?

---

### Post by samjh on 2008-10-30
> **jimi_hendrix said:**
> i am no C pro but cant you malloc(sizeof(pointer-to-string));?

Malloc does not initialise the allocated memory space, so it won't solve the OP's problem of having junk in his string. :)

---

### Post by isak84 on 2008-10-30
> **samjh said:**
> Malloc does not initialise the allocated memory space, so it won't solve the OP's problem of having junk in his string. :)

But calloc on the other hand does.

---

### Post by jimi_hendrix on 2008-10-30
> **isak84 said:**
> But calloc on the other hand does.

what does calloc do?

---

### Post by Can+~ on 2008-10-30
> **jimi_hendrix said:**
> what does calloc do?

Fill the reserved space with zeroes.

But that's just overkill, you can just set the first character of a string to '\0', if you need to start with an "empty" string.

The code doesn't add the finishing '\0' to the string, which probably causes to read more than it should, probably hitting a \r that wipes the content of the terminal, and finally getting to a \0 just by luck.

Why not just plain ol' scanf? Sure it has some oddities (not removing the trailing \n of the stdin) but gets the job done, or are you trying to avoid scanf?

---

### Post by dwhitney67 on 2008-10-31
To initialize a char array to nulls, use either of the following:
[php]
char string[80] = {'\0'};

/* or */

char string[80] = {0};
[/php]

Do which ever you think requires less typing.

As for reading in a string, you are doing it in an odd way... with getchar()?!

Try using fgets().  The use of scanf() to read in strings is frowned upon these days (that is, in the s/w industry), because it can lead to a stack corruption if the user enters a string that is longer than can fit in the declared char array.

Example of fgets():
[php]
char string[80] = {0};

printf("Enter a string: ");
fgets(string, sizeof(string), stdin);

// fgets will store the newline character entered by the user; remove it
*(strchr(string, '\n')) = '\0';

...
[/php]

---

### Post by dribeas on 2008-10-31
> **jimi_hendrix said:**
> i am no C pro but cant you malloc(sizeof(pointer-to-string));?

No you can't, and you can't calloc to get initialization either.

```

int *ip = new int[100];
char *cp = new char[20];

std::cout << sizeof(ip) << std::endl; // 4 (32 bits arch, or 8 for 64 bits)
std::cout << sizeof(cp) << std::endl; // same as above

```

sizeof applied to a pointer will give you the size of the pointer, not the size of the memory the pointer refers to.

---


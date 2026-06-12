---
title: "Curious with the string"
date: 2011-02-28
forum: Programming Talk
---

### Post by bennychenbc on 2011-02-28
Hi:
I am pretty new to C, and today I found something weird that I couldn't really find a solution on the web.

the code is as follows:

/This file is used to print names

#include <stdio.h>
#include <stdlib.h>

int main (void)
{
    char first_name[100];
    int count;

    printf("Please input your name\n");
    printf("First name:");
    fgets(first_name,100,stdin);


    for (count=0; count<100; count++)
    {
        if (&first_name[count]==0)
        {
            break;
        }
        printf("The character is %c\n",first_name[count]);

    }

}

when I print the string, I found out that the output was actually non zero value for the rest of the string that was suppose to be empty.

output:

Please input your name
First name:Yufei
The character is Y
The character is u
The character is f
The character is e
The character is i
The character is 

The character is 
The character is 
The character is m
The character is &#65533;
The character is &#65533;
The character is 
The character is 
The character is 
The character is 
The character is 
The character is 
The character is :
The character is 
The character is &#65533;
The character is 
The character is G
The character is &#65533;
The character is 
The character is &#65533;
The character is 5
The character is &#65533;
The character is &#65533;
The character is p

etc...

does anyone know why is the rest of the string pointing to random things?

---

### Post by ibuclaw on 2011-02-28
> **bennychenbc said:**
> 
    char first_name[100];

Is not initialised, so could be pointing to any garbage on the stack.

> **bennychenbc said:**
> 
if (&first_name[count]==0)

You shouldn't be testing the address, but the actual value.

```

if (first_name[count] == '\0')

```

Regards.

---

### Post by Peter76 on 2011-02-28
> **ibuclaw said:**
> Is not initialised, so could be pointing to any garbage on the stack.

Is that really what it is? Sounds like a fun project to use that for something.

---

### Post by ibuclaw on 2011-02-28
> **Peter76 said:**
> Is that really what it is? Sounds like a fun project to use that for something.

Uninitialised data (the use of) is one of the big causes of bugs, among other things. :)

---


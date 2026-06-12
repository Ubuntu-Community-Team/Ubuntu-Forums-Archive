---
title: "unable to pass character array in C in gdb"
date: 2014-05-20
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-20
Hello,
On running the following program on gdb, When I try and enter an input character array at the gets line, it doesn't take the array even after I press Enter.
In fact, the gdb prompt doesn't even return, and I'm forced to a Ctrl+c followed by quit to kill it.

How do I go about giving an input string?

```
#include <stdio.h>


int main(void)
{
 char* str;


 str = malloc(200 * sizeof(char));
 gets(str);


 printf("entered argument is : [%s]\n",str);


 return 0;
}
```


Thanks.

---

### Post by dwhitney67 on 2014-05-20
For starters, never use gets().  It it vulnerable to input buffer overruns should the user elect to enter more characters than those allocated (in your case, 200).  Instead of gets(), use fgets().  Also, it would be helpful if you presented a prompt to the user asking them to input data.

For example:
```

...

char name[200];    // note:  I would not waste time allocating such a small buffer.

printf("Enter your name: ");
fgets(name, sizeof(name), stdin);    // note: fgets() will retain the entered 'newline' if there is sufficient space in the buffer.

printf("Hello %s!\n", name);

...

```
As for not being able to debug your code using 'gdb', I have no idea why.  You did not indicate how you compiled your code, much less what steps you took to debug it, and afterwards what you did to interact with 'gdb'.

P.S.  In your original code above, you forgot to include <stdlib.h> for malloc(), and you forgot to call free() to deallocate the memory.  Oh the horror!

---

### Post by IAMTubby on 2014-05-21
> **dwhitney67 said:**
> For starters, never use gets().  It it vulnerable to input buffer overruns should the user elect to enter more characters than those allocated (in your case, 200).  Instead of gets(), use fgets(). 

Also, it would be helpful if you presented a prompt to the user asking them to input data.

P.S. In your original code above, you forgot to include <stdlib.h> for malloc(), and you forgot to call free() to deallocate the memory. Oh the horror! 
Thank you for the suggestions. Have modified code accordingly. Please see below. 
```

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
int main(void)
{
 char* name;
 name = malloc(200 * sizeof(char));


 printf("Please enter name : ");
 fgets(name,100,stdin);
 //gets(name);

 printf("entered name is : [%s]\n",name);

 free(name); 

 return 0;
}

```


> 
As for not being able to debug your code using 'gdb', I have no idea why.  You did not indicate how you compiled your code, much less what steps you took to debug it, and afterwards what you did to interact with 'gdb'.
I built my code as : gcc -g main.c and used gdb -tui a.out to enter gdb.
I then did **b main**, **r** (to run the code) and kept stepping using **s**
But when I reach the fgets line, after entering input string and hitting enter, nothing happens. It just stays there, and I have to do a Ctrl+c to come back to gdb prompt. I would have expected it to step to the next line. 

**I corrected it by hitting Ctrl+Enter after entering the input string, instead of just Enter(lucky guess),**

> For starters, never use gets()
I understand the advantage of using fgets and also understand that gets is bad.
But every time I make up my mind to use fgets, I'm put off by things like, fgets accepting the newline character(**'\n'**) at the end, when I'm actually using it to  stop taking input.
Is there any way to tell fgets to _not take_ the new line character at the end as part of input, apart from doing 
```
for(i=0;i<strlen(str);i++)
 if(str[i] == '\n'){str[i] = '\0'};
```

---

### Post by dwhitney67 on 2014-05-21
> **IAMTubby said:**
> ...

**I corrected it by hitting Ctrl+Enter after entering the input string, instead of just Enter(lucky guess),**

You should only have to use the 'Enter' key to terminate your input.  Also, use the 'n' (next) command for stepping through the code.  The 's' (step) command is useful when you want to step into a function.  It's unlikely you want to step into fgets(), printf(), etc.

> **IAMTubby said:**
> 
I understand the advantage of using fgets and also understand that gets is bad.
But every time I make up my mind to use fgets, I'm put off by things like, fgets accepting the newline character(**'\n'**) at the end, when I'm actually using it to  stop taking input.
Is there any way to tell fgets to _not take_ the new line character at the end as part of input, apart from doing 
```
for(i=0;i<strlen(str);i++)
 if(str[i] == '\n'){str[i] = '\0'};
```
Everybody has this same issue, thus you should not be put off by it.  Just deal with the nuance; perhaps even create a simple function to remove the newline.
```

void removeNewline(char* str)
{
    char* newline = strchr(str, '\n');

    if (newline) *newline = '\0';
}

```

---

### Post by IAMTubby on 2014-05-23
> **dwhitney67 said:**
> You should only have to use the 'Enter' key to terminate your input.  Also, use the 'n' (next) command for stepping through the code.  The 's' (step) command is useful when you want to step into a function.  It's unlikely you want to step into fgets(), printf(), etc.
dwhitney, sorry for the late reply.
But when I use just Enter(and step with n), I hit the same problem. This is what I get when I hit Enter twice and then hit Ctrl+Enter. As you can see, it keeps taking carriage returns.
(gdb) p str
$1 = 0x804b008 "hello\r\r"

> 
Everybody has this same issue, thus you should not be put off by it.  Just deal with the nuance; perhaps even create a simple function to remove the newline.
```

void removeNewline(char* str)
{
    char* newline = strchr(str, '\n');

    if (newline) *newline = '\0';
}

```
Thanks dwhitney, I shall start using it.

---


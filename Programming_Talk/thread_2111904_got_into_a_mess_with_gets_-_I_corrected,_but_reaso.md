---
title: "got into a mess with gets - I corrected, but reason ?"
date: 2013-02-03
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-03
Hello,
I have got myself into a tricky situation here.

I was doing something along these lines,
```

main()
{
 gets(name);
 system("ssh root@....); 
}

```
**problem :**the gets(name) part was not happening, and control would go directly to the system command. Upon coming back from ssh, the gets(name) part would happen.

**my fix : **
I did something like this to get it working   
```

while(!strlen(name))
{
 gets(name)
}

``` 
[i]
I was trying to replicate this in a simple example, but the example code was not giving the same problem, so posting the pseudo-code above.[/i]

I have few questions:
1) Why was the problem coming without the while loop ?
2) Why was it working when using scanf("%s",name); even without the while loop?
3) is it possible to get space seperated arguments using scanf ?
4) I was getting this,[b]/tmp/cc0868oR.o: In function `main':
main.c:(.text+0x634): warning: the `gets' function is dangerous and should not be used.
[/b], So people don't use gets ?

Thanks.

---

### Post by Bachstelze on 2013-02-03
Do not use gets(). Ever.

---

### Post by IAMTubby on 2013-02-03
> **Bachstelze said:**
> Do not use gets(). Ever.
Thanks Bachstelze, what would you suggest for getting string input ? **fgets(name,100,stdin) ?**

But the only reason why I have always felt hesitant to use it is because, the second argument asks for max length to be hardcoded. Shouldn't that be completely upto the user ?

Thanks.

---

### Post by Bachstelze on 2013-02-03
> **IAMTubby said:**
> 
But the only reason why I have always felt hesitant to use it is because, the second argument asks for max length to be hardcoded.

So what? The size of your buffer is hardcoded, either way. Just put the size of your buffer in the argument of fgets().

C is bad for interactive I/O. Take input as command-line arguments if at all possible.

---

### Post by IAMTubby on 2013-02-03
> **Bachstelze said:**
> So what? The size of your buffer is hardcoded, either way. Just put the size of your buffer in the argument of fgets().

Right Bachstelze, thanks and will start using fgets from today.

---

### Post by trent.josephsen on 2013-02-03
The easy/conventional method is
```
fgets(buffer, sizeof buffer, stdin);
```

This way you don't have extra magic numbers floating around. Don't forget to check the return value if an error could ruin your day, and keep in mind that if the user enters content longer than the buffer, the input will be split across two or more calls to fgets().

---

### Post by IAMTubby on 2013-02-03
> **trent.josephsen said:**
> Don't forget to check the return value if an error could ruin your day
Sure sir, shall take care of that.

> 
keep in mind that if the user enters content longer than the buffer, the input will be split across two or more calls to fgets().
I shall try this out and get back to you in some time.

Thanks.

---

### Post by IAMTubby on 2013-02-04
> **trent.josephsen said:**
> keep in mind that if the user enters content longer than the buffer, the input will be split across two or more calls to fgets().
Sir, I tried giving a longer input than the size of the buffer, but couldn't observe this behaviour. Or have I not understood your explanation ? Is the output as expected ? Following is the code and output.

**code**
```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 char* name;
 name = malloc(10 * sizeof(char));

 fgets(name,10,stdin);

 printf("\nthe name is : [%s]",name);

 return 0;
}

```

**input**
123456789123456789
(basically 18 characters, size of buffer == 10)

**output**
the name is : [123456789]

---

### Post by Bachstelze on 2013-02-04
> **IAMTubby said:**
> Sir, I tried giving a longer input than the size of the buffer, but couldn't observe this behaviour. Or have I not understood your explanation ? Is the output as expected ? Following is the code and output.

The additional calls to fgets() don't make themselves, of course... The system has no way to know whether or not additional input is available until you tell it to read it. And if it were to read the additional input, where would it store it?

---

### Post by trent.josephsen on 2013-02-04
Try this program to see what I meant:

```
#include <stdio.h>
int main(void)
{
    char buffer[10] = {0};
    do {
        printf("============================================================\n"
            "Enter at most 9 characters: ");
        fflush(stdout);
        fgets(buffer, sizeof buffer, stdin);
        printf("You entered: '%s'\n", buffer);
    } while (strcmp(buffer, "quit\n"));
    return 0;
}
```

It's supposed to echo each line of input back to the user for confirmation, and loop until the user types "quit". But if the user types 10 or more characters (counting the newline), the first call to fgets() will return only the first 9 characters, and each subsequent call will return the next 9 characters, until a newline is encountered. The program may appear to skip calls to fgets (because it doesn't wait for you to type) when in fact it's just continuing to process the previous line.

---

### Post by IAMTubby on 2013-02-09
> **trent.josephsen said:**
> 
It's supposed to echo each line of input back to the user for confirmation, and loop until the user types "quit". But if the user types 10 or more characters (counting the newline), the first call to fgets() will return only the first 9 characters, and each subsequent call will return the next 9 characters, until a newline is encountered. The program may appear to skip calls to fgets (because it doesn't wait for you to type) when in fact it's just continuing to process the previous line.
trent.josephsen, thanks a lot for the reply. I tried out the example you gave and I get it :)
PS : Sorry for the late response, I did not have access to a system last couple of days.

---


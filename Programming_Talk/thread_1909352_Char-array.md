---
title: "Char-array"
date: 2012-01-15
forum: Programming Talk
---

### Post by nmrod on 2012-01-15
#include <stdio.h>
#include <string.h>

int main() {
    char str_a[20];
    
    strcpy(str_a, "Hello, world!\n");
    printf(str_a);
    }

What does char_array2.c:8:2: warning: format not a string literal and no format arguments and
char_array2.c:9:2: warning: control reaches end of non-void function mean?

---

### Post by Bachstelze on 2012-01-15
For starters, never use strcpy(), always strncpy().
For the first warning, you shouldn't use string variables in printf() because a malicious user could exploit it (by passing a string that contains %n). Use puts() or printf("%s", str_a).
The third warning is because the main() function returns an int, but you have not specified a return value. Either add a return statement or compile in C99 mode (where main() implicitly returns 0 if no explicit return statement is given).

---

### Post by nmrod on 2012-01-15
how do I specify a return value, sorry for all the questions but I really want to learn how to program the write way.

---

### Post by Bachstelze on 2012-01-15
Just like in the code in your previous thread. ;)

---

### Post by nmrod on 2012-01-15
Would it look something like this.
#include <stdio.h>
#include <string.h>

int main() 
{ 
    char str_a[20];
    
    strcpy(str_a,"Hello, world!\n");
    puts(str_a[20]);
    }

---

### Post by Bachstelze on 2012-01-15
No, it's [font=monospace]puts(str_a)[/font], but puts() automatically adds a newline, so you probably don't want to include it in your string if you use it. You can also do [font=monospace]fputs(str_a, stdout)[/font] (which does not add a newline).

---

### Post by nmrod on 2012-01-15
I still don't understand I get the same error from a different program.:(
char_array2.c:10:2: warning: control reaches end of non-void function
#include <stdio.h>

int main() 
{
printf("The 'int' data type is\t\t %d bytes\n", sizeof(int));
printf("The 'unsigned int' data type is\t %d bytes\n", sizeof(unsigned int));
printf("The 'short int' data type is\t %d bytes\n", sizeof (short int));
printf("The 'long int' data type is\t %d bytes\n",sizeof(long int));
printf("The 'long long int' data type is %d bytes\n",sizeof(long int));
printf("The 'float' data type is\t%d bytes\n", sizeof(float));
printf("The 'char' data type is\t\t %d bytes \n", sizeof(char));

}

---

### Post by schauerlich on 2012-01-15
> **nmrod said:**
> I still don't understand I get the same error from a different program.:(
char_array2.c:10:2: warning: control reaches end of non-void function


Read the error message and try to piece it together. "Control reaches end of non-void function". Control reaching the end of the function means that the compiler has found a possible route through your code without hitting a return statement. Since the function is not void (it's declared as int main(), not void main()), this isn't allowed, so the compiler complains. Since void main() is not legal in ANSI C, you must return a value from main. The conventional value to return is 0 if nothing went wrong.

---

### Post by nmrod on 2012-01-15
Thankyou for the help I know I can be hard headed at times. I've written down everything for future reference.

---


---
title: "number input only (C language-gcc)"
date: 2007-10-18
forum: Programming Talk
---

### Post by mitchi on 2007-10-18
hi, i am trying to create a program wherein it only accepts numbers. when other characters/symbols are entered the program tells me that i have an invalid input. is this possible with c language using gcc.

i just dont know what parameter to put in the condition.

> 
if(**var==*???***)
{
number input correct
}
else
{
invalid input
}

---

### Post by slavik on 2007-10-18
well, depends on how you want to do input.

you can do scanf, or you can read a line into a buffer and then check it for invalid characters ...

look at ctype.h :) (for starters)

---

### Post by mitchi on 2007-10-18
of course, use scanf for input, but how can i complete the condition? what am i supposed to do, to be able compare or differentiate numbers from characters/symbols?

---

### Post by dwhitney67 on 2007-10-19
as slavik mentioned, look at ctype.h   (in /usr/include/ctype.h)

or just run this command:

[FONT="Courier New"]$ man isdigit
$ man isalpha[/FONT]

---

### Post by samjh on 2007-10-19
It depends on what var is.

If var is a string, then you can use ctype.h and its isdigit function to test whether each character in that string is a number.  The reason why you'll need to test each character is because the isdigit function only checks for values between 0 to 9.

So first of all, do: ```
#include <ctype.h>
```

Then after retrieving the input value into var using scanf, run loop through your string to check whether each character is a numeric digit using the isdigit function.

Example (pardon the crappy code):
```
#include <stdio.h>
// Need ctype.h for isdigit and isalnum functions.
#include <ctype.h>

int main(void)
{
	char var[10];    // This is the variable to store input.
	int i = 0;
	int varisnum = 0;    // Is var all numbers?  1 for yes, 0 for no.
	
	scanf("%s", var);

	while (isalnum(var[i]) != 0) {    // Loop until it a character is not alpha-numeric.
		if (isdigit(var[i]) != 0) {    // Is var[i] a numeric digit?
			varisnum = 1;
		} else {
			varisnum = 0;
			break;    // If we encounter a non-numeric character, there is no need to keep looping, so just break out.
		}
		i++;    // Move counter to the next element.
	}
	
	if (varisnum == 0)
		printf("Input was not all numbers.\n");
	else
		printf("Input was all numbers.\n");
	
	return 0;
}
```

---

### Post by gnusci on 2007-10-19
Here another code, it is similar to the code posted before by **samjh**, but I am aware that not whole the variable must be filled with data, so it scan for numbers while there are data in the string, here the code:

[PHP]
#include<stdio.h>
#include<ctype.h>


int is_number(char * pchar, int lnum){
    int i, is_num=0;
    for(i=0; i<lnum; i++){
        if(!isalnum(*pchar)) break;
        // printf("%c - ",*pchar);
        if(!isdigit(*pchar)){
            is_num++;
            break;
        }
        pchar++;
    }
    // printf("\nis_num = %i\n",is_num);
    return is_num;
}


int main(void){
    char num[50];

    printf("\n number: ");
    scanf("%s",num);

    if(!is_number(num,50)){
        printf("number input correct\n");
    }else{
        printf("invalid input\n");
    }
    return 0;
}

[/PHP]

---

### Post by slavik on 2007-10-19
```

int in_num;
scanf("%d", &in_num);

```

btw, never use scanf to read in a string ... you are just asking for a buffer overflow.

---


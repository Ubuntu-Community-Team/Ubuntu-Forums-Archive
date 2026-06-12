---
title: "in c, can scanf set strings?"
date: 2009-01-18
forum: Programming Talk
---

### Post by kapok on 2009-01-18
```

{
char input[20];  /*assuming it can't be longer than 20 characteres*/
scanf("%c", &input);
printf("%c", input);
}

```
doesn't work.
i've tried %s in place of the %c already.
is there a way for scanf to set strings?
or do i need to use a different input function?

---

### Post by Zugzwang on 2009-01-18
You need to use use the correct address to the char array:
```

#include <stdlib.h>
#include <stdio.h>
int main()
{
  char input[20];  /*assuming it can't be longer than 20 characteres*/
  scanf("%s", input);
  printf("%s", input);
}

```
"input" is an array, therefore just writing "input" refers to the address of its first element, so adding a "&" is not what you want.

---

### Post by eye208 on 2009-01-18
To make sure that your char buffer doesn't overflow, use scanf like this:
```
char input[20];
scanf("%19s", input); /* one char reserved for string terminator */
```
Up to 19 chars and a trailing '\0' will be stored in the buffer.

---

### Post by kapok on 2009-01-18
still doesn't work; here is the whole program with you're suggestions:

```

#include <stdio.h>
#include <stdlib.h>


/*i entered the math for the conversion as a different function*/
float celsius_to_fahrenheit_conversion( int x)
{
  return (((9.00/5)*x) + 32);
}
/**************************************************************/


/*and here is the main*/
int main()
{
  float x;
  char units[20];

  printf("please input a number followed by a space and 'celsius' to be converted to fahrenheit: " );
  scanf( "%f %19s", &x, units);    /*does the space actually matter when things are input?*/
  		
	if ( units == "celsius")    /*if the units input after a number and a space are celsius:*/
 	{
		printf("%f fahrenheit\n", celsius_to_fahrenheit_conversion( x )); /*convert them to fahrenheit using the function above, using the input number*/
		getchar(); /*i don't know what this little tid-bit does, but the program doesn't work without it*/
 	}  
}
  
```

it compiles with no errors, displays the "please input a number..." text, and lets you enter something, but after you enter it, the program stops and you are brought back to the terminal.

oh, and what does getchar(); do?

---

### Post by jespdj on 2009-01-18
```
if ( units == "celsius")
```
This is not how you compare strings in C. Do you know what this does? It checks if 'units' points to the same memory address of the string literal "celsius". This will always be 'false'.

Use the [strcmp()](http://en.wikipedia.org/wiki/Strcmp) function to compare strings:
```
if (strcmp(units, "celsius") == 0)
```
Note that strcmp returns 0 when the strings are equal.

[getchar](http://www.opengroup.org/onlinepubs/000095399/functions/getchar.html) (Google knows everything! ;) )

---

### Post by jimi_hendrix on 2009-01-18
> **kapok said:**
> oh, and what does getchar(); do?

gets 1 char of user input

---

### Post by kapok on 2009-01-18
thank you very much.

its odd that i can't find that information in any of the tutorials i have bookemarked. :/

thread = solved

---

### Post by Krupski on 2009-01-18
> **kapok said:**
> ```

{
char input[20];  /*assuming it can't be longer than 20 characteres*/
scanf("%c", &input);
printf("%c", input);
}

```
doesn't work.
i've tried %s in place of the %c already.
is there a way for scanf to set strings?
or do i need to use a different input function?

Are you trying to generate strings with the contents of variables?

If so, this should point your mind in the right direction:

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    char buffer[BUFSIZ];
    int num = 10; 

    sprintf(buffer, "I like the number %d\n", num); // generate a string
    fprintf(stdout, buffer); // print the string
    fflush(stdout);
    return(0); /* exit no error */
}

```


-- Roger

---


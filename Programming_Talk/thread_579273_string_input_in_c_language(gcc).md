---
title: "string input in c language(gcc)"
date: 2007-10-18
forum: Programming Talk
---

### Post by mitchi on 2007-10-18
im trying to input string in this program,

> 
#include<stdio.h>
#include<stdlib.h>

main()
{

char* enter;

system("clear");
printf("The power is currently turned OFF.\n");
printf("Please type \'on\' to turn ON the power.");
scanf("Press on");scanf("%s",&enter);


if(enter="on")
{
printf("The power is currently turned ON.\n");
}
else
{
printf("Wrong command.\n");
}

}


but both conditions executes the same output. Help please.

---

### Post by samjh on 2007-10-18
You're doing a few things wrong.

I've modified your code so it behaves correctly.  See the comments for explanation.  I've included style changes too, because you need to discipline yourself to use good style.
```
#include <stdio.h>
#include <stdlib.h>

/* Always specify the return variable type, 
and if your main method doesn't accept parameters, 
use void.  This is part of the C standard. */

int main(void)
{

	/* A string is an array of characters, not merely a character pointer.  
	In this case, you string will be at most 3 characters long, 
	requiring an array of 4 elements (from 0 to 3), with the fourth element 
	used for storing the EOL. */

	char* enter[3];

	system("clear");
	printf("The power is currently turned OFF.\n");
	printf("Please type \'on\' to turn ON the power.");

	/* Try not to have two statements in one line. */

	scanf("Press on");

	/* An array does not require & for scanf. */

	scanf("%s", enter);

	/* To compare a string with a value, use the strcmp function.  
	The strcmp function will return the value 0 if the string and the
	target value are equal. */

	if(strcmp(enter, "on") == 0)
	{
		printf("The power is currently turned ON.\n");
	}
	else
	{
		printf("Wrong command.\n");
	}

	/* Standard C requires the main() function to return an integer.
	Return value of 0 indicates a clean finish.
	Other return values indicate errors. */

	return 0;

}
```

---

### Post by weresheep on 2007-10-18
Hi,

Reading input directly with scanf is risky becuase you can never know what the user will type. A better approach might be to use fgets to read the whole line and then sscanf to pick out the bits your interested in.

Anyway, here is an updated version of your program that works using scanf.

-weresheep

```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/* Allocate enough space for the largest expected string +1 for \0. */
#define BUF_SIZE 3

int main(void) {
  char enter[BUF_SIZE];

  system("clear");
  printf("The power is currently turned OFF.\n");
  printf("Please type \'on\' to turn ON the power. ");

  /* Specify the maximum field (%2s) width for scanf so that it doesn't try
  to write more characters into our string than we've allocated space for. */
  if (scanf("%2s", enter) != 1) {
    /* Scanf did not match a string on the input line. */
    printf("Invalid input.\n");
  }
  else {
    if (!strcmp(enter, "on")) {
      printf("The power is currently turned ON.\n");
    }
    else {
      printf("Wrong command.\n");
    }
  }

  return 0;
}

```

---

### Post by mitchi on 2007-10-18
thanks samjh, the code worked. so i would just declare my variable as an array all the time? i just shifted from TurboC on Windows. Some of the functions are not working. Thanks for the help anyway.

---

### Post by bigboy_pdb on 2007-10-18
I think you might be missing what went wrong with your program in the if statement. When you wrote 'if (enter="on")', the program was trying assigning a value to the variable enter and then checking if that value evaluates to being true. Since your code was always assigning the variable "enter" the same value, the same block of the conditional statement was being visited.

To check if a variable that is a string is equivalent to another string you should use "strcmp(*var*, *string*)". It will return 0 if the variable *var* has the same characters as *string*.

---

### Post by gnusci on 2007-10-18
here some notes about your code:

[PHP]
#include<stdio.h>
#include<string.h> // <---- include string functions
#include<stdlib.h>

int main(void){

    char enter[10]; // <---- give a string size

    system("clear");
    printf("The power is currently turned OFF.\n");
    printf("Please type \'on\' to turn ON the power. \n Press on: ");
    scanf("%s",enter); // <---- without &

    // (enter="on") <---- it is wrong (enter = "on") boolean operation is (enter == "on")

    // strcmp(string1,string2) = 0 if string1 == string2
    //                         != 0 if string1 != string2
    if(!strcmp(enter,"on")){ 
        printf("The power is currently turned ON. \n");
    }else{
        printf("Wrong command. \n");
    }
    return 0;
}

[/PHP]

---


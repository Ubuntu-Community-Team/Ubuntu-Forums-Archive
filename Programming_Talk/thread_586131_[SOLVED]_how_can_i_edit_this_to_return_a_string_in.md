---
title: "[SOLVED] how can i edit this to return a string instead of integer(c language)"
date: 2007-10-22
forum: Programming Talk
---

### Post by nite owl on 2007-10-22
Hi I was hoping someone could tell me how I could edit this piece of code to return a string instead of integer, it keeps giving me the error message, incompatible types in assignment on line 40(which is the line of the function call).:

```
void get_field2rev(FILE *input, char ptr[], int width)
{
    int i;
    char returnValue[15];
    for(i=0;i<width;i++) ptr[i]=fgetc(input);
    ptr[i]='\0';

    return;
}

```

This is the calling function
```
record1.description = get_field2rev(tfile, str, 6);
```

and this is the prototype
```
void get_field2rev(FILE *input,  char ptr[], int width);
```

Any help would be great...thanks

---

### Post by Beggar on 2007-10-22
prototype should be

```
char* get_field2rev(FILE *input,  char ptr[], int width);
```

function should be 

```

char* get_field2rev(FILE *input, char ptr[], int width)
{
    int i;
    char returnValue[15];
    for(i=0;i<width;i++) ptr[i]=fgetc(input);
    ptr[i]='\0';

    return returnValue;
}

```

---

### Post by nite owl on 2007-10-22
```

char* get_field2rev(FILE *input, char ptr[], int width)
{
    int i;
    char returnValue[15];
    for(i=0;i<width;i++) ptr[i]=fgetc(input);
    ptr[i]='\0';

    return returnValue;
}

```[/QUOTE]

Hi thanks for the quick reply, I did make a mistake in that in the function the
 "char returnValue[15];".... isnt meant to be there, I accidentally didn't delete it before posting from when I was trying to get it to work?

---

### Post by Beggar on 2007-10-22
sorry, I didnt read through what you were doing, are you trying to return what you put into ptr?

---

### Post by nite owl on 2007-10-22
> **Beggar said:**
> sorry, I didnt read through what you were doing, are you trying to return what you put into ptr?

yes see what the function is doing(because I have left out the rest of the code) is reading into a text file and grabbing out a specific field from it; the field is however characters and not integers.

the text file is set out like this(each line on the text file is set like this); 5 18 drums

I have already organized 5 and 18 into record structure, I just need to grab drums now, but the function seems to be having errors because it isn't an integer so I am looking for some advice on how I could accommodate this.

---

### Post by slavik on 2007-10-22
am I missing something or could you accomplish your task with an fget() or an fread.

---

### Post by nite owl on 2007-10-22
> **slavik said:**
> am I missing something or could you accomplish your task with an fget() or an fread.

yes I could if I was simply trying to read the line. But what I am doing is feeding the text file through my program, organizing each of the fields into record structured format and then outputting to another file.

The fields being 5 18 drums; customerID, itemID and description respectively

---

### Post by slavik on 2007-10-22
then how about
```

#include <stdio.h>
#include <string.h>

...

FILE *file = fopen("data","r");
int custID, itemID;
char description[20];
fscanf("%d %d",&custID, &itemID);
fgets(description, 20, file);
if (description[strlen(description)] == '\n') description[strlen(description)] == NULL;

...

```

---

### Post by gnusci on 2007-10-22
here one small code with some ideas:

[PHP]
#include<stdio.h>


void get_field2rev(FILE *input, char ptr[], int width)
{
    int i;
    for(i=0;i<width;i++) ptr[i]=fgetc(input);
    ptr[i]='\0';
    //return; <--- no need, a void function does not return a value!
}

int main()
{
	char returnValue[15];
	FILE * file;
	
	file = fopen("number.txt","r");
	get_field2rev(file,returnValue,9);
	printf("value = %s\n",returnValue);
	
	return 0;
}
[/PHP]

the input file **number.txt** contains the line:

```

123456789

```

The program open and read the file and print the number read from the file.  know it is not exactly what you need but I think is a good starting point for your problem.

---

### Post by nite owl on 2007-10-22
Hi I have solved the problem. Thanks for all your help, If I ever get stuck on a problem this forum is always great for helping me out.

As this is a pretty specialised problem I am not posting the code in this post. But if anyone would like me to or is just curious I would be more then happy to post the working code :) Thanks again

---


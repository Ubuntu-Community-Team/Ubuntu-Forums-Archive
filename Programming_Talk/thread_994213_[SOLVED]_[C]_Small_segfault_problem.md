---
title: "[SOLVED] [C] Small segfault problem"
date: 2008-11-26
forum: Programming Talk
---

### Post by OutOfReach on 2008-11-26
I was practicing somethings that was discussed in a chapter in my C book.
Here is the code:
[PHP]
#include <stdio.h>
#include <ctype.h>
#include <string.h>

main()
{
    /* Appending on string to another with strcat() */
    char firstName[40], lastName[40];
    puts("Enter your first name: ");
    gets(firstName);
    puts("Enter your last name: ");
    gets(lastName);
    strcat(firstName, " ");
    strcat(firstName, lastName);
    printf("So your name is %s huh?\n", firstName);
    
    /* Using toupper() and tolower() */
    int userAnswer;
    printf("Are you sure you want to continue? ");
    userAnswer = getchar();
    getchar();   /* Discard the extra space left in the buffer. */
    if (toupper(userAnswer) == 'Y')
    {
        printf("Ok good.\n");
        printf("Erasing hard drive!\n");
        printf("Calm down, I'm joking.\n");
    }
    
    /* Using isalpha() and isdigit() */
    int userNumber;
    char userString[40];
    
    printf("Enter a number, any number! ");
    scanf(" %d", &userNumber);
    
    if (isdigit(userNumber))
    {
        printf("Ok, you can follow orders.\n");
    }
    
    printf("Now enter a string ");
    gets(userString);
    
    if (isalpha(userString))
    {
        printf("Your string contains alphabet characters.\n");
        
        if (isdigit(userString))
        {
            printf("It also contains numbers! Intriguing.\n");
        }
    }
    
    printf("Goodbye.\n");
    
    return 0;

}
[/PHP]

Yes, I understand that some of the concepts (such as defining functions) is a little outdated because the book im reading is from 1994. I plan on reading a more updated book from 2005 after this book.

Everything compiles fine (except a warning that gcc gives me about gets() being dangerous, if someone can explain that id be happy). But it segfaults

I used gdb to find the problem and this what it returns:
```

Program received signal SIGSEGV, Segmentation fault.
0x080486f7 in main () at FifteenthProgramStringFunc.c:68
68	    if (isalpha(userString))

```
Apparently the problem is with isalpha().

Any help is appreciated.

---

### Post by snova on 2008-11-26
Well, I don't know how this would equate to a segfault, but isalpha() is supposed to operate on characters, not strings.

---

### Post by doojsdad on 2008-11-26
> **OutOfReach said:**
> 

[php]
char firstName[40], lastName[40];
puts("Enter your first name: ");
gets(firstName); 
[/php]

Everything compiles fine (except a warning that gcc gives me about gets() being dangerous, if someone can explain that id be happy). 



Try inputting anything that occupies more memory than you are expecting and watch what happens (enter a name longer than 40 chars). There are many functions in C that have no bounds checking and you should avoid them if you can.

---

### Post by doojsdad on 2008-11-26
> **OutOfReach said:**
> 
[PHP]

    
    printf("Now enter a string ");
    gets(userString);
    
    if (isalpha(userString))
    {
        printf("Your string contains alphabet characters.\n");
        
        if (isdigit(userString))
        {
            printf("It also contains numbers! Intriguing.\n");
        }
    }
    
[/PHP]



Also, isalpha is expecting a single char value, and by supplying it with userString you are passing an address not a value. You need to go through a loop until the '\0' character for each index in userString and supply userString[index] to isalpha.

---

### Post by OutOfReach on 2008-11-26
Ahh I see, so isalpha() and isdigit() need to be used on characters.
Thanks guys I'll get it to work with a for loop.

[QUOTE=doojsdad]
Try inputting anything that occupies more memory than you are expecting and watch what happens (enter a name longer than 40 chars). There are many functions in C that have no bounds checking and you should avoid them if you can.[/QUOTE]

Interesting, now I see. I don't really like using scanf() though because it won't allow spaces.

---

### Post by doojsdad on 2008-11-26
> **snova said:**
> Well, I don't know how this would equate to a segfault, but isalpha() is supposed to operate on characters, not strings.

I think since the function is expecting 8 bits but OutOfReach is supplying it with many more it is going into "la la land". I'm surprised this isn't a compiler error for incompatible data types.

---

### Post by ubuser_7 on 2008-11-26
> Interesting, now I see. I don't really like using scanf() though because it won't allow spaces.

You can use fgets instead of gets/scanf.

---

### Post by OutOfReach on 2008-11-26
fgets looks interesting I will look into it, thanks for the suggestion.

---

### Post by doojsdad on 2008-11-26
> **OutOfReach said:**
> I don't really like using scanf() though because it won't allow spaces.

You could store a string with spaces (by whatever method you choose wisely) and then use sscanf to parse it.

---

### Post by geirha on 2008-11-26
You want to use fgets instead of gets.

```

char firstname[40];
fgets(fistname, 40, STDIN);

```
The above is safe since you set the maximum read size to 40. That will make it read at most 39 chars, and add a '\0' at the end.

Also, when using strcat, make sure the destination string can contain at least the length of both the strings you cat. In your case, you should make a third string, char fullname[80]; so it can hold up to 39 characters from firstname, 39 characters from lastname, the space in between and the terminating '\0'. Also consider using strncat which is safer than strcat in the same way fgets is safer than gets.

---

### Post by Nemooo on 2008-11-26
Another thing you should change is the declaration of main(). Since main always is returning a value to the OS to tell whether the program succeeded or not, main() should be declared as returning an integer value:

```
int main(void)
```

**void** to explicitly say that your program takes no arguments: [http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1043284376&answer=1044841143](http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1043284376&answer=1044841143)

---


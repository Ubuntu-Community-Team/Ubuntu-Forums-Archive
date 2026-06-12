---
title: "new c learner need help = how to use string.h ..."
date: 2007-09-09
forum: Programming Talk
---

### Post by AlexenderReez on 2007-09-09
please anybody expert here....how do i use this preprocessor /library to to change user input from capital letter to small latter or via versa like "i love programming "  to " I LOVE PROGRAMMING"....I hope you just give example and clue how do i define parameter ....how to i detect letter and do looping...

---

### Post by dwhitney67 on 2007-09-09
use the toupper() and tolower() functions (or are they macros?).

Basically, do something like this:

[PHP]#include <stdio.h>
#include <ctype.h>

int main()
{
  char myChar = 'a';

  printf( "uppercase %c is %c\n", myChar, toupper(myChar) );
}[/PHP]

---

### Post by dwhitney67 on 2007-09-09
This is a good question.  I personally cannot remember how to obtain just one character without blocking for the carriage return.

Here however is some code that might assist you (note, there is also a tolower() function/macro available):
[PHP]#include <stdio.h>
#include <unistd.h>
#include <ctype.h>

int main()
{
  while ( 1 )
  {

    char input[2];
    read(0, input, sizeof input);

    printf( "uppercase of %c is... %c\n", input[0], toupper(input[0]) );
  }
}[/PHP]
Perhaps someone else can lend you assistance on how to obtain just one character (keyboard strike) and then continue.

---

### Post by gnusci on 2007-09-09
I hope this code can be useful to you even that I did not use [COLOR="Red"]string.h[/COLOR], cause I built the two necessary functions:

[PHP]

#include <stdio.h>

void str_lw( char* s ){
   while( *s ){
      if( *s >= 'A' && *s <= 'Z' )
         *s += 32;
      s++;
   }
}

void str_up( char* s ){
   while( *s ){
      if( *s >= 'a' && *s <= 'z' )
         *s -= 32;
      s++;
   }
}

int main(void){
	char msg_mx[] = "I loVe PRoGRaMMiNG";
	char msg_up[] = "I LOVE PROGRAMMING";
	char msg_lw[] = "i love programming";
	
	str_lw(msg_up);
	printf("%s\n",msg_up);
	
	str_up(msg_lw);
	printf("%s\n",msg_lw);
	
	str_lw(msg_mx);
	printf("%s\n",msg_mx);

   return 0;
}
[/PHP]

---

### Post by Compyx on 2007-09-09
Unfortunately, all the above programs have errors in them.

First of all, tolower() and toupper() take an int as an argument which has to be an unsigned char value, so the correct way to call these functions is:

```

#include <stdio.h>
#include <ctype.h>

int main(void)
{
    char myChar = 'a';

    printf("The upper case of '%c' is '%c'\n", myChar, toupper((unsigned char)myChar));

   return 0;
}

```

Also, using a construct such as:
```

if (ch >= 'a' && ch <= 'z')

```
is non-portable since it assumes ASCII, which is why functions such as tolower(), isalpha() exist.

The C standard only guarantees that the digits '0' through '9' are sequential (not sure that's the proper English term for it), that is: '1' follows '0' in the character set and '2' follows '1', and so on.

So assuming a char having a digit in it ('0'-'9'), it can be converted to an integer by doing something such as this:
```

char ch = '3';
int i = ch - '0';

```
but this would be non-portable again:
```

char ch = '3';
int i = ch - 0x30;

```
since it assumes ASCII (where '0' is 0x30 (48 decimal)).


I know this all seems like nitpicking, but if you want to learn C, you might as well learn to do it proper. ;)

---

### Post by eph1973 on 2007-09-09
```
#include <stdio.h>
#include <ctype.h>

#define MAX 100

int main()
{
    int c, i;
    int string[MAX];

    printf("Enter a string: ");
    for(i = 0; (c = getchar()) != '\n' && c != EOF && i < MAX; i++){
        string[i] = c;
    }
    string[i] = '\0';   
    printf("Your string in lower case is '");
    for(i = 0; string[i]; i++){
        putchar(tolower(string[i]));
    }
    printf("'\n");
    return 0;
}
```In this example, it uses the library function tolower() from <ctype.h> to lower the case of the input string.  The first for loop gets the input from the user, and stores it in the array.  It checks to see if it has reached the end of the string (the '\n' character), an end of file input, or the maximum range of the string.  The second loop puts each character in turn back onto the screen after the tolower() function from <ctype.h> has turned it into a lower case letter.  There is also a toupper() function from <ctype.h> that will do the reverse.

Note that <string.h> does not have a function to change the case of a string.  It has a number of other things it can do with strings, such as comparing them, concatenating them,  and  copying them.  To  change the case, you would have to go through each character of the string and use <ctype.h> or build your own function, like gnusci did, to change the case of each letter.

If you are asking how to change the case of a letter as someone is typing it, that answer is a little bit more complex.

---

### Post by gnusci on 2007-09-09
> **Compyx said:**
> Unfortunately, all the above programs have errors in them.

> First of all, tolower() and toupper() take an int as an argument which has to be an unsigned char value, so the correct way to call these functions is:

[code]
#include <stdio.h>
#include <ctype.h>

int main(void)
{
    char myChar = 'a';

    printf("The upper case of '%c' is '%c'\n", myChar, toupper((unsigned char)myChar));

   return 0;
}


I think you did not understand thread, he said:

> I hope you just give example and clue how do i define parameter ....how to i detect letter and do looping...

It is mean he wants some hints no that somebody has to solve the problem, I just wanted to show him some ideas. But anyway here is a proper code:

[PHP]

#include <stdio.h>
#include <ctype.h>

void str_lw( char* s ){
   while( *s ){
		*s = tolower((int)*s);
		s++;
   }
}

void str_up( char* s ){
   while( *s ){
		*s = toupper((int)*s);
		s++;
   }
}

int main(void){
	char msg_mx[] = "I loVe PRoGRaMMiNG";
	char msg_up[] = "I LOVE PROGRAMMING";
	char msg_lw[] = "i love programming";
	
	str_lw(msg_up);
	printf("%s\n",msg_up);
	
	str_up(msg_lw);
	printf("%s\n",msg_lw);
	
	str_lw(msg_mx);
	printf("%s\n",msg_mx);

   return 0;
}
[/PHP]

The above code can be realized from the two first answers.

BTW: You make a big mistake what you said:

> First of all, tolower() and toupper() take an int as an argument which has to be an unsigned char value

The right argument for tolower() and toupper() is and [COLOR="Red"]int[/COLOR] cause is completely necessary for another purposes that maybe you don't know, anyway better learn to programing before to pretend to be a master.

[http://www.cplusplus.com/reference/clibrary/cctype/tolower.html](http://www.cplusplus.com/reference/clibrary/cctype/tolower.html)

---

### Post by AlexenderReez on 2007-09-09
to all gurus,**[COLOR="Blue"]thanks a lot....[/COLOR]**


but i need time to understand the difference between those difference guide....i'm really new to c ...but again...thanks a lot....

i will ask if i don't understand....

---

### Post by AlexenderReez on 2007-09-09
actually i want to make program like


running
> 
enter your sentences
= i like programming

uppercase of
i like programming

is
I LIKE PROGRAMMING
is it possible ?

can i make like this


is it possible to make like this ?
> 
#include <stdio.h>
#include <unistd.h>
#include <ctype.h>

int main()
{
int loop = 1;
while ( loop == 1 )
{

char input[2];
printf ("\nprintf enter your sentences\n");
read(0, input, sizeof input);
if( ) //don't sure how to make?
{
loop = 0;
}
printf( "\nuppercase of \n %c \n are... %c\n", input[0], toupper(input[0]) );
}

__________________

---

### Post by AlexenderReez on 2007-09-09
done !!


thnaks all especially **gnusci** :)


> #include <stdio.h>
#include <ctype.h>

void str_lw( char* s ){
   while( *s ){
        *s = tolower((int)*s);
        s++;
   }
}

void str_up( char* s ){
   while( *s ){
        *s = toupper((int)*s);
        s++;
   }
}

int main(void){
    char msg_mx[1000] /*= "I loVe PRoGRaMMiNG"*/;
    char msg_up[1000] /*= "I LOVE PROGRAMMING"*/;
    char msg_lw[1000] /*= "i love programming"*/;
    
printf("please neter your sentence\n ");
 fgets ( msg_lw,1000, stdin );  
    

//str_lw(msg_up);
   // printf("%s\n",msg_up);
    
    str_up(msg_lw);
    printf("%s\n",msg_lw);
    
  //  str_lw(msg_mx);
  //  printf("%s\n",msg_mx);

   return 0;
}  

---


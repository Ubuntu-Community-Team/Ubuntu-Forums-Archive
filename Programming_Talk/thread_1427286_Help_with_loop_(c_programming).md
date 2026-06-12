---
title: "Help with loop (c programming)"
date: 2010-03-11
forum: Programming Talk
---

### Post by devaj on 2010-03-11
Hi all,
C programming newbie here.
I have created a program which I would like to to display the error message as specified by printf and not end with it.I would like the program to ask for the user's input again if the user inputs a invalid option like special characters or alphabets.
(I know I have to use a loop to get the desired result but am not able to solve it.)
The same program can be written with else-if but I would be really grateful if anyone could help me get the solution with switch-case,giving me some basic idea.
Thank you.
Here is the code:


#include <stdio.h>

int main ()

{

char c;

printf ("press 1 for breakfast.\npress 2 for lunch.\npress 3 for dinner.\npress 4 to quit.\n");

c=getchar ();

if ((c>='a') && (c<='z') || (c>='A') && (c<='Z'))

printf ("no alphabets allowed.\n");

switch (c)

{

case '1':

printf ("breakfast.\n");

break;

case '2':

printf ("lunch.\n");

break;

case '3':

printf ("dinner.\n");

break;

case '4':

printf ("thank you.\n");

break;

default:

printf ("not a valid option.\n");

}

return (0);

}

---

### Post by Bachstelze on 2010-03-11
You can use a while loop for that. Here's one way to do it in pseudocode:

```
ask user for input
while c is non-valid
    print error message
    ask user for input
your switch goes here
```

---

### Post by n0dix on 2010-03-11
Switch statement compare int values and not char values.
[Wikipedia doc]("http://en.wikipedia.org/wiki/Switch_statement#C.2C_C.2B.2B.2C_Java.2C_php.2C_ActionScript").
In your program is more easy compare with integer instead of character.

---

### Post by Bachstelze on 2010-03-11
> **n0dix said:**
> Switch statement compare int values and not char values.

A char can be losslessly converted to an int. Using switch on chars is surefine.

---

### Post by falconindy on 2010-03-11
> **n0dix said:**
> Switch statement compare int values and not char values.
[Wikipedia doc]("http://en.wikipedia.org/wiki/Switch_statement#C.2C_C.2B.2B.2C_Java.2C_php.2C_ActionScript").
In your program is more easy compare with integer instead of character.
Incorrect. A char is valid for a switch block. It's simple a 1 byte numerical field. Changing to an int in this case won't change anything.

Bach has the right idea of catching the user's input in a while loop until it validates, and **then** moving on to the switch.

---

### Post by n0dix on 2010-03-11
> **Bachstelze said:**
> A char can be losslessly converted to an int. Using switch on chars is surefine.

Sorry for my wrong affirmation. I've been lost my C skills. :lolflag:

---

### Post by devaj on 2010-03-11
Thank you all for all your prompt replies.
I used while as [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") suggested and the code compiles without any errors but the output ends like it did earlier.
And whenever I input an alphabet or special character the program is caught in an endless loop which it didn't use to do earlier (have to use Ctrl+C to end it.)
I would be thankful if someone could tell me what am I doing wrong.

#include <stdio.h>

int main ()

{

char c;

printf ("press 1 for breakfast.\npress 2 for lunch.\npress 3 for dinner.\npress 4 to quit.\n");

c=getchar ();

[COLOR=DarkGreen]while ((c>='a') && (c<='z') || (c>='A') && (c<='Z'))

printf ("no alphabets allowed.\nplease try again.\n");

c=getchar ();[/COLOR]  

switch (c)

{

case '1':

printf ("breakfast.\n");

break;

case '2':

printf ("lunch.\n");

break;

case '3':

printf ("dinner.\n");

break;

case '4':

printf ("thank you.\n");

break;

default:

printf ("not a valid option.\n");

}

return (0);

}

---

### Post by Compyx on 2010-03-11
All the while statement does is repeat the single line that comes after it.

Change to:

```

while (isalpha(c)) {
    puts("No alphabets allowed");
    c = getchar();
}

```
(you'll need to #include <ctype.h> to use isalpha() and friends)

And change the declaration of c to 'int c;': getchar() returns an int, not a char, that way you can check the return value of getchar() against EOF which signals either end-of-file or an error condition.

---

### Post by ApEkV2 on 2010-03-11
@ OP, you should use code tags.
Here's my example
```
#include <stdio.h> 

void main(void)
{
     int c;
     while ((c = getchar()) != EOF)
     {
          switch (c)
          {
               case '1':
                    printf("1\n");
                    break;
               case '2':
                    printf("2\n");
                    break;
               default:
                    break;
          }
     }
}
```

---

### Post by devaj on 2010-03-11
Thank you all for your valuable input.
Though the problem wasn't solved but it gave me a fairly big idea how to proceed.
It also gave the insight that I still have a long way to go.
Thank you all for your precious time.
May all of you have good life.
GOD bless all.

---


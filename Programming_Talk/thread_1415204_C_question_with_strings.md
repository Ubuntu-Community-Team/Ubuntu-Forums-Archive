---
title: "C question with strings"
date: 2010-02-24
forum: Programming Talk
---

### Post by hakermania on 2010-02-24
Hi, I would like to ask you how do strings work...
I have made this program:
```
#include <stdio.h>
#include <string.h>

int main()
{
   int a, s2;
   char s1[256];
   char s3[256];
   printf("     Choose what do you wanna do:\n 1=Answer to a retorical question\n2=Answer to a mathematical question\n 3=Answer to a computer's question\n:");
   scanf("%d",&a);
   if (a == 1);
   {printf("Na zei kaneis h' na mhn zei?\n");
       scanf("%c",s1);
if (s1 = "na zei");
       printf("Kai gt na zei parakalw?\n");
       else if (s1 = "na mhn zei" );
       printf("Psofos!!!\n");
       else printf("     ERROR\n\n");}
else if (a = "2");
   {printf("Poso mas kanei 2 + 2?\n");
      scanf("%d",s2);
       if (s2 = 4);
         printf("Swsta\n");
       else printf("La8os\n");}
else if (a = "3");
   {printf("Geia, eimai to pc su.Me exeis talaipwreisei poly! To 3ereis?\n");
      scanf("%c",s3);
       if (s3 = "3erw" );
           printf("Pali kala, gt mu exeis bgalei thn pisth!!!\n");
       else if (s3 = "den 3erw" )
           printf("kala 8a kaneis na ma8eis!\n");
       else printf("Eimai to pc su kai den katalaba ti mu apanthses!!!\n");}
else printf("Den edwses ute 1 ute 2 ute 3.3anaprospa8hse se parakalw!\n");

    return ;
}
```
Em......I know that does not work at all.
Can you please tell me how is this supposed to work?:confused:??

---

### Post by JDShu on 2010-02-24
First thing that jumps out to me is that for comparisons, use "==" not "=". You're assigning in the if statement when you're supposed to be comparing.

EDIT: ok.. I just realized there more than that... you ended your if statements prematurely, a is an integer when you're comparing it to a string, and you can't compare strings in the first place in C. You need to use strcmp() or something.

---

### Post by Barrucadu on 2010-02-24
You can't check for string equality like that, you have to use strcmp() (or strncmp()).

And what's with all the extra semicolons? (eg: "if (s1 = "na zei");")

---

### Post by Xyro on 2010-02-24
scanf("%c",s1);

This reads in a single character, not a string. You want:

scanf("%s",s1);

Since this is not safe, you should avoid using scanf(). However, for learning it is fine. No one will hack your system and perform a buffer overflow attack with your test program...

Edit:
> **Barrucadu said:**
> ...And what's with all the extra semicolons? (eg: "if (s1 = "na zei");")

Yea, you've got a whole swack of extra semicolons and unbalanced parenthesis. Remember, if you open it  '(,{,[' you've gotta close it '),},]'.


Try this: (may have errors, did a quick once over for obvious mistakes...)

```

#include <stdio.h>
#include <string.h>

int main()
{
   int a, s2;
   char s1[256];
   char s3[256];
   printf("     Choose what do you wanna do:\n 1=Answer to a retorical question\n2=Answer to a mathematical question\n 3=Answer to a computer's question\n:");
   scanf("%d",&a);
   if (a == 1) {
      printf("Na zei kaneis h' na mhn zei?\n");
      scanf("%s",s1);
      if ( strcmp(s1, "na zei") == 0 )
         printf("Kai gt na zei parakalw?\n");
      else if ( strcmp( s1, "na mhn zei") == 0 )
         printf("Psofos!!!\n");
      else
         printf("     ERROR\n\n");
   }
   else if (a == 2) {
      printf("Poso mas kanei 2 + 2?\n");
      scanf("%d",&s2);
      if (s2 == 4)
         printf("Swsta\n");
      else
         printf("La8os\n");
   }
   else if (a == 3) {
      printf("Geia, eimai to pc su.Me exeis talaipwreisei poly! To 3ereis?\n");
      scanf("%s",s3);
      if ( strcmp(s3, "3erw") == 0 );
         printf("Pali kala, gt mu exeis bgalei thn pisth!!!\n");
      else if ( strcmp(s3, "den 3erw") == 0 )
         printf("kala 8a kaneis na ma8eis!\n");
      else
         printf("Eimai to pc su kai den katalaba ti mu apanthses!!!\n");
   }
   else printf("Den edwses ute 1 ute 2 ute 3.3anaprospa8hse se parakalw!\n");

   return 0;
}

```

---

### Post by Some Penguin on 2010-02-24
> **hakermania said:**
> Hi, I would like to ask you how do strings work...
I have made this program:
```
#include <stdio.h>
#include <string.h>

int main()
{
   int a, s2;
   char s1[256];
   char s3[256];

```

Your life will be easier if you develop good habits re: variable naming.

If you were reading code and s1 and s3 were declared as character arrays of one particular size, would you expect s2 to be an integer?  Probably not...

> ```

   printf("     Choose what do you wanna do:\n 1=Answer to a retorical question\n2=Answer to a mathematical question\n 3=Answer to a computer's question\n:");
   scanf("%d",&a);

```

Something to consider:  inputs that aren't numbers.

```
> 
   if (a == 1);

```

This isn't Bourne shell.   That semicolon is not only unnecessary, it leads to behavior radically different than what you want.

Vaguely related recommendation:  add -Wall to your compilation flags.  Read the warnings.  Look them up and understand them.

```
> 
   {printf("Na zei kaneis h' na mhn zei?\n");
       scanf("%c",s1);
if (s1 = "na zei");

```

-Wall would have told you that you shouldn't do that.

strncmp, stricmp, strcasecmp...

Etc.

---

### Post by hakermania on 2010-02-26
All in all what I wanna do is to check the user's answer and then if he/she answered the one thing to do this and if he/she answer the other thing to do the other.how do I "compare" strings? Em...How do I use strcmp() and strncmp()?And what could I use except of scanf?

---

### Post by MadCow108 on 2010-02-26
manpages are your friend (if you installed devhelp)
man strcmp
man strncmp

```

if (strncmp(string1, string2, max_length_to_compare) == 0) 
{
printf("zero means equal")
}

```

instead of using scanf, you can write your own function parsing your input
if that makes any sense depends on the problem, often scanf is the way to go.

---

### Post by dwhitney67 on 2010-02-26
For reading strings from the user, fgets() is preferred versus scanf().

fgets() permits the programmer to specify the maximum bytes to read from stdin, thus mitigating the overrunning of a buffer.

Example:
```

char input[80];

printf("Enter something: ";
fgets(input, sizeof(input), stdin);

/* NOTE:  fgets() may insert a newline character into the
          buffer.  You will have to remove this character
          should its presence not be desired/required.

          fgets() will always null-terminate the buffer.
*/

/* to remove the a newline character from the buffer */
char *nl = strchr(input, '\n');

if (nl) { *nl = '\0'; }

```
Read the manpage for fgets() for more details.

---

### Post by hakermania on 2010-02-27
Guys, I have to say that you do great work here! I understood everything.Thank you thank you and thank you

---


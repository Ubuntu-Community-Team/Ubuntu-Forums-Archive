---
title: "buffer problem (i think) only on my ubuntu system"
date: 2011-09-14
forum: Programming Talk
---

### Post by MJClark505 on 2011-09-14
I'm writing a simple C program to test a macro and a function. I used a menu to allow the user to select either the macro, the function or Quit. After the first selection, the menu runs twice, not waiting for user input but instead apparently ignoring the fflush and grabbing something from the buffer that shouldn't be there (return char?) 

The program compiles and runs perfectly when I scp it to my school's solaris system.
I need to get this problem fixed so that I can confidently code and compile on my own system ( I wont have access to the school's ssh forever). This is a relatively fresh Ubuntu install, gcc is up to date and the only other software that might conflict is a Mono Develop installation used for my C# class. 

Here is the typescript of the problem including the code. 

```
Script started on Wed 14 Sep 2011 01:07:43 PM EDT
megan@ubuntu:~/workspace/cprog/week2/assn2$ gcc main.c
megan@ubuntu:~/workspace/cprog/week2/assn2$ ls
a.out  main.c  typescript
megan@ubuntu:~/workspace/cprog/week2/assn2$ ./a.out
Do you want to test the (M)acro, the (F)unction or (Q)uit: m
Enter a number to be tested with the macro: 23
The absolute value of 23 is 23.
Do you want to test the (M)acro, the (F)unction or (Q)uit: Error in switch.Do you want to test the (M)acro, the (F)unction or (Q)uit: f
Enter a number to be tested with the function: -23
The absolute value of -23 is 23.
Do you want to test the (M)acro, the (F)unction or (Q)uit: Error in switch.Do you want to test the (M)acro, the (F)unction or (Q)uit: q
megan@ubuntu:~/workspace/cprog/week2/assn2$ exit
exit

Script done on Wed 14 Sep 2011 01:08:10 PM EDT
/*
 * Name:  Megan Clark
 * Date:  09/13/2011
 * Assignment:  PS Assn2
 * Purpose: Create a macro and a function
 * to determine the absolute value of a 
 * given number.
 */
 
#include <stdio.h>

#define ABS(a) (a) < 0 ? -(a) : (a)

int abs_val(int num);
int getInt(char type[]);
char menu(void);

int 
main (void)
{
  int num, test, done = 0;
  char macro[6]="macro", func[9] = "function", sel;
  
  while(!done)
  {
    sel = menu();
    switch(sel){
      case 'M':
        num = getInt(macro);
        printf("The absolute value of %d is %d.\n", num, abs(num));
        break;
      case 'F':
        num = getInt(func);
        test = abs_val(num);
        printf("The absolute value of %d is %d.\n", num, test);  
        break;
      case 'Q':
        done = 1;
        break;
      default:
        printf("Error in switch.");
        break;
    } // end SWITCH
  } // end WHILE
  
  return 0;
} // end MAIN

/*
 * Functions
 */
int abs_val(int num)
{
 if (num < 0)
   num = 0 + -num;
 return num;
}
int getInt(char type[])
{
  int num;
  printf("Enter a number to be tested with the %s: ", type);
  scanf("%d", &num);
  fflush(stdin);
  return num;
}
char menu(void){
  char sel;
  printf("Do you want to test the (M)acro, the (F)unction or (Q)uit: ");
  sel = getchar();
  fflush(stdin);
  sel = toupper(sel);
  return sel;
}
```

---

### Post by Seq on 2011-09-14
The behaviour of fflush on an input stream is undefined, and it would appear unimplemented in GCC in accordance with that.

[http://www.gidnetwork.com/b-57.html](http://www.gidnetwork.com/b-57.html)

---

### Post by Senesence on 2011-09-14
As Seq said - it's undefined.

Use this function instead:

[php]
void input_flush(){
    while(getchar() != '\n')
        ;
}
[/php]

"getchar" removes a character from the input buffer, so if you keep doing it, it will clear it.

---

### Post by Seq on 2011-09-14
> **Senesence said:**
> As Seq said - it's undefined.

Use this function instead:

[php]
void input_flush(){
    while(getchar() != '\n')
        ;
}
[/php]

"getchar" removes a character from the input buffer, so if you keep doing it, it will clear it.

The problem with that is if you don't have anything in your input buffer, it will hang until something is. It should work for the menu, since if you enter a single char 'm', it puts two chars in stdin "m\n". So read one character, flush until \n, and you're good.

If you want to ditch sscanf, you need to do a bit more work. Here is a sample that doesn't do everything you need (doesn't do negative numbers, etc). This will read an entire line, fetching all digits and using them in the number ("2 3 4 a 5 \n" would be 2345. Not necessarily the best).

```

int getInt(char type[])
{
  int num=0;
  char sel;
  printf("Enter a number to be tested with the %s: ", type);
  while ( sel = getchar() )
      if ( sel == '\n' )
          return num;
      else if ( sel >= '0' && sel <= '9' )
          num = (num*10) + (int)(sel-'0');
}

```

As you can see, it is not as nice to look at as as a single 'sscanf'. It has also been a while since I've done C, so perhaps there are some better methods to clear the input buffer without hanging when it is empty.

---

### Post by dwhitney67 on 2011-09-14
> **Seq said:**
> 
```

int getInt(char type[])
{
  int num=0;
  char sel;
  printf("Enter a number to be tested with the %s: ", type);
  while ( sel = getchar() )
      if ( sel == '\n' )
          return num;
      else if ( sel >= '0' && sel <= '9' )
          num = (num*10) + (int)(sel-'0');
}

```


@ Seq -

The code above is far from perfect (and is missing a return statement), thus I cannot understand why you even posted it.

Do you really consider "123abc456\n" to be valid input for a number?  What about with an input of "abc\n"?  This is certainly not the same as if the user entered "0\n".

Anyhow, sscanf() is a practical function to use for performing post-analysis of an entire line of input that has be entered by a user.  You got to know how to parse the string, and also to verify that the proper number of fields were found.

The safest bet to capture user input is to use fgets().  Don't even trust scanf() for numbers.

---

### Post by Seq on 2011-09-14
> **dwhitney67 said:**
> @ Seq -

The code above is far from perfect (and is missing a return statement), thus I cannot understand why you even posted it.

It returns on '\n', which should be at the end of any input line. I suppose it should check for EOF causing the buffer to fill without an EOL, and it would be nicer form to have the 'return' at the bottom of the function, but that's a style thing.

> **dwhitney67 said:**
> Do you really consider "123abc456\n" to be valid input for a number?  What about with an input of "abc\n"?  This is certainly not the same as if the user entered "0\n".

No, which is why I made a note of that behaviour. It could just as easily have stopped including input at the first non-digit character (like sscanf), and just read to the next '\n', or kept looping for more lines until it was sure it had seen at least one digit.

It has been a number of years since I've really done anything in C (I believe I noted that, but if not I should have), and I can't even remember most functions available. Hopefully nobody expected me to write perfect code covering all edge cases in 25 minutes while on lunch break.

> **dwhitney67 said:**
> The safest bet to capture user input is to use fgets(). Don't even trust scanf() for numbers. 

That is indeed a much better option. Read the line at once, iterate over the char[] until you've got some digits, loop if you didn't get any.

I'd write a sample, but I wouldn't be posting it here.

---

### Post by gardnan on 2011-09-14
Well, for what it's worth, I will give my way of obtaining raw user input. Of course, there is probably some buffer overflow error you can yell at me for in here somewhere (it is, after all, C), but it works for me in general.
```
#include<stdio.h>
#include<string.h>
int
main (int argc, char **argv)
{
  char *c;
  char string[20];
  fgets(string, 20, stdin);
  if((c=strchr(string, '\n')) == NULL)
    {
      while(getchar() != '\n');
    }
  else
    {
      *c = '\0';
    }
  fputs(string, stdout);
  fgets(string, 20, stdin);
  fputs(string, stdout);
  return 0;
}

``` The second fgets is just to show that the input buffer is empty and will not fill the buffer with unwanted data. After you get the raw input (I assumed, perhaps incorrectly, you did not want the newline), you can parse the string using sscanf or a custom parser like the one you posted. 

P.S. As far as I know, this code is secure, but if someone sees an error, I would be grateful for a fix.

---


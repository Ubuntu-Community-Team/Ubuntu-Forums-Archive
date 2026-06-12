---
title: "weird program execution after compiling"
date: 2008-04-10
forum: Packaging and Compiling Programs
---

### Post by kb1lqd on 2008-04-10
Hey everyone,
     Im learning C right now, Ive gotten basic programs to compile under my ubuntu 7.10 but once I began using while loops and such, the program compiled fine, but I got really wierd output from the program... repeated text lines, unrecognized variables.... I compiled them using both cc and gcc.... I've attached a screenshot of some of the output....

By the way, the code is correctly written, and runs fine on my schools computer labs running solaris... I'm happy to provide more info so just ask!

PS) In the screenshot, the word "madam" should have been recognized as a palindrone but wasnt... I used a printf() to display each character that was recognized by the program from the user and it only printed "mada".... its not recognizing the last charecter... and if you switch variables around things get real dicy and do not act as if they were simply switched around, but instead a random order....

---

### Post by jpkotta on 2008-04-10
You should post your code and the command you use to compile.

---

### Post by kb1lqd on 2008-04-10
> 
# include <stdio.h>
# include <stdlib.h>

/*--------------------------- main function --------------------------------
Purpose:Determine if the word or number input from the user is a palindrome
Returns:EXIT_SUCCESS signal to OS
----------------------------------------------------------------------------*/
# include <stdio.h>
# include <stdlib.h>

int main( )
{
   int done, num, num1, num2, num3, num4, num5;
   char input, ch1, ch2, ch3, ch4, ch5;



   done = 0;

   while(!done){
      printf("Please enter 'n' for a number, a 'w' for a word, or 't' to end the
 program: ");
      scanf("%c", &input);
      fflush (stdin);

      if( input == 't')
         done = 1;

      else if (input == 'n'){
         printf("Please enter a 5 digit number: ");
         scanf("%d", &num);
         fflush(stdin);

         num5 = num % 10;
         num4 = (num/10) % 10;
         num3 = (num/100) % 10;
         num2 = (num/1000) % 10;
         num1 = (num/10000) % 10;
            if ( num1 == num5 && num2 == num4)
               printf("This number is a palindrome!\n");
            else
               printf("This number is not a palindrome\n");
        }

      else if (input == 'w'){
         printf("Please enter a 5-letter word: ");
         scanf("%c%c%c%c%c", &ch1, &ch2, &ch3, &ch4, &ch5);
         fflush (stdin);
         if (ch1 == ch5 && ch2 == ch4)
            printf("This word is a palindrome!\n");
         else
            printf("This word is not a palindrome!\n");
         }
      else
         printf("Incorrect input!, please try again\n");

      }
      printf("******TERMINATED******\n");


   return (EXIT_SUCCESS);
}



The file is called "palin.c"
I used "cc palin.c"
then to run the program "./a.out"

PS) I realize looking now that I have two headers (Repeated the #include)... would that possible be a problem?

---

### Post by jaddle on 2008-04-10
I'm not positive, but I expect there's an issue with the linefeed (when you press enter) after the first scanf ends up as ch1 in the letters scanf. Basically, you're waiting for user input on stdin, the user enters two characters: w and \n. You put the w into a variable and act on it. Then you read another 5 characters - the \n is still waiting in stdin since you haven't read it yet, so that becomes the first character.

The simplest solution is probably just to always read an extra character when you scanf. Though it'll make things messy if the person enters in too many characters! 'wblabla\n' would leave a bunch of junk for the next scanf to read. Probably better to just scanf('%s', s) instead, to make sure that you've read the whole line, and then use s[0] for the first character, etc.

---

### Post by kb1lqd on 2008-04-10
Ok, Ill give it a shot and see what happens... but would that explain why the program works perfect on the computer lab machine running solaris and getting all these weird problems when I run it in ubuntu?

---

### Post by kb1lqd on 2008-04-10
Ya, sorry it didn't fix the problem

---

### Post by jaddle on 2008-04-10
You tried reading the whole string in? What was the result?

Different OSes have different ways of handling the terminal, so I could see that it could change how this would function... see [http://c-faq.com/osdep/cbreak.html](http://c-faq.com/osdep/cbreak.html) for some examples (though not referring to scanf...)

---

### Post by kb1lqd on 2008-04-10
hmm ok, Im in class right now, I'll try it again and get a screenshot to show you. I'm pretty sure the output was the same.... or at least repeated "Please enter input type" alot.... I'll post back later today, thanks for the help so far!

---

### Post by kb1lqd on 2008-04-10
Just a claification by looking back at the requirments. We have to use scanf("%c%c%c%c%c", &var1, &var2, &var3, &var4, &var5);

Ill gate a better screen shot of all the inputs and outputs to the program, I gotta run, but just wanted to throw that out there... I think the program works fine, It's something inside of my computer maybe?

---

### Post by kb1lqd on 2008-04-10
Ok, Heres the screenshot... Heres what I inputed in order:

-----------------
n
12345
n
15551
w
racar
w
madam
w
hello
t
--------------------

---

### Post by Can+~ on 2008-04-10
I haven't check the code, but let me introduce you to arrays:

Instead of :
```
int num1, num2, num3...
char ch1, ch2, ch3, ch4...
```

Use:
[PHP]char mychar[20];
int mynums[20];[/PHP]
(where [20] is the length).

An array of characters is also known as a String. So, thefore, instead of printing:
[PHP]printf("%c%c%c...", ch1, ch2...);[/PHP]

With a string is just about:
[PHP]printf("%s", mystring);[/PHP]

strings also store, on the last element, a number 0 to indicate the end of the string, so you can use the function in <string.h> to get the length of the string:
[PHP]int charlen = strlen(mystring);[/PHP]

This would simplify a lot the complexity of your code:

[PHP]int i, ispal, L = strlen(mystring);
for (i=0, ispal=1; i < L; i++)
	if (mystring[i] != mystring[L-i])
	{
		ispal = 0; break; // Exit the loop as soon as a different element is found, ispal == 0 means it's not a palindrome.
	}[/PHP]
		

Also, is to note that a character is basically a number interpreted on the asciii code, so:

[PHP]
char i;
for (i=0; i < 256; i++)
	printf("character %c is %d in ascii", i, i);[/PHP]

(this will return you an ascii table).

So, the solution to the palindrome, is basically, starting from the end of the array, and comparing to the start of the array, until you hit n/2. *edited*

---

### Post by jpkotta on 2008-04-11
> PS) I realize looking now that I have two headers (Repeated the #include)... would that possible be a problem?

That shouldn't be a problem, because all good C programmers will make their headers idempotent.

[http://en.wikipedia.org/wiki/Idempotent](http://en.wikipedia.org/wiki/Idempotent)
[http://c-faq.com/cpp/nestincl.html](http://c-faq.com/cpp/nestincl.html)

> Also to note, that a word with an odd number of characters can't be a palindrome.

Huh?  Why not?

---

### Post by jpkotta on 2008-04-11
I agree with Can+~ about the strings (arrays).  I would use fgets().  BTW, there is no reason to treat the numbers differently, because you're treating them as decimal numbers in both conversions, so you might as well just treat them as strings.

---


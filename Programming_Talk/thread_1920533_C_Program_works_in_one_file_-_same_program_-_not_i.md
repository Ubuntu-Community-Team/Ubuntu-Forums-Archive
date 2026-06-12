---
title: "C Program works in one file - same program - not in the other"
date: 2012-02-05
forum: Programming Talk
---

### Post by ClientAlive on 2012-02-05
This crap always seems to happen to me. For the life of me I can-not-understand-this. I litterally copied and pasted the code from PracticePad-PlayTime[01] into Strings. It was working fine, in Strings.c where I pasted it, in the beginning. I tried to wrap a while around the sob to make the program keep running until the user chooses to quit... started giving me probs. Stripped it back down and it started doing what it does now. Then I went back and copy/ pasted the code from PracticePad... to Strings again and still no difference in behavior. I've been over and over it. I'm sure my eyes are just not seeing something that should be obvious. A missing semicolon or something stupid. Can I get another set of eyes on this to help me identify what's going on here?

Attached screenshots of both programs running (code for both pasted below => ctrl + a then ctrl + c then ctrl + v - right from my editor to here)

Thanks so much. I really appreciate it.


For PracticePad-PlayTime[01].c

```

/*
Question: Can I come up with a little program that takes the first letter
of a word the user enters, moves it to the end of the word, then adds
the letters 'ay' to the end, then prints back the modified word?

Tip:

Status: Works to take a word and output the pig latin equivalent.

To Do:

~ Check that only letters are input and issue error message if not.
~ Check number of characters user inputs. If exceeded, issue error
  and return them to top of program (entering input again).

Next steps: Move out of main and into function. Move into lab 03 source file.
*/

#include <stdio.h>

void PigLatin(char String[]);

int main(void)
{
char String[37];

printf("Please enter a word (up to 34 characters in length): ");
fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array

PigLatin(String);

return 0;
}

void PigLatin(char String[])
{
	int i;

		for(i = 0; i < 35; ++i) //move first letter to end of word then null terminate
		{
			 if(String[i] == '\0')
			 {
					String[i - 1] = String[0];
					String[i] = 'a';
					String[i + 1] = 'y';
					String[i + 2] = '\n';
					break;
			 }
		}

		i = 1;		

		while(String[i] != '\0') //move all characters left by one element
		{
			String[i - 1] = String[i];
			String[i] = '\0';
			++i;
		}

	printf("The Pig Latin equvalent of the word you entered is: %s", String);

}


```


For Strings.c

```

/*
Jacob Fines
Lab 03
CSC 250
Spring 2012

Assignment Spec:

This lab focuses on the manipulation of c-strings.  The user will be prompted
to enter a word.  They will then be given a menu with the following options:

1.Pig Latin
2.Count Vowels & Consonants
3.Quit

Menu Item 1:

Pig Latin is a form of coded language often used for amusement.  Many variations
exist in the methods used to form pig-Latin phrases.  For simplicity, use the
following algorithm:

1.Move the first letter of the word to the end
2.Add the letters &#8220;ay&#8221;

Thus the word &#8220;jump&#8221; becomes &#8220;umpjay,&#8221; the word &#8220;the&#8221; becomes &#8220;hetay&#8221; and the word
&#8220;computer&#8221; becomes &#8220;omputercay.&#8221;  You can assume all words have at least 2 letters.

The printing of the pig latin word MUST be done in a function. The function will
take the string (character array) as a parameter, and print the pig latin version.

Menu Item 2:

This menu item will print the number of vowels and the number of consonants.  When
this menu item is picked, a function will be called which will take the array, a
variable for the number of vowels, and a variable for the number of consonants as
parameters.  The counting will be done, and the variables will be modified in the
function.  The variables must simulate pass by reference so their values are
retained after the function has finished executing.

Other Notes:

The input for the menu choice must be validated. You will accept the number in as a
character, then use the isdigit (covered on p. 312 in your books) function to verify
a valid digit has been entered.  If it is a digit you will convert it to an integer
(atoi &#8211; p. 318 in your books), and verify it is a number 1-3.  If it is not valid
they will be prompted for a new entry.
*/

#include <stdio.h>

void Menu(void);
void PigLatin(char String[]);
//char CharacterCount(char Characters, int *Vowels, int *Consonants);

int main (void)
{
	int Selection = 0;
	char String[37]; //supercalifragilisticexpialidocious (34 characters) + 2 for "ay" + 1 for NULL

	Menu();
	scanf("%d", &Selection);

	switch(Selection)
	{
		case 1:
		{
		//1.Pig Latin

			printf("Please enter a word (up to 34 characters in length): \n");
			fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array

			PigLatin(String);

			break;
		}

		//Case 2:
		//{
		//2.Count Vowels & Consonants
			//CharacterCount(Characters, &Vowels, &Consonants);
			//break;
		//}
	} //end switch

return 0;
} //end main

void Menu(void)
{
printf("Please select one of the following - you may Quit at any time: \n");
printf("1.Pig Latin\n");
printf("2.Count Vowels & Consonants\n");
printf("3.Quit\n");
}

void PigLatin(char String[])
{
	int i;

		for(i = 0; i < 35; ++i) //move first letter to end of word, tack on 'a' and 'y' then null terminate
		{
			 if(String[i] == '\0')
			 {
					String[i - 1] = String[0];
					String[i] = 'a';
					String[i + 1] = 'y';
					String[i + 2] = '\n';
					break;
			 }
		}

		i = 1;		

		while(String[i] != '\0') //shift all characters left by one element then null terminate
		{
			String[i - 1] = String[i];
			String[i] = '\0';
			++i;
		}

	printf("The Pig Latin equvalent of the word you entered is: %s", String);

}

/*
char CharacterCount(char Characters, int Vowels, int Consonants)
{
//do something
}
*/


```

---

### Post by trent.josephsen on 2012-02-05
I haven't examined your code very closely, but I'm guessing it's because you never pull the \n out of the input stream after calling scanf().  Replace that scanf() with fgets+atoi or fgets+strtol would be my suggestion -- scanf() is for structured input, and what a user types at a keyboard is about as unstructured as it gets.

---

### Post by nvteighen on 2012-02-05
First of all, initialize your string using memset (string.h). That will prevent the string being filled with all that garbage you see after the word.

I agree with trent.josephsen: the '\n' from the first input (the menu) is being read when asking for the second input... The easiest way to deal with this is by using a "trash bin" variable (that's my own term) whose function is to flush stdin and prepare it for more user input (you can't do fflush(stdin), as its behavior is undefined). Another alternative is to have Selection be a char[2], so that you read the \n with it.

For the menu input, I'd use getchar, rather than anything else... It's simpler.

EDIT: Wtf are you use for indenting? The code below looks horrible even though I reindented it perfectly on Emacs!

```

#include <stdio.h>
#include <string.h>

void Menu(void);
void PigLatin(char String[]);
//char CharacterCount(char Characters, int *Vowels, int *Consonants);

int main (void)
{
	int Selection = 0;
	char String[37]; //supercalifragilisticexpialidocious (34 characters) + 2 for "ay" + 1 for NULL
    memset(String, 0, sizeof(String));

	Menu();
    Selection = getchar();

	switch(Selection)
	{
    case '1':
    {
		//1.Pig Latin

        // [nvteighen] We know there'll be always something in stdin here...
        char trash[2];
        fgets(trash, sizeof(trash), stdin);

        printf("Please enter a word (up to 34 characters in length): \n");
        fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array

        PigLatin(String);

        break;
    }

    //Case 2:
    //{
    //2.Count Vowels & Consonants
    //CharacterCount(Characters, &Vowels, &Consonants);
    //break;
    //}
	} //end switch

    return 0;
} //end main

void Menu(void)
{
    printf("Please select one of the following - you may Quit at any time: \n");
    printf("1.Pig Latin\n");
    printf("2.Count Vowels & Consonants\n");
    printf("3.Quit\n");
}

void PigLatin(char String[])
{
	int i;

    for(i = 0; i < 35; ++i) //move first letter to end of word, tack on 'a' and 'y' then null terminate
    {
        if(String[i] == '\0')
        {
            String[i - 1] = String[0];
            String[i] = 'a';
            String[i + 1] = 'y';
            String[i + 2] = '\n';
            break;
        }
    }

    i = 1;		

    while(String[i] != '\0') //shift all characters left by one element then null terminate
    {
        String[i - 1] = String[i];
        String[i] = '\0';
        ++i;
    }

	printf("The Pig Latin equvalent of the word you entered is: %s", String);

}

/*
  char CharacterCount(char Characters, int Vowels, int Consonants)
  {
//do something
}
*/

```

---

### Post by ClientAlive on 2012-02-05
Sorry about the formatting. These code boxes mangle it for some reason. Happens to me with pastebin too.

Thanks for the help. I was truly stumped on that one. Got er' working now but had to place the lines a little differently.

```

   int Selection = 0;
   char String[37];

   memset(String, 0, sizeof(String));

   Menu();

   scanf("%d", &Selection);
   char trash[2];
   fgets(trash, sizeof(trash), stdin);

   switch(Selection)
   {
      case 1:
      {
         //1.Pig Latin

         printf("Please enter a word (up to 34 characters in length): ");
         fgets(String, 35, stdin); //passing in a sizeof = 35 (two less     than the actual size of the array
         printf("\n");

         PigLatin(String);

         break;
      }

```

And the rest is the same except for a couple formatting tweaks for the output.
--------------

Edit:

Fwiw, I thought I'd show what I came up with so far  :)

It's attached. Again, sorry about the formatting. Taking it from Geany to a text file mangles it. It's just too much to go through line by line trying to fix it up.

---

### Post by ClientAlive on 2012-02-05
nvteighen, I don't quite understand what you were saying. I was hoping you could clarify it for me. You talked about "...the '\n' from the first input (the menu) is being read when asking for the second input..."

How can it be input when it's in a printf statement? (the Menu function contains printf statements). I thought printf sent to output not input.

And how can a \n get from there to going into input where the user's entry is expected?

I mean, I know something like that was going on but I don't really get how that can happen. I think it would really be a huge leap for me if I could grasp that.

Also, I though maybe I could pose another question I'm having a little trouble understanding. I've tried to ask my instructor for clarification on these things in the past but her responses never really made sense to me.

Part of the instruction for the assignment had to do with validating the user's input:

> 
Other Notes:

The input for the menu choice must be validated. You will accept the number in as a
character, then use the isdigit (covered on p. 312 in your books) function to verify
a valid digit has been entered.  If it is a digit you will convert it to an integer
(atoi &#8211; p. 318 in your books), and verify it is a number 1-3.  If it is not valid
they will be prompted for a new entry.


I having a hard time making sense of how what she describes would accomplish that. It sounds like she's saying to take a number in as a char insted of an int (for openers) then check whether it's a number or not and if it is convert it to an int with atoi? It just seems like a lot of unnecessary going back and forth to me and I don't get what it's supposed to accomplish.

And what much difference does it make whether it's an int or a char data type? Either it's a number or it isn't right? There's two library functions (isdigit and isalpha) that can determine that, right? Why all the converting data type back and forth? Or am I misunderstanding what atoi does?

One of my classmates was asking me about this too and showed me and email response he'd gotten from our instructor about it. Based on what I read, if she responded the same way to me I would be even more confused.

Well, anyhow, I just thought I'd put that out there. If I have to I just omit that altogether and hope for the best. (Not that I want to though).

Thanks.

---

### Post by Arndt on 2012-02-05
> **ClientAlive said:**
> nvteighen, I don't quite understand what you were saying. I was hoping you could clarify it for me. You talked about "...the '\n' from the first input (the menu) is being read when asking for the second input..."

How can it be input when it's in a printf statement? (the Menu function contains printf statements). I thought printf sent to output not input.

And how can a \n get from there to going into input where the user's entry is expected?


I think he means that when you end your input by pressing the Return key, the end-of-line indicator will also be sent to the program, and it is the character '\n'.

---

### Post by ClientAlive on 2012-02-05
> **Arndt said:**
> I think he means that when you end your input by pressing the Return key, the end-of-line indicator will also be sent to the program, and it is the character '\n'.


Ok. Just wondered how it would get there I guess. I can try looking it up too tho.


Thanks.

---

### Post by Bachstelze on 2012-02-06
> **ClientAlive said:**
> nvteighen, I don't quite understand what you were saying. I was hoping you could clarify it for me. You talked about "...the '\n' from the first input (the menu) is being read when asking for the second input..."

How can it be input when it's in a printf statement? (the Menu function contains printf statements). I thought printf sent to output not input.

And how can a \n get from there to going into input where the user's entry is expected?

I mean, I know something like that was going on but I don't really get how that can happen. I think it would really be a huge leap for me if I could grasp that.

```
firas@av104151 ~ % cat test.c                                         
#include <stdio.h>

int main(void)
{
    int c;
    printf("Type a letter: ");
    c = getchar();
    printf("%d\n", c);
    c = getchar();
    printf("%d\n", c);
}
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@av104151 ~ % ./test                                             
Type a letter: a
97
10

```

When I am asked to type a letter, I type [font=monospace]a <return>[/font]. I send TWO characters, the 'a' and a newline. getchar() only reads one, so it only reads the 'a' (ASCII code 97). The newline is still there, so when I call getchar() again it doesn't prompt me and directly reads the newline (ASCII code 10).


> I having a hard time making sense of how what she describes would accomplish that. It sounds like she's saying to take a number in as a char insted of an int (for openers) then check whether it's a number or not and if it is convert it to an int with atoi? It just seems like a lot of unnecessary going back and forth to me and I don't get what it's supposed to accomplish.

And what much difference does it make whether it's an int or a char data type? Either it's a number or it isn't right? There's two library functions (isdigit and isalpha) that can determine that, right? Why all the converting data type back and forth? Or am I misunderstanding what atoi does?

What getchar() does is that it reads a character, and stores its ASCII value in a variable **of type int**. For integers, the ASCII value of the character that represents them is different from their numeric value (the integers 0-9 are represented by ASCII values 48-57). What atoi does basically is convert ASCII values to numeric values.

When reading integers via getchar, the basic workflow is:

```
int n = getchar();
if (isdigit(n)) {
    int n = n-48;
}
```

It is important that the variable you store the result of getchar() in be of type int or larger. You may only convert it to char after you have made sure it will fit in a char (a char is just a small int). This is what isdigit() does, but in a more general setting you can use isascii().

---

### Post by trent.josephsen on 2012-02-06
> **Bachstelze said:**
> When reading integers via getchar, the basic workflow is:

```
int n = getchar();
if (isdigit(n)) {
    int n = n-48;
}
```
Minor nit:  subtract '0' rather than the magic number 48 to make sure it works universally.

---

### Post by lisati on 2012-02-06
> **trent.josephsen said:**
> Minor nit:  subtract '0' rather than the magic number 48 to make sure it works universally.

Good catch: for example, I am reminded that ASCII & EBCDIC have different mappings.

---

### Post by Bachstelze on 2012-02-06
Yeah but that would make it more difficult to understand. I don't think he has fully grasped the characters-are-really-integers thing yet.

---

### Post by Arndt on 2012-02-06
> **Bachstelze said:**
> Yeah but that would make it more difficult to understand. I don't think he has fully grasped the characters-are-really-integers thing yet.

Why stop half-way on the path to understanding? If you don't understand n - '0', you don't really understand n - 48 either.

---

### Post by Bachstelze on 2012-02-06
> **Arndt said:**
> Why stop half-way on the path to understanding? If you don't understand n - '0', you don't really understand n - 48 either.

One has to stop at one point, I don't think *The C Programming Language* would fit in a forum post.

Also, no, n-'0' is not the same thing as n-48, because it has a character constant, so you have to explain that character constants are really integers, so it's ok to use them in arithmetic expressions. n-48, you are using a "natural" integer constant, so you don't have that "issue".

---

### Post by trent.josephsen on 2012-02-06
It's a fair point, and a fairly classic question about how much is enough simplification.  In this case I'd say the potential for confusion over '0' isn't worth teaching bad habits.  But I tend to err on the side of confusion anyway.

---

### Post by Bachstelze on 2012-02-06
> **trent.josephsen said:**
> It's a fair point, and a fairly classic question about how much is enough simplification.  In this case I'd say the potential for confusion over '0' isn't worth teaching bad habits.  But I tend to err on the side of confusion anyway.

I was meaning it more like "it's a lesson for another day", just like people who begin in C use scanf() to input data easily, even though you shouldn't do it in Real Life™. I don't think that's "teaching bad habits", it's just understanding that one cannot learn everything at once. There is no question that '0' is the correct thing to do in "production" code.

---

### Post by ClientAlive on 2012-02-07
> **Bachstelze said:**
> Yeah but that would make it more difficult to understand. I don't think he has fully grasped the characters-are-really-integers thing yet.

I think I just did. Well, sort of...

I guess I started out thinking the difference between int and char was that int was for numbers and char was for letters (to me "letter" and "character" were synonymous). So, to me, it was as thought they were names for what kind of thing you would put in them. I knew about ascii in a general sense but hadn't really put together that int and char really had nothging to do with whether something is a number or letter - right?

So what I'm getting from this is that where the difference that's any difference at all, lies, is in whether something is stored as it's ascii value or not. (And maybe a little bit about how big of a something can be stored in a particular data type).

I'm still not perfectly clear on applying this to that part of our assignment. But I'm getting that isdigit does not just tell whether something is a number; but, more specifically, whether it is an ascii value or not - right? So in the end I think I just misunderstood my instructor's terminology.

> 
Other Notes:

The input for the menu choice must be validated. You will accept the number in as a
character, then use the isdigit (covered on p. 312 in your books) function to verify
a valid digit has been entered.  If it is a digit you will convert it to an integer
(atoi &#8211; p. 318 in your books), and verify it is a number 1-3.  If it is not valid
they will be prompted for a new entry.


That's the last paragraph/ section in the spec for this lab.

Yeah, the terminology is confusing ("character" not char, "number", "integer", "digit"). Are any of them really synonymous where programming is concerned?

So I guess when I saw "character" in "You will accept the number in as a character..." I immediately thought 'char'. Now that I see it again (after reading all your posts) it doesn't seem to mean that. Right?

So now I'm thinking something like the following example is what's being asked for:

```

#include <stdio.h>
int main(void)
{
int n;

printf("Enter a number: \n");
n = getchar(); //this is what's responsible for it being stored as an ascii value a "character"

if(isdigit(c)) //check 2 things - is it an ascii value? and is it a number?
{
   c = atoi(c); //convert it from the ascii value to a number

   if(c != 1 || c != 2 || c != 3) //check for specific numbers
   {
      printf("Invalid entry. Please enter a valid selection: \n");
   }

   else
   {
      break; //let them continue on? (terrible algorith throughout, sorry)
   }
}

return 0;
}

```

I don't really think that code above is the right way to do it. I was trying to think of a general example to show how I think it's supposed to work. If my understanding on it is correct I'd probably put it into a function that returns one of several possible return values. It might be like passing the user's entry into the function so it get's run throught the code inside it then setting that variable that stores their selection to whatever return value from the function is appropriate based on their entry. It would be like passing it through the function to control how the program responds based on what they entered.

Anyway, thanks all you. I may not have this totally right but it makes a whole lot more sense now.

Jake

---

### Post by Bachstelze on 2012-02-07
> **ClientAlive said:**
> I think I just did. Well, sort of...

I guess I started out thinking the difference between int and char was that int was for numbers and char was for letters (to me "letter" and "character" were synonymous).

That's true in some languages, but not in C. Remember computers only know numbers, so internally, everything (in every language) is represented as numbers. Some languages provide separete character and number types, in the sense that you cannot add a number and a character for example. In C, however, the type [font=monospace]char[/font] is really an integer type, just like type [font=monospace]int[/font] and others.

But surely there is a reason why it's called [font=monospace]char[/font], and not something like [font=monospace]short short int[/font], right? Mostly, it's because it is the smallest integer type that is still large enough to hold all the characters of whatever character system the machine uses, so when you want to store a character, you store it in a [font=monospace]char[/font] even though technically you could store it in an [font=monospace]int[/font], because you don't need the extra space [font=monospace]int[/font] provides. Consequently, all the string functions in the standard library expect strings to be array of [font=monospace]char[/font]s, not arrays of [font=monospace]int[/font]s.

>  So, to me, it was as thought they were names for what kind of thing you would put in them. I knew about ascii in a general sense but hadn't really put together that int and char really had nothging to do with whether something is a number or letter - right?

Right, because everything is numbers, so the issue of knowing whether something is a "letter" or a number just doesn't exist. ;)

> So what I'm getting from this is that where the difference that's any difference at all, lies, is in whether something is stored as it's ascii value or not.

A character is always stored as its ASCII value (or its value in whatever character set the machine uses). On machines that use ASCII, [font=monospace]'a'[/font] and [font=monospace]97[/font] are ***the exact same thing*** as far as the compiler is concerned: constants of type [font=monospace]int[/font] with numeric decimal value 97. Of coutse, in a program, you use one or the other depending on what you mean, but the compiler won't see any difference.

> (And maybe a little bit about how big of a something can be stored in a particular data type).

This is machine-dependent. On an x86, char is 8 bits, int is 32 bits and long int is 32 or 64 bits.

> I'm still not perfectly clear on applying this to that part of our assignment. But I'm getting that isdigit does not just tell whether something is a number; but, more specifically, whether it is an ascii value or not - right? So in the end I think I just misunderstood my instructor's terminology.

You give it an int, and it tells you whether it corresponds to the character code of a digit. Of cours,e if it's the character code of a digit, then it certainly is a character code in the first place. ;)

> Yeah, the terminology is confusing ("character" not char, "number", "integer", "digit"). Are any of them really synonymous where programming is concerned?

No. The meaning of "character" even depends on who you talk to. If you tell a user "enter a character", he will enter probably a letter or a digit, maybe a punctuation sign. To the programmer, "character" is basically anything that can be input thrgough read(), meaning alphanumeric, punctuation, whitespace, control characters, and everything else. There are 256 possible characters, with each character corresponding to one possible value of the type [font=monospace]unsigned char[/font] (0 to 255).

[font=monospace]char[/font] is a data type, more specifically an integer type, generally 8 bits in size. If it is signed, the positive values (0 to 127) can store all the ASCII characters, not the others (128 to 255). (This is one reason why you need to make sure a character is ASCII before you store it in a [font=monospace]char[/font].)

"number" is also an informal notion. Basically, it means any number, integer or not. when you tell a user "enter a number", they will probably type something like 123 or 56.78, not [font=monospace]abcde[/font]. (But you have to be prepared  for them to type "abcde" anyway.) The C parlance for "the set of all types that can hold numbers" is *arithmetic types*.

"integer" is again an informal nothion. C parlance for "the set of all types that can hold integer values" is *integer types*.

"digit" is even more informat, because it can mean a number of different thing. It can mean a character in the range 0-9, a single-digit integer, or one particular digit of a number (integer or not). When you use this term, generally context makes it clear what is meant.

> So I guess when I saw "character" in "You will accept the number in as a character..." I immediately thought 'char'. Now that I see it again (after reading all your posts) it doesn't seem to mean that. Right?

Close, but not really. It basically means that you are going to store the ASCII code of the character entered, not its numeric value.

> So now I'm thinking something like the following example is what's being asked for:

```

#include <stdio.h>
int main(void)
{
int n;

printf("Enter a number: \n");
n = getchar(); //this is what's responsible for it being stored as an ascii value a "character"

if(isdigit(c)) //check 2 things - is it an ascii value? and is it a number?
{
   c = atoi(c); //convert it from the ascii value to a number

   if(c != 1 || c != 2 || c != 3) //check for specific numbers
   {
      printf("Invalid entry. Please enter a valid selection: \n");
   }

   else
   {
      break; //let them continue on? (terrible algorith throughout, sorry)
   }
}

return 0;
}

```

Close. First, you seem to have renamed variable c to n when you declare it, but you forgot to rename it in other parts of your program. Second, atoi() takes a string (null-temrinated array of chars), not a single ASCII value. To convert a character digit stored as a single ASCII value to its numeric value, you do

```
c = c-'0';
```

i.e. you substract from it the ASCII code of the character 0 (zero). Think about it.

---

### Post by ClientAlive on 2012-02-08
I don't know why I'm having such a hard time with this and I'm not really sure how to define what I'm confused about. A lot of what is being shared with me here makes a lot of sense and opens my eyes to some new things. At the end of the day though I'm just not seeing how what this instructor asked us to do is supposed to work. I may end up having to submit my version that doesn't contain any validation component to it. It works, just has no validation of the user's input.

Have you ever talked with someone where you ask them something or even try to relate something to them and you can hear from their response that there was some miscommunication somewhere? That the response doesn't line up at all? This is what happens between my instructor and I at every communication transaction. I ask somthing and the response I get is off target. I try again, and again the same thing. I get tired of trying; and, more than that, don't want to frustrate or anger the person - so I quit asking. In the end I'm no better off than I started. Worse for both of us actaully - the time we both spent produces nothing.

How in the world are you going to take a something that started out as one data type, a something which is spread around all over the code and the code is depending on it remaining that data type, expecting it to stay that data type - to take that and convert it to a different data type and expect not to break the whole thing to sh... ?? That's what atoi does right? It take a char (even worse a char pointer - which my program does not use a pointer, it's not useing an array, why would you use an array for a single entry?) - so it takes this char pionter (that's referring to a data type right - a char is a data type - and converts it to an int - again, a data type).

If all that's totally off base I wish to God and all that's good it would be pointed out somehow (and that my dumb @ss would get it - lord knows you guys are trying). On the one hand it's truly excruciating on the other I feel as though some deliciouse treat is dangling just oustide my reach and I've got to have it.
------------------------

Edit:

Ok, sorry. I think I let my frustration get the better part of me.

Would it be possible to see an example of how isdigit and atoi can work togeter in the context of some small program that (1) takes in and stores a user's selection (2) makes use of those two functions, and (3) does something ?

---

### Post by trent.josephsen on 2012-02-08
You're not at fault for not understanding.  C is a lot to take in all at once, and I think you're making good progress in understanding.

I can't really give an example program because that would basically do all your work for you -- but I can show you how each part might work.

atoi() doesn't change the value you *pass* it, it merely reads any numeric characters at the beginning of the string and interprets them as an integer.  Here's an example:
```
char s[] = "24 hours";
int i = atoi(s);
printf("%s => %d\n", s, i);
```
That code will print "24 hours => 24" if you run it.  When you call atoi(), the non-numeric suffix " hours" is ignored for the conversion -- but the string itself is left intact.  I hope this answers some questions.

Now, the problem (well, one of the problems) with atoi() is when you pass it a string like "hello, world".  Try it -- atoi() returns 0, because it didn't find any numeric characters at the beginning of the string.  But that means you can't tell the difference between garbage input like "hello, world" and the user actually entering the number zero.

A rudimentary form of error checking in this case would be to check if the first character in the string (s[0]) is a digit.  This is fairly easy to do:
```
char s[] = "hello, world";
if (isdigit(s[0])) {
    printf("s starts with a digit\n");
} else {
    printf("s does not start with a digit\n");
}
```

So the only issue now is how to get hold of the user input as a string, instead of as individual characters.  This is easy to do with fgets(), but let's look again at this requirement which I assume your instructor wrote:

> You will accept the number in as a character, then use the isdigit (covered on p. 312 in your books) function to verify a valid digit has been entered.  If it is a digit you will convert it to an integer (atoi &#8211; p. 318 in your books)
Stop right there.  If you read it in as a character (presumably using getchar) you can't use atoi() on it.  I conclude that your instructor is probably incompetent (and believe me, he or she is not alone).  So your question is how to resolve this fundamental error, which basically comes down to a judgment call between:

1) Pretend you didn't notice the instructor (hereafter "him") telling you to use atoi() and just convert it with c - '0'

2) Pretend you didn't notice him telling you to read it in as a single character and use fgets() instead so you can then use atoi() on it

3) Point out his error and ask for clarification.

Depending on what kind of instructor we're dealing with here, option 3 could be the best or the worst option available; incompetent profs are often very sensitive and he may take exception to being corrected by a student.  You probably don't want to be on his blacklist this early in the semester.  On the other hand, you could face poor grades if you take either option 1 or option 2 (and he might be one of those that will mark you off for doing either one just because it's not exactly what he said).

I'm gauging worst case scenarios here -- you know him better than I do and are better equipped to make the call.

Should you need further help with either option 1 or option 2, feel free to ask again.

---

### Post by Bachstelze on 2012-02-08
> **ClientAlive said:**
> so it takes this char pionter (that's referring to a data type right - a char is a data type - and converts it to an int - again, a data type).

When we say "a char", or "an int" or something similar, what is really meant is either "a variable of type char/int/..." or "an expression of type ..." or "a value of type...". (Generally, context makes it clear which is meant, but if there is a risk of confusion, you use variable/expression/value explicitly.) Converting "a data type" to another doesn't make sense, but you can convert a value that is of one data type to another value of another data type. For example, consider:

```
double f = 32;
```

The expression [font=monospace]32[/font] is of type [font=monospace]int[/font], and the variable [font=monospace]f[/font] is of type [font=monospace]double[/font]. So normally, I shouldn't be allowed to do that, but the C standard says that in such cases, the value of the [font=monospace]int[/font] expression is converted to a [font=monospace]double[/font] value in the obvious manner, so this code will be equivalent to

```
double f = 32.0;
```

(Note that you should be careful when using implicit conversions like that, sometimes the manner in which conversion is performed is not at all obvious.)

But in other cases it's not that easy. You can't just do

```
int n = "42";
```

and expect it to convert the string [font=monospace]"42"[/font] to an [font=monospace]int[/font] of value 42 for you. But since it's a common thing that people want to do, the standard library includes the function atoi() (and some others) that will do that, so ou can do:

```
int n = atoi("42");
```

(Of course here you would just do [font=monospace]int n = 42;[/font], but sometimes you can't do that, for example if your string comes from I/O, as it does in your case.)

---

### Post by ClientAlive on 2012-02-08
> **trent.josephsen said:**
> You're not at fault for not understanding.  C is a lot to take in all at once, and I think you're making good progress in understanding.

I can't really give an example program because that would basically do all your work for you -- but I can show you how each part might work.

atoi() doesn't change the value you *pass* it, it merely reads any numeric characters at the beginning of the string and interprets them as an integer.  Here's an example:
```
char s[] = "24 hours";
int i = atoi(s);
printf("%s => %d\n", s, i);
```
That code will print "24 hours => 24" if you run it.  When you call atoi(), the non-numeric suffix " hours" is ignored for the conversion -- but the string itself is left intact.  I hope this answers some questions.

Now, the problem (well, one of the problems) with atoi() is when you pass it a string like "hello, world".  Try it -- atoi() returns 0, because it didn't find any numeric characters at the beginning of the string.  But that means you can't tell the difference between garbage input like "hello, world" and the user actually entering the number zero.

A rudimentary form of error checking in this case would be to check if the first character in the string (s[0]) is a digit.  This is fairly easy to do:
```
char s[] = "hello, world";
if (isdigit(s[0])) {
    printf("s starts with a digit\n");
} else {
    printf("s does not start with a digit\n");
}
```

So the only issue now is how to get hold of the user input as a string, instead of as individual characters.  This is easy to do with fgets(), but let's look again at this requirement which I assume your instructor wrote:


Stop right there.  If you read it in as a character (presumably using getchar) you can't use atoi() on it.  I conclude that your instructor is probably incompetent (and believe me, he or she is not alone).  So your question is how to resolve this fundamental error, which basically comes down to a judgment call between:

1) Pretend you didn't notice the instructor (hereafter "him") telling you to use atoi() and just convert it with c - '0'

2) Pretend you didn't notice him telling you to read it in as a single character and use fgets() instead so you can then use atoi() on it

3) Point out his error and ask for clarification.

Depending on what kind of instructor we're dealing with here, option 3 could be the best or the worst option available; incompetent profs are often very sensitive and he may take exception to being corrected by a student.  You probably don't want to be on his blacklist this early in the semester.  On the other hand, you could face poor grades if you take either option 1 or option 2 (and he might be one of those that will mark you off for doing either one just because it's not exactly what he said).

I'm gauging worst case scenarios here -- you know him better than I do and are better equipped to make the call.

Should you need further help with either option 1 or option 2, feel free to ask again.


Well thanks for the encouragement.

Actually, I've tried option 3 and it doesn't work. In fact, I've been trying option 3 for a semester and a half and it never has worked. So often when I begin to dig into the technical details of something (like these two functions and what they take in and put out) something doesn't make sense. Other times what I'm told by consensus of folks who's experience I trust contradicts what I'm told by him. Almost everyone on one of the popular irc programming channels has made a similar comment about the him at one time or other. I guess all I can do is the best I can. It's a tough call but in the end I think that learning to code correctly holds the highest value.

Perhaps it's a bit hackish but the code I attached does 'seem' to work. I was basically trying to trick atoi and fed it the address of an int. I'm not really sure if it's a very good way to do it but I think at least I can pull in a decent grade and maintain a decent relationship with him if I put the code he wants in the file and the screenshots show it works.

Regading the attached code. Some of the decisions I made when writing it that way came from things I've been told on the irc channel in the past.

~ That you don't use char with getchar, you use int

And, on a personal level, I was hoping to find a way to write it so it includes both those functions that were asked for. 'He' has insisted in the past that you do use char with getchar (despite my sharing what I was told otherwise) but I think using int with it in this lab is something I can get away with if I can put those two functions in there and can make the program work (or at least have the appearance of working). I write code on the side anyhow so I have opportunities to learn that way too.

Thankfully, he's always graded easy. I get 50/50's all the time. It's probably just my ego talking but sometimes I wonder if the person isn't learning more from us than the other way round. I consider an article I read one time about a person who somehow landed a job as Coordination Director of a prominent company in their area (event planning). The article was written by the person. They didn't have any prior experience or education in it and expressed how worried and nervous they were about being able to pull it off. In the article the person described their reliance on others in the feild (ouside their organization) for picking up what they needed to do. Apparently it all worked out for that person in the end. He/ she learned a great deal and gained skills and ultimately became very good at their job. It was an interesting article.

Aside from all that, I wonder what it is that accounts for something being stored as an ascii value of not to begin with. And, similarly, what it is that accounts for something being read as an ascii value or not? I just feel there's a much deeper issue at stake here (possibly one that transcends any particular language).
---------------------

Edit:

I should clarify that last thing a little better:

atoi appears to convert the ascii value to the value itself, but what prevent's the next thing from reading it as an ascii value and muckering up the whole works after that?

For instance:

As shown in the second run in the screenshot attached - the value of "Selection" is 50 going into atoi. 50 happens to be the ascii value for the number 2 (the number I entered). "ValidSelection" shows a value of 2. This the value atoi spit out after running what was entered throught it - right? Now, in the code following the use of atoi, there is a condidtional statement which arguments are for the values 1 or 2 or 3 (not the ascii values? or are they? How is if reading 1 or 2 or 3?). If "if" is not reading them as ascii values, then why not? Hence my question, "...what it is that accounts for something being stored as an ascii value of not to begin with. And, similarly, what it is that accounts for something being read as an ascii value or not?"

Now, in reality, a question like that is really just the start of something that opens up a whole can of worms. Then one starts so question, how do you tell which one reads which one or which one stores which one; and, especially, why?
----------------------

Edit:

There is something that seems odd about the line of code with isdigit in it. I wrote it into the code attached the same way you wrote it Trent; but, how can you have a conditional statement "if" where there isn't some kind of equality operator in the argument? We wrote it "if(isdigit(SomeVariable))" but ifisdigit what? Is what I wonder. I've never seen that before but it appears to work.

---

### Post by Bachstelze on 2012-02-08
```
if (expression) {
    statement;
}
```

is equivalent to

```
if (expression != 0) {
    statement;
}
```

In other words, it will execute the block following the if if and only if the value of the expression is not zero.

As for what determines whether the value is stored as an ASCII value or as the numeric value of an integer, it's how you read it.

```
int n = getchar();
```

will store the ASCII value of the character, becuase it's the only thing that makes sense. If getchar() were to store a digit as its numeric value, what is it supposed to do if you don't enter a digit?

```
int n;
scanf("%d", &n);
```

will store the numeric value of the integer in the variable n, because you told scanf via %d that what it gets really is an integer. Conversely:

```
int n = 50;
printf("%c %d\n", n, n);
```

Will print [font=monospace]2 50[/font], because printf with %c interprets the value as an ASCII code, and with %d it interprets it as an integer.

*EDIT:* Also please don't post code as attachment, unless it consists of several large files. Just paste it in your post around CODE tags, or use a pastebin. Reading attachments is cumbersome.

---

### Post by ClientAlive on 2012-02-08
> **Bachstelze said:**
> ```
if (expression) {
    statement;
}
```

is equivalent to

```
if (expression != 0) {
    statement;
}
```

In other words, it will execute the block following the if if and only if the value of the expression is not zero.

As for what determines whether the value is stored as an ASCII value or as the numeric value of an integer, it's how you read it.

```
int n = getchar();
```

will store the ASCII value of the character, becuase it's the only thing that makes sense. If getchar() were to store a digit as its numeric value, what is it supposed to do if you don't enter a digit?

```
int n;
scanf("%d", &n);
```

will store the numeric value of the integer in the variable n, because you told scanf via %d that what it gets really is an integer. Conversely:

```
int n = 50;
printf("%c %d\n", n, n);
```

Will print [font=monospace]2 50[/font], because printf with %c interprets the value as an ASCII code, and with %d it interprets it as an integer.

*EDIT:* Also please don't post code as attachment, unless it consists of several large files. Just paste it in your post around CODE tags, or use a pastebin. Reading attachments is cumbersome.


So it sounds like it's either in the conversion character used (when one is used) or it's in the function's spec.

```

#include <stdio.h>

int main (void)
{
int Selection = 0;
int ValidSelection = 0;

printf("Code line 25: The value of Selection is: %d\n", Selection);
printf("Code line 26: The value of ValidSelection is: %d\n", ValidSelection);

printf("Enter 1, 2, or 3: \n");
Selection = getchar();

char Trash[2];
fgets(Trash, sizeof(Trash), stdin);

if(isdigit(Selection))
{
	printf("Code line 36: The value of Selection is: %d\n", Selection);
	ValidSelection = atoi(&Selection);
	printf("Code line 38: The value of ValidSelection is: %d", ValidSelection);

	if(ValidSelection == 1 || ValidSelection == 2 || ValidSelection == 3)
	{
		int Sum = 0;

		printf("The user's selection was 1, 2, or 3\n");
		Sum += 1;
		printf("The value of Sum is: %d\n", Sum);
	}

	else
	{
		printf("\nThe user's selection was not 1, 2, or 3\n");
	}
}

return 0;
}

```


While that seems to work alright, trying to work it into my actual program sure doesn't. Tried several things and no luck so far. Maybe a miracle will happen sometime in the next 78 hrs.

---

### Post by Bachstelze on 2012-02-08
This is "OK". Between quotes because this:

```
	ValidSelection = atoi(&Selection);
```

Will work as expected on little-endian machines only, so I guess you can keep it for now but be aware that you shouldn't do it normally.

Now if I'm following correctly, the only thing left to do is make the program ask repeatedly until a value of 1, 2 or 3 is entered. For that you can use a while() loop and a [font=monospace]quit[/font] variable.

---

### Post by ClientAlive on 2012-02-09
> **Bachstelze said:**
> This is "OK". Between quotes because this:

```
	ValidSelection = atoi(&Selection);
```

Will work as expected on little-endian machines only, so I guess you can keep it for now but be aware that you shouldn't do it normally.

Now if I'm following correctly, the only thing left to do is make the program ask repeatedly until a value of 1, 2 or 3 is entered. For that you can use a while() loop and a [font=monospace]quit[/font] variable.


Well, apparently that code doesn't work for validation in the larger program. Maybe it does and my error lies somewhere else in the code. Lord knows I've tried a half dozen things with this beast. Partly I'm an idiot because I take these labs and want to do awesome stuff with it - make it more user friendly and such. She writes the spec so it leaves a lot of room for interpretation and I interpret it, in this case, to mean make it so each individual program continues to loop until the user enters a certain thing. When in case 1 or case 2, don't ask them to enter something every time they do the program, just keep going until they choose to enter what breaks them out of the loop. Then, when they break out of the case 1 or 2 loop they go to the outer one with the main menu in it. They can then make the choices available from the main menu (ie: choose which of the two things to run (PigLatin or CharacterCount or to quit entirely). This adds complexity to the program. When I did that and saved the validation part to the end it made things more difficult for me.

Anyhow, the short answer, it's the validation that's kickin' my butt.

I attached the most recent code I have (what I worked on up to a few hrs ago). I attached it because it is kind of a lot of code (though I hear you on just pasting small code into code tags). I do have a working version I saved to the side that has no validation. Worse comes to worse I'll submit it - but I'd rather get the validation working. Truthfully? I'm spent. I'm just fresh out of hope for getting anywhere with it.

---

### Post by trent.josephsen on 2012-02-09
1_ An easy mistake to make:

```
if(ValidSelection != 1 || ValidSelection != 2 || ValidSelection != 3)
```

Do you see why this is always true?

2_ The only 'return' statement in ValidationControl is inside the else branch -- which means ValidationControl always returns garbage because 'return' is never reached.

3_ Do try to think about the inner if...else block (lines 198-216 in the code you posted).  What is it supposed to do?  Why is it broken?

One more thing, that may qualify as nitpicking but can cause some very confusing behavior:  stdout is sometimes/often line buffered, which means that nothing you print to it will *necessarily* be displayed unless it ends in a newline.  When you want to make sure something is displayed even though it doesn't end in a newline (like your "please enter a word" prompt), follow the printf() with fflush(stdout); like this:

```
printf("Please enter a word (up to 34 characters in length): ");
fflush(stdout);
```

Like I said, it might be nitpicking, but I have had it bite me before, and now I reflexively add the fflush line after (almost) every printf that doesn't end in \n.

---

### Post by Arndt on 2012-02-09
> **ClientAlive said:**
> 

```

	printf("Code line 38: The value of ValidSelection is: %d", ValidSelection);


```



Lines like these will not be correct for very long. There is a preprocessor symbol available which contains the current line number of the source code: __LINE__.

About doing atoi(&x) where x contains a character: atoi wants a C string, and a C string should be ended by a Nul character (ASCII code 0). There is no guarantee that the single character you have in x is followed by a zero, and then atoi will return the wrong value (not crash, because it never does).

---

### Post by Bachstelze on 2012-02-09
> **Arndt said:**
> 
There is no guarantee that the single character you have in x is followed by a zero,

There certainly is (though, as I said, on little-endian machines only). On big-endian machines, atoi() will return 0 (because it will get the empty string).

---

### Post by trent.josephsen on 2012-02-09
Note that in atoi(&Selection), Selection is an int, not a char -- so it actually does "work" fairly reliably, and only a bizarre value of EOF could make it fail... I think.  As Bachstelze noted, only on little endian machines with some assumptions about representation.

It's a really ugly hack, but it does allow ClientAlive to combine character input with isdigit() and atoi(), so perhaps it's best to let the instructor deal with the hackishness if he notices.  (I've known profs who might actually have given extra credit for a "clever" solution like this, even though it's clearly Bad.)

*Edit: gotta type faster*

---

### Post by ClientAlive on 2012-02-09
> **trent.josephsen said:**
> 1_ An easy mistake to make:

```
if(ValidSelection != 1 || ValidSelection != 2 || ValidSelection != 3)
```

Do you see why this is always true?

2_ The only 'return' statement in ValidationControl is inside the else branch -- which means ValidationControl always returns garbage because 'return' is never reached.

3_ Do try to think about the inner if...else block (lines 198-216 in the code you posted).  What is it supposed to do?  Why is it broken?

One more thing, that may qualify as nitpicking but can cause some very confusing behavior:  stdout is sometimes/often line buffered, which means that nothing you print to it will *necessarily* be displayed unless it ends in a newline.  When you want to make sure something is displayed even though it doesn't end in a newline (like your "please enter a word" prompt), follow the printf() with fflush(stdout); like this:

```
printf("Please enter a word (up to 34 characters in length): ");
fflush(stdout);
```

Like I said, it might be nitpicking, but I have had it bite me before, and now I reflexively add the fflush line after (almost) every printf that doesn't end in \n.


1_ Makes sense. Under those conditions, if it were 1 you would want it to prove false because that's an acceptable entry but it still wouldn't be 2 or 3. So, rather than prove false it would prove true. Likewise for the other entries (2 and 3) that you would want to prove false for that statement. I needed to use the && logic. Ok.

2_ I'm working on that. I don't quite see it but I do see the behavior of the program and I'm racking my brain why.

I've digressed to making it a void return function and attempting to manipulate the variable that's passed in directly using pass by reference. When run, it hangs after you hit return (after entering a selection). The thing is, it does this whether I use a void return function and pass by reference or have it return an int to attempt to modify the variable. The impression I get is that either:

(1) It isn't actually returning anything (or modifying the variable when using pass by reference) for some reason.

Or

(2) It's that stupid deal with getchar() where it hangs because it's waiting on a newline or something. But I have garbage collection for that and I don't see why the garbage collection wouldn't be working since that part of the code hasn't changed from the working version on to this.

This makes me want to eliminate the whole getchar() causing it to hang possibility and say it's in that block of code (lines 198 - 216) wtih the If...else statements in it. But why? I'm pretty sure I recall doing something like this in a function before and it worked fine. What am I missing here?

Here's what it looks like now (maybe it isn't too big to put in code tags, idk):

```


#include <ctype.h>
#include <stdio.h>
#include <string.h>

void Menu(void);
void ValidationControl(int *Selection);
void PigLatin(char String[]);
void CharacterCount(char String[], int *TotalCount, int *VowelCount);

int main(void)
{
	int Selection = 0;

	while(Selection != 3)
	{
		do
		{
		Menu();

		Selection = getchar();
		char Trash[2];
		fgets(Trash, sizeof(Trash), stdin);

		ValidationControl(&Selection);

		} while(Selection == -1);

		switch(Selection)
		{
			case 1:
			{
				//Pig Latin

				//int Continue;

				//do
				//{
					//printf("Enter 3 to return to the main menu\n");
					//Continue = getchar();
					//char Trash[2];
					//fgets(Trash, sizeof(Trash), stdin);

					//ValidationControl(&Continue);

					char String[37]; //supercalifragilisticexpialidocious (34 characters) + 2 for "ay" + 1 for NULL
					memset(String, 0, sizeof(String));

					printf("Please enter a word (up to 34 characters in length): ");
					fflush(stdout);
					fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array
					printf("\n");

					PigLatin(String);

				//} while(Continue != 3); //selection to "return to the main menu")

				break;
			} //end case 1

			case 2:
			{
				//Count Vowels & Consonants

				//int Continue;

				//do
				//{
					//printf("Enter 3 to return to the main menu\n");
					//Continue = getchar();
					//char Trash[2];
					//fgets(Trash, sizeof(Trash), stdin);

					//ValidationControl(&Continue);

					char String[100];
					int TotalCount = 0;
					int VowelCount = 0;

					memset(String, 0, sizeof(String));

					printf ("Enter a sentence: ");
					fgets(String, 100, stdin);

					CharacterCount(String, &TotalCount, &VowelCount);

					printf("The total number of characters is: %d\n", TotalCount);
					TotalCount = TotalCount - VowelCount;
					printf("You entered: %d total consonants and %d total vowels\n", TotalCount, VowelCount);
				//} while(Continue != 3); //selection to "return to the main menu")

				break;
			} //end case 2
		} //end switch
	} //end outer while

return 0;
} //end main

void Menu(void)
{
	printf("Please select one of the following (you may Quit from the main menu at any time): \n\n");
	printf("1.Pig Latin\n");
	printf("2.Count Vowels & Consonants\n");
	printf("3.Quit\n");
} //end function

void ValidationControl(int *Selection) //function to validate the user's entry
{
	int ValidSelection = 0;

	if((isdigit(*Selection) != 0)) //it is a number 0 - 9
	{
		//printf("Line 182: Value of Selection is: %d", *Selection);
		ValidSelection = atoi(Selection); //convert the ascii value to it's corresponding number
		//printf("Line 184: Value of ValidSelection is: %d", ValidSelection);
		char Trash[2];
		fgets(Trash, sizeof(Trash), stdin);

		if(ValidSelection != 1 && ValidSelection != 2 && ValidSelection != 3) //it isn't 1, 2, or 3
		{
			printf("Line 190: Invalid selection.\n\n");
			*Selection = -1;
		} //end second nested if

		else if(ValidSelection == 1 || ValidSelection == 2 || ValidSelection == 3)
		{
			if(ValidSelection != 3)
			{
				*Selection = 0;
			}

			else if(ValidSelection == 1)
			{
				*Selection = 1;
			}

			else if(ValidSelection == 2)
			{
				*Selection = 2;
			}

			else
			{
				*Selection = 3;
			}
		} //end second nested else
	} //end outer if

	else
	{
		printf("Line 220: Invalid selection.\n\n");
		//printf("Line 121: Value of Selection is: %d", *Selection);
		//printf("Line 122: Value of ValidSelection is: %d", ValidSelection);
	}
} //end function

void PigLatin(char String[])
{
	int i;

		for(i = 0; i < 35; ++i) //move first letter to end of word, tack on 'a' and 'y' then null terminate
		{
			 if(String[i] == '\0')
			 {
					String[i - 1] = String[0];
					String[i] = 'a';
					String[i + 1] = 'y';
					String[i + 2] = '\n';
					break;
			 }
		}

		i = 1;		

		while(String[i] != '\0') //shift all characters left by one element then null terminate
		{
			String[i - 1] = String[i];
			String[i] = '\0';
			++i;
		}

	printf("The Pig Latin equvalent of the word you entered is: %s\n", String);
} //end function

void CharacterCount(char String[], int *TotalCount, int *VowelCount)
{
	const char Vowels[11] = {'a', 'A', 'e', 'E', 'i', 'I', 'o', 'O', 'u', 'U', '\0'};
	char Store;
	int i, j;

	for(i = 0; String[i] != '\0'; ++i)
	{
		if(isalpha(String[i]) != 0)
		{
			++*TotalCount;
		}
	}

	for(i = 0; Vowels[i] != '\0'; ++i)
	{
		Store = Vowels[i];

		for(j = 0; String[j] != '\0'; ++j)
		{
			if(Store == String[j])
			{
				++*VowelCount;
			}
		}
	}
} //end function


```

---

### Post by Bachstelze on 2012-02-09
I don't think passing a pointer (C does not do pass-by-reference *stricto sensu*) to ValidationControl is a good idea. It should just take the integer, and return 1 (true) if it is valid and 0 (false) if it is not. There should be no need to modify it.

*EDIT:* Also, shouldn't line 128 be ==?

---

### Post by Arndt on 2012-02-09
> **Bachstelze said:**
> There certainly is (though, as I said, on little-endian machines only). On big-endian machines, atoi() will return 0 (because it will get the empty string).

I think the way I put it is better.

---

### Post by ClientAlive on 2012-02-09
> **Bachstelze said:**
> I don't think passing a pointer (C does not do pass-by-reference *stricto sensu*) to ValidationControl is a good idea. It should just take the integer, and return 1 (true) if it is valid and 0 (false) if it is not. There should be no need to modify it.

*EDIT:* Also, shouldn't line 128 be ==?


Which line? I made some modification in the mean time which changed the line numbers. I'm guessing you meant the last line shown below?


```

					printf("Please enter a word (up to 34 characters in length): ");
					fflush(stdout);
					fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array
					printf("\n");

					PigLatin(String);

				//} while(Continue != 3); //selection to "return to the main menu")

```

I think part of why I tried to go that route (modifying the user's selection) was because I was looking for a way to have the code inside the case(s) just keep running until they a certain value and not ask them to enter something over and over. In hindsight I don't think my approach to that was very good.

Interestingly, I was trying out a small piece of code to see if I can use if...else statements inside a function and have it return a variety of different values depending on what condition is met. Just started with it but the way I tried it so far, my compiler complains:

```

error: control reaches end of non-void function

```

I think I know why though. I think I'm on to something; that, if I can get right, will lead me to the solution. I'm thinking very hard on your advice too. Perhaps it's enough that the function return just zero or one (false or true). Maybe there's a better way to implement that thing I described using code in main.
----------------------

Edit:

This works (sample code below), thought it does not involve using atoi or making any conversion. It is, however, using scanf with %d and not getchar. Trent, I think that was one of suggested options you gave me earlier. I tried it the other way. I tried to do it her way and include everything she asked for. It doesn't work. I'm not a mind reader so I don't know how he'll take it but I guess it's better to have some kind of validation control than none at all (even if it doesn't include what was asked for.

```

/*
To Do: Test using if...else statements in a function and having the varible
in main get modified as a result.
*/

#include <ctype.h>
#include <stdio.h>
#include <string.h>

int TestConditional(int Variable);

int main(void)
{
int Variable = 0;

printf("The value of the Variable is: %d\n\n", Variable);

printf("Enter 1, 2, or 3: \n");
scanf("%d", &Variable);

Variable = TestConditional(Variable);

printf("The value of the Variable is: %d", Variable);

return 0;
} //end main

int TestConditional(int Variable)
{
	//Variable = Variable - '0';

	if(Variable == 1)
	{
		Variable = 10;
	}

	if(Variable == 2)
	{
		Variable = 20;
	}

	if(Variable == 3)
	{
		Variable = 30;
	}

return Variable;
}

```

---

### Post by Bachstelze on 2012-02-09
*EDIT:* Never mind that with line 128, I get it now.

---

### Post by ClientAlive on 2012-02-09
Thx.

Because this works:

```

/*
To Do: Test using if...else statements in a function and having the varible
in main get modified as a result.
*/

#include <ctype.h>
#include <stdio.h>
#include <string.h>

int TestConditional(int Variable);

int main(void)
{
int Variable = 0;

printf("The value of the Variable is: %d\n\n", Variable);

printf("Enter 1, 2, or 3: \n");
scanf("%d", &Variable);

Variable = TestConditional(Variable);

printf("The value of the Variable is: %d", Variable);

return 0;
} //end main

int TestConditional(int Variable)
{
	//Variable = Variable - '0';

	Variable = Variable + '0';

	if(isdigit(Variable))
	{
		Variable = Variable - '0';

		if(Variable == 1)
		{
			Variable = 10;
		}

		else if(Variable == 2)
		{
			Variable = 20;
		}

		else if(Variable == 3)
		{
			Variable = 30;
		}
	}

return Variable;
}

```


I would think then that this would work:

```

/*
Jacob Fines
Lab 03
CSC 250
Spring 2012

Assignment Spec:

This lab focuses on the manipulation of c-strings.  The user will be prompted
to enter a word.  They will then be given a menu with the following options:

1.Pig Latin
2.Count Vowels & Consonants
3.Quit

Menu Item 1:

Pig Latin is a form of coded language often used for amusement.  Many variations
exist in the methods used to form pig-Latin phrases.  For simplicity, use the
following algorithm:

1.Move the first letter of the word to the end
2.Add the letters &#8220;ay&#8221;

Thus the word &#8220;jump&#8221; becomes &#8220;umpjay,&#8221; the word &#8220;the&#8221; becomes &#8220;hetay&#8221; and the word
&#8220;computer&#8221; becomes &#8220;omputercay.&#8221;  You can assume all words have at least 2 letters.

The printing of the pig latin word MUST be done in a function. The function will
take the string (character array) as a parameter, and print the pig latin version.

Menu Item 2:

This menu item will print the number of vowels and the number of consonants.  When
this menu item is picked, a function will be called which will take the array, a
variable for the number of vowels, and a variable for the number of consonants as
parameters.  The counting will be done, and the variables will be modified in the
function.  The variables must simulate pass by reference so their values are
retained after the function has finished executing.

Other Notes:

The input for the menu choice must be validated. You will accept the number in as a
character, then use the isdigit (covered on p. 312 in your books) function to verify
a valid digit has been entered.  If it is a digit you will convert it to an integer
(atoi &#8211; p. 318 in your books), and verify it is a number 1-3.  If it is not valid
they will be prompted for a new entry.
----------------------------------------------------------------------------------

Question: Can I add the validation fuctionality to this program using a function
to which my variables for the user's selection are passed. The function checks
the variable and either returns zero or prints that the user needs to re-enter
their selection.

Tip: Strings-Program.c contains a functional program. Revert to it if/ when
necessary.

isdigit takes an int and returns an int

atoi takes a pointer to a char and returns an int

Status: Made changes to code inside ValidationControl (oh yeah, renamed it
to "ValidationControl"), using getchar instead of scanf in main, chaged to
char instead of int for "Selection" and both "Continue", trying to use isdigit
and atoi. Getting a few errors when attempting to compile.

Also see the pasted chat dialog in the file "Temp-dialogFrom-IRC-ProgrammingChannel..."

Testing: //do some

Next steps: Debug, test, submit... Err... make validation work...
*/

#include <ctype.h>
#include <stdio.h>
#include <string.h>

void Menu(void);
int ValidationControl(int Selection);
void PigLatin(char String[]);
void CharacterCount(char String[], int *TotalCount, int *VowelCount);

int main(void)
{
	int Selection = 0;

	while(Selection != 3)
	{
		do
		{
		Menu();

		scanf("%d", &Selection);
		char Trash[2];
		fgets(Trash, sizeof(Trash), stdin);

		Selection = ValidationControl(Selection);

		} while(Selection == 0); //zero value returned means invalid

		switch(Selection)
		{
			case 1:
			{
				//Pig Latin

				//int Continue;

				//do
				//{
					//printf("Enter 3 to return to the main menu\n");
					//scanf("%d", &Continue);
					//char Trash[2];
					//fgets(Trash, sizeof(Trash), stdin);

					//Continue = ValidationControl(Continue);

					char String[37]; //supercalifragilisticexpialidocious (34 characters) + 2 for "ay" + 1 for NULL
					memset(String, 0, sizeof(String));

					printf("Please enter a word (up to 34 characters in length): ");
					fflush(stdout);
					fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array
					printf("\n");

					PigLatin(String);

				//} while(Continue != 3); //selection to "return to the main menu")

				break;
			} //end case 1

			case 2:
			{
				//Count Vowels & Consonants

				//int Continue;

				//do
				//{
					//printf("Enter 3 to return to the main menu\n");
					//scanf("%d", &Continue);
					//char Trash[2];
					//fgets(Trash, sizeof(Trash), stdin);

					//Continue = ValidationControl(Continue);

					char String[100];
					int TotalCount = 0;
					int VowelCount = 0;

					memset(String, 0, sizeof(String));

					printf ("Enter a sentence: ");
					fgets(String, 100, stdin);

					CharacterCount(String, &TotalCount, &VowelCount);

					printf("The total number of characters is: %d\n", TotalCount);
					TotalCount = TotalCount - VowelCount;
					printf("You entered: %d total consonants and %d total vowels\n", TotalCount, VowelCount);
				//} while(Continue != 3); //selection to "return to the main menu")

				break;
			} //end case 2
		} //end switch
	} //end outer while

return 0;
} //end main

void Menu(void)
{
	printf("Please select one of the following (you may Quit from the main menu at any time): \n\n");
	printf("1.Pig Latin\n");
	printf("2.Count Vowels & Consonants\n");
	printf("3.Quit\n");
} //end function

int ValidationControl(int Selection) //function to validate the user's entry
{
	//int ValidSelection = 0;

	Selection = Selection + '0';

	if(isdigit(Selection)) //it is a number 0 - 9
	{
		Selection = Selection - '0';

		if(Selection == 1)
		{
			Selection = 1;
		}

		else if(Selection == 2)
		{
			Selection = 1;
		}

		else if(Selection == 3)
		{
			Selection = 1;
		}

		else
		{
			printf("Line 223: Invalid selection.\n\n");
			Selection = 0;
		}
	}

return Selection;
} //end function

void PigLatin(char String[])
{
	int i;

		for(i = 0; i < 35; ++i) //move first letter to end of word, tack on 'a' and 'y' then null terminate
		{
			 if(String[i] == '\0')
			 {
					String[i - 1] = String[0];
					String[i] = 'a';
					String[i + 1] = 'y';
					String[i + 2] = '\n';
					break;
			 }
		}

		i = 1;		

		while(String[i] != '\0') //shift all characters left by one element then null terminate
		{
			String[i - 1] = String[i];
			String[i] = '\0';
			++i;
		}

	printf("The Pig Latin equvalent of the word you entered is: %s\n", String);
} //end function

void CharacterCount(char String[], int *TotalCount, int *VowelCount)
{
	const char Vowels[11] = {'a', 'A', 'e', 'E', 'i', 'I', 'o', 'O', 'u', 'U', '\0'};
	char Store;
	int i, j;

	for(i = 0; String[i] != '\0'; ++i)
	{
		if(isalpha(String[i]) != 0)
		{
			++*TotalCount;
		}
	}

	for(i = 0; Vowels[i] != '\0'; ++i)
	{
		Store = Vowels[i];

		for(j = 0; String[j] != '\0'; ++j)
		{
			if(Store == String[j])
			{
				++*VowelCount;
			}
		}
	}
} //end function

```


But it doesn't.

My error must be in main somewhere.
-----------------------------

Edit:

Getting closer...

---

### Post by ClientAlive on 2012-02-09
Annndddd... Can I get a drumroll please!

```

/*
Jacob Fines
Lab 03
CSC 250
Spring 2012

Assignment Spec:

This lab focuses on the manipulation of c-strings.  The user will be prompted
to enter a word.  They will then be given a menu with the following options:

1.Pig Latin
2.Count Vowels & Consonants
3.Quit

Menu Item 1:

Pig Latin is a form of coded language often used for amusement.  Many variations
exist in the methods used to form pig-Latin phrases.  For simplicity, use the
following algorithm:

1.Move the first letter of the word to the end
2.Add the letters &#8220;ay&#8221;

Thus the word &#8220;jump&#8221; becomes &#8220;umpjay,&#8221; the word &#8220;the&#8221; becomes &#8220;hetay&#8221; and the word
&#8220;computer&#8221; becomes &#8220;omputercay.&#8221;  You can assume all words have at least 2 letters.

The printing of the pig latin word MUST be done in a function. The function will
take the string (character array) as a parameter, and print the pig latin version.

Menu Item 2:

This menu item will print the number of vowels and the number of consonants.  When
this menu item is picked, a function will be called which will take the array, a
variable for the number of vowels, and a variable for the number of consonants as
parameters.  The counting will be done, and the variables will be modified in the
function.  The variables must simulate pass by reference so their values are
retained after the function has finished executing.

Other Notes:

The input for the menu choice must be validated. You will accept the number in as a
character, then use the isdigit (covered on p. 312 in your books) function to verify
a valid digit has been entered.  If it is a digit you will convert it to an integer
(atoi &#8211; p. 318 in your books), and verify it is a number 1-3.  If it is not valid
they will be prompted for a new entry.
----------------------------------------------------------------------------------

Question: Can I add the validation fuctionality to this program using a function
to which my variables for the user's selection are passed. The function checks
the variable and either returns zero or prints that the user needs to re-enter
their selection.

Tip: Strings-Program.c contains a functional program. Revert to it if/ when
necessary.

isdigit takes an int and returns an int

atoi takes a pointer to a char and returns an int

Status: Made changes to code inside ValidationControl (oh yeah, renamed it
to "ValidationControl"), using getchar instead of scanf in main, chaged to
char instead of int for "Selection" and both "Continue", trying to use isdigit
and atoi. Getting a few errors when attempting to compile.

Also see the pasted chat dialog in the file "Temp-dialogFrom-IRC-ProgrammingChannel..."

Testing: //do some

Next steps: Debug, test, submit... Err... make validation work...
*/

#include <ctype.h>
#include <stdio.h>
#include <string.h>

void Menu(void);
int ValidationControl(int Selection);
void PigLatin(char String[]);
void CharacterCount(char String[], int *TotalCount, int *VowelCount);

int main(void)
{
	int Selection = 0;

	while(Selection != 3)
	{
		do
		{
		Menu();

		scanf("%d", &Selection);
		//char Trash[2];
		//fgets(Trash, sizeof(Trash), stdin);

		Selection = ValidationControl(Selection);

		} while(Selection == 0); //zero value returned means invalid

		switch(Selection)
		{
			case 1:
			{
				//Pig Latin

				//int Continue;

				//do
				//{
					//printf("Enter 3 to return to the main menu\n");
					//scanf("%d", &Continue);
					char Trash[2];
					fgets(Trash, sizeof(Trash), stdin);

					//Continue = ValidationControl(Continue);

					char String[37]; //supercalifragilisticexpialidocious (34 characters) + 2 for "ay" + 1 for NULL
					memset(String, 0, sizeof(String));

					printf("Please enter a word (up to 34 characters in length): ");
					//fflush(stdout);
					fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array
					printf("\n");

					PigLatin(String);

				//} while(Continue != 3); //selection to "return to the main menu")

				break;
			} //end case 1

			case 2:
			{
				//Count Vowels & Consonants

				//int Continue;

				//do
				//{
					//printf("Enter 3 to return to the main menu\n");
					//scanf("%d", &Continue);
					char Trash[2];
					fgets(Trash, sizeof(Trash), stdin);

					//Continue = ValidationControl(Continue);

					char String[100];
					int TotalCount = 0;
					int VowelCount = 0;

					memset(String, 0, sizeof(String));

					printf ("Enter a sentence: ");
					fgets(String, 100, stdin);

					CharacterCount(String, &TotalCount, &VowelCount);

					printf("The total number of characters is: %d\n", TotalCount);
					TotalCount = TotalCount - VowelCount;
					printf("You entered: %d total consonants and %d total vowels\n", TotalCount, VowelCount);
				//} while(Continue != 3); //selection to "return to the main menu")

				break;
			} //end case 2
		} //end switch
	} //end outer while

return 0;
} //end main

void Menu(void)
{
	printf("Please select one of the following (you may Quit from the main menu at any time): \n\n");
	printf("1.Pig Latin\n");
	printf("2.Count Vowels & Consonants\n");
	printf("3.Quit\n");
} //end function

int ValidationControl(int Selection) //function to validate the user's entry
{
	//int ValidSelection = 0;

	Selection = Selection + '0';

	if(isdigit(Selection)) //it is a number 0 - 9
	{
		Selection = Selection - '0';

		if(Selection == 1)
		{
			Selection = 1;
		}

		else if(Selection == 2)
		{
			Selection = 2;
		}

		else if(Selection == 3)
		{
			Selection = 3;
		}

		else
		{
			printf("Line 223: Invalid selection.\n\n");
			Selection = 0;
		}
	}

return Selection;
} //end function

void PigLatin(char String[])
{
	int i;

		for(i = 0; i < 35; ++i) //move first letter to end of word, tack on 'a' and 'y' then null terminate
		{
			 if(String[i] == '\0')
			 {
					String[i - 1] = String[0];
					String[i] = 'a';
					String[i + 1] = 'y';
					String[i + 2] = '\n';
					break;
			 }
		}

		i = 1;		

		while(String[i] != '\0') //shift all characters left by one element then null terminate
		{
			String[i - 1] = String[i];
			String[i] = '\0';
			++i;
		}

	printf("The Pig Latin equvalent of the word you entered is: %s\n", String);
} //end function

void CharacterCount(char String[], int *TotalCount, int *VowelCount)
{
	const char Vowels[11] = {'a', 'A', 'e', 'E', 'i', 'I', 'o', 'O', 'u', 'U', '\0'};
	char Store;
	int i, j;

	for(i = 0; String[i] != '\0'; ++i)
	{
		if(isalpha(String[i]) != 0)
		{
			++*TotalCount;
		}
	}

	for(i = 0; Vowels[i] != '\0'; ++i)
	{
		Store = Vowels[i];

		for(j = 0; String[j] != '\0'; ++j)
		{
			if(Store == String[j])
			{
				++*VowelCount;
			}
		}
	}
} //end function

```


Clean up the mess (comments && commented out) and I'm golden.

Except...

Is there any suggestion on how I can implement that feature I was talking about. I'm an idiot for being so stubborn about it. It's just a stupid lab, I know. But is it? If this were a more important program and I were using it - I'd want it to keep running the item I'd selected until I told it to stop. One day, if I'm lucky, they will be more important programs. Then perhaps some value will come from having been so stubborn.

---

### Post by Bachstelze on 2012-02-09
Haha, you have something very funny. :)

```
189         if(Selection == 1)
190         {
191             Selection = 1;
192         }
193 
194         else if(Selection == 2)
195         {
196             Selection = 2;
197         }
198 
199         else if(Selection == 3)
200         {
201             Selection = 3;
202         }

```

Not sure what you mean by "running the item"...

Also, if you are using scanf, you need a totally different validation method. As it it, your ValidationControl function is close to useless.

*EDIT:* Run it, type 'a' at the prompt and see what happens.

---

### Post by Bachstelze on 2012-02-09
Other problems: if I enter a word of 34 letters in Pig Latin, the last letter disappears:

```
Please enter a word (up to 34 characters in length): abcdefghijklmnopqrstuvwxyzabcdefgh

The Pig Latin equvalent of the word you entered is: bcdefghijklmnopqrstuvwxyzabcdefgaay

```

you don't flush the input after reading, so if I enter a longer word, it does something probably not intended:

```
Please select one of the following (you may Quit from the main menu at any time): 

1.Pig Latin
2.Count Vowels & Consonants
3.Quit
1
Please enter a word (up to 34 characters in length): aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

The Pig Latin equvalent of the word you entered is: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaay

Please select one of the following (you may Quit from the main menu at any time): 

1.Pig Latin
2.Count Vowels & Consonants
3.Quit
Please enter a word (up to 34 characters in length): 
The Pig Latin equvalent of the word you entered is: aaaaaaaaaaaaaaaaaaaaaaaaay

Please select one of the following (you may Quit from the main menu at any time): 

1.Pig Latin
2.Count Vowels & Consonants
3.Quit

```

(Same thing with #2.)

---

### Post by ClientAlive on 2012-02-09
I guess the way it's set up there's really no way to tell if the function is doing anything or if the program is just using the variable value directly.

I did change my conversion character in scanf to %c and change the return and input type for my function to char to correspond. Then I was able to delete the line reading:

```

Selection = Selection + '0';

```

I do see that entering a letter doesn't print "Invalid Selection" to the user. It does, however, keep them in the loop - just that the loop runs twice instead of only once (probably a do...while thing?). If you enter a valid entry after that it will work normally.


> **Bachstelze said:**
> 
Not sure what you mean by "running the item"...



I was hoping to have it so when you enter 1, at the beginning of the program, it takes you into PigLatin (into case 1 in the code). You use the 'item' inside case 1 (in this case PigLatin) by entering your word and press enter - it gives you the converted word, it runs again just like it would right after you chose 1 and hit enter in the beginning, you use it again, it runs again, and on and on - until - you enter a particular number. That number being 3 (the same number you enter to quit. While your using PigLating it does not ask you to enter whether you want to do it again every time you use it, it just keeps going until you enter 3. When you do enter 3, it doesn't exit the entire program, it just breaks out of the case. Now you are looking at the main menu where you started and you can choose 1 for PigLatin or 2 for CharacterCount or 3 to quit. Ultimately, to exit the entire program from where you are running PigLatin you would have to press 3 then enter then 3 then enter.

Likewise for selection two. Selection two would be 'item' 2 and corresopond to 'case 2', the code in case 2.

So whatever you choose to run from the main menu (barring 3 to quit) just keeps going until you enter what it takes to make it stop, then you just go back to the first menu and it's 3 to quit (or 1 or 2 if you like).

---

### Post by Bachstelze on 2012-02-09
Ok, that's easy, but I think for now you should concentrate on getting input right, because that's basically what the assignment is about. If I do what you say, it's a little better, but I get;

```
Please select one of the following (you may Quit from the main menu at any time): 

1.Pig Latin
2.Count Vowels & Consonants
3.Quit
12345
Please enter a word (up to 34 characters in length): 
The Pig Latin equvalent of the word you entered is: 453ay

Please select one of the following (you may Quit from the main menu at any time): 

1.Pig Latin
2.Count Vowels & Consonants
3.Quit

```

still not really what I would expect. You should flush the input buffer after every read.

---

### Post by ClientAlive on 2012-02-09
Tried a couple things to see what would happen - no improvement.

Tried...

```

fflush(stdin);

```

...on the line following my scanf

no change.

Perhaps I misunderstood.

---

### Post by Bachstelze on 2012-02-09
You already do it with your Trash variable, you just need to do the same thing everywhere.

[http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392](http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392)

---

### Post by ClientAlive on 2012-02-10
fwiw, here's what I ended up submitting. I sure appreciate all you guys help. It has helped me to learn some things.

It still had a couple issues but I just got tired of fiddling with it. I have a pretty good hunch it's somthing hanging in the buffer that's causing the issues. Apparenly, no amount of grabage collection in the world was gonna fix it (at least that's what I tell myself so I can sleep at night :)

```


/*
Jacob Fines
Lab 03
CSC 250
Spring 2012

Assignment Spec:

This lab focuses on the manipulation of c-strings.  The user will be prompted
to enter a word.  They will then be given a menu with the following options:

1.Pig Latin
2.Count Vowels & Consonants
3.Quit

Menu Item 1:

Pig Latin is a form of coded language often used for amusement.  Many variations
exist in the methods used to form pig-Latin phrases.  For simplicity, use the
following algorithm:

1.Move the first letter of the word to the end
2.Add the letters &#8220;ay&#8221;

Thus the word &#8220;jump&#8221; becomes &#8220;umpjay,&#8221; the word &#8220;the&#8221; becomes &#8220;hetay&#8221; and the word
&#8220;computer&#8221; becomes &#8220;omputercay.&#8221;  You can assume all words have at least 2 letters.

The printing of the pig latin word MUST be done in a function. The function will
take the string (character array) as a parameter, and print the pig latin version.

Menu Item 2:

This menu item will print the number of vowels and the number of consonants.  When
this menu item is picked, a function will be called which will take the array, a
variable for the number of vowels, and a variable for the number of consonants as
parameters.  The counting will be done, and the variables will be modified in the
function.  The variables must simulate pass by reference so their values are
retained after the function has finished executing.

Other Notes:

The input for the menu choice must be validated. You will accept the number in as a
character, then use the isdigit (covered on p. 312 in your books) function to verify
a valid digit has been entered.  If it is a digit you will convert it to an integer
(atoi &#8211; p. 318 in your books), and verify it is a number 1-3.  If it is not valid
they will be prompted for a new entry.
*/

#include <ctype.h>
#include <stdio.h>
#include <string.h>

void Menu(void);
void Instruction(void);
char ValidationControl(char Selection);
char* PigLatin(char String[]);
void CharacterCount(char String[], int *TotalCount, int *VowelCount);

int main(void)
{
	char Selection = 0;

	while(Selection != 3)
	{
		do
		{					
		Menu();
		scanf("%c", &Selection);
		Selection = ValidationControl(Selection);
		} while(Selection == 0); //zero value returned means invalid

		switch(Selection)
		{
			case 1:
			{
				//Pig Latin

					char Trash[2];
					fgets(Trash, sizeof(Trash), stdin);

					char String[37]; //supercalifragilisticexpialidocious (34 characters) + 2 for "ay" + 1 for NULL
					memset(String, 0, sizeof(String));

					Instruction();

					do{
						printf("Please enter a word (up to 34 characters in length): ");
						fflush(stdout);
						fgets(String, 35, stdin); //passing in a sizeof = 35 (two less than the actual size of the array

						printf("The Pig Latin equvalent of the word you entered is: %s\n", PigLatin(String));
						printf("\n");
					} while(String[0] != '3');

				break;
			}

			case 2:
			{
				//Count Vowels & Consonants

					char Trash[2];
					fgets(Trash, sizeof(Trash), stdin);

					int TotalCount = 0;
					int VowelCount = 0;

					char String[100];
					memset(String, 0, sizeof(String));

					Instruction();

					do{
						printf ("Enter a sentence: ");
						fgets(String, 100, stdin);

						CharacterCount(String, &TotalCount, &VowelCount);

						printf("\nThe total number of characters is: %d\n", TotalCount);
						TotalCount = TotalCount - VowelCount;
						printf("You entered: %d consonants and %d vowels\n\n", TotalCount, VowelCount);
					} while(String[0] != '3');

				break;
			}
		} //end switch
	} //end while

return 0;
} //end main

void Menu(void)
{
	printf("\nMain Menu:\n");
	printf("Please select one of the following (you may Quit from the main menu at any time): \n\n");
	printf("1.Pig Latin\n");
	printf("2.Count Vowels & Consonants\n");
	printf("3.Quit\n");
} //end function

void Instruction(void)
{
	printf("\nContinue to make entries as many times as you like, pressing enter after each one.\n");
	printf("Enter 3 to return to the main menu.\n\n");
} //end function

char ValidationControl(char Selection) //function to validate the user's entry
{
	if(isdigit(Selection) != 0) //if it is a number 0 - 9 (equivalent to "isdigit(Selection) != 0")
	{
		Selection = Selection - '0';

		if(Selection == 1)
		{
			Selection = 1;
		}

		else if(Selection == 2)
		{
			Selection = 2;
		}

		else if(Selection == 3)
		{
			Selection = 3;
		}

		else
		{
			printf("\nInvalid selection.\n\n");
			Selection = 0;
		}
	}

	else
	{
		printf("\nInvalid selection.\n\n");
		Selection = 0;
	}

	return Selection;
} //end function

char* PigLatin(char String[])
{
	int i;

	for(i = 0; i < 35; ++i) //move first letter to end of word, tack on 'a' then 'y' then null terminate
	{
		 if(String[i] == '\0')
		 {
				String[i - 1] = String[0];
				String[i] = 'a';
				String[i + 1] = 'y';
				String[i + 2] = '\n';
				break;
		 }
	}

	i = 1;		

	while(String[i] != '\0') //shift all characters left by one element then null terminate
	{
		String[i - 1] = String[i];
		String[i] = '\0';
		++i;
	}

	return String;
} //end function

void CharacterCount(char String[], int *TotalCount, int *VowelCount)
{
	const char Vowels[11] = {'a', 'A', 'e', 'E', 'i', 'I', 'o', 'O', 'u', 'U', '\0'};
	char Store;
	int i, j;

	*TotalCount = 0;
	*VowelCount = 0;

	for(i = 0; String[i] != '\0'; ++i)
	{
		if(isalpha(String[i]) != 0)
		{
			++*TotalCount;
		}
	}

	for(i = 0; Vowels[i] != '\0'; ++i)
	{
		Store = Vowels[i];

		for(j = 0; String[j] != '\0'; ++j)
		{
			if(String[j] == Store)
			{
				++*VowelCount;
			}
		}
	}
} //end function

```
----------------------------

Edit:

Guess I didn't notice how he said "the printing of the pig latin word MUST be done in a function". Ahh well...

---

### Post by Arndt on 2012-02-10
Something is left in a buffer and not cleared. See the line after "unsay".

```


Main Menu:
Please select one of the following (you may Quit from the main menu at any time): 

1.Pig Latin
2.Count Vowels & Consonants
3.Quit
1

Continue to make entries as many times as you like, pressing enter after each one.
Enter 3 to return to the main menu.

Please enter a word (up to 34 characters in length): strawberry
The Pig Latin equvalent of the word you entered is: trawberrysay


Please enter a word (up to 34 characters in length): sun
The Pig Latin equvalent of the word you entered is: unsay
rysay


Please enter a word (up to 34 characters in length): 

```

---

### Post by dwhitney67 on 2012-02-10
> **ClientAlive said:**
> fwiw, here's what I ended up submitting. I sure appreciate all you guys help. It has helped me to learn some things.

It still had a couple issues but I just got tired of fiddling with it. I have a pretty good hunch it's somthing hanging in the buffer that's causing the issues. Apparenly, no amount of grabage collection in the world was gonna fix it (at least that's what I tell myself so I can sleep at night :)


It's unfortunate that you gave up so easily.  What's also unfortunate is that you continued to use scanf() to read a single character when prompting the user to choose a menu item.  You should have used fgets().  I believe someone mentioned that earlier in this thread, yet it seems you chose to use fgets() as a last resort when collecting unwanted data from the input stream.

Based on the instructions offered by your instructor for this assignment, you could have simplified things alot if you had merely stuck to printing the Pig Latin result rather than attempt to put together a new string.  Consider this:
```

printf("%s%cay", string+1, string[0]);

```
The line of code above could have been used to replace all the code you have in PigLatin().

Here's some code you can play with:
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

void PigLatin_Easy(const char* str)
{
    if (str != NULL && strlen(str) >= 2)
    {
        printf("%s%cay\n", str+1, str[0]);
    }
    else
    {
        printf("%say\n", str);
    }
}

char* PigLatin_Advanced(const char* str)
{
    char* newstr = NULL;

    if (str != NULL)
    {
        // allocate length sufficient to store incoming string, "ay", and a terminating null-character.
        newstr = malloc(strlen(str) + 2 + 1);

        sprintf(newstr, "%s%cay", str+1, str[0]);
    }

    return newstr;
}

void stripNewLine(char* str)
{
    char* nl = strchr(str, '\n');
    if (nl)
    {
        *nl = '\0';
    }
}

int main()
{
    char string[36];

    printf("Enter a string: ");
    fgets(string, sizeof(string), stdin);
    stripNewLine(string);

    printf("In Pig Latin, %s is... ", string);
    PigLatin_Easy(string);

    char* newstr = PigLatin_Advanced(string);
    printf("In Pig Latin, %s is... %s\n", string, (newstr ? newstr : "<error>"));
    free(newstr);

    return 0;
}

```

---

### Post by ClientAlive on 2012-02-10
> **dwhitney67 said:**
> It's unfortunate that you gave up so easily.  What's also unfortunate is that you continued to use scanf() to read a single character when prompting the user to choose a menu item.  You should have used fgets().  I believe someone mentioned that earlier in this thread, yet it seems you chose to use fgets() as a last resort when collecting unwanted data from the input stream.


Just got tired of guessing. Would have mentioned it last night but I was dead tired - Whatever I was thinking of to try and solve the buffer issue would either break the program one way; or, if I tried to do it another way, would break the program another way. I kept going back and forth and just got sick of it.

I was under the impression that fgets is only for arrays. I tried feeding it the address of Selection but got an infinite loop out of the deal. When I considered changing to use an array to store the selection I realized how much stuff I'd have to change in the program to do it (plus the lab spec called for a single character).

> **dwhitney67 said:**
> 
Based on the instructions offered by your instructor for this assignment, you could have simplified things alot if you had merely stuck to printing the Pig Latin result rather than attempt to put together a new string.  Consider this:


I hadn't thought of that. That really is spectacular. Thanks for the code samples to play with too by the way.

---


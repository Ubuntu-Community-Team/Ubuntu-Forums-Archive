---
title: "C programming - getting started"
date: 2008-10-09
forum: Programming Talk
---

### Post by benreilly013181 on 2008-10-09
Hi Guys & Gals,

I'm just new in UBUNTU and i'm studying about C Programming. I already installed build-essential and i'm using geany as editor and compiler but i'm having trouble as i go on....

Here's my problem...

I'm running the palindrome program.

#include<stdio.h>
#include<string.h>
#define size 26

void main()
{
char strsrc[size];
char strtmp[size];

printf("\n Enter String:= "); gets(strsrc);

strcpy(strtmp,strsrc);
strrev(strtmp);

if(strcmp(strsrc,strtmp)==0)
printf("\n Entered string \"%s\" ispalindrome",strsrc);
else
printf("\n Entered string \"%s\" is not palindrome",strsrc);
} 

upon building it (F9), i get this error:

gcc -Wall "palindrome.c" -o "palindrome" (in directory: /home/benreilly)
palindrome.c:6: warning: return type of ‘main’ is not ‘int’
palindrome.c: In function ‘main’:
palindrome.c:13: warning: implicit declaration of function ‘strrev’
/tmp/ccdLquFl.o: In function `main':
palindrome.c:(.text+0x2f): warning: the `gets' function is dangerous and should not be used.
palindrome.c:(.text+0x4c): undefined reference to `strrev'
collect2: ld returned 1 exit status
Compilation failed.

Please kindly help...

---

### Post by Canis familiaris on 2008-10-09
(1) use: int main() and return 0 instead of void main()
(2) Don't use gets()
(3) Make your own reverse a string function. strrev is not defined in string.h.

---

### Post by dwhitney67 on 2008-10-09
> **Anurag_panda said:**
> ...
(2) Don't use gets()
...

That's right.  Use fgets() instead.
[PHP]
#include <stdio.h>
#include <string.h>

int main()
{
  ...
  char strsrc[20] = {0};   // initialize all chars to null (0)

  fgets( strsrc, sizeof(strsrc), stdin );

  // and if you want to remove the newline at the end of the input string...
  char *newline = strchr( strsrc, '\n' );
  if ( newline ) *newline = '\0';

  ...
  return 0;
}
[/PHP]

---

### Post by benreilly013181 on 2008-10-09
Thanks a lot for the info. I'll gonna try it...

You're great guys...

I'll keep you posted.

---

### Post by benreilly013181 on 2008-10-09
> **Anurag_panda said:**
> (1) use: int main() and return 0 instead of void main()
(2) Don't use gets()
(3) Make your own reverse a string function. strrev is not defined in string.h.

Could anyone code this palindrome program for me? The one that is using string compare and the one using only loops?

Thanks a lot guys...

---

### Post by Canis familiaris on 2008-10-09
> **benreilly013181 said:**
> Could anyone code this palindrome program for me? The one that is using string compare and the one using only loops?

Thanks a lot guys...


I've modified your program and applied dwhitney67's method for fgets()
Note: This will work but would give a warning with pedantic argument so for your program since ISO C90 forbids variable-size array &#8216;cpstr&#8217;
In case you want to to compile with gcc -pedantic then use "char cpstr[SIZE]" - though I mention it would be much more inefficient, since it would not work with strings with length more than SIZE, though it won't affect this program

I am using the simplest algorithm. There are many more efficient algorithms too. I suggest in order to see how it works you should print the value of
i and strlen(str)-i-1 in the loop (which I've commented)

```
[color=#BC7A00]#include<stdio.h>
#include<string.h>
#define SIZE 26
[/color]
[color=#B00040]void[/color] [color=#0000FF]revstr[/color]([color=#B00040]char[/color][color=#666666]*[/color] str)
{
    [color=#B00040]int[/color] i;


    [color=#B00040]char[/color] cpstr[strlen(str)[color=#666666]+[/color][color=#666666]1[/color]];


    [color=#008000]**for**[/color](i[color=#666666]=[/color][color=#666666]0[/color]; i [color=#666666]<[/color] strlen(str); i[color=#666666]++[/color])
    {
        [color=#408080][i]//printf("%d\t%d\t", i, strlen(str)-i-1);
[/i][/color]        cpstr[i] [color=#666666]=[/color] str[strlen(str)[color=#666666]-[/color]i[color=#666666]-[/color][color=#666666]1[/color]];
    }
    cpstr[i] [color=#666666]=[/color] [color=#BA2121]'\0'[/color];

    strcpy(str, cpstr);

}


[color=#B00040]int[/color] [color=#0000FF]main[/color]()
{
[color=#B00040]char[/color] strsrc[SIZE];
[color=#B00040]char[/color] strtmp[SIZE];

printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121] Enter String:= "[/color]);
fgets(strsrc, SIZE, stdin);

[color=#B00040]char[/color] [color=#666666]*[/color]newline [color=#666666]=[/color] strchr( strsrc, [color=#BA2121]'\n'[/color] );
[color=#008000]**if**[/color] ( newline ) [color=#666666]*[/color]newline [color=#666666]=[/color] [color=#BA2121]'\0'[/color];

strcpy(strtmp,strsrc);
revstr(strtmp);



[color=#008000]**if**[/color](strcmp(strsrc,strtmp)[color=#666666]==[/color][color=#666666]0[/color])
    {
    printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121] Entered string [/color][color=#BB6622]**\"**[/color][color=#BA2121]%s[/color][color=#BB6622]**\"**[/color][color=#BA2121] is palindrome"[/color],strsrc);
    }
[color=#008000]**else**[/color]
    printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121] Entered string [/color][color=#BB6622]**\"**[/color][color=#BA2121]%s[/color][color=#BB6622]**\"**[/color][color=#BA2121] is not palindrome"[/color],strsrc);

[color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---

### Post by scottptn on 2008-10-09
This would work too :

```


#include<stdio.h>
#include<string.h>
#define size 26

int main()
{
	char strsrc[size];
	char strtmp[size];
	
	int i , j = 0 ;

	printf("\n Enter String:= ");
	
	/*Get user input from the keyboard implied by stdin*/
	
	fgets(strsrc,80,stdin);  /*80 is the maximum number of characters that can be entered */
	
	char *newline = strchr( strsrc, '\n' ); /*Find the occurence of '\n' character . Location stored in newline. */
	
 	if ( newline )
 		 *newline = '\0'; /*Replace the '\n' character by '\0' to terminate the string */
			 	
  	/*Copy the source string to a temporary variable*/

	strcpy(strtmp,strsrc);
		
	/*Check if palindrome*/
	
	for(i = strlen(strsrc)-1 ; i >= 0 ; i--)
	{	
		
		if(strsrc[i] != strtmp[j] )	
		{
			printf("\n Entered string \"%s\" is not palindrome",strsrc);
			
			return 0 ;
		}
		
		j++;	
	}	
	
	printf("\n Entered string \"%s\" is palindrome",strsrc);
		
	return 0;
}


```

Actually, in my code im comparing the original string with itself , so strcpy(strtmp,strsrc) is not really required, and we can simply do strsrc[i] != strsrc[j] ;) .

---

### Post by dribeas on 2008-10-09
> **scottptn said:**
> 
```

	/*Check if palindrome*/
	for(i = strlen(strsrc)-1 ; i >= 0 ; i--)
	{	
		if(strsrc[i] != strtmp[j] )	
		{
			printf("\n Entered string \"%s\" is not palindrome",strsrc);
			return 0 ;
		}
		j++;	
	}	
}

```


Checking the whole string is double checking all characters. The loop could run for just half the string. Also you could go with just one counter.

```

int i = 0;
int len = strlen( str );
for ( i = 0; i < len/2; ++i )
{
   if ( str[i] != str[len-1-i] ) 
   {
      printf( "The string '%s' is not a palindrome.\n", str );
      return 0; // distinct: not palindrome
   }
}
```

---

### Post by nvteighen on 2008-10-09
> **benreilly013181 said:**
> Could anyone code this palindrome program for me? The one that is using string compare and the one using only loops?

Thanks a lot guys...

1. A kindly advice: don't ask someone to write code for you, otherwise you'll never learn. Sometimes people will write it and sometimes even I do it, but when it's clear that the poster has a reasonable knowledge on the language and that his/her question is specific to a problem, not the whole code. Ask for concepts and ways to do; it's usually better and you'll learn much more...

2. Is C your first programming language? If yes, I really recommend you to learn Python or any other easier language that helps you to understand the basics of programming. 

C is a very very "tiny" language (in the sense that it has very little stuff built-in and the rest is got from libraries or coded by hand) that was designed for creating the UNIX operating system and therefore, is designed to control the computer at its most. But, programming is not just about controlling a computer, but very roughly said, it's to describe some process that you can then simulate on a computer. 

You want to describe how to detect whether a string is a palindrome or not... and rely on a computer to do the check. But C will require you to control the computer in order to set it up before you can ever tell it to do what you want it to do. Think about it: you don't even have a string data type in C... actually, a "string" in C is a variable holding a memory address (a pointer) to a character. That's why you shouldn't use gets(), as it potentially can overwrite memory... The question is, why do you have to care about that if you want to just check whether a string is a palindrome or not? Or why should you declare the main() function as a function that returns an integer? (never write "void main()", but "int main(void)" and make it return 0). Yeah, there's a reason for all that, but not related to your problem.

C's properties make (a lot of) sense when you're writing an operating system or a very important system utility (e.g. a shell). There you **need** to control memory, get speed and finally create something on top of which other programs can run... as you see, all of that is necessary computer-specific stuff, which is programming too (after all, you keep describing processes, the difference is that the process described is about the same simulation tool you'll use), but just a part of it.

Of course, if you already have learned some C, that knowledge will be useful. Moreover, all programmers should know C. What I suggest you is to give priority to a simpler language; this doesn't mean you should leave C aside... If you can, you could learn both at the same time or apply the general programming concepts you learned by learning C...

---

### Post by Canis familiaris on 2008-10-09
> **nvteighen said:**
>  Or why should you declare the main() function as a function that returns an integer? (never write "void main()", but "int main(void)" and make it return 0). Yeah, there's a reason for all that, but not related to your problem.

Well said

Offtopic:
 But could you tell me the reason why this is the rule that main() should return int. Is it due to error handling of the OS? Or is there any other reason.

 I remember coding void main() a lot in an old compiler.

---

### Post by nvteighen on 2008-10-09
> **Anurag_panda said:**
> 
Offtopic:
 But could you tell me the reason why this is the rule that main() should return int. Is it due to error handling of the OS? Or is there any other reason.

 I remember coding void main() a lot in an old compiler.

Because the standard says it has to be that way :p

It's because of the C/UNIX philosophy: a program/system should be designed by small parts that communicate with eachother. You do never know who's calling your main(), so you better return something for that caller.

But yes, "void main()" was accepted before... (IIRC in K&R C, pre-ANSI C) even just "main()" was accepted...

---

### Post by pmasiar on 2008-10-09
> **nvteighen said:**
> 2. Is C your first programming language? If yes, I really recommend you to learn Python or any other easier language that helps you to understand the basics of programming. 


Python is easier because it works on much higher level. Python was designed to use programmer's time well (making CPU work harder for same tasks), and is excellent for processing text. C was designed to use CPU in the most efficient way, even if programmer has to work much much harder to accomplish the same task.

Ie test if some string is a palindrome in Python is 3 lines of code calling a standard library functions.

[php]
# enter this in IDLE
def is_palindrome(text):
	copy = list(text) # convert text to list of characters
	copy.reverse()    # and reverse the list
	return text == ''.join(copy)

# and test it in IDLE
>>>is_palindrome('123')
False
>>>is_palindrome('ABBA')
True
[/php]

Learn basics in Python, after that C will make more sense. Best Python feature is interactive shell, so you can try and learn language one line at a time, without the need to write and compile small programs to test every feature. See wiki in my sig for links.

---

### Post by scottptn on 2008-10-09
One of the excellent texts for learning Python is "[A Byte of Python]("http://www.swaroopch.com/notes/Python#Download")" by Swaroop CH . This book has been made available for free download by the author . Really a good book to learn Python.

---

### Post by Canis familiaris on 2008-10-09
> **scottptn said:**
> One of the excellent texts for learning Python is "[A Byte of Python]("http://www.swaroopch.com/notes/Python#Download")" by Swaroop CH . This book has been made available for free download by the author . Really a good book to learn Python.

Yes. I am learning from that book only. :)

---

### Post by rnodal on 2008-10-09
OP, if your goal is to learn C then do just that. Like someone mentioned before, write your own code that way you learn. Don't be afraid to struggle. If you get to a point where you can't find the solution then by all means go ahead and ask a question. But please, do not listen to all these comments about learning language X. Unfortunately it is a trend in this forum to automatically recommend an alternative to C/C++/PHP etc. As you mentioned, you want to learn C so DO that. If you are learning programming for the first time then it could be debated which language you should learn first. The way I see it. At some point in your life you will find yourself needing to use a scripting language or a compiled language so in my honest opinion it does not matter. Whatever you do stick to it and then move into another. 

-r

---

### Post by LaRoza on 2008-10-09
> **rnodal said:**
> OP, if your goal is to learn C then do just that. Like someone mentioned before, write your own code that way you learn. Don't be afraid to struggle. If you get to a point where you can't find the solution then by all means go ahead and ask a question. But please, do not listen to all these comments about learning language X. Unfortunately it is a trend in this forum to automatically recommend an alternative to C/C++/PHP etc. As you mentioned, you want to learn C so DO that. If you are learning programming for the first time then it could be debated which language you should learn first. The way I see it. At some point in your life you will find yourself needing to use a scripting language or a compiled language so in my honest opinion it does not matter. Whatever you do stick to it and then move into another. 

-r

If you follow this advice to ignore other advice, take my advice to ignore this advice.

---

### Post by nvteighen on 2008-10-09
> **rnodal said:**
> OP, if your goal is to learn C then do just that. Like someone mentioned before, write your own code that way you learn. Don't be afraid to struggle. If you get to a point where you can't find the solution then by all means go ahead and ask a question. But please, do not listen to all these comments about learning language X. Unfortunately it is a trend in this forum to automatically recommend an alternative to C/C++/PHP etc. As you mentioned, you want to learn C so DO that. If you are learning programming for the first time then it could be debated which language you should learn first. The way I see it. At some point in your life you will find yourself needing to use a scripting language or a compiled language so in my honest opinion it does not matter. Whatever you do stick to it and then move into another. 

-r

Have you read my post's last paragraph?

> **nvteighen said:**
> Of course, if you already have learned some C, that knowledge will be useful. Moreover, all programmers should know C. What I suggest you is to give priority to a simpler language; this doesn't mean you should leave C aside... If you can, you could learn both at the same time or apply the general programming concepts you learned by learning C...

I think I was pretty clear on stating that OP shouldn't abandon what he/she began, but that it would be better to complement it with something else.

---

### Post by rnodal on 2008-10-09
> **LaRoza said:**
> If you follow this advice to ignore other advice, take my advice to ignore this advice.

I think you misunderstood me. I did say that if OP is learning programming for the first time then it can be argued which programming OP should start with but if OP wants to learn C then advices like learn language x is out of place.

-r

---

### Post by rnodal on 2008-10-09
[QUOTE=nvteighen]Have you read my post's last paragraph?[/QUOTE]
I missed it actually. I actually wrote my post out of anger that every time someone comes to this forum saying I want to learn C/C++ etc someone jumps and says  "You should learn this language....". Please stop that. The OP is not asking "What language should I use for ....?". Unless I'm missing something, when you program you design an algorithm first in a logical way using your brain and then you implement it following the rules of the language that you use. How is the problem of factoring a number, lets say, "different" in C/C++/PHP/Perl/Python/Etc? To me it is the same. They always through the "programming concepts" around. Could someone define "programming concepts" for me so maybe I can understand why when someone says "I'm studying C...." there needs to be a need for "You should learn ... instead."?

-r

---

### Post by Sinkingships7 on 2008-10-09
> **rnodal said:**
> I think you misunderstood me. I did say that if OP is learning programming for the first time then it can be argued which programming OP should start with but if OP wants to learn C then advices like learn language x is out of place.

-r

Wrong. It is not out of place. Let's say you need to get to destination <x> from starting point <y>. When you yourself map it out, you determine that you will have to drive 150 miles to reach your destination. If you stop at a gas station somewhere and someone offers you a shortcut that will allow you to reach your destination in 75 miles instead of 150, are they out of place for suggesting a better alternative?

[quote=LaRoza]If you follow this advice to ignore other advice, take my advice to ignore this advice.[/quote]
Very clever! :)

---

### Post by pmasiar on 2008-10-09
> **rnodal said:**
> OP, if your goal is to learn C then do just that. ...
But please, do not listen to all these comments about learning language X. Unfortunately it is a trend in this forum to automatically recommend an alternative to C/C++/PHP etc.

Please do not listen to people who are against languages - listen only people who are FOR a language!

Yes, learn C - but as second language, it will by faster that way.

> Don't be afraid to struggle. 

And the more OP struggles, the more sure OP is that randomly selected first path is the right path, correct? 8-)

> If you are learning programming for the first time then it could be debated which language you should learn first. 

Yes, it was debated many times (see stickies) and Python is recommended by majority. :-)

OP: here is small but noisy minority which strongly believes in existence of a cabal promoting Python on this forum, and this noisy minority relentlessly try to entice others to learn programming "hard way", by starting in C, C++ or other complicated languages - most of them know only that one language and feel threatened if beginners will learn simpler languages and overcome them. Compared to that, most people promoting Python know many languages, some (like me) more than a dozen, and can compare languages not from prejudice and ignorance but from experience.

> At some point in your life you will find yourself needing to use a scripting language or a compiled language so in my honest opinion it does not matter. 

So why you argue against opinion of other, who have experience that order **does** matter? And that Python is better language for beginner than C?

> Whatever you do stick to it and then move into another. 

This is really stupid advice: if OP started with less optimal language, why would you advice to stick to it? Experienced people suggest to learn the simpler language (like Python) first, **then** continue to learn more, like C (which I suggest as best **second** language) ;-)

---

### Post by nvteighen on 2008-10-09
> **rnodal said:**
> I think you misunderstood me. I did say that if OP is learning programming for the first time then it can be argued which programming OP should start with but if OP wants to learn C then advices like learn language x is out of place.

-r

I agree with you that only in that case such an advice is appropriate and that if OP has prior experience, then it's clearly out-of-place... But, if you read my post again, you'll notice all my advice is under the condition "Is C your first programming language? If yes, ...". You're talking to a Linguistics student, I am trained to exploit all holes in languages :D

---

### Post by pmasiar on 2008-10-09
> **rnodal said:**
> I actually wrote my post out of anger that every time someone comes to this forum saying I want to learn C/C++ etc someone jumps and says  "You should learn this language....". Please stop that. 

No I will not.

OP who asks how to learn C/C++ is misleadingly informed by people with little experience that C or C++ are good languages for beginners, because they are "widely used". But that criteria is:
1) irrelevant to a beginner who needs language easy to learn
2) ignores that Python is also widely used (even if less than C) - that noisy minority just lacks experience in it
3) excellent language to know anyway, because is very complementary to C: Python is best tool to solve 80% of simple problems where CPU efficiency is not the most important criteria, but effective use of programmer time is important.

> The OP is not asking "What language should I use for ....?". 

Because OP is asking wrong question. Asking right question is halfway to correct answer :-)

> When you program you design an algorithm in a logical way and then you implemented following the rules of the language. 

Exactly. So best way to learn programming is to learn simple language which allows you to implement design with most flexibility. Which is not C nor C++. C code is fast but writing the code is slow. 8-)

> Could someone define "programming concepts" for me so maybe I can understand why when someone says "I'm studying C...." there needs to be a need for "You should learn ... instead."?

See stickies.

---

### Post by rnodal on 2008-10-09
[QUOTE=Sinkingships7]Wrong. It is not out of place. Let's say you need to get to destination <x> from starting point <y>. When you yourself map it out, you determine that you will have to drive 150 miles to reach your destination. If you stop at a gas station somewhere and someone offers you a shortcut that will allow you to reach your destination in 75 miles instead of 150, are they out of place for suggesting a better alternative?
[/QUOTE]

If you consider learning another language first so then you can move to another language in my opinion it is more of like an alternate route and not a shortcut.  

As I said before the OP said "I'm studying C..." he did not say "I'm new to programming..." therefore I stand correct.

-r

---

### Post by rnodal on 2008-10-09
> **nvteighen said:**
> I agree with you that only in that case such an advice is appropriate and that if OP has prior experience, then it's clearly out-of-place... But, if you read my post again, you'll notice all my advice is under the condition "Is C your first programming language? If yes, ...". You're talking to a Linguistics student, I am trained to exploit all holes in languages :D

Well I can NOT argue there but I did mentioned that I missed your post ;).

-r

---

### Post by rnodal on 2008-10-09
[QUOTE=pmasiar]Please do not listen to people who are against languages - listen only people who are FOR a language!
[/QUOTE]

Since when I am against a programming language?

[QUOTE=pmasiar]
And the more OP struggles, the more sure OP is that randomly selected first path is the right path, correct? 8-)
[/QUOTE]

Since when struggling is not part of learning?

[QUOTE=pmasiar]
Yes, it was debated many times (see stickies) and Python is recommended by majority. :-)
[/QUOTE]

Sometimes the majority is not right. And as far as I am concerned the OP is not learning programming for the first time.

[QUOTE=pmasiar]
OP: here is small but noisy minority which strongly believes in existence of a cabal promoting Python on this forum, and this noisy minority relentlessly try to entice others to learn programming "hard way", by starting in C, C++ or other complicated languages - most of them know only that one language and feel threatened if beginners will learn simpler languages and overcome them. Compared to that, most people promoting Python know many languages, some (like me) more than a dozen, and can compare languages not from prejudice and ignorance but from experience.
[/QUOTE]

I never said for OP to learn C/C++ for the first time. I said, if you want to learn C then learn C. Do not learn python (since you mentioned) and then learn C. You consider me part of a small group yet every post of yours promotes python so should I call you FAN BOY!?

 [QUOTE=pmasiar]
So why you argue against opinion of other, who have experience that order **does** matter? And that Python is better language for beginner than C?
[/QUOTE]

One more time you are assuming the OP is a beginner but I'm not.


[QUOTE=pmasiar]
This is really stupid advice: if OP started with less optimal language, why would you advice to stick to it? Experienced people suggest to learn the simpler language (like Python) first, **then** continue to learn more, like C (which I suggest as best **second** language) ;-)
[/QUOTE]

I apologize for having a hard time expressing myself in English (since is not my first language, no python or C/C++ were not also my first languages) and not getting my message across the f*cking right way so you can understand that I was advising against language hoping.   

-r

---

### Post by rnodal on 2008-10-09
[QUOTE=pmasiar]
 C code is fast but writing the code is slow. 8-)
[/QUOTE]

Most of the good things in life are like that, it takes time.:)

-r

---

### Post by Sinkingships7 on 2008-10-09
> **rnodal said:**
> 
I apologize for having a hard time expressing myself in English (since is not my first language, no python or C/C++ were not also my first languages) and not getting my message across the f*cking right way so you can understand that I was advising against language hoping.   

-r

STOP!

Banhammertime!

---

### Post by pmasiar on 2008-10-09
> **rnodal said:**
> Since when struggling is not part of learning?

It is, but glorification of the strggling will make you into a marine, not a competent programmer. If you ever read Camel book, you know that three virtues of programmer is lazyness, impatience and hubris 8-)

> Sometimes the majority is not right. 

Yes, but quite often it is ;-)

> One more time you are assuming the OP is a beginner but I'm not.

OK let's wait for OP's response - my ESP says  OP is green beginner.

> I apologize for having a hard time expressing myself in English (since is not my first language, no python or C/C++ were not also my first languages) 

Exactly my situation in every count ;-)

---

### Post by pmasiar on 2008-10-09
> **rnodal said:**
> Most of the good things in life are like that, it takes time.:)

Yes, but it does not mean that the road which takes the most time (C) is the best one. Quite the opposite: plenty of people can muddle by using Python as the single language, but surviving with C alone would be much harder. Any competent C programmer knows couple more languages for solving problems where speed is NOT critical - as often is the case.

---

### Post by rnodal on 2008-10-09
[QUOTE=pmasiar]

OK let's wait for OP's response - my ESP says  OP is green beginner.

[/QUOTE]

I think that is a great idea. It seems that we have been more into this that OP has :).

-r

---

### Post by rnodal on 2008-10-09
> **pmasiar said:**
> Yes, but it does not mean that the road which takes the most time (C) is the best one. Quite the opposite: plenty of people can muddle by using Python as the single language, but surviving with C alone would be much harder. Any competent C programmer knows couple more languages for solving problems where speed is NOT critical - as often is the case.

Agreed and that's why I said that at some points you will find yourself doing one of the two or both. I never imagined that I will ever touch a programming language that was not ASM/C/C++ and so far I have been doing quite a lot of perl and php. I would like to of course add python to the list :). The ironic thing here is that one of my goal for my project is to support a scripting language that resembles a lot python. Of course that is far in the future (I still have no even thought about how I'm going to do this :) ).

-r

---

### Post by lisati on 2008-10-09
> **pmasiar said:**
>  Any competent C programmer knows couple more languages for solving problems where speed is NOT critical - as often is the case.

Knowing the basics of a couple of languages is always useful, regardless of whether it's C or not....amongst other things, it can sometimes help you find a solution to a particular problem more easily. 

(insert irrelevant rant about preferences here) 

Having said that, if the OP wants to learn C, then go for it!

Although not proficient with the language, I have enough knowledge C to be able to follow a simple program, which is sometimes useful in reading discussions on this forum.

---

### Post by benreilly013181 on 2008-10-09
Thanks for the code, just wanna use it to compare to what i'm doing so that i can easily, catch up to it.

Thanks for all the advise guys & i apologize for bothering.

I appreciate all the info & your help. Thanks so much....

---

### Post by benreilly013181 on 2008-10-09
For just FYI guys, YEAH i am a beginner in C and i want to learn it the fastest way i can so i was asking for codes and explanation for that. If you could give me, sites where codes are in step by step explanation, it'll be very helpful. I want to learn C for now and i'll stick to that. I'll try to study PHYTON maybe but what i need is C.

I apologize guys for this bothering & i am thankful to those who helps so relentlessly.

You're all a big help; others who makes me want to pursue more on this and others who makes me learn it the fastest way and that fastest way for me is the code itself and the explanation for that, for this i'm so much THANKFUL to all of you.

You don't have to argue about me guys but thanks anyway.

---

### Post by LaRoza on 2008-10-10
> **Sinkingships7 said:**
> 
Very clever! :)

Thanks :-)

> **rnodal said:**
> 
I apologize for having a hard time expressing myself in English (since is not my first language, no python or C/C++ were not also my first languages) and not getting my message across the f*cking right way so you can understand that I was advising against language hoping.   


Please don't use masked swear words (explicitly against the CoC) and I think you meant "hopping", not "hoping".

> **benreilly013181 said:**
> For just FYI guys, YEAH i am a beginner in C and i want to learn it the fastest way i can so i was asking for codes and explanation for that. If you could give me, sites where codes are in step by step explanation, it'll be very helpful. I want to learn C for now and i'll stick to that. I'll try to study PHYTON maybe but what i need is C.


You can try my wiki for learning it.

I don't know if it applies to C, but it has been found in studies that learning Python then Java leads to quicker Java proficiency than starting with Java.

C is an extremely simple language, if you already know *programming*, otherwise, it is very complicated.

---

### Post by dribeas on 2008-10-10
> **benreilly013181 said:**
> You don't have to argue about me guys but thanks anyway.

Don't worry, it is not about you, it is a long standing fight over first language to be learnt. Funny part is that there is an agreement on the subject but not on the form.

I can agree that C is not the best first language, but I won't ever agree in pushing 'learn python' into any beginner as is your case. There might be other reasons to elect a language than learning curve. I try to keep out of these useless discussions, even if I cannot really help jumping each so often :)

---

### Post by Canis familiaris on 2008-10-10
/me pushes C++ with all my might because it's the only language I know.
/me bashes Python, Perl, PHP, Lisp and all languages I'm not well versed with...

BAWWWWWWWWWWWW

</joke>

Personally I think any language is great for learning.
But with my only 3 day "experience" of python, I can say it was much quicker to learn. Maybe I suppose this is because it's my second programming language but the fact that so many things that you don't have to care about in Python, you have to care about in C and that will probably ease steps of beginner.
But C++ is also a good first programming language too, at least for me. :)
I guess any programming langauge is good...at least for people who want to enjoy programming and just not "learn" it for getting good jobs, or such.

---

### Post by scourge on 2008-10-10
> **pmasiar said:**
> Ie test if some string is a palindrome in Python is 3 lines of code calling a standard library functions.

[php]
# enter this in IDLE
def is_palindrome(text):
	copy = list(text) # convert text to list of characters
	copy.reverse()    # and reverse the list
	return text == ''.join(copy)
[/php]


That's not how I would do it. Why not use slices? I think it's one of the first things a Python programmer should learn anyway. Like this:

```

def is_palindrome(text):
	return text == text[::-1]

```

I benchmarked it, and it's about 5.5 times faster as well.


I'm staying out of the C vs. Python debate, everything has been said already. But I do have to say that I appreciate Python more now that I'm using it on a university course where I have to write a ton of little text-processing applications.

---

### Post by Canis familiaris on 2008-10-10
> **scourge said:**
> That's not how I would do it. Why not use slices? I think it's one of the first things a Python programmer should learn anyway. Like this:

```

def is_palindrome(text):
	return text == text[::-1]

```

I benchmarked it, and it's about 5.5 times faster as well.


I'm staying out of the C vs. Python debate, everything has been said already. But I do have to say that I appreciate Python more now that I'm using it on a university course where I have to write a ton of little text-processing applications.

Can you explain how '::' works in the text string. I understand how ':' works but now how :: works

---

### Post by pmasiar on 2008-10-10
> **scourge said:**
> Why not use slices? I think it's one of the first things a Python programmer should learn anyway.

yes, but your solution looks like magic. I wanted to show beginner how program in Python can be obvious, and show the steps of solving a problem: create structure which helps you to model the problem, and process the data using this structure.

Slices are fundamental to Python but your solution is rather advanced use of slices. I like it ;-)

> I benchmarked it, and it's about 5.5 times faster as well.

Of course, my solution creates whole bunch of objects. My focus was on obviousness.

---

### Post by rnodal on 2008-10-10
[QUOTE=LaRoza]

Please don't use masked swear words (explicitly against the CoC) and I think you meant "hopping", not "hoping".

[/QUOTE]

Please accept my apologies. And thanks for the correction.

-r

---

### Post by mike_g on 2008-10-10
> **dribeas said:**
> I can agree that C is not the best first language, but I won't ever agree in pushing 'learn python' into any beginner as is your case. There might be other reasons to elect a language than learning curve. I try to keep out of these useless discussions, even if I cannot really help jumping each so often :)
Yep, I agree. 

IMO when someone starts a thread asking for help with C and it degrades into yet another argument about Python the thread should be split with the tail end dumped in recurring discussions. After all this must be the most commonly recurring discussion on this board :P

---

### Post by LaRoza on 2008-10-10
> **rnodal said:**
> Please accept my apologies. And thanks for the correction.

-r

Its alright, I personally rarely mod in this forum but I have seen things I ignored get reported or something and another mod act on it, so I figured I'd try to prevent such things from happening.

> **mike_g said:**
> 
IMO when someone starts a thread asking for help with C and it degrades into yet another argument about Python the thread should be split with the tail end dumped in recurring discussions. After all this must be the most commonly recurring discussion on this board :P

Actually, I think it is the people who respond to the Python posts that bring it off track. It is like stringing a bunch of beads of knowledge for the OP, but when Python is mentioned, that bead is then used to make a circle which gets no where instead of adding to it.

No one got hurt from knowing too much. I wish someone gave me advice when I started, because I knew absolutely nothing (and didn't have the internet at home) so I went by what was on the cover of programming books in the bookstore.

---

### Post by pmasiar on 2008-10-10
> **mike_g said:**
> IMO when someone starts a thread asking for help with C and it degrades into yet another argument about Python 

IMO this thread was about learning programming, and OP was misled into thinking that C is the best way to do it, which is wrong, and I pointed it out.

Quite often people have hard time to solve a problem because they ask wrong question, as is obvious in this case. And yes, this mistake is rather widespread, sadly.

Best way to solve problems, in my experience, is to **question unstated assumptions**, before diving into solving the stated problems. Quite often the person asking question is not expert in the problem area (duh, obviously, otherwise would not ask, right?), but has wrong bias and preconceptions. So if you solve problem as asked, instead to understand what the real problem is, you may solve the wrong problem, as is often the case.

---

### Post by scourge on 2008-10-10
> **Anurag_panda said:**
> Can you explain how '::' works in the text string. I understand how ':' works but now how :: works

text[::-1] is the same as text[-1::-1]. So we start the slice from the end (the first -1), we don't specify where the slice ends (nothing between the colons), and we traverse the original string in reverse order (the second -1).

So if I wanted to reverse the string, but cut off the first two characters, I would use text[-1:1:-1].

---

### Post by scourge on 2008-10-10
> **pmasiar said:**
> yes, but your solution looks like magic. I wanted to show beginner how program in Python can be obvious, and show the steps of solving a problem: create structure which helps you to model the problem, and process the data using this structure.

Okay, I guess you solution is more obvious, though a beginner may wonder what ''.join(copy) does and why it's needed.

---

### Post by mike_g on 2008-10-10
> Actually, I think it is the people who respond to the Python posts that bring it off track. 
Yes, they usually are. I never said otherwise, but the ensuing arguments are inane never the less considering the amount of times we have been here before.

> IMO this thread was about learning programming, and OP was misled into thinking that C is the best way to do it, which is wrong, and I pointed it out.
What makes you believe that the OP was mislead into anything. He asked for help with a C program. 
> Best way to solve problems, in my experience, is to question unstated assumptions
I don't perceive any unstated assumptions from the OP that C is the best language. From your post you seem to be inventing language wars in your mind before they even exist. Maybe its just something you long for ;)
> So if you solve problem as asked, instead to understand what the real problem is, you may solve the wrong problem
Personally I dont consider "not using Python" to be the root problem of everything :) Although I would agree that the OP may find the task easier to accomplish in Python, same as it would be in any other HLL; however as we all know by now, on this board it always ends up in tears. So why bother?

---

### Post by pmasiar on 2008-10-10
> **mike_g said:**
> What makes you believe that the OP was mislead into anything. He asked for help with a C program. 

What makes you to assume that decision to learn  C was taken after careful consideration of other better options?

> I don't perceive any unstated assumptions from the OP that C is the best language. From your post you seem to be inventing language wars in your mind before they even exist. Maybe its just something you long for ;)

Maybe you project your own thinking and longing for language war?

C is excellent language (and I like it), but not as first language for beginners. But you are part of that small but vocal minority which raises exactly the same noise every time. Is there a secret society aimed to mislead beginners?

> Personally I dont consider "not using Python" to be the root problem of everything :) 

What makes you think I do? Some unstated assumptions? 8-)

> Although I would agree that the OP may find the task easier to accomplish in Python, same as it would be in any other HLL; 

Any HLL would be better advice for beginner than C. But you did not recommended any other HLL, did you?

> however as we all know by now, on this board it always ends up in tears. So why bother?

Exactly. Why you cherish being part of noisy minority which bothers to raise exactly same complains in every thread about beginning programming, and inevitably run out of arguments is every one? Why won't you create a thread about first language to learn, or better find one from stickies, and contribute there? Do you hope that with this noise you can manage mislead some beginners into less optimal way of learning?

---

### Post by lisati on 2008-10-10
How are we getting on helping the OP with the original problem?

---

### Post by gomputor on 2008-10-10
> **lisati said:**
> How are we getting on helping the OP with the original problem?

Let us first decide on which the 'original problem' really is and later we can see about that!
In the meantime the OP can learn a couple of languages to keep him busy.
:lolflag:

---

### Post by scourge on 2008-10-10
> **lisati said:**
> How are we getting on helping the OP with the original problem?

The problem was pretty much solved on the first page, although the solutions weren't all optimal (using strlen() needlessly in a tight loop, etc.).

Here's my solution:
```

#include <stdio.h>
#include <string.h>

#define BUF_SIZE 20

static int is_palindrome(const char *text)
{
	int i;
	int len = strlen(text);
	
	for (i = 0; i < len; i++) {
		if (text[i] != text[len - i - 1])
			return 0;
	}
	
	return 1;
}

int main(void)
{
	char text[BUF_SIZE];
	char *lastc;
	
	printf("Enter string: ");
	fgets(text, BUF_SIZE, stdin);
	
	lastc = text + strlen(text) - 1;
	if (*lastc == '\n')
		*lastc = '\0';
	
	if (is_palindrome(text))
		printf("Entered string \"%s\" is a palindrome\n", text);
	else
		printf("Entered string \"%s\" is not a palindrome\n", text);

	return 0;
}

```

---

### Post by Tomosaur on 2008-10-11
Don't know if this has been covered since it's more of a side-issue, but worth knowing for future reference anyway :P

The actual reason the main method needs a return value is that whatever it returns will be the exit code for the program's execution. Normally, this would be '0' to signify that the program exited normally. Other times a '1' may signify that whatever the user wanted to achieve couldn't be achieved, but the program functioned as normal otherwise. There are probably some standards you should stick to, but many people simply overlook it or consider it irrelevant.

Return codes are important because a well written program should **never** just crash. If problems occur during execution, the program should either deal with it or exit gracefully, alerting the user AND providing a relevant return code. Not everybody ever bothers with anything other than simply returning '0' though, regardless of whether or not something disastrous happened.

A **very** good time to use the main method's return value properly is when your program is likely to be called from a script. It helps find problems and allows the script developer to control everything much more easily.

A quick exercise:
```

int main(int arg, char * argv[]){
    return 12;
}

```Compile that, then in the terminal, run the program. Once it's finished executing, use the following to get the program's exit / return value:
```

echo $?

```(The '$?' is the bash reserved variable for the exit code of the last foreground program executed).

Some command line apps use return values which allow scripters much better control, allows easier error finding etc. The 'ls' command, for example, has this to say:
```

Exit status is 0 if OK, 1 if minor problems, 2 if serious trouble.

```So there you go! Potentially useless information but worth knowing anyway :)

---

### Post by rnodal on 2008-10-11
> So there you go! Potentially useless information but worth knowing anyway :)

I don't agree with you (just kidding). :) This is a must know for anyone that wants to be a good and responsible programmer. If you want to develop for Linux/Unix this is must since like you said, when you call a program through a script the return code is a very important information. I would really hate for a script to output a lot of garbage text like "I could not read file...." instead of returning a code that represents something like that. Thanks for bringing that up (even thought I think someone made a reference to it in one of the first posts I believe).

-r

---

### Post by slavik on 2008-10-12
The problem with recommending Python in this thread is that the OP clearly stated that he is "studying about C Programming" ... I know that all the people recommending Python posted with best of intentions, but let's not steer the OP off the track he is on, that is not nice. Things are learned best the hard way, and it is best to learn them early on.

Next, why make things so complicated, why create a variable to store the copy of the string? Why not just check str == str.reverse() ???

Onto the other stuff ...
@OP, have you learned about loops? If you have, I have another suggestion for you which will be faster than all solutions posted ... simply compare the first half of the string with the last half of the string. :) (scourge's solution upto len/2).

and of course a Perl one liner ... (OP, do not pay attention to the following, as it was my exercise in brain twisting)
map { chomp $_; print $_ if($_ eq reverse $_); } <>;

BTW, sorry for late reply. :)

---

### Post by LaRoza on 2008-10-12
> **slavik said:**
> The problem with recommending Python in this thread is that the OP clearly stated that he is "studying about C Programming" ... I know that all the people recommending Python posted with best of intentions, but let's not steer the OP off the track he is on, that is not nice. 

Don't recommend Python...

> 
Things are learned best the hard way, and it is best to learn them early on.

Anyone with any education in psychology or education would say that is not true. Learning the hard way works, but it isn't the best way.

> 
and of course a Perl one liner ... (OP, do not pay attention to the following, as it was my exercise in brain twisting)
map { chomp $_; print $_ if($_ eq reverse $_); } <>;

BTW, sorry for late reply. :)

...while I bring up Perl.

---

### Post by pmasiar on 2008-10-12
> **slavik said:**
> OP clearly stated that he is "studying about C Programming"

but until OP will be back we will not know if he picked (IMHO mistakenly) C as first language, or learning C after being experienced programmer in some HHL.

> ... I know that all the people recommending Python posted with best of intentions, but let's not steer the OP off the track he is on, that is not nice. Things are learned best the hard way, and it is best to learn them early on.

maybe we all should just calm down and wait to OP response if he wants to learn things hard way, or prefers simpler way :-) IMHO hard way might be good for marines, but for programmers? I have my doubts 8-)

> Why not just check str == str.reverse() ???

because string is not a list? And lst.reverse() reverses list in place, without returning value?

---

### Post by slavik on 2008-10-12
why is your assumption that the OP picked the language? and why is it a mistake picking C? in all the studies for first programming language ever scited, never was Python compared against C (only against C++ and Java).

you mean a string is not a string? I would expect that reading a line from stdin would return a string, not a list in a high level language ...

---

### Post by Vox754 on 2008-10-12
> **pmasiar said:**
> 
...
Best way to solve problems, in my experience, is to question unstated assumptions, before diving into solving the stated problems. **Quite often the person asking question ... has wrong bias and preconceptions.** So if you solve problem as asked, instead to understand what the real problem is, you may solve the wrong problem, as is often the case.

The other day I was at the Ubuntu IRC channel, #ubuntu, and someone asked for information on becoming a proficient Bash programmer.

Instead of immediately giving him the link to the "Advance Bash Scripting Guide", I asked him why he wanted to study it in the first place. He said he wanted to write a device driver for his printer, which was unsupported.
Of course, a bunch of people noticed that and we told him that Bash was not actually what he was looking for.

"What do I do, then?" he asked. I told him: "get your facts straight. Learn what programming languages are used to develop drivers, what compilation means, the difference between low-level and high-level languages, the difference between compiled and interpreted languages, etc. Once you are more knowledgeable you may attempt to start programming."
" ...and read the stickies in the Programming Talk subforum."

I think this kind of questioning works best on IRC channels, because you get to ask and answer immediately, there is no delay, whereas in the forums, people tend to be lazy, original posters often don't state their problem correctly, word badly what they want to achieve, and when asked for more information they don't even care to get the message across.
We just have to deal with it.

---

### Post by Vox754 on 2008-10-12
> **mike_g said:**
> ...
I don't perceive any unstated assumptions from the OP that C is the best language. From your post you seem to be inventing language wars in your mind before they even exist. Maybe its just something you long for ;)

Personally I dont consider "not using Python" to be the root problem of everything :) Although I would agree that the OP may find the task easier to accomplish in Python, same as it would be in any other HLL; however as we all know by now, on this board it always ends up in tears. So why bother?

I don't think you are a complete troll or hijacker pmasiar, but what mike_g says is correct, sometimes you push too hard, and it really seems like you want these flamewars.

The *"inventing language wars in your mind before they even exist"* is kinda catchy, I like it.

---

### Post by LaRoza on 2008-10-12
> **Vox754 said:**
> I don't think you are a complete troll or hijacker pmasiar, but what mike_g says is correct, sometimes you push too hard, and it really seems like you want these flamewars.

I don't think he wants flamewars, otherwise, he'd be more clever instead of straightforward ;)

---

### Post by Canis familiaris on 2008-10-12
> **Tomosaur said:**
> 
[code]
int main(int arg, char * argv[]){
    return 12;
}

Thanks but what exactly do the arguments: arg, *argv[] (pointer to array?) do?

---

### Post by cmay on 2008-10-12
[php]  
#include <stdio.h>
char *progname;
int main(int argc,char **argv)
{
      progname=argv[0];
      if(argc ==1)
       {
          printf("%s usage:counts arguments\n",progname);
          return 0;
         }

             printf(" number of argc[%d]\n",argc);
            return 0;
}
[/php]it takes arguments from the commandline.
running this little example will show better than i can explain myself in English.:)

---

### Post by Canis familiaris on 2008-10-12
> **cmay said:**
> [php]  
#include <stdio.h>
char *progname;
int main(int argc,char **argv)
{
      progname=argv[0];
      if(argc ==1)
       {
          printf("%s usage:counts arguments\n",progname);
          return 0;
         }

             printf(" number of argc[%d]\n",argc);
            return 0;
}
[/php]it takes arguments from the commandline.
running this little example will show better than i can explain myself in English.:)

Thanks. 
So I gather argv[i] is used to track arguments, argv[0] is program name,while argc is for the number of arguments. Am I right?

---

### Post by nvteighen on 2008-10-12
> **Anurag_panda said:**
> Thanks. 
So I gather argv[i] is used to track arguments while argc is for the number of arguments. Am I right?
Exactly.

---

### Post by Tomosaur on 2008-10-12
> **Anurag_panda said:**
> Thanks but what exactly do the arguments: arg, *argv[] (pointer to array?) do?

Well in the program I gave they do absolutely nothing :P

But as cmay showed you, it allows command line arguments. The 'arg' (should have really been 'argc' (argument count) to illustrate better, but technically it can be called whatever you want) is the number of arguments given (on the command line, arguments are seperated by a space). The argv[] is the actual array of the command line arguments. argv will contain the path to the executable file as it's first element.

So if you launch a program from the command line using the following command:
```

myProgram -a -b

```Then 'arg' will be '3', and 'argv' will contain the path to the executable, '-a' and '-b' as elements.

---

### Post by pmasiar on 2008-10-12
> **slavik said:**
> why is your assumption that the OP picked the language?

I have hard time to comprehend what you are asking.

> and why is it a mistake picking C? 

C is not recommended as a first language by majority of forum, including me - see stickies. Do you want to reopen that poll?

> in all the studies for first programming language ever scited, never was Python compared against C (only against C++ and Java).

C++ and Java are similar to C: statically typed. C is simpler (not OO) in some sense, but harder in another: too low level, no high-level constructs directly.

> you mean a string is not a string? 

Do you have reading comprehension problem? ;-) I said **string** is not a list. string does not have reverse() method, list does.

> I would expect that reading a line from stdin would return a string, not a list in a high level language ...

it does exctly that.

---

### Post by pmasiar on 2008-10-12
> **Vox754 said:**
> I don't think you are a complete troll or hijacker pmasiar, but what mike_g says is correct, sometimes you push too hard, and it really seems like you want these flamewars.

Thank you for not calling me troll directly ;-)

I am not sure why it is wrong to ask OP how he decided that C is the best language for whatever he wants, and why are so many people so upset if I ask that trivial question.

Or maybe you are famous ESP mage and can read OP's mind? 8-) I cannot, so I always ask. I wish I has as clear ESP vision as you, but alas...

---

### Post by gomputor on 2008-10-12
> **pmasiar said:**
> I am not sure why it is wrong to ask OP how he decided that C is the best language for whatever he wants, and why are so many people so upset if I ask that trivial question.

Can you please point out to me where/when did you make that question to the OP? Because I can't find it myself.

---

### Post by LaRoza on 2008-10-12
> **pmasiar said:**
> 
I am not sure why it is wrong to ask OP how he decided that C is the best language for whatever he wants, and why are so many people so upset if I ask that trivial question.

[http://ubuntuforums.org/showthread.php?t=942709](http://ubuntuforums.org/showthread.php?t=942709)

> 
Or maybe you are famous ESP mage and can read OP's mind? 8-) I cannot, so I always ask. I wish I has as clear ESP vision as you, but alas...

Calling James Randi...

---

### Post by pp. on 2008-10-12
> **benreilly013181 said:**
> ... i'm studying about C Programming. I already installed build-essential ...

> **pmasiar said:**
> Python is easier because it works on much higher level. ... 

Learn basics in Python, after that C will make more sense. Best Python feature is interactive shell, so you can try and learn language one line at a time, without the need to write and compile small programs to test every feature. See wiki in my sig for links.

The subtitle of this forum contains the text:

> The questions do not have to be directly related to Ubuntu and any programming language is allowed. 

After reading this thread twice, I came to the conclusion to suggest the following amendment to the subtitle:

> The questions do not have to be directly related to Ubuntu and any programming language is allowed, provided you know Python. If you don't, you can ask any question, but it has to be about Python which is the only language suitable for beginners.

But then, why go to all that trouble and let the OPs suffer, when we could tell them to drop their attempts to learn those difficult programming languages and spend their time learning to ski which is much better for them, anyway?

---

### Post by LaRoza on 2008-10-12
> **pp. said:**
> 
But then, why go to all that trouble and let the OPs suffer, when we could tell them to drop their attempts to learn those difficult programming languages and spend their time learning to ski which is much better for them, anyway?

Because studies have shown (and personal experience) people gain programming skills by studying certain types of languages before others. As mentioned, learning Python before Java leads to swifter Java proficiency in Java than studying Java only.

The OP can't be given too much information. I'd have been most grateful if someone stopped me in Borders when I was buying "Teach Yourself C++ in 24 Hours" and gave me the O'Reilly book on Python (which was there, but lower and didn't catch my eye) back when I started.

---

### Post by pp. on 2008-10-12
> **LaRoza said:**
> Because studies have shown (and personal experience) people gain programming skills by studying certain types of languages before others. 

I am aware of the existence of such studies.

Still, answering someone who is in the process of learning something by telling "brand x is better and this is how you go about it with brand x" is - ahem - not done where I live.

If you really feel so strongly about brand x, you can politely ***suggest to consider*** brand x. Members who feel they routinely have to suggest brand x to other members on a daily basis can prepare their argumentations in their blogs or - pending permission - in permanently accessible thread of their own to which they can link whenever the need arises.

@op: with my apologies to the further hijacking of his or her thread.

---

### Post by mike_g on 2008-10-12
[quote="pmasiar"]Any HLL would be better advice for beginner than C. But you did not recommended any other HLL, did you?[/quote]
I did not specify any other language because, like I said, I am sick of the language wars and the last thing I would want is to get myself dragged into yet another. I imagine you would like to lure me in then batter me with thousands of reasons to use Python that you have gone over countless times before here.

Anyway, you seem to have missed my point. My point was that I dont agree with constantly pushing advice to switch to X/Y/Z language.

> Why you cherish being part of noisy minority which bothers to raise exactly same complains in every thread about beginning programming, and inevitably run out of arguments is every one? 
And what noisy minority am I a part of then? If you havent already realised, I like Python and would recommend it as a suitable language for a begginer that wants fast results.

> Why won't you create a thread about first language to learn, or better find one from stickies, and contribute there?
Why? I dont particularly care for selling any particular language, but by all means do so yourself. That way you could keep it out of irrelevant threads and save repeating yourself a million times.

> Do you hope that with this noise you can manage mislead some beginners into less optimal way of learning.
How am I misleading beginners? If someone asks a question about C and I can help I often will. Same with other languages. I dont offer my opinion on the optimal way to learn as to me its irrelevant.

---

### Post by pmasiar on 2008-10-12
> **pp. said:**
> But then, why go to all that trouble and let the OPs suffer...

Your post is borderline trolling, and you know that.

I never said "don't ever learn C" - I just happen to think (based on my experience, IMHO longer and more substantial than many other posters) that C is not the best first language: Python is. C is excellent second language.

There is quite noisy minority lacking experience in Python, which considers somehow their own position attacked by other people learning Python, and answering this own insecurity by attacking me for my suggestion to learn Python. And because they cannot argue on issues, they try to sneak characher attack, or, as you do, attack integrity of the forum.

If you feel so strongly about C, why you don't talk about how good it is for beginner? Why you attack character of poster, or integrity of advice in forum?

See [ Lessons about biases learned from language flamewars](http://ubuntuforums.org/showthread.php?t=896087) and also [ It's not wrong not knowing, but it's wrong not wanting to know](http://ubuntuforums.org/showthread.php?t=890695).

Why you feel that I should have my right to express my opinion (different from yours) revoked? I do not want to silence your opinion (just dispite your positions), why so many people are so insistent in silencing me?

Why we cannot wait to OP? I think OP never considered Python, you are sure Python is not answer, but we will never know untill OP responds. So why character attacks?

---

### Post by pmasiar on 2008-10-12
> **mike_g said:**
> I dont offer my opinion on the optimal way to learn as to me its irrelevant.

so why you so vehemently disagree with majority of people in whose experience some language are better suited for beginners, and who consider irresponsible to point to beginner that opinion?

I do not respond to post where I do not have position/opinion. Why you do? And what might be the goal of such response? 

"don't listen to advice from this guy, that advice is wrong, and BTW I have no opinion about the matter, I just want to disagree with that guy" does not make much sense to me - only if it is a disagreement with whatever given person posts. It is personal disagreement, in substance. I am genuinely confused.

---

### Post by LaRoza on 2008-10-12
This is getting out of hand. pmasiar expressed an opinion that is nothing unique and quite logical. 

The OP's question about C has been answered (if not, see the stickies, see my wiki).

Closed.

---


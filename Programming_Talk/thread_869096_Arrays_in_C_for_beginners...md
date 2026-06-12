---
title: "Arrays in C for beginners.."
date: 2008-07-24
forum: Programming Talk
---

### Post by dynamethod on 2008-07-24
Hi there, 


I'm reading through K&R 2nd edition


I'm up to page 20 excersise 1.13 and omfg...


i just cant figure this excersise out, for the life of me.


can someone please recommend me some lighter tutorials? because it seems to me im missing alot from K&R... especially when it comes to arrays regarding this book(so far)

---

### Post by LaRoza on 2008-07-24
> **dynamethod said:**
> 
I'm up to page 20 excersise 1.13 and omfg...

Could you be more specific? I have K&R 2d Edition and I can see no such thing.

> 
i just cant figure this excersise out, for the life of me.
Skip it and come back to it.

> 
can someone please recommend me some lighter tutorials? because it seems to me im missing alot from K&R... especially when it comes to arrays regarding this book(so far)
C is a small language, and K&R is perfect for it. If you find the lower level concepts of C confusing (as they can be), try a high level language with more diverse data structures.

You are in chapter one, so "so far" hold little meaning ;) Arrays will be explained in more depth when you get to pointers.

If you want to stick with C, try my site and check out the C tutorials. However, C will not change, so if K&R didn't work...

---

### Post by Lster on 2008-07-24
How about something like:

[http://www.cprogramming.com/tutorial/c/lesson8.html](http://www.cprogramming.com/tutorial/c/lesson8.html)

But if you describe the problem (you were originally) having, then we may be able to help. :)

---

### Post by LaRoza on 2008-07-24
> **Lster said:**
> 
But if you describe the problem (you were originally) having, then we may be able to help. :)

I can't find what the OP was referencing directly, but I did notice some of the array exercises had possibly confusing words in them.

@OP How about giving the exercise? It may be simpler than you think?

---

### Post by pmasiar on 2008-07-24
> **dynamethod said:**
> I'm up to page 20 excersise 1.13 and omfg...

i just cant figure this excersise out, for the life of me.

can someone please recommend me some lighter tutorials?

Let me guess, is C your first try to learn programming? And some of your friend recommended K&R as excellent book?

Let me break bad news for you: some experienced programmers forgot how it is to be beginner, and give really bad advice to beginner, some even with intention to inflict pain on you (they believe pain is good). See this flamewar: [http://ubuntuforums.org/showthread.php?t=868101](http://ubuntuforums.org/showthread.php?t=868101)

Bad advice like starting with C (which is excellent language for system programming, but too strict and unforgiving for beginners), and K&R book (which is excellent for people with experience in programming in other languages, but not intended for beginners.

Read sticky FAQ: majority of programmers agree that Python is better for beginners (I am looking forward for another flamewar :-)). See wiki in my sig for links specially selected for beginners.

/me running for cover

---

### Post by slavik on 2008-07-24
1.13 ... it might be one to display the histogram of text (where you measure the length of words).

to the OP: keep at it. :) winners never quit, quitters never learn C. :)

---

### Post by dynamethod on 2008-07-24
I was referring to the excersise that asks you to:

"Write a program to print a histogram of the lengths of words in its input"

A bit harsh for only the 13th excersise!

---

### Post by slavik on 2008-07-24
actually, it is not.

the solution is very simple if the problem is exactly that (I don't have the K&R book next to me, sadly).

I remember that problem and I remember the modification of that problem where the histogram must be horizontal (which is a bit more difficult).

EDIT: pmasiar, I really cannot agree with you on switching languages if the OP is having trouble with that problem, since it is pretty much the same difficulty in all languages that can be related to C (Python, Perl, Ruby, Java, C++, etc.)

---

### Post by dynamethod on 2008-07-24
Ah ok, its just that i find the array thing quite difficult to visualise, ill keep at it

---

### Post by iofthemourning on 2008-07-24
In my experience, K&R is really better as a reference manual for someone who already knows C.

If you're really new to programming, I'd recommend learning python. There are tons of great tutorials on the internet.

---

### Post by lisati on 2008-07-24
> **dynamethod said:**
> Ah ok, its just that i find the array thing quite difficult to visualise, ill keep at it
An array is kinda like a list, where you have a name for the whole list (the array name), and a way of referencing the individual items in the list (the index(es))

Hope that helps

---

### Post by LaRoza on 2008-07-24
> **slavik said:**
> 
EDIT: pmasiar, I really cannot agree with you on switching languages if the OP is having trouble with that problem, since it is pretty much the same difficulty in all languages that can be related to C (Python, Perl, Ruby, Java, C++, etc.)

Everyone has trouble when starting, but if it brings her studies to a halt, then there has to be another solution. I had lots of troulbe with C++, it made no sense to me, but I never once stopped trying.

---

### Post by Lster on 2008-07-24
It's hard for me to say without looking at the actual question, but if you mean something that would accept input like:

> hello there im on ubuntu

And produce output like:

> 1: 0
2: 2
3: 0
4: 0
5: 2
6: 1
...

...First just think about finding the length of each word (perhaps printing it to the screen). Then use an array to store the frequency of each word length such that word_length[length] is the number of words with a length of length.

If you get stuck post your code and we can give you some hints but keep trying! :)

---

### Post by dynamethod on 2008-07-24
It's ok actually, i've also got another book called "C Primer Plus, Fith Edition" which is a bit easier reading, i found K&R a bit tearse tbh

---

### Post by nvteighen on 2008-07-24
Just of you haven't looked at it, the GNU C Programming Tutorial is a great resource:

[http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/)

And Lster has given you a good hint.

---

### Post by pmasiar on 2008-07-24
> **slavik said:**
> EDIT: pmasiar, I really cannot agree with you on switching languages if the OP is having trouble with that problem, since it is pretty much the same difficulty in all languages that can be related to C (Python, Perl, Ruby, Java, C++, etc.)

You don't have to agree, just please don't start Turing equivalence on me. We had our unscientific poll, see sticky :-) And don't try to sell me that statically typed languages are as easy to learn as dynamically typed, you agree that your favorite Perl is easier to learn than monstrosity like Java. So... dynamic typing is one less problem to solve right for a beginner, so obviously helps learning (even if inflicts less pain - static typing pain can be handled later, IMHO).

I asked OP if C is his first language (no answer so far). I liked K&R myself (because I had previous programming experience) but authors said it is not for beginners, should I value your opinion over K&R? :-)

---

### Post by dynamethod on 2008-07-24
About that excersise actually i was thinking, would i be cheating if i used say strlen even though i havent come across it in K&R as yet?

That is for finding the length of a word

so say like

```

#include<stdio.h>
#include<string.h>
#define MAXL = 10

int main(void)
{
 int i, wlen, input, word, index[MAXL];
 
 for(i=0;i<MAXL;i++)
  index[i]=0;

 while((input=getchar())!=EOF)
 {
  word=0;
  if(input==' ' || input=='\n' || input=='\t')
  ++word;
  if(input!=' ' || input!='\n' || input!='\t')
  {
   wlen=strlen(input);
   index[word]+wlen;
  }
 }
 return 0;
}


```

Oh and i have tried a few languages now, but never stuck to anything

I've tried python, C++ and now C

I enjoyed python and found that VERY easy to understand, but i want to learn C, no reason i just feel like it.

I stopped teaching myself C++ only because at the time i was tied up with other things, otherwise i would have kept at it(i have forgotten MUCH of the C++ i did teach myself in between then and now though).  The reason im going for C this time instead of C++ is because im told that if i learn C i should find learning C++ a bit easier, so here i am

---

### Post by pmasiar on 2008-07-24
> **dynamethod said:**
> I enjoyed python and found that VERY easy to understand, but i want to learn C, no reason i just feel like it.


In that case, of course C is what you should stick with! :-) I still would recommend to become reasonably competent Python programmer first (just because Python is so much easier to explore in Py shell), and/or stick with books for C beginners.

---

### Post by dynamethod on 2008-07-24
Ok, thats cool ill stick with C Primer Plus for a bit then, but as for the code i pasted before, am i getting warmer?

---

### Post by Lster on 2008-07-24
I don't think it would be cheating but for the fun of it, why don't you code your own function? It's easy enough if you think about the structure of a string ([http://en.wikipedia.org/wiki/Null_character](http://en.wikipedia.org/wiki/Null_character)).

---

### Post by slavik on 2008-07-24
> **pmasiar said:**
> You don't have to agree, just please don't start Turing equivalence on me. We had our unscientific poll, see sticky :-) And don't try to sell me that statically typed languages are as easy to learn as dynamically typed, you agree that your favorite Perl is easier to learn than monstrosity like Java. So... dynamic typing is one less problem to solve right for a beginner, so obviously helps learning (even if inflicts less pain - static typing pain can be handled later, IMHO).

I asked OP if C is his first language (no answer so far). I liked K&R myself (because I had previous programming experience) but authors said it is not for beginners, should I value your opinion over K&R? :-)

you missed my point, my point is that the algorithm can look the same in all those languages. what does the poll have to do with this?

Perl being easier to learn than Java has nothing to do with when it defines types ...

OP: here's a solution, this one will print an equal sign for every regular alphabet character. the histogram will be vertical. the problem you are trying to solve asks for horizontal, I think.

```

#include <stdio.h>

#include <ctype.h>


int main() {

	int character; //character storage

	int flag = 0;  //flag to know whether we printed a newline (1 yes, 0 no)

	while ((character = getchar()) != EOF) {

		if (isalpha(character)) {

			printf("=");

			flag = 0;

		}

		else {

			if (flag == 0) {

				printf("\n");

				flag = 1;

			}

		}

	}

	return 0;

}

```

pmasiar, you really want to say that the above algorithm will be very different in another language (I could do the same in Perl by using regex though).

---

### Post by pmasiar on 2008-07-24
> **slavik]I really cannot agree with you on switching languages if the OP is having trouble with that problem, since it is pretty much the same difficulty in all languages that can be related to C[/quote]

[QUOTE=slavik said:**
> you missed my point, my point is that the algorithm can look the same in all those languages. what does the poll have to do with this?

I was not talking how code looks. I assumed that OP is green beginner (he since clarified his experience, but I did not know that - my ESP is obviously not as strong as yours). I suggested Python as simpler language for beginner, as our FAQ and poll does.

> Perl being easier to learn than Java has nothing to do with when it defines types ...

:confused: you mean when variable name is bound to type? :-) Late binding is not 100% of why Perl is easier than Java, but it is more than 0%. And Perl lacks shell, which is excellent tool to try a language, especially for beginner.

---

### Post by slavik on 2008-07-24
> **pmasiar said:**
> I was not talking how code looks. I assumed that OP is green beginner (he since clarified his experience, but I did not know that - my ESP is obviously not as strong as yours). I suggested Python as simpler language for beginner, as our FAQ and poll does.



:confused: you mean when variable name is bound to type? :-) Late binding is not 100% of why Perl is easier than Java, but it is more than 0%. And Perl lacks shell, which is excellent tool to try a language, especially for beginner.
if an interactive shell is that important, then why not suggest Haskell as a language for beginners? there are no types to think about, everything is a function and there is an interactive shell.

---

### Post by dynamethod on 2008-07-24
It's ok, im finding C Primer Plus MUCH easier to follow :)

---

### Post by pmasiar on 2008-07-24
> **slavik said:**
> if an interactive shell is that important, then why not suggest Haskell as a language for beginners? 

Are you kidding, arguing just for sake to disagree with me, or trying to start a flamewar? Haskel for beginners?

As you very well know, (we discussed that many times, and is mentioned in FAQ), shell is not the only reason why Python is the best for beginners. 

Why you trying to argue about something I never said? because you as forum staff cannot be reported?

---

### Post by LaRoza on 2008-07-24
> **slavik said:**
> if an interactive shell is that important, then why not suggest Haskell as a language for beginners? there are no types to think about, everything is a function and there is an interactive shell.

[http://uazu.net/freeware/psh/](http://uazu.net/freeware/psh/)

> **slavik said:**
> 
pmasiar, you really want to say that the above algorithm will be very different in another language (I could do the same in Perl by using regex though).

I think the point was made with the assumption the OP was learning C as a first language and out of K&R only. This seems to be not the case. 


> **pmasiar said:**
> 
Why you trying to argue about something I never said? because you as forum staff cannot be reported?

Just to let everyone know. staff can be reported and should be reported when there is a breech of the Code of Conduct.

For this thread, no one is acting as staff. As staff, we have to be careful what you say and try to not start flamewars, even by accident. This can be our posts less pointed than we'd like, but it is something we should all learn.

---

### Post by nvteighen on 2008-07-25
I suppose I'm allowed to interrupt your recurrent flamewar by answering the OP's concerns.

> **dynamethod said:**
> About that excersise actually i was thinking, would i be cheating if i used say strlen even though i havent come across it in K&R as yet?

Well, no. In fact, I recommend you to learn what functions you have in the Standard Library, how they work, when to use them, etc. So you avoid reimplementing things others have already done for you (and probably work much better than yours...). Of course, Lster's advice to reimplement strlen() is a nice one for learning, but if you're coding something serious, the more you can profit from reliable libraries, the faster you'll concentrate on the problem.

```

#include<stdio.h>
#include<string.h>
#define MAXL 10 /* Corrected. You don't need the = */

int main(void)
{
 int i, wlen, input, word, index[MAXL];
 
 for(i=0;i<MAXL;i++)
  index[i]=0;

 while((input=getchar())!=EOF)
 {
  word=0;
  if(input==' ' || input=='\n' || input=='\t')
  ++word;
  if(input!=' ' || input!='\n' || input!='\t')
  {
   wlen=strlen(input); /* What type is input of? */
   index[word]+=wlen; /* Corrected. You meant +=, not + */
  }
 }
 return 0;
}


```

There's a problem: you're telling strlen() to calculate the length of an **integer array**. If you want to use strlen(), you should save the string in a char * and apply strlen() to it.

---


---
title: "C language problem"
date: 2008-07-23
forum: Programming Talk
---

### Post by IloveTux on 2008-07-23
```
#include <stdio.h>
void main(void)
{
    int val = 1;
    printf("A test with postfix %d\n", val--);
    printf("The value after decrementation %d\n", val);
    val = 1;
    printf("A test with prefix %d\n", --val);
    printf("The value after decrementation %d\n", val);
}

```
I hope i posted correctly. Sorry if not, i`m a beginner.I need some time to accomodate with the forum.:lolflag:
Anyway, i am learning the c language and i have a problem. This code works great but when i compile it, it says "warning: return type of 'main' is not 'int'. Even with this warning the code works. The problem is that i can`t find any mistakes. I saw even in a c book exactly the same code.
Can someone tell me what`s wrong?

---

### Post by ilrudie on 2008-07-23
try
```
#include <stdio.h>
int main(void)  /*or: int main(int argc, char *argc[]) */
{
    int val = 1;
    printf("A test with postfix %d\n", val--);
    printf("The value after decrementation %d\n", val);
    val = 1;
    printf("A test with prefix %d\n", --val);
    printf("The value after decrementation %d\n", val);
return 0;
}
```Its standard for main to have a return code.  0 for success.  Not zero for error.  Thats what the warning is about.

---

### Post by loganwm on 2008-07-23
```
#include <stdio.h>
void main(void)
{
    int val = 1;
    printf("A test with postfix %d\n", val--);
    printf("The value after decrementation %d\n", val);
    val = 1;
    printf("A test with prefix %d\n", --val);
    printf("The value after decrementation %d\n", val);
}
```

Function "main" is defined to return a voided value.
Change the return of main to "int"

```
#include <stdio.h>
**int** main**()**
{
    int val = 1;
    printf("A test with postfix %d\n", val--);
    printf("The value after decrementation %d\n", val);
    val = 1;
    printf("A test with prefix %d\n", --val);
    printf("The value after decrementation %d\n", val);
}
```

In the second code block I posted the changes are bolded, try that.

---

### Post by ilrudie on 2008-07-23
> **loganwm said:**
> ```
#include <stdio.h>
void main(void)
{
    int val = 1;
    printf("A test with postfix %d\n", val--);
    printf("The value after decrementation %d\n", val);
    val = 1;
    printf("A test with prefix %d\n", --val);
    printf("The value after decrementation %d\n", val);
}
```Function "main" is defined to return a voided value.
Change the return of main to "int"

```
#include <stdio.h>
**int** main**()**
{
    int val = 1;
    printf("A test with postfix %d\n", val--);
    printf("The value after decrementation %d\n", val);
    val = 1;
    printf("A test with prefix %d\n", --val);
    printf("The value after decrementation %d\n", val);
}
```In the second code block I posted the changes are bolded, try that.
You will get an error about no return value.  Add a return 0; at the end and your code is good.  It shouldn't matter that main is void although traditionally i think it should take 2 arguments like 
```
int main (int argc, char *argv[])
```  Havnt written c in a while so i don't recall if thats exactly it but I'm pretty sure thats standard.  This is how you handle command line inputs.  argc is the number of arguments and argv i think is an array of pointers to the beginnings of the string (c has not native string so its actually a character array) of what each argument was.

---

### Post by bruce89 on 2008-07-23
> **ilrudie said:**
> It shouldn't matter that main is void although traditionally i think it should take 2 arguments like 
```
int main (int argc, char *argv[])
```  Havnt written c in a while so i don't recall if thats exactly it but I'm pretty sure thats standard.

It only matters if you are wanting to take in parameters on the command line. Otherwise a standard
[PHP]
int
main (void)
[/PHP]
will do.

---

### Post by ilrudie on 2008-07-23
Yup.  Thats what I was trying to say.  Maybe I didnt describe it well.  Thanks for the backup in simplify my overly complex answer.

---

### Post by IloveTux on 2008-07-23
Thanks very much! It works now..

---

### Post by pmasiar on 2008-07-23
> **IloveTux said:**
> i`m a beginner.... learning the c language 

ISO Standard advice is to start with a language simpler to learn, like Python :-) Now watch the flamewars!

---

### Post by bruce89 on 2008-07-23
> **pmasiar said:**
> ISO Standard advice is to start with a language simpler to learn, like Python :-) Now watch the flamewars!

Not this again. Please answer peoples' questions, don't force your views on them.

For the record, "real" C is ANSI C89.

---

### Post by weresheep on 2008-07-23
A couple of tips for C programming...

Install the manpages-dev package

```
sudo apt-get install manpages-dev
```

This enables you to get help for all the standard C library functions as well as the OS system calls (like read() and connect()). Once installed you can access the help for printf (for instance) by doing...

```
man 3 printf
```

To understand why you need the 3 in the above command look at the section descriptions in the man manual i.e. run...

```
man man
```



Secondly, bookmark the [**C FAQ**](http://c-faq.com/) and use it as a second source (after man pages) of help. It is a brilliant resource.

-weresheep

---

### Post by dribeas on 2008-07-23
> **bruce89 said:**
> For the record, "real" C is ANSI C89.

I believe the current [C standard]("http://www.open-std.org/jtc1/sc22/wg14/") is a little more modern: ISO/IEC 9899 dated in 99, together with three corrigenda TC1, TC2 and TC3, last of which dates from 2007, for those who believe C is obsolete and not changing...

BTW, they are as of now working on some new features for the 'old' standard, as decimal floating point arithmetic...

To keep on the flame war... just wait for C++0x to be standard. :P

---

### Post by bruce89 on 2008-07-23
> **dribeas said:**
> I believe the current [C standard]("http://www.open-std.org/jtc1/sc22/wg14/") is a little more modern: ISO/IEC 9899 dated in 99, together with three corrigenda TC1, TC2 and TC3, last of which dates from 2007, for those who believe C is obsolete and not changing...

I know, but most people seem to keep to C89.

---

### Post by ceclauson on 2008-07-23
> 
ISO Standard advice is to start with a language simpler to learn, like Python  Now watch the flamewars!


Isn't this the definition of trolling?

---

### Post by LaRoza on 2008-07-23
> **ceclauson said:**
> Isn't this the definition of trolling?

No, it is a joke...

Look the the OP's problem:

> 
Anyway, i am learning the c language and i have a problem. This code works great but when i compile it, it says "warning: return type of 'main' is not 'int'. Even with this warning the code works. The problem is that i can`t find any mistakes. I saw even in a c book exactly the same code.
Can someone tell me what`s wrong?

It indicates no experience in programming, and being hung up on a detail that doesn't matter (in the big picture). When I started programming, I never asked questions like this. I read and I researched when I had questions.

---

### Post by dwhitney67 on 2008-07-23
> **pmasiar said:**
> ISO Standard advice is to start with a language simpler to learn, like Python :-) Now watch the flamewars!
Troll!

---

### Post by LaRoza on 2008-07-23
> **dwhitney67 said:**
> Troll!

If people came onto a math forum and asked what the funny looking "E" meant, would you feel it is best to explain what it means or recommend starting somewhere a bit more managable?

---

### Post by dwhitney67 on 2008-07-23
The "funny" E is the greek uppercase symbol for epsilon, and with respect to mathematics, it is used to denote that a collection of (specified/specific) values that should be summed together.

Would I recommend that a person skip their mathematics courses and just rely on a calculator?  Not a chance.

P.S.  From the wiki pages:
*An Internet troll, or simply troll in Internet slang, is someone who posts controversial and usually irrelevant or off-topic messages in an online community, such as an online discussion forum or chat room, with the intention of baiting other users into an emotional response[1] or to generally disrupt normal on-topic discussion.[2]*

---

### Post by slavik on 2008-07-24
@ pmasiar and laroza: personally I am of the opinion of letting people learn from their own mistakes and teaching them to ask proper questions by simply answering whatever they ask (if they want a different answer, they need to ask a different question).

as far as ISO C goes, there are 2 ISO C standards, C89 which has also been adapted by ANSI (C89 and ANSI C are two separate standards although they are the same standard, ANSI is independent of ISO). The second ISO C standard is C99 which adds stuff that was introduced in C++ (// for comments, static variable declaration on the heap like **for (int i = 0; ....**

---

### Post by nvteighen on 2008-07-24
> **dwhitney67 said:**
> The "funny" E is the greek uppercase symbol for epsilon, and with respect to mathematics, it is used to denote that a collection of (specified/specific) values that should be summed together.


No, it's the uppercase of sigma. An uppercase epsilon looks exactly the same as an uppercase E.

Anyway, I don't think it's wrong to start with any decent language. C has the great advantage of having a lot of documentation around... well, you'll profit from that only if you use it, of course.

---

### Post by pmasiar on 2008-07-24
> **slavik said:**
> @ pmasiar and laroza: personally I am of the opinion of letting people learn from their own mistakes and teaching them to ask proper questions by simply answering whatever they ask (if they want a different answer, they need to ask a different question).

I am personally of opinion that if beginner is confused and has no clue how confused and misguided her quest is, best help is to guide it to the path where learning will be more fruitful. It is counterproductive to search for a black cat in a dark room in blindfold. Pain does not help learning and information retention. Pain discourages learning.

Of course now you are forum staff, so Perl won :-)

To all who  suggested I am a troll: I consider you BOFH :-) Quite a lot of people who learned python as second language or later, wish they started with Python. If you love C and are champions it does not mean that C is the best language for beginner - especially for such a green beginner without drive to solve such trivial problem by himself.

---

### Post by dwhitney67 on 2008-07-24
> **pmasiar said:**
> I am personally of opinion that if beginner is confused and has no clue how confused and misguided her quest is, best help is to guide it to the path where learning will be more fruitful. It is counterproductive to search for a black cat in a dark room in blindfold. Pain does not help learning and information retention. Pain discourages learning.

Your statement reminds me of the nonsense I am seeing in today's society... "everybody is a winner!".  Let's coddle everybody and dole out medals for participating in whatever event.  Failure doesn't exist because those who are close to failing are directed into another direction where they will be safe from "danger".

"Pain" is the driving force behind learning, whether you wish to accept it or not.  My one year old daughter learns about pain each time she falls down after taking a few steps.  She will learn that falling is painful and that it should be avoided.

When it comes to programming, I could say that Python is equally as painful to learn as C or assembly language.  It all boils down to the level of pain one can tolerate.  Many, but not all, of the kids coming out of school today are such wimps that it appears they always seek the path of least resistance to any challenge.

As was mentioned in an earlier post, the OP was "lazy" and didn't have the motivational drive to perform a little research to solve an otherwise trivial problem.  I agree with this assessment; however I doubt his/her resolve would be any different if dealing with Python or any other language, given a similarly trivial error.

So if you find C to be to challenging, then don't use, don't knock it down, just mind your own business.  If someone has a query concerning Python, feel free to add your comments.  But to troll in a thread that concerns itself with a language other than the language that you are most comfortable with is low, and frankly insulting to the OP, regardless of their programming prowess.

So please show respect... I know, I know... another virtue not taught today.

---

### Post by pmasiar on 2008-07-24
> **dwhitney67 said:**
> Let's coddle everybody and dole out medals for participating in whatever event.  Failure doesn't exist because those who are close to failing are directed into another direction where they will be safe from "danger".

BS. Read my other posts, I often argue against such attitude, towards giving man fishing rod, not a fish, and I got infractions because my low tolerance to fools.

{quote]"Pain" is the driving force behind learning, whether you wish to accept it or not.  My one year old daughter learns about pain each time she falls down after taking a few steps.  She will learn that falling is painful and that it should be avoided.[/quote]

So I assume you do not have railings? The more pain, the faster the learning? Another BS.

Pain is useful if it helps to guide learning. pain without the rewards is just evilness.

> When it comes to programming, I could say that Python is equally as painful to learn as C or assembly language. 

Don't be ridiculous. Comparing ASM and Python? 

Learning is based on rewards. If you can get little reward, learner is ready to take on more pain to get more reward. Too much pain upfront discourages learning.

> Many, but not all, of the kids coming out of school today are such wimps that it appears they always seek the path of least resistance to any challenge.

Not my kids :-) But adding unnecessary pain does not build character.

> As was mentioned in an earlier post, the OP was "lazy" and didn't have the motivational drive to perform a little research to solve an otherwise trivial problem.

> however I doubt his/her resolve would be any different if dealing with Python or any other language, given a similarly trivial error.

Remains to be seen.

> So if you find C to be to challenging, then don't use, 

C challenging for me? Excuse me I used C back in '80, and it is excellent replacement for what used be solved by ASM. But it does not mean it is good first language for learner. You seems to mix those categories, I wonder why?

> But to troll in a thread that concerns itself with a language other than the language that you are most comfortable...So please show respect... I know, I know... another virtue not taught today.

Listen, kid. If you think Python is the only language I know, and I am just out of the school, let me just tell you that programming in Algol68 was harder than what you are used to :-)

---

### Post by LaRoza on 2008-07-24
> **pmasiar said:**
> I am personally of opinion that if beginner is confused and has no clue how confused and misguided her quest is, best help is to guide it to the path where learning will be more fruitful. It is counterproductive to search for a black cat in a dark room in blindfold. Pain does not help learning and information retention. Pain discourages learning.
Yes, the question indicates a lot of confusing in the future, and will be a hinderance to learning programming.

> 
Of course now you are forum staff, so Perl won :-)
We don't know how that happened...

> 
To all who  suggested I am a troll: I consider you BOFH :-) Quite a lot of people who learned python as second language or later, wish they started with Python. If you love C and are champions it does not mean that C is the best language for beginner - especially for such a green beginner without drive to solve such trivial problem by himself.

+1 I started with C++, and I got through it (without asking questions on forums every warning and error), but I wish I studied something else!

Although since this thread has been solved, there isn't much use in going further in depth. I belive we have threads in the sticky for what languages to start with and why to love, hate, or make fun of other languages.

---

### Post by bruce89 on 2008-07-24
It's your own decision which language(s) you learn, so IMO, you shouldn't preach your own opinions to them. It's no better than all that rediculous "Just use Ubuntu instead of Windows" nonsense.

---

### Post by LaRoza on 2008-07-24
> **bruce89 said:**
> It's your own decision which language(s) you learn, so IMO, you shouldn't preach your own opinions to them. It's no better than all that rediculous "Just use Ubuntu instead of Windows" nonsense.

I agree. This thread was solved and is readdressing something that is in the sticky (what is better to learn first).

As for "Just use Ubuntu instead of Windows", I am shocked we have anything like that on this forum...

Thread closed to prevent flamewars and to make a mountain out of an ant-hill.

---


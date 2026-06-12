---
title: "Question about C's string literals"
date: 2007-02-10
forum: Programming Talk
---

### Post by Bluetech on 2007-02-10
I wrote a little program to demonstrate my question:

```

int main()
{
	char str[] = "My string";
	char *ch = strchr(str, 's');
	printf("%s\n", str);
	*ch = 'S';
	printf("%s\n", str);
	return 0;
}

```

This works as it should. But if i replace the first line to:
```
 char *str = "My string"; 
```
then the line
```
*ch = 'S';
```
Causes a seg fault. Can someone tell me whats the difference between the two declarations?

---

### Post by kpatz on 2007-02-10
String literals in C are read-only.  In your sample code, "My string" is a string literal.

The str[] declaration copies the literal into writable memory (stack or heap).  Therefore, your program can modify the string.

The * declaration initializes a pointer to the literal itself, so you have a pointer to a read-only segment.  If you try to overwrite it, you get the SEGV.

---

### Post by duff on 2007-02-10
char* will place in the string in a static string table
char[] does the same thing, but will allocate memory on your function's stack and copy the string into that space

compile your code with '-S' to get the assembly code if want to see how it gets laid out.

---

### Post by lnostdal on 2007-02-10
[http://www.c-faq.com/decl/strlitinit.html](http://www.c-faq.com/decl/strlitinit.html)

next question is: why does C put stuff that isn't declared `const' into non-writable memory in the first place? .. maybe `const' should have been "stronger" :)

---

### Post by LordHunter317 on 2007-02-10
It's implictly-declared const, just like all other literals.  I'm not sure why anyone would raise issues of "implicit const" with literals, given all the other implict things you can do in C.

---

### Post by lnostdal on 2007-02-10
> **LordHunter317 said:**
> It's implictly-declared const, just like all other literals.  I'm not sure why anyone would raise issues of "implicit const" with literals, given all the other implict things you can do in C.

so ```
int i = 5;
``` is implicitly const -- compared with ```
const int i = 5;
```..?

then do the same with: 
```
char* str = "My string";
```
..and..
```
const char* = "My string";
```

(i understand the differences and reasons here, but i don't care about that because the result is "stupid")

---

### Post by Bluetech on 2007-02-10
> **lnostdal said:**
> [http://www.c-faq.com/decl/strlitinit.html](http://www.c-faq.com/decl/strlitinit.html)

next question is: why does C put stuff that isn't declared `const' into non-writable memory in the first place? .. maybe `const' should have been "stronger" :)

Well, from the same (quite useful, by the way) faq:
[http://www.c-faq.com/ansi/strlitnotconst.html](http://www.c-faq.com/ansi/strlitnotconst.html)

My problem arose from the fact that many books get so excited about the pointer/array interchangeability, that they sometimes fail to mention the differences.

---

### Post by LordHunter317 on 2007-02-10
> **lnostdal said:**
> so ```
int i = 5;
``` is implicitly const -- compared with ```
const int i = 5;
```..?No.  The literal '5' is const.  In fact, it's generally put in as an immediate value.

> (i understand the differences and reasons here,You clearly do not, because your post is nonsense.

>  but i don't care about that because the result is "stupid")Then why are you posting?  If you don't about a subject then don't post about it.  If you do, then stop with this bullshit act because it doesn't stop you from having to defend yourself.  It's hypocritical, childish, annoying, unprofessional and against the spirit of this forum.  Grow up.

---

### Post by lloyd mcclendon on 2007-02-10
sounds like someone has a raging hangover right now

drink some water & try to calm down

---

### Post by lnostdal on 2007-02-10
> You clearly do not, because your post is nonsense.
No it's not. Your post is nonsense (hah! take that). It hasn't even said anything relevant. My post makes perfect sense. Again:

In the first case, no const means I can change the stored data - and const means I cannot change the stored data. Hey, it's _supposed_ to be "CONSTant" - as declared by me, right? While - in the second case, both no const and const means I cannot change the stored data. Oh, yeehz - because _that_ is obviously what I want .. x_x .. You know what? It does not come as a shock to me that this _is_ a Frequently Asked Question. 

(oh, and c++ is way more full of this kind of crap btw. (c is clean as silk compared) -- hah! take that! ahahah! ...)

..disregarding the, interesting I'm sure - details; I don't like the result or the default behavior here. That's not nonsense. It's a fact. What yours or other peoples "facts" are doesn't interfere with this. I already know what the standard "allows", and I (yes; annoying "king dick-head" here .. hi! *waves*) think it's stupid. End of story.

> Then why are you posting? 
Uhm, why are you posting?

>  If you don't about a subject then don't post about it.
If I don't what?

> 
If you do, then stop with this bullshit act because it doesn't stop you from having to defend yourself.  

Defend myself - about what? (maybe I knew this was coming - lol - I'm having a hard time understanding why you even bother)

---

### Post by Wybiral on 2007-02-10
lol... You two... AGAIN? Seriously...

Anyway, I think those problems come up a lot because people don't learn how C compiles certain things. If you understand how C stores that data, then it makes absolute sense.

But, I wont deny the fact that if someone is new to C and doesn't understand what is going on, how that would cause confusion.

But... Once you understand them, C and C++ make a lot of sense. I'm of the mind to say "dump your program to assembly and take a look at what's really going on"

Once you do, C becomes a fast and efficient way to write assembly.

---

### Post by lnostdal on 2007-02-10
> **Wybiral said:**
> lol... You two... AGAIN? Seriously...

lol .. "He started it, mom!"


[quote=wybiral]..the problem you people have with realizing that the world actually is flat and that this makes perfect sense - is based on the fact that you do not go out there and check stuff out for yourselves..[/quote]

..ups.. i mean:


[quote=wybiral]Anyway, I think those problems come up a lot because people don't learn how C compiles certain things. If you understand how C stores that data, then it makes absolute sense.[/quote]

Ah, you've learned by heart that "no const" _actually_ means "const" in _some_ cases? In my world, that does not make sense. Well - at least not in this context.


[quote=wybiral]But, I wont deny the fact that if someone is new to C and doesn't understand what is going on, how that would cause confusion.[/quote]

The reason it does not cause confusion with someone experienced is because they have learned the exception to the rule by heart. That doesn't make the thing itself any less "stoopid". The newbies have a point.


[quote=wybiral]I'm of the mind to say "dump your program to assembly and take a look at what's really going on"[/quote]

Yeahyeahyeah, great. You don't have to view the assembly to see what's going on here. It's simple. You can compile and run it then deduce what is going on by the stuff that happens. And what happens is also explained in tonnes of FAQs and posts on the Internet (string literal ==> char* == non-writable memory .. blabla).

Hey; I love C, and Lisp - but that isn't to say both have what I view as problems and/or parts that I think are "stoopid".

---

### Post by Wybiral on 2007-02-10
Agreed.

Languages are written by people and no person is perfect.
So, in theory, no language is PERFECT.

Not to mention that computers aren't perfect...
So a language to speak to them is going to have quirks.

I guess it just depends what is comfortably quirky for you.

For me... Lisp is hard to read and difficult to manage.
BUT I've heard the same about C++, and I view C++ the exact opposite.

It's just because I am so used to C++ and I prefer it's structure.

I'm sure a language like lisp makes more sense to someone who prefers it's structure and is more used to it.

---

### Post by LordHunter317 on 2007-02-10
> **lnostdal said:**
> It hasn't even said anything relevant.Yes it does.  it shows you do not understand the difference between a literal and a variable.

> In the first case, no const means I can change the stored dataRight.  But that's a property of the **variable**, not of the **literal**.  The difference is clearly paramount and clearly beyond you.

The reason you can modify:```
int i = 5;
``` is because the storage is allocated on the stack, a writable area.  The same applies to:```
char i = 'a';
```

>  While - in the second case, both no const and const means I cannot change the stored data.That's because you bound to the pointed-to type, instead of the pointer.  The issue here is const on the LHS binds to something different.

> It does not come as a shock to me that this _is_ a Frequently Asked Question. I would say that's because the binding rules for const are non-obvious. since we don't write them consistent with the RHS application they use.[2]  Also, people aren't taught hte difference between a pointer, where the pointer is stored, the scope and lifetime of the pointer, and the scope and lifetime of the data the pointer points to.

> I already know what the standard "allows",But you don't.  you confused:```
const char* i;
const int i;
```as being equivalent.  They're not:```
char* const i;
const int i;
```are[1].  The proof is that in the former case, I can still mutate the pointer address.  

> (oh, and c++ is way more full of this kind of crap btw. (c is clean as silk compared) -- hah! take that! ahahah! ...)No, it isn't.  The rules for const are exactly indentical and were only extended to member methods.  And the binding rules are still identical.

> If I don't what?Care.  You said it was stupid and dumb and don't care about the subject.  If you don't care, don't post, especially when you're just wrong and furthering confusion.


[1]One could make the case that they are semantically equivalent, because I'm attempting to mutate the data.  I'm not sure that's a valid definition, since it implies the address of the pointer is somehow less important than the data it points to.  Sometimes this is true, sometimes it is not.  However, the semantically equivalent definition seems loose given that const T* always allows me to mutate a pointer address.

[2]When you say:```
const char* foo;
```You really mean:```
char const* foo;
```Actually writing code this way is only common with some C++ authors.  It does have the advantage of being consistent with the rules, though visually unappealing somehow (unfamilarity if nothing else).

---

### Post by LordHunter317 on 2007-02-10
> **lnostdal said:**
> In my world, that does not make sense. Well - at least not in this context.It does once you understand the const binding rules.  You don't. 

> The reason it does not cause confusion with someone experienced is because they have learned the exception to the rule by heart.It's not an exception.  The rules are being consistently applied.

---

### Post by lnostdal on 2007-02-11
LordHunter: Listen; you can stop saying that I do not understand because I understand perfectly well. Just to make this short: I like the old default behavior better. It's that simple.

edit: ..and const binding rules is a totally different issue; it has nothing to do with what's going on with a declaration like `char*' where const isn't even mentioned.

---

### Post by LordHunter317 on 2007-02-11
> **lnostdal said:**
> LordHunter: Listen; you can stop saying that I do not understand because I understand perfectly well.You do not.  I proved it with source code.

> Just to make this short: I like the old default behavior better. It's that simple.**There was no old default behavior, *it has never changed.***

> edit: ..and const binding rules is a totally different issue;No, they're not.  They're the proof you don't understand what you're talking about.

> it has nothing to do with what's going on with a declaration like `char*' where const isn't even mentioned.Yeah, but you didn't talk about just char*.  And I answered that case: you made a non-sequitur by talking about properties of varabiles, not literals.  Like I said, the literal is either emitted in a non-writable segment (strings) or generally as an immediate operand (numbers and the like).  In this case, the assembly backs me up.

---

### Post by LordHunter317 on 2007-02-11
If you don't believe me, see the section on Constants and Constant Expressions in the C specification.  In the line:```
int x = 3;
```3 is defined as an integer *constant*.  Its value may not change.  This is no different from "foo bar", it is also constant and may not change.

I'll admit saying "implictly-const" originally was confusion and wasn't a clear enough delineation between variables and literals.  But all literals are constants in C, and whether the variable is declared as const or not is 100% orthogonal to that.

---

### Post by lnostdal on 2007-02-12
No, you are wrong on many points - but I do not care to go into this any further with you as it is a total waste of my time.

---

### Post by LordHunter317 on 2007-02-12
> **lnostdal said:**
>  but I do not care to go into this any further with you as it is a total waste of my time.Right, which is why you were able to use source code, the C standard, and a reasonable application of logic in your defense :rolleyes:.

---

### Post by lnostdal on 2007-02-12
I feel absolutely no need to defend what I've said - it can support itself. I do not care to go into this any further with you as it a total waste of my time.

---

### Post by Arndt on 2007-02-14
> **LordHunter317 said:**
> If you don't believe me, see the section on Constants and Constant Expressions in the C specification.  In the line:```
int x = 3;
```3 is defined as an integer *constant*.  Its value may not change.  This is no different from "foo bar", it is also constant and may not change.

I'll admit saying "implictly-const" originally was confusion and wasn't a clear enough delineation between variables and literals.  But all literals are constants in C, and whether the variable is declared as const or not is 100% orthogonal to that.

Maybe it helps to point out that there is a way to get a warning from gcc in cases like these:

```
$ gcc -Wwrite-strings -c foo.c
grik.c: In function ‘main’:
grik.c:3: warning: initialization discards qualifiers from pointer target type

```

Why this warning is not included in -Wall is probably because this way of writing was correct for a long time.

You can also go the opposite way, and make string literals writable, with another option to gcc.

---

### Post by ameermawia on 2009-04-14
Oh i know this is way too much old thread.
But I wanted to know what this gave(just above) wanted to tell through his post.Why dont peaple writing a post make them selves clear.

Hey you(@ARNDT) what does you want to say through ur post .Can u make ur self clearer?

---

### Post by Jiraiya_sama on 2009-04-14
I have to know, why doesn't gcc/g++ throw an error in this case? Why doesn't it throw an warning when you assign a string literal to a normal pointer by default? Everywhere else if you assign a const to a normal pointer it throws an warning, so why not here?

I did read this:
> Why this warning is not included in -Wall is probably because this way of writing was correct for a long time.

But if it's no longer valid to write to string literals, then why no warning?

---


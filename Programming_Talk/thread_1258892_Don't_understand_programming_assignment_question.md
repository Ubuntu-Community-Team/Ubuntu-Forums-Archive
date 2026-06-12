---
title: "Don't understand programming assignment question"
date: 2009-09-05
forum: Programming Talk
---

### Post by s3a on 2009-09-05
"5. What are the values of first and second in the following code:
   int first = 10;
   int second = 17;
   first = first + second;
   second = first + second;
   first = first - second;
6. Rewrite the code in the previous exercise to be shorter, by declaring the variables together
   and by using the special assignment operators (e.g., +=, -=, *=, and /=) as appropriate."

I've successfully created the program for #5. I don't understand how to make the program different because I don't understand what *+=, -=, *=, and /=* mean. Initially (I read the question too fast), I only picked up on the word different so instead of making a program that had lets say:

something = something;
something = something;
something = something;

I altered it to something like:

something = something; something = something; something = something;

and thought I was done with the question (6).

Basically what I am asking here is for an explanation as to what *+=, -=, *=, and /=* mean.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by jnorthr on 2009-09-05
the use of an arithmetic operator together with the equal sign implies there is only a single variable involved in the logic. Here are two examples:

let a = a + 1
let a += 1

both are identical in achieving the same end result. the 2nd choice just saves a little keyboard action :)

the other operations are the same : save some keystrokes.

first = first + second;  becomes first += second;

---

### Post by socool274 on 2009-09-05
That's easy, for an a = a+b sort of question, it would be a += b. Same with -, and /, an *.

---

### Post by Arndt on 2009-09-06
> **s3a said:**
> "5. What are the values of first and second in the following code:
   int first = 10;
   int second = 17;
   first = first + second;
   second = first + second;
   first = first - second;
6. Rewrite the code in the previous exercise to be shorter, by declaring the variables together
   and by using the special assignment operators (e.g., +=, -=, *=, and /=) as appropriate."

I've successfully created the program for #5. I don't understand how to make the program different because I don't understand what *+=, -=, *=, and /=* mean. Initially (I read the question too fast), I only picked up on the word different so instead of making a program that had lets say:

something = something;
something = something;
something = something;

I altered it to something like:

something = something; something = something; something = something;

and thought I was done with the question (6).

Basically what I am asking here is for an explanation as to what *+=, -=, *=, and /=* mean.

Any help would be greatly appreciated!
Thanks in advance!

Are you really on your own with these assignments? It's never happened to me that I took a course in something, and was not told where to find enough information to learn the appropriate things. Either books, lectures, lecture notes, or specific documentation pages on the Internet.

It's not as if += and the rest are fundamental elements of programming or mathematics, and you supposed to know them - not all programming languages have them. They are quite hard to look up, too, since they are not words.

As far as I know, they do mean the same in all languages where they occur, though, which is a good thing.

---

### Post by DaithiF on 2009-09-06
forum posts don't seem the most efficient way for you to learn java.  From your posts in the last last week it sounds to me like you're trying these assignments without any background reading.  If you're studying Java, surely you must be following some course with book(s), notes etc.  Are you using those before posting?

[LIST]
[*]Don't understand programming assignment question
[*]How do you add numbers in Java?
[*]Moderately complex java program question
[*]Java - Printing only one of the numbers from a certain inputed multi-character number
[*]Java - Swaping the value of two variables
[*]Created two basic java programs succesfully but still have a question about them
[*]Java System.out.println() question on Strings and numbers
[*]Basic Java programming assignment, can't see my mistake
[*]How do I use kate to compile/launch a java program?
[*]Simple Java programming Question (I am a beginner)
[/LIST]

---

### Post by defacto on 2009-09-06
You can not write Java without knowing it's syntax. From your question, we clearly see that you haven't read a single line of your book or other materials you have access to. These operators is an essential part of Java programming course and most probably, are discussed in one of the very first lessons.

```
a = a + b;    // a += b
a = a - b;    // a -= b
```

---

### Post by meson2439 on 2009-09-06
My advice is:

Open up your favorite programming language,  I recommend python for the interactivity. Just type each of this into your python console

```
first=10
second=17
first = first + second
print
second = first + second
print
first = first - second
print
```

Then try replacing = with += -= *= or /=

You'll understand it automatically.

---

### Post by s3a on 2009-09-06
Thanks! I get it now! I do have a book and notes but they show things in a very basic way and not any "creative" ways but yes I do consult those first. I also try to learn as much as I can at home before a course so that I can have better questions to ask my teacher if you know what I mean.

---

### Post by cjnkns on 2009-09-06
I do not frequent this forum much, but I have to say...

I am really, really impressed that the OP was helped and not just simply given the answer!

The cheers for the Ubuntu community's commitment to learning!

---

### Post by MindSz on 2009-09-07
+1

---


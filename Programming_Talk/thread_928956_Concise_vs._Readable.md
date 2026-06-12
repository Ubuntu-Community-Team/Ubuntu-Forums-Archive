---
title: "Concise vs. Readable"
date: 2008-09-24
forum: Programming Talk
---

### Post by akbeancounter on 2008-09-24
What are your thoughts on readability of code?  More specifically, when concise code isn't easy for an outsider to read, and readable code is much longer than it could be, what is your general preference?

Example: One of our early classroom assignments was to write a simple output program.  The most readable version I can think of would look like this:

**Partial C++ code:**
[php]
cout << "CCCCCCC      ++          ++\n";
cout << "CC           ++          ++\n";
cout << "CC       ++++++++++  ++++++++++\n";
cout << "CC           ++          ++\n";
cout << "CCCCCCC      ++          ++\n";
[/php]

It involves a single statement which we learned in week one, and it's obvious even to a non-programmer what this program does.  Recently, though, our Prof. suggested slightly more complicated methods of accomplishing this task, such as using strings:

**Partial C++ code:**
[php]
string line1 = "CCCCCCC      ++          ++\n";
string line2 = "CC           ++          ++\n";
string line3 = "CC       ++++++++++  ++++++++++\n";

cout << line1 << line2 << line 3 << line2 << line 1;
[/php]

It's shorter, so the file will be smaller, but it's not quite as obvious what the code does.  I could probably break it into even more strings to shorten the program further, but again, readability would suffer.

I won't even get into the Prof's suggestions regarding setw and setfill, because that would be far too much effort for such a simple task.  I'm going to assume that she's just trying to relate a new concept to a task we've performed before, not that we should invoke all these new functions just to show that we can.

Back to the original question, though, when readability and brevity are pulling in opposite directions, how much weight do you give to each?

-- A.

---

### Post by LaRoza on 2008-09-24
Just use a comment to show what the string looks like.

---

### Post by nvteighen on 2008-09-24
I'd choose for number two. Yes, it isn't the most obvious piece of code, but it's more concise because of being more modular, which is a good thing... it's not just an obscure piece of concise code and with some effort, you'll see what is the code about.

Yes, the first one is "easier", but is not better programming. IMO, the readability is very much related to be able to break the code into pieces; in the second case, you see that everything related to "preparing data" is written at the top and only the last line executes something.

When the code grows up, code like in your first example would probably be unreadable, I guess.

Thoughts?

---

### Post by themusicwave on 2008-09-24
I tend to side more on the readability side.

However, that example really isn't that hard to figure out.  As Laroza, a comment would help make it more understandable.

Generally, I optimize where I can, but never at the expense of making something unreadable.  If I can compact it and it is still fairly easy to comprehend that is fine.

However, too often I see people doing cute little tricks to make 5 lines of code into 1 or something like that.  Sure that's nice you can make an ugly monstrous line of code and it is a cool trick to show your friends, but don't put it in your program.

This is an issue where you need to find balance usually.  Make it readable, but don't go too crazy.

Also, it often depends on your requirements of the application.  A few times I have written an embedded program that I had to go back and try to compact a bit to get it to fit in the ram of the micro controller.  In that case being concise wins.  

If it is a desktop application, a few extra kilobytes or even megabytes may not be a big deal.

---

### Post by Tomosaur on 2008-09-24
Readability is 'probably' more important for most desktop and trivial applications, but if your app relies on speed, then optimise away. There is no substitute for well documented code though, so regardless of which approach you choose, **always document**. Documenting allows you to get away with horrible looking, but extremely concise code, so if you come across such a situation, I see no real problem in going for the concise route. As long as you make it clear through comments what the hell your code is doing, you should be fine.

---

### Post by akbeancounter on 2008-09-24
> **nvteighen said:**
> I'd choose for number two. Yes, it isn't the most obvious piece of code, but it's more concise because of being more modular, which is a good thing... 

I'm learning that now, as I work with named constants*.  It's much easier to change one constant from '1.50' to '2.00' than to look up and change every line where '1.50' (or an equivalent number intended to accomplish the same task) appears.

> Yes, the first one is "easier", but is not better programming. 

That's why I tried to avoid terms like "easier" or "better."  What is easy to read isn't necessarily easy to code, and neither of these is necessarily the most efficient approach.

Back when I worked as an external auditor, the most important criterion for our audit documentation was, "If an experienced auditor, with no prior knowledge of this particular client, reviewed your work papers, would s/he be able to determine, solely by reading your documentation, what tests you performed and what results you received?"  That's a very long sentence, but one I believe will aid my progression as a programmer.  Since I don't yet know what an experienced programmer sees when s/he looks at source code, I can't yet rely on my own assumptions of good style.

-- A.
* I really really dislike my current textbook, because I consider it a far better reference than a tutorial.  I'm following along with Brian Overland's *C++ Without Fear* and Michael Dawson's *Beginning C++ Through Game Programming*.  Wikis are great and all, but I do most of my reading on a bus.

---

### Post by akbeancounter on 2008-09-24
> **themusicwave said:**
> However, that example really isn't that hard to figure out.  As Laroza, a comment would help make it more understandable.

Sure, but I didn't want to get bogged down in the details, so I used the most trivial program I could think of.

> too often I see people doing cute little tricks to make 5 lines of code into 1 or something like that.  Sure that's nice you can make an ugly monstrous line of code and it is a cool trick to show your friends, but don't put it in your program.


That's kind of where I was going with that.  Is there a benefit to uber-brevity, and is it really worth it if your neighbor* can't figure out how your program works?

-- A.
* I mean this in the Four Freedoms sense, as in "help your neighbor."

---

### Post by Wybiral on 2008-09-25
Generating text... It's not going to be too complex to understand (it doesn't have to look like the text you're generating). However, for more complicated processes, things beyond the triviality of outputting text, you should almost always sacrifice code size for readability (within reason), and you'll understand this more once you have to manage some old code :)

---

### Post by slavik on 2008-09-25
there are also times when certain idioms of the language get invented, because the certain piece of code that is used often and is not very readable comes up so often that it is almost wearing a giant red sign on it as if it was a function with everything spelled out.

---

### Post by Erdaron on 2008-09-25
Readability is not just for other people. I've sometimes gone back to something I myself have written a year ago, and then stared blankly at a page of undocumented logic operations, trying to figure our what it did.

Convoluted compressions of code are acceptable if they provide a significant increase in performance, and are well-explained in documentation.

---

### Post by lisati on 2008-09-25
> **akbeancounter said:**
> What are your thoughts on readability of code?  More specifically, when concise code isn't easy for an outsider to read, and readable code is much longer than it could be, what is your general preference?

Example: One of our early classroom assignments was to write a simple output program.  The most readable version I can think of would look like this:

**Partial C++ code:**
[php]
cout << "CCCCCCC      ++          ++\n";
cout << "CC           ++          ++\n";
cout << "CC       ++++++++++  ++++++++++\n";
cout << "CC           ++          ++\n";
cout << "CCCCCCC      ++          ++\n";
[/php]

It involves a single statement which we learned in week one, and it's obvious even to a non-programmer what this program does.  Recently, though, our Prof. suggested slightly more complicated methods of accomplishing this task, such as using strings:

**Partial C++ code:**
[php]
string line1 = "CCCCCCC      ++          ++\n";
string line2 = "CC           ++          ++\n";
string line3 = "CC       ++++++++++  ++++++++++\n";

cout << line1 << line2 << line 3 << line2 << line 1;
[/php]

It's shorter, so the file will be smaller, but it's not quite as obvious what the code does.  I could probably break it into even more strings to shorten the program further, but again, readability would suffer.

I won't even get into the Prof's suggestions regarding setw and setfill, because that would be far too much effort for such a simple task.  I'm going to assume that she's just trying to relate a new concept to a task we've performed before, not that we should invoke all these new functions just to show that we can.

Back to the original question, though, when readability and brevity are pulling in opposite directions, how much weight do you give to each?

-- A.

If it means getting the functionality of the program working more quickly I'd go for option 1 while developing the program, in the interests of readability while debugging, and then slowly move to option 2 - with comments as required - as the work on finessing the program proceeds. It can be difficult to debug a program if it isn't immediately obvious what it's meant to be doing.

---

### Post by akbeancounter on 2008-09-25
> **Erdaron said:**
> Readability is not just for other people. I've sometimes gone back to something I myself have written a year ago, and then stared blankly at a page of undocumented logic operations, trying to figure our what it did.

That's me in a nutshell.  There are many times when I've built a financial projection or a probability model*, then after it's been used for decision-making, I put it away so I don't have to start from scratch next time.  By the time I come back for it, though, I've lost all context and/or I've progressed enough that I don't understand my own n00bish scribblings.

-- A.
* As the username suggests, I'm an accountant by trade.

---

### Post by Greyed on 2008-09-25
There's a concept in here that isn't touched on.  Concise but readable.

Here's a simple example in Python that isn't contrived.  IE, it was real code.

```

if value != None and value != '':
    do_something()

```

Now, the code is functional and, yes, it is explicit in what it does.  If the value isn't None nor is it an empty string, do something.  But the thing is both of those evaluate to false.  So this if statement is really saying if not false and not false do something.  The more concise statement would be this.

```

if not value:
    do_something()

```

If it's not false, do something.  More concise than the explicit statement above and also easier to read.  Especially when the name of the variable (or function) being tested is a descriptive noun

```

if not raw_input('Shall we play a game?'):
    do_something()
else:
    print 'Oh, the silent type?'

```

To me code is much like writing prose.  Good prose is made when you take away everything that is not needed to convey the intent, but no more.

---

### Post by Tomosaur on 2008-09-25
> **akbeancounter said:**
> What are your thoughts on readability of code?  More specifically, when concise code isn't easy for an outsider to read, and readable code is much longer than it could be, what is your general preference?

Example: One of our early classroom assignments was to write a simple output program.  The most readable version I can think of would look like this:

**Partial C++ code:**
[php]
cout << "CCCCCCC      ++          ++\n";
cout << "CC           ++          ++\n";
cout << "CC       ++++++++++  ++++++++++\n";
cout << "CC           ++          ++\n";
cout << "CCCCCCC      ++          ++\n";
[/php]It involves a single statement which we learned in week one, and it's obvious even to a non-programmer what this program does.  Recently, though, our Prof. suggested slightly more complicated methods of accomplishing this task, such as using strings:



Could you not also do it like this?:
[php]
string line1 = "CCCCCCC      ++          ++\n";
string line2 = "CC           ++          ++\n";
string line3 = "CC       ++++++++++  ++++++++++\n";
       line2 = "CC           ++          ++\n";
       line1 = "CCCCCCC      ++          ++\n";
[/php]I'm pretty sure that g++ would spot the pointlessness of re-assigning values of line1 and line2 and skip them when compiling. This way you have the benefit of readability without the cost of 5 assignments.

I don't really know if this is true, and I'll leave it for someone with more knowledge of g++ to weigh in here, but I'm pretty sure it'd work as described.

Of course, it's probably best to avoid fluff in your code, but I don't think it would have any negative impact on the compiled binary.

---

### Post by dribeas on 2008-09-26
> **Tomosaur said:**
> I'm pretty sure that g++ would spot the pointlessness of re-assigning values of line1 and line2 and skip them when compiling.

This answer is not quite in the line of the OP question, it is more of a side note.

Standard C++ won't allow the compiler to do this [*]. The reason being is that the C++ compiler cannot really know if that assignment is useless or not. Operator = can be overloaded for an specific data type, and it might have side effects. The compiler cannot know before hand any of this. Not even of a 'standard type' as std::string, since the standard defines the interface of the type and not its inner workings.

As a side note, there is one thing that the compiler can assume: copy construction constructs an object that is a exact copy of another. This is used in optimizations of function returns of internal variables. As far as I know, that is the only assumption that the standard allows the compiler to make.

```

T f()
{
   T rtn;
   // operate on rtn
   return rtn; // copy construct an unamed temporary from rtn
               // compilers are allowed to optimize the copy away
}

```

[*] as if a standard could force an implementor... anyway it would not be a standard compiler

---

### Post by Tomosaur on 2008-09-26
> **dribeas said:**
> This answer is not quite in the line of the OP question, it is more of a side note.

Standard C++ won't allow the compiler to do this
[*]. The reason being is that the C++ compiler cannot really know if that assignment is useless or not. Operator = can be overloaded for an specific data type, and it might have side effects. The compiler cannot know before hand any of this. Not even of a 'standard type' as std::string, since the standard defines the interface of the type and not its inner workings.

As a side note, there is one thing that the compiler can assume: copy construction constructs an object that is a exact copy of another. This is used in optimizations of function returns of internal variables. As far as I know, that is the only assumption that the standard allows the compiler to make.

```

T f()
{
   T rtn;
   // operate on rtn
   return rtn; // copy construct an unamed temporary from rtn
               // compilers are allowed to optimize the copy away
}

```
[*] as if a standard could force an implementor... anyway it would not be a standard compiler

Seems like there'd be at least some rudimentary 'needless assignment' logic in the compiler - I understand that the compiler will never know when the assignment is useless or not, but it seems like it should be an option - like 'If assignment 1 = 'x = 1' and assignment 2 = 'x = 1' then delete assignment 2. Of course this doesn't even begin to take into account stuff like multiple threads accessing the same variable or anything, but it seems like it could be part of some 'extreme optimisation' option.

Either way it's straying into stupid territory here - easiest solution is to just do the first three strings then print the 2nd and 1st - it's not like anybody reading it is going to be completely lost.

---


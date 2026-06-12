---
title: "Programming using g++, gdb, and vim not viable?"
date: 2011-02-02
forum: Programming Talk
---

### Post by W-Unit on 2011-02-02
Hi there,

I've been programming (mostly C++) on Windows using Visual Studio for years.
I'm trying to "make the switch" to Linux, more or less, and finding programming to be a very difficult and complicated task now.

Here are some reasons:
1) g++ does not seem to support some C++ language features supported by Visual Studio. The ones I've encountered so far are **enum**s and the **static** modifier. I can work around this, but I'd prefer not to (**enum**s make code SO much more readable, **static**s GREATLY improve code organization)
2) The big one by far. Let's say I compile some code, and there are errors in it. So I go into the code, fix the errors, and try to compile again. About 6 times out of 10, I will get the exact same errors.
This became most obvious when in one particular project, I had a file called "ArgsParser.cpp" that was causing approximately one bazillion errors. So I decided to just scrap the whole thing and replace it with a file called "IOHandler.cpp." After an hour or so of rewriting a fairly major part of this project, I tried compiling again, only to receive a bunch of errors coming from ArgsParser.cpp. Mind you, there WAS NO SUCH FILE ON MY COMPUTER!! And there were no references to it or anything, I am positive. Yet it still complained about all the errors it was getting from ArgsParser.cpp. Um...... What!?!?
3) g++ appears to be very moody. Sometimes, if I have a for loop like this:
```
for (int x=0; x<10; ++x)
cout << x << endl;
```
It will compile fine. Other times, if the code inside the loop is perhaps a bit more complex, it will give some error about changing the variable name of 'x' for "ISO C++ scoping rules." I wish I could reproduce this error and show you the responsible code, but as I said, it just occurs unpredictably and so I regrettably cannot. I've gotten this error many times since trying to make the switch to Linux though.

So, my question is, what's the best way to compile and test programs during the design process on *nix? I'm rather set on learning to use vim as my editor, but this g++ nonsense is simply unacceptable - there needs to be either a simple explanation for all this, or else a better way to go about compiling programs, else I shall forsake attempting to program on Linux. That might sound a bit extreme, but I've got dozens of programs I wrote on Visual Studio that compile and run just fine, and DO NOT make use of any Windows-specific or .NET features, but have hundreds of errors when I try to compile them with g++. That's a bit ridiculous, if you ask me.

Thanks :)

---

### Post by fct on 2011-02-02
The nice thing about C++ standards is that there are many to choose from, and each compiler is unique, just like all the others:

[http://stackoverflow.com/questions/3595750/g-standards-support](http://stackoverflow.com/questions/3595750/g-standards-support)

Visual Studio might allow language constructs that shouldn't be available in C++ standards. Check if you're using C++ enums correctly:

[http://enel.ucalgary.ca/People/Norman/enel315_winter1997/enum_types/#TypeConv](http://enel.ucalgary.ca/People/Norman/enel315_winter1997/enum_types/#TypeConv)

Personally, I'd suggest you try some IDE. Qt Creator, Anjuta, Code::Blocks, Eclipse with CDT...

Don't forget that you're coming from Windows to UNIX development. There is a learning curve and you'll discover that code portability is not as easy as it theoretically should, be it with C++, Java or C#.

Edit: also, 2) is just plain bizarre. Either something's really messed up in your system or you've missed something in your checks.

---

### Post by worksofcraft on 2011-02-02
> **W-Unit said:**
> Hi there,

I've been programming (mostly C++) on Windows using Visual Studio for years.
I'm trying to "make the switch" to Linux, more or less, and finding programming to be a very difficult and complicated task now.

Here are some reasons:
1) g++ does not seem to support some C++ language features supported by Visual Studio. The ones I've encountered so far are **enum**s and the **static** modifier. I can work around this, but I'd prefer not to (**enum**s make code SO much more readable, **static**s GREATLY improve code organization)
2) The big one by far. Let's say I compile some code, and there are errors in it. So I go into the code, fix the errors, and try to compile again. About 6 times out of 10, I will get the exact same errors.
This became most obvious when in one particular project, I had a file called "ArgsParser.cpp" that was causing approximately one bazillion errors. So I decided to just scrap the whole thing and replace it with a file called "IOHandler.cpp." After an hour or so of rewriting a fairly major part of this project, I tried compiling again, only to receive a bunch of errors coming from ArgsParser.cpp. Mind you, there WAS NO SUCH FILE ON MY COMPUTER!! And there were no references to it or anything, I am positive. Yet it still complained about all the errors it was getting from ArgsParser.cpp. Um...... What!?!?
3) g++ appears to be very moody. Sometimes, if I have a for loop like this:
```
for (int x=0; x<10; ++x)
cout << x << endl;
```
It will compile fine. Other times, if the code inside the loop is perhaps a bit more complex, it will give some error about changing the variable name of 'x' for "ISO C++ scoping rules." I wish I could reproduce this error and show you the responsible code, but as I said, it just occurs unpredictably and so I regrettably cannot. I've gotten this error many times since trying to make the switch to Linux though.

So, my question is, what's the best way to compile and test programs during the design process on *nix? I'm rather set on learning to use vim as my editor, but this g++ nonsense is simply unacceptable - there needs to be either a simple explanation for all this, or else a better way to go about compiling programs, else I shall forsake attempting to program on Linux. That might sound a bit extreme, but I've got dozens of programs I wrote on Visual Studio that compile and run just fine, and DO NOT make use of any Windows-specific or .NET features, but have hundreds of errors when I try to compile them with g++. That's a bit ridiculous, if you ask me.

Thanks :)

Well you have come to the right forum, but we will need some clearer descriptions of the problems because AFIK both enum and static work just fine in g++.

I have heard there was some change to scoping rules of variables declared in the control list of for loops, but it was changed so that their scope only lasts to the end of the loop. Thus the following two declarations of int i do not conflict.
```

int main() {
	for (int i = 0; i < 10; ++i) printf("%d\n", i);
	for (int i = 0; i < 10; ++i) printf("%d\n", i);
	return !printf("exits normally\n");
}

```

p.s. AFIK there is only one C++ standard but it gets updated and is usually backward compatible with the previous ones.

---

### Post by unknownPoster on 2011-02-02
> **worksofcraft said:**
> Well you have come to the right forum, but we will need some clearer descriptions of the problems because AFIK both enum and static work just fine in g++.



They both work as of about 3 months ago. I worked on a project that made use of both features and it worked fine.

---

### Post by psusi on 2011-02-02
> **W-Unit said:**
> 
Here are some reasons:
1) g++ does not seem to support some C++ language features supported by Visual Studio. The ones I've encountered so far are **enum**s and the **static** modifier. I can work around this, but I'd prefer not to (**enum**s make code SO much more readable, **static**s GREATLY improve code organization)

It most certainly supports enum and static.

> **W-Unit said:**
> 2) The big one by far. Let's say I compile some code, and there are errors in it. So I go into the code, fix the errors, and try to compile again. About 6 times out of 10, I will get the exact same errors.
This became most obvious when in one particular project, I had a file called "ArgsParser.cpp" that was causing approximately one bazillion errors. So I decided to just scrap the whole thing and replace it with a file called "IOHandler.cpp." After an hour or so of rewriting a fairly major part of this project, I tried compiling again, only to receive a bunch of errors coming from ArgsParser.cpp. Mind you, there WAS NO SUCH FILE ON MY COMPUTER!! And there were no references to it or anything, I am positive. Yet it still complained about all the errors it was getting from ArgsParser.cpp. Um...... What!?!?

Without knowing what you are running it is hard to venture a guess.  Are you using a Makefile, or invoking g++ directly?  If the latter, what is the full command and exact error?

> **W-Unit said:**
> 3) g++ appears to be very moody. Sometimes, if I have a for loop like this:
```
for (int x=0; x<10; ++x)
cout << x << endl;
```
It will compile fine. Other times, if the code inside the loop is perhaps a bit more complex, it will give some error about changing the variable name of 'x' for "ISO C++ scoping rules." I wish I could reproduce this error and show you the responsible code, but as I said, it just occurs unpredictably and so I regrettably cannot. I've gotten this error many times since trying to make the switch to Linux though.

You mean this:

test.cpp:8: error: name lookup of ‘x’ changed for ISO ‘for’ scoping
test.cpp:8: note: (if you use ‘-fpermissive’ G++ will accept your code)

This is because you tried to refer to x AFTER the loop.  According to the standard since you define x inside the loop, it no longer exists outside the loop.  Last I heard, MSVC fails to conform to the standard and lets you get away with this.  g++ is kind enough to tell you that it sees what you meant, and that it is not allowed by the standard, but you can tell it to let you get away with it with -fpermissive.

> **W-Unit said:**
> So, my question is, what's the best way to compile and test programs during the design process on *nix? I'm rather set on learning to use vim as my editor, but this g++ nonsense is simply unacceptable - there needs to be either a simple explanation for all this, or else a better way to go about compiling programs, else I shall forsake attempting to program on Linux. That might sound a bit extreme, but I've got dozens of programs I wrote on Visual Studio that compile and run just fine, and DO NOT make use of any Windows-specific or .NET features, but have hundreds of errors when I try to compile them with g++. That's a bit ridiculous, if you ask me.


I strongly suggest that you give up on vim and use emacs.  In addition to being a much more kick *** editor, it has a number of features that are similar to Visual Studio.  For instance, you can type "M-x compile" to have it compile your program and show the output in another window where you can scroll to an error message and hit enter and it will take you to the offending line of code.  You can also have it run the debugger and it will step through your code in the other window.  It also has something called speedbar that lets you browse your class hierarchy as a tree in a floating window.  Another very handy tool is you can hit M-. and it will look up the definition of the variable or function name your cursor is on and take you there.  If it is in the same file and you want to go back to where you came from, you can hit C-x x.  Hit it again and it will swap back to the first location.

---

### Post by W-Unit on 2011-02-03
> **psusi said:**
> It most certainly supports enum and static.
Alright, so why does this code not compile?
```
#include <iostream>
enum MyEnum { ZERO, ONE };

int main()
{
        MyEnum e = MyEnum::ZERO;
        std::cout << e << std::endl;
        return 0;
}

```
When I try to compile that, I get this:
```
test.cpp: In function ‘int main()’:
test.cpp:6: error: ‘MyEnum’ is not a class or namespace
```

> **psusi said:**
> Without knowing what you are running it is hard to venture a guess.  Are you using a Makefile, or invoking g++ directly?  If the latter, what is the full command and exact error?
I am invoking g++ directly. Perhaps this is my mistake, but I'm not following the conventional method of **#include**'ing .h (header) files whilst compiling .cpp (source) files, because at some point I thought that trying to do this was actually causing the errors. So instead, I am simply **#include**'ing all the other cpp files in my Main.cpp, then using **g++ -o prog Main.cpp** to compile.
I do not know what you mean by a Makefile. Perhaps this is the key?

> **psusi said:**
> You mean this:

test.cpp:8: error: name lookup of ‘x’ changed for ISO ‘for’ scoping
test.cpp:8: note: (if you use ‘-fpermissive’ G++ will accept your code)

This is because you tried to refer to x AFTER the loop.  According to the standard since you define x inside the loop, it no longer exists outside the loop.  Last I heard, MSVC fails to conform to the standard and lets you get away with this.  g++ is kind enough to tell you that it sees what you meant, and that it is not allowed by the standard, but you can tell it to let you get away with it with -fpermissive.
Yes, that is the error, but I do not think that it came up because of that. If VS *does* allow variables declared in a for loop to scope beyond the loop body, that's news to me - I never thought that they did or should, and I would be most surprised if I actually did write code that expected a variable declared in a for-loop initialization to have scope beyond the loop itself. Are you certain that this is the only way this error can occur?

> **psusi said:**
> I strongly suggest that you give up on vim and use emacs.  In addition to being a much more kick *** editor, it has a number of features that are similar to Visual Studio.  For instance, you can type "M-x compile" to have it compile your program and show the output in another window where you can scroll to an error message and hit enter and it will take you to the offending line of code.  You can also have it run the debugger and it will step through your code in the other window.  It also has something called speedbar that lets you browse your class hierarchy as a tree in a floating window.  Another very handy tool is you can hit M-. and it will look up the definition of the variable or function name your cursor is on and take you there.  If it is in the same file and you want to go back to where you came from, you can hit C-x x.  Hit it again and it will swap back to the first location.
These features do sound intriguing... heh, guess I'll have to give it a look-see. All that time I've been investing in learning to use vim efficiently though... #-o

I really appreciate all the replies, thanks a bunch!! :D

---

### Post by GeneralZod on 2011-02-03
> **W-Unit said:**
> Alright, so why does this code not compile?
```
#include <iostream>
enum MyEnum { ZERO, ONE };

int main()
{
        MyEnum e = MyEnum::ZERO;
        std::cout << e << std::endl;
        return 0;
}

```
When I try to compile that, I get this:
```
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:6: error: &#8216;MyEnum&#8217; is not a class or namespace
```



Based on a quick glance at the standard, I'm fairly sure that is not valid C++.  Instead, do:

```
#include <iostream>
enum MyEnum { ZERO, ONE };

int main()
{
        MyEnum e = ZERO;
        std::cout << e << std::endl;
        return 0;
}

```

Edit:

See e.g. [http://bytes.com/topic/c/answers/139295-problem-enumerators](http://bytes.com/topic/c/answers/139295-problem-enumerators)

---

### Post by fct on 2011-02-03
> **W-Unit said:**
> I am invoking g++ directly. Perhaps this is my mistake, but I'm not following the conventional method of **#include**'ing .h (header) files whilst compiling .cpp (source) files, because at some point I thought that trying to do this was actually causing the errors. So instead, I am simply **#include**'ing all the other cpp files in my Main.cpp, then using **g++ -o prog Main.cpp** to compile.
I do not know what you mean by a Makefile. Perhaps this is the key?

Avoid that include thingie, the side-effects of errors can be hard to read.

Makefiles are the standard UNIX way to build projects. Basically it's a config file for the "make" program that specifies how to build a project from the source files.

Here you have a basic Makefile tutorial: [http://mrbook.org/tutorials/make/](http://mrbook.org/tutorials/make/)

Since it can be cumbersome, you can use an IDE. That'd take care of automatic builds without delving in Makefiles. Visual Studio also takes care of build configuration, but uses a similar mechanism underneath. There are alternatives to "make" in Linux, like scons or cmake.

Still, I suggest you learn at least how to use Makefiles for simple projects.

---

### Post by psusi on 2011-02-03
> **W-Unit said:**
> Alright, so why does this code not compile?
```
#include <iostream>
enum MyEnum { ZERO, ONE };

int main()
{
        MyEnum e = MyEnum::ZERO;
        std::cout << e << std::endl;
        return 0;
}

```
When I try to compile that, I get this:
```
test.cpp: In function ‘int main()’:
test.cpp:6: error: ‘MyEnum’ is not a class or namespace
```

That error message is as clear as day.  MyEnum is not a class or namespace, so you can not scope into it with MyEnum::.  Enums do not create a new child namespace; the names are defined in the current namespace.  

> **W-Unit said:**
> I am invoking g++ directly. Perhaps this is my mistake, but I'm not following the conventional method of **#include**'ing .h (header) files whilst compiling .cpp (source) files, because at some point I thought that trying to do this was actually causing the errors. So instead, I am simply **#include**'ing all the other cpp files in my Main.cpp, then using **g++ -o prog Main.cpp** to compile.
I do not know what you mean by a Makefile. Perhaps this is the key?

Oh dear lord, absolutely positively NEVER #include a .cpp.  Rap yourself on the knuckles with a ruler for that ;)

> **W-Unit said:**
> Yes, that is the error, but I do not think that it came up because of that. If VS *does* allow variables declared in a for loop to scope beyond the loop body, that's news to me - I never thought that they did or should, and I would be most surprised if I actually did write code that expected a variable declared in a for-loop initialization to have scope beyond the loop itself. Are you certain that this is the only way this error can occur?

I can't be absolutely certain, but the message is very specific about what is wrong, so I would bet money on it.

---

### Post by matthew.ball on 2011-02-03
> **W-Unit said:**
> These features do sound intriguing... heh, guess I'll have to give it a look-see. All that time I've been investing in learning to use vim efficiently though... #-o

I really appreciate all the replies, thanks a bunch!! :D
While I have nothing to say about the topic of this thread, there are a few "vim emulation" type hacks available for emacs so you essentially get the best of both worlds.

The first one [viper-mode]("http://www.emacswiki.org/emacs/ViperMode") is what I have heard most emacs users advocating, so probably best to start here. The second one [vim-mode]("http://www.emacswiki.org/emacs/VimMode") was just the first result from google.

Hope it works out!

---

### Post by schauerlich on 2011-02-03
> **psusi said:**
> Oh dear lord, absolutely positively NEVER #include a .cpp.  Rap yourself on the knuckles with a ruler for that ;)

Sometimes it makes sense with [templates](http://www.parashift.com/c++-faq-lite/templates.html#faq-35.13). I was taught that, when you make a templated class, you should separate the declaration and implementation as you normally would, and then #include the implementation at the bottom of the declaration file. But I fully acknowledge that may be wrong. I'm by no means a C++ expert, nor do I use it much if I don't have to.

---

### Post by worksofcraft on 2011-02-03
> **schauerlich said:**
> Sometimes it makes sense with [templates](http://www.parashift.com/c++-faq-lite/templates.html#faq-35.13). I was taught that, when you make a templated class, you should separate the declaration and implementation as you normally would, and then #include the implementation at the bottom of the declaration file. But I fully acknowledge that may be wrong. I'm by no means a C++ expert, nor do I use it much if I don't have to.

Yes I fully support this view :)

It is much easier to understand the interface to a module if the header file contains ONLY declartions (and quality comments). All the definitions and implementation can then be encapsulated in other files.

For templates implementation is by necessity also an include file as they cannot be instantiated out of context, so instead of putting all the template implementation in the same header as it's declaration I like to split it as follows:

[LIST=1]
[*].h suffix to identify declaration header files
[*].hpp for corresponding template implementation details.
[*]Non-template implementation in .cc files so they can be compiled to object modules
[*]The ones that contain a main() I put in .cpp files
[/LIST]

building an application is then in principle:
```

g++ -Wall -c *.cc
# optionally put *.o in a library now instead in next command
g++ -Wall main.cpp *.o -llibraries

```

simple really ;)

---

### Post by ibuclaw on 2011-02-05
> **W-Unit said:**
> Alright, so why does this code not compile?
```
#include <iostream>
enum MyEnum { ZERO, ONE };

int main()
{
        MyEnum e = MyEnum::ZERO;
        std::cout << e << std::endl;
        return 0;
}

```
When I try to compile that, I get this:
```
test.cpp: In function ‘int main()’:
test.cpp:6: error: ‘MyEnum’ is not a class or namespace
```


FYI, this is a new feature of C++0x. And has been working for sometime now in G++, but disabled by default.

To compile the above, use
```
g++ -std=c++0x
```

Regards

---

### Post by psusi on 2011-02-05
Interesting... I really need to take a look at that new standard.

---


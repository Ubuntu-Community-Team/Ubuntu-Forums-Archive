---
title: "Is C a good language to start with"
date: 2006-08-07
forum: Programming Talk
---

### Post by %hMa@?b&lt;C on 2006-08-07
I have been starting really concidering starting to learn a "real" programming language.  I am decent at shell, and am looking to learn another language.  I have been thinking C or C++, which one would be better to start with and why?? If you have any other suggestions on which language to learn, or how to start, please tell me!

---

### Post by x64Jimbo on 2006-08-07
C++. 
Reason:
[http://en.wikipedia.org/wiki/C%2B%2B](http://en.wikipedia.org/wiki/C%2B%2B)

---

### Post by IYY on 2006-08-07
I'd start with C if I were you. Everything you learn in C you'll also need in C++, and there's less to learn.

---

### Post by cantormath on 2006-08-07
c and c++ are good to learn, if you learn c++, you learn all the c you'd want to know in the process.

---

### Post by simonn on 2006-08-07
My 0.02c...

I agree with IYY, learn C, then move to an OO or OO-esque language, if only because C does not hide you from allocating memory, and more importantly freeing the memory you have alloc-ed. 

A lot of the newer langauges hide you from this, including C++ to a certain, but lesser, extent.

While relying on garbage collectors and classes to free themselves is good a good thing as far as application development goes, IMO things should be hard when you are learning e.g. I think you are much better to learn to drive a manual car, even if you are planning on driving an automatic in the future because your understanding of what is going on is actualyl going to be that much better.

Do not learn a language that does not use pointers as your first langauge.

---

### Post by siimo on 2006-08-07
C# all the way baby! (-:

---

### Post by azmrb on 2006-08-07
It is OK to start with C and migrate to C++ but if you stay with C too long you will begin to think about how to solve problems proceduraly instead of the object oriented way of problem solving.  So dip your toe in the water with C but don't stay too long before you plunge into C++

---

### Post by Skia_42 on 2006-08-07
I know it wasn't one of the choices but Python is also worth looking into, I started learning it 2 weeks ago and it seems to be very easy to pick up. It's my fisrt language though so I am not comparing it to C or C++

---

### Post by Christmas on 2006-08-08
It doesn't really matter if you start with C or C++, there's no big difference between them except that C++ has OO. I'd recommend C because as far as I could see it's used more in Linux. Consider C/C++ the first language to learn before languages like Perl/Python/TCL/PHP. Those you will be able to learn in a flash after you know C, which is probably harder and can cause headaches, but allows you to make complex operations and work with pointers, etc. It also learns you not to program, but to think better.

---

### Post by Mathiasdm on 2006-08-08
> **jeffc313 said:**
> I have been starting really concidering starting to learn a "real" programming language.  I am decent at shell, and am looking to learn another language.  I have been thinking C or C++, which one would be better to start with and why?? If you have any other suggestions on which language to learn, or how to start, please tell me!
I'll disagree with earlier posts.
I think you should start with something like Java or C# (Yeah, I know, suggesting Java in here is probably heresy. Not that I care :-P )
I started using Java, and we created procedural programs during the first 1.5 months.
Then, we moved on to OOP during the next 1.5 months.

I just think it's better if you know both procedural and OOP as soon as possible.

Then, move on to C or C++ (that's what I'm doing know).

---

### Post by Kvark on 2006-08-08
Pick any high level object oriented language with a lot of premade libs as your native programming language. That'll teach you good habits like use classes/objects/functions and use work others have already done for you as much as possible. If I have to pick one language then Python is the best language to start with and the best language to use for most tasks. But the important part is to learn to design good algorithms, not which language you use to write down your algorithms. No matter which one you start with learn and get comfortable with several languages that are as different from your native langauge and eachother as possible even if you're not going to use them.

Here is a Python program that takes each line of text you write and prints all words that ends with "ing":
```
import sys
for line in sys.stdin.readlines():
    for word in line.split():
        if word.endswith('ing'):
            print word
```

Here is a C program that does exactly the same thing:
```
#include <sys/types.h>
#include <regex.h>
#include <stdio.h>
#define BUFFER_SIZE 1024

int main(int argc, char **argv) {
     regex_t space_pat, ing_pat;
     char buffer[BUFFER_SIZE];
     regcomp(&space_pat, "[, \t\n]+", REG_EXTENDED);
     regcomp(&ing_pat, "ing$", REG_EXTENDED | REG_ICASE);

     while (fgets(buffer, BUFFER_SIZE, stdin) != NULL) {
         char *start = buffer;
         regmatch_t space_match;
         while (regexec(&space_pat, start, 1, &space_match, 0) == 0) {
             if (space_match.rm_so > 0) {
                 regmatch_t ing_match;
                 start[space_match.rm_so] = '\0';
                 if (regexec(&ing_pat, start, 1, &ing_match, 0) == 0)
                     printf("%s\n", start);
             }
             start += space_match.rm_eo;
         }
     }
     regfree(&space_pat);
     regfree(&ing_pat);

     return 0;
}
```
In case anyone cares, I copied those example programs from the preface of the [Natural Language Toolkit documentation]("http://nltk.sourceforge.net/lite/doc/en/").

---

### Post by Christmas on 2006-08-08
Kvark, yes it's true. Languages like Perl/Python seem to be more simpler. However you didn't mention that they are languages which are interpreted by an interpreter, so for long programs they will take much more time to run than a C program which is compiled and converted into machine code. 

Also, all these advanced functions, for example to sort things, or compare strings with numbers directly, or to insert a substring in a string at a specified position, they all have behind more complex code written in C or other language. C helps you to learn to think. Of course, it also counts what are you going to use for your programs. If it's going to be some simple script then obviously a more accesible language like Perl/Python is recommended, if you want some complex application than C.

---

### Post by loell on 2006-08-08
go with c , and some script base language of your choice ie(Python, Ruby).

---

### Post by slimdog360 on 2006-08-08
> **simonn said:**
> My 0.02c...

do you mean $0.02.

anyway on with the question, I suppose it depends on what you want to do with the language. c++ is probably a bit more popular as far as I can see these days and would let you do pretty much whatever you wanted to do.
Though I havent actually used any c++ before, just read bit and pieces about it. I have done some c, for microprocessors etc, and its not that hard to learn if you can already code. However it can be cumbersome at times compared to other languages.
The reaon I say c++ though is that Id imagine that its almost just as functional but perhaps just a few more commands to make it easier. Though like I said I havent used it before.

---

### Post by siimo on 2006-08-08
Same code in C#.  So much easier to understand than the C code :cool: 

```


using System;
using System.Collections.Generic;
using System.Text;
using System.IO;

namespace UselessConsoleApplication
{
    class Program
    {
        static void Main(string[] args)
        {
            while(true)
                RunProgram();
        }

        private static void RunProgram()
        {
            Console.WriteLine("Type stop and press enter to terminate input\n");
            List<string> lines = ReadStandardIn();
            Console.WriteLine("\nWords ending with 'ing' are :\n");
            foreach (string line in lines)
            {
                char[] seperator = { ' ' };
                string[] words = line.Split(seperator);

                foreach (string word in words)
                    if(word.ToLower().EndsWith("ing"))
                        Console.WriteLine(word);
            }
            Console.WriteLine();
        }

        private static List<string> ReadStandardIn()
        {
            List<string> inputStrings = new List<string>();
            for (string line; (line = Console.In.ReadLine()) != null; )
            {
                if (line.ToLower().Trim() == "stop")
                    return inputStrings;
                inputStrings.Add(line);
            }
            return inputStrings;
        }
    }
}



```

---

### Post by kabus on 2006-08-08
[http://ubuntuforums.org/showthread.php?t=216476](http://ubuntuforums.org/showthread.php?t=216476)
[http://ubuntuforums.org/showthread.php?t=202314](http://ubuntuforums.org/showthread.php?t=202314)
[http://ubuntuforums.org/showthread.php?t=166198](http://ubuntuforums.org/showthread.php?t=166198)
[http://ubuntuforums.org/showthread.php?t=133907](http://ubuntuforums.org/showthread.php?t=133907)
[http://ubuntuforums.org/showthread.php?t=210419](http://ubuntuforums.org/showthread.php?t=210419)
[http://ubuntuforums.org/showthread.php?t=208880](http://ubuntuforums.org/showthread.php?t=208880)

---

### Post by simonn on 2006-08-08
> **slimdog360 said:**
> do you mean $0.02

Nope. My opinion is usually undervalued :).

---

### Post by Kvark on 2006-08-08
Christmas, the programmer's time is worth a lot more then the proccessor's time. It's better to write a simple program that is slightly slower then a fast program that is much more complicated, takes more time to write and is harder to debug. If you program for a pocket calculator then you'll need to use a low level language but on a modern PC the speed difference usually isn't noticeable even for big programs. Python's interpreter is surpricingly efficient and most of Python's builtin functions are written in C. For really demanding programs you can write the CPU intensive parts in C or even Assembler and the rest in Python.

But when it comes to some interpreted languages I'll agree with you. Java's interpreter is noticeably more memory hungry and slower then pre-compiled code. Which is sad because Java itself is an excellent training language used in many programming courses.

I agree that C helps you to learn to think. And so does any other language to some degree. Thats why I said it's good to learn several languages, perferably that are very different from what you are used to. It's excellent training to have to define your algorithms in new and different ways. But before doing that I think it's best to have a high level OO language as your "native" language and get used to high level OO habits from the start.

---

### Post by [h2o] on 2006-08-08
I second the opinion of going for a higher level language first. I just discovered Python a few months ago, and that is my current language of choice for everything right now :)

---

### Post by kriding on 2006-08-08
What are good resource sites to start learning C++ from?, since going over to Linux, I have lost most of the ability to do the graphical work I used to (Gimp does not quite measure up to PS CS2), so I may aswell learn to programme as well:p

---

### Post by siimo on 2006-08-08
Monodevelop now even has a pretty GUI builder how cools that!
[http://www.monodevelop.com/files/e/eb/Stetic-in-monodevelop.png](http://www.monodevelop.com/files/e/eb/Stetic-in-monodevelop.png)

---

### Post by aktiwers on 2006-08-08
Im starting on my new school in about 3 weeks. Its Computer Science and Business. We are gonna learn Java as our first language. I dont know why though.

---

### Post by tseliot on 2006-08-08
I have moved this thread to the "Programming Talk" section

---

### Post by Christmas on 2006-08-08
[quote=Kvark]Christmas, the programmer's time is worth a lot more then the proccessor's time. It's better to write a simple program that is slightly slower then a fast program that is much more complicated[/quote]
The programmer's time is worth a lot, but not when you have to make a big application, say a game. They are all (or almost all) made in C. I didn't say someone has to make a fast program in a complicated way, I said someone has to make a big program in "that" complicated way, because otherwise the program will be very slow. Now, I don't exactly know how much the time difference between a C program and a Perl program for example is, but I know that most major applications are not done in Perl. They are all used for scripts, small working programs, and that's it. Of course, each one has its own opinion about how somebody should start learning programming, there are arguments on both sides.
[quote=[h2o]]I second the opinion of going for a higher level language first. I just discovered Python a few months ago, and that is my current language of choice for everything right now[/quote]
Depends on what you want to do with it. For educational purposes, I recommend C, and it's not only me, but for example my country's  schools only C/Pascal are teach as a language. A high-level language will let you do everything you do in C, but in a more simpler way, without letting you know exactly how things work, how the memory is allocated, etc. And all this things have to be known to be an efficient programmer. If you skip learning a medium-level language like C and go directly with one of the high-level ones, you'll also skip the basic learning of mathematical algorithms, the beauty of programming and thinking as a programmer.

---

### Post by slimdog360 on 2006-08-08
> **simonn said:**
> Nope. My opinion is usually undervalued :).

lol

---

### Post by jordilin on 2006-08-08
> **jeffc313 said:**
> I have been starting really concidering starting to learn a "real" programming language.  I am decent at shell, and am looking to learn another language.  I have been thinking C or C++, which one would be better to start with and why?? If you have any other suggestions on which language to learn, or how to start, please tell me!

Forget C and C++, if you wanna be really productive and learn quickly then go for Python.
[www.python.org](www.python.org)

---

### Post by [h2o] on 2006-08-08
> **Christmas said:**
> The programmer's time is worth a lot, but not when you have to make a big application, say a game. They are all (or almost all) made in C. I didn't say someone has to make a fast program in a complicated way, I said someone has to make a big program in "that" complicated way, because otherwise the program will be very slow. Now, I don't exactly know how much the time difference between a C program and a Perl program for example is, but I know that most major applications are not done in Perl. They are all used for scripts, small working programs, and that's it. Of course, each one has its own opinion about how somebody should start learning programming, there are arguments on both sides.
Writing games is not the luxury of many programmers (getting paid doing it, that is) and most programs don't require speed. If you have the need for speed (games, calculations, convertions, etc) then go for a compiled low level language. Even assembler if you have to. But if you don't care wether it takes 0.1 or 0.05 seconds to open a window in your office application, then go for something higher if you want.


> Depends on what you want to do with it. For educational purposes, I recommend C, and it's not only me, but for example my country's  schools only C/Pascal are teach as a language. A high-level language will let you do everything you do in C, but in a more simpler way, without letting you know exactly how things work, how the memory is allocated, etc. And all this things have to be known to be an efficient programmer. If you skip learning a medium-level language like C and go directly with one of the high-level ones, you'll also skip the basic learning of mathematical algorithms, the beauty of programming and thinking as a programmer.
Skipping algorithms? Yes, perhaps you don't have to write your own hashed list structure, or sorting trees, but then again: That is not something I want to do everytime I build a new program. I much rather used well tested and fast pre built libraries for that. And yes, I have programmed algorithms and structures for most things as part of university studies.
Actually, at the university here we started with Lisp, to procede to Ada and then Java. It has at least given me a good insight in three different programming paradigms.

---

### Post by ember on 2006-08-08
Well - it highly depends on what you intend, yet a general rule is, as many people said, learn OO-Programming. Python is very nice, despite its fame, Java became quite usable with version 5. I can highly recommand the [Head First Java]("http://www.oreilly.com/catalog/hfjava/") book from Oreilly (and the Head First Design Patterns when you decide to dive into professional software development). As a general rule you can say:

1) OO-programming will earn you more money than non-OO (from my experience a solid OO-knowledge can double the price you can take for a hour of work)
2) Java/C# programming will earn you more than scripting languages. That's not fair, but the truth - the gain is not as high as in 1, but it seems you are only taken as a serious developer, if you know at least one of Jave, C# or C++.
3) You should learn C++ if you intend to work on hardware-related projects like drivers or embedded devices (yet mobile phones offer Java mostly)

---

### Post by tseliot on 2006-08-08
> **ember said:**
> 3) You should learn C++ if you intend to work on hardware-related projects like drivers or embedded devices (yet mobile phones offer Java mostly)
Isn't the Linux kernel written in C ?

---

### Post by JDD on 2006-08-08
> **tseliot said:**
> Isn't the Linux kernel written in C ?

That and assembler if im correct[-o<

---

### Post by ember on 2006-08-08
Yes, I guess you are correct. So for the Linux case C might be appropriate. Yet, if I remember correctly, QNX and some other embedded operating system support C++ for driver development.

---

### Post by [h2o] on 2006-08-08
I am on a bit of a deep water here now, but as long as you don't have the problem of getting libraries linked in dynamically then C++ code should work just fine on an embedded device.
I mean, machine instructions are machine instructions regardless from what language they were compiled?

---

### Post by Daverz on 2006-08-08
> **jeffc313 said:**
> I have been starting really concidering starting to learn a "real" programming language.  I am decent at shell, and am looking to learn another language.  I have been thinking C or C++, which one would be better to start with and why?? If you have any other suggestions on which language to learn, or how to start, please tell me!

C is a good first language in that 

a) mere mortals can become proficient in most of the syntax that matters in a reasonable amount of time.  The language can be kept in ones head, so to speak.
b) it teaches some basic low level computing concepts
c) it teaches discipline, since that is required to create programs that don't crash
d) it's the *lingua franca* of unix

It is not a good first programming language in that it can take many months to learn how to create non-trivial programs that don't segfault all over the place (particularly if you don't have a very experienced C programmer to mentor you).  Also, simple things like string handling are much more difficult than they need to be.

My advice is to learn C because it's too useful to ignore, but to learn Python as well so you can be productive right away.

---

### Post by LordHunter317 on 2006-08-08
> **IYY said:**
> I'd start with C if I were you. Everything you learn in C you'll also need in C++, and there's less to learn.No, you will not.  C and C++ are distinct languages with distinct programming styles.  The only thing they share is some syntax and a small common standard library (which is crap, so you don't ever use it in C++ unless you must).

Syntax is easy to learn, so it's not worth it.  

[quote=simonn]I agree with IYY, learn C, then move to an OO or OO-esque language, if only because C does not hide you from allocating memory, and more importantly freeing the memory you have alloc-ed.[/quote]Neither does C++.  More importantly, this is a non-sequitur: being OO or not OO has nothing to do with whether you have to explictly allocate or release memory or not.

Even more importantly, that's a bunk reason.  Memory management is just a form of resource management, and you have to do manual resource management (for some resources) in *all* languages.  The lessons you learn there can generally be applied to memory without much trouble or modification.

> IMO things should be hard when you are learningNo, I'm not sure that's true.  

> e.g. I think you are much better to learn to drive a manual car, even if you are planning on driving an automatic in the future because your understanding of what is going on is actualyl going to be that much better.But it's not because manual and automatic transmissions share very little in common but the fact they have gears.

> Do not learn a language that does not use pointers as your first langauge.Also nonsense, as that excludes a lot of functional languages.  My guess (I could be mistake) is you were trying to exclude Java and C#, but they have pointers anyway.

**Kavark:** That C program doesn't quite do the same thing at the implementation level.  It uses regexes (very slow for this) as opposed to ordinary string functions.

[quote=Kavark]Christmas, the programmer's time is worth a lot more then the proccessor's time.[/quote]That's not to say that the processor's time isn't worth something.  If there weren't bounds on this relationship, then no optimization would ever be bothered with.

> Python's interpreter is surpricingly efficientNo, it's suprisingly crap.

> But when it comes to some interpreted languages I'll agree with you. Java's interpreter is noticeably more memory hungry and slower then pre-compiled code.Actually, the JVM is relatively memory efficent.  The fact that Java has a huge standard library has a lot to do with it.

> Which is sad because Java itself is an excellent training language used in many programming courses.No, it really isn't. It lacks a lot of features it really ought to have.  Also, good introductory programming material in Java is hard to find.  The crap grossly outweighs the good stuff.

[quote=Christmas]Depends on what you want to do with it. For educational purposes, I recommend C, and it's not only me, but for example my country's schools only C/Pascal are teach as a language.[/quote]C is a terrible teaching language.  Horrid.  It lacks tons of basic features, a worthwhile standard library, and any good teaching material.  Even Java is better than it in all respects.

> And all this things have to be known to be an efficient programmer.Nonsense.  If that were true, Java would not be one of the world's most popular (if not the most popular) language.

> you'll also skip the basic learning of mathematical algorithms, the beauty of programming and thinking as a programmer.Now you plainly don't know what you're talking about.  I have alogrithms books in 3 languages (Java, C++, Pascal).  Algorithms can be taught without even using a real programming language (e.g., Kunth's Art of Computer Programming where he makes a language up to use in the book). 

You clearly don't understand algorithms based on these last couple of statements.

[quote=Daverz]a) mere mortals can become proficient in most of the syntax that matters in a reasonable amount of time.[/quote]They can in Java too, and Java removes a lot of the annoying but required parts of C syntax, like declaration mimics usage.

> b) it teaches some basic low level computing conceptsThat's not an *ipso facto* positive.

> c) it teaches discipline, since that is required to create programs that don't crashThat's true of all languages.

---

### Post by jordilin on 2006-08-08
Python's interpreter is surpricingly efficient
> **LordHunter317 said:**
> 
No, it's suprisingly crap.

Why? You must have a good reason to say this. I find Python really nice and powerful. It's true that is not as fast as Mono or JVM, but does it really matter when we have extremely powerful hardware?

---

### Post by LordHunter317 on 2006-08-08
> **jordilin said:**
> Why? You must have a good reason to say this.It's not:[list][*]Thread safe[*]Particulary smart about it's memory allocations (memory allocated for primatives must always be used for those primatives)[/list]There are some other nagging issues, but those are the two biggest.

Don't get me wrong, I like python as a language.  But the interpreter needs to be replaced.  Especially if they want more penetration in things like web space, where a threaded interpreter makes designing web applications much eaiser (as opposed to FastCGI).  State sharing and stuff is just less headache then.

> It's true that is not as fast as Mono or JVM, but does it really matter when we have extremely powerful hardware?It can matter, yes, because we don't always have the luxury of extremely powerful hardware.

---

### Post by Daverz on 2006-08-08
> **LordHunter317 said:**
> 
No, it's suprisingly crap.


It's good enough for me right now.  Of course, the GIL must die as multi-core CPUs become ubiquitous.  But it's more likely that the whole interpreter will just be replaced in a couple years. See

[http://codespeak.net/pypy/dist/pypy/doc/architecture.html#mission-statement](http://codespeak.net/pypy/dist/pypy/doc/architecture.html#mission-statement)

And then there are alternate implementations like IronPython and Jython.

> 
They can in Java too, and Java removes a lot of the annoying but required parts of C syntax, like declaration mimics usage.


I just don't think Java is as useful to know on unix as C is.  If you're a sys admin or unix user who occaisonally programs, then a little C will pay off a lot more than Java, particularly if you have to fiddle with the tons of existing C code. Though I'd choose Java over C for application programming if those were my only choices (and I was being paid), C is *the* language for unix systems programming.

> 
That's not an *ipso facto* positive.


Yeah, all my positives are meant to have an implied converse.

---

### Post by LordHunter317 on 2006-08-08
> **Daverz said:**
> It's good enough for me right now.Well, it's "good enough" for lots of things.  But it's still pretty poor compared to a lot of other JIT-interpreters out there.

> I just don't think Java is as useful to know on unix as C is.  If you're a sys admin or unix user who occaisonally programs, then a little C will pay off a lot more than Java, A little Perl and SH will pay off orders more.

> C is *the* language for unix systems programming.Most programming isn't systems programming though.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]C is a terrible teaching language. Horrid. It lacks tons of basic features, a worthwhile standard library, and any good teaching material. Even Java is better than it in all respects.[/quote]
Then why C/C++ are so widely used in schools? They teach one to think.
[quote=LordHunter317]Nonsense. If that were true, Java would not be one of the world's most popular (if not the most popular) language.[/quote]
I know hundreds of applications made in C/C++ and I can't remember right now one made in Java. Also, how Java developers get paid in contrast to C developers?

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> Then why C/C++ are so widely used in schools?Because it's what the professors knows?

> I know hundreds of applications made in C/C++ and I can't remember right now one made in Java.Just because you don't see them doesn't mean they're not there. Think websites.

> Also, how Java developers get paid in contrast to C developers?As well if not better.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]Now you plainly don't know what you're talking about. I have alogrithms books in 3 languages (Java, C++, Pascal). Algorithms can be taught without even using a real programming language (e.g., Kunth's Art of Computer Programming where he makes a language up to use in the book).

You clearly don't understand algorithms based on these last couple of statements.[/quote]
I think you misunderstood my affirmation. I didn't said you need C to learn algorithms, I said C is better for learning algorithms than high-level programming languages. I will give a simple example. In most such  high-programming languages you will always have a sort function which you will be able to use at any time for sorting things. In C you will have to manually make that function, in any way you like, to sort numbers or strings, and you can choose any algorithm you like for sorting, not a pre-defined one. This is what really takes you to learning and understanding programming.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> I think you misunderstood my affirmation. I didn't said you need C to learn algorithms, I said C is better for learning algorithms than high-level programming languages. I will give a simple example. In most such  high-programming languages you will always have a sort function which you will be able to use at any time for sorting things.But this is also a non-sequitur.  Just because you have a sort function doesn't mean you have to use it.

>  In C you will have to manually make that function, in any way you like, to sort numbers or strings, and you can choose any algorithm you like for sorting, not a pre-defined one.But I can do that in Scheme, C++, Lisp, Python, Java, C# too.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]Because it's what the professors knows?[/quote]
...because it prooved to be one of the best for educational purposes at least. Also there is Pascal. No school I know uses Java as a teaching language.
[quote=LordHunter317]
Just because you don't see them doesn't mean they're not there. Think websites.[/quote]
I wasn't thinking websites but languages for general purposes. Wasn't this the thing the OP was looking for?
[quote=LordHunter317]As well if not better.[/quote]
And in, say two years? Java is not so hard to learn as C from what I've heard.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> ...because it prooved to be one of the best for educational purposes at least.No, it hasn't.  You never answered my points. 

> No school I know uses Java as a teaching language.Plenty of schools do.  Most HS do now because it's the language used on the AP CS exam.  Most colleges use it because it's what the HS use.

> I wasn't thinking websites but languages for general purposes.Java is a general-purpose language.  The fact you see it most often running web applications has nothing to do with it.  It's primarily used in business.  It's the "new COBOL".  And just like COBOL, you don't see most Java code.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]But this is also a non-sequitur. Just because you have a sort function doesn't mean you have to use it.[/quote]
Most will do because it'll be simpler for them.
[quote=LordHunter317]But I can do that in Scheme, C++, Lisp, Python, Java, C# too.[/quote]
You can but at the cost of speed, I already said that in a previous post.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]Plenty of schools do. Most HS do now because it's the language used on the AP CS exam. Most colleges use it because it's what the HS use.[/quote]
Maybe in your country, in my country it is not used. They have strict program given by the Minister of Education, so no teacher can make up his mind by himself and teach whatever he wants just because "he uses" it.

---

### Post by Daverz on 2006-08-08
> **LordHunter317 said:**
> 
A little Perl and SH will pay off orders more.


<Wrinkles nose a mention of Perl> 

True, but lets just forget it was ever mentioned :-$  

I sort of assume any serious unix user will learn Bourne shell.

---

### Post by x64Jimbo on 2006-08-08
> **Christmas said:**
> Maybe in your country, in my country it is not used. They have strict program given by the Minister of Education, so no teacher can make up his mind by himself and teach whatever he wants just because "he uses" it.
Java is the primary learning language around here as well (Colorado, USA)
I think it's because it's a cross-platform language, and the interpreter is nearly ubiquitous. I took the intro Java course and hated how verbose it was (public static void main string AARRGGGHH!!!) but I understood why it was becoming so huge. Programs like Azureus don't have to be re-coded each time they want to release a new version. There's a few subtle differences for each OS in terms of the GUI, but the core is all the same. They might not teach Java first where you live, but it's a simple, Object Oriented programming language that does its  own garbage management, it can very easily make a web application (the direction many apps are going these days) and much more. As much as I disliked the class, I very much came to respect the language. 
And now, back to your regularly scheduled thread.

---

### Post by Christmas on 2006-08-08
Looks like things differ from country to country. I'm in Bucharest at a computer university and, at least in the first year, no Java present. Maybe in the following years, I'll ask somebody who knows.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> Most will do because it'll be simpler for them.Sure, when they're writing real programs because it's less work to do.  They will not use them when they are learning algorithms, because the whole purpose is to learn algorithms, duh.

It's a fallacy to suggest that because something is there, someone will use that something when they're learning how to create it.  It just plain makes no sense, unless we're dealing the irrational or lazy.  It's not worth talking about them because they're going to take any shortcuts they can no matter what.

And C provides a sorting function, so you premise is factually incorrect *anyway*.

> You can but at the cost of speed, I already said that in a previous post.No you didn't and no it isn't.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]No you didn't and no it isn't.[/quote]
Yes I did here:
[quote=Christmas]However you didn't mention that they are languages which are interpreted by an interpreter, so for long programs they will take much more time to run than a C program which is compiled and converted into machine code.[/quote]
Well from what I've read the applications are slower. If they weren't then why aren't most of the applications made in Perl/Python/Java? Or at least in the same quantity as the C ones?

---

### Post by LordHunter317 on 2006-08-08
That statement isn't relevant to the discussion of whether one can and should write their own algorithims in those languages.  The fact that some of them are interpreted and that makes them slower is irrelevant.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]That statement isn't relevant to the discussion of whether one can and should write their own algorithims in those languages. The fact that some of them are interpreted and that makes them slower is irrelevant.[/quote]
How can it be irrelevant? If all the software, GNOME, KDE would be written in such a language how would it work? Isn't the "fast" factor one of the most important in a software? Aren't most of discussions in this forums about "it should be fast", "it will get improved" etc?
It is very important that the applications are fast. It's one thing to wait 5 seconds for a task to complete or to wait 20 seconds. Just think you or your program has to do that task 10 times a day.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> How can it be irrelevant?Algorithm study isn't concerned with such details.

> It is very important that the applications are fast. It's one thing to wait 5 seconds for a task to complete or to wait 20 seconds. Just think you or your program has to do that task 10 times a day.But that's not relevant to algorithm study, in the manner you're thinking.

---

### Post by ember on 2006-08-08
> **Christmas said:**
> Isn't the "fast" factor one of the most important in a software? 


Actually it is not the most important. The most important factors are:

1) Does is cover all required features (completeness)?
2) Is it stable (correctness)?
3) Can you easily modify it (maintainability)?

and then comes:

4) Is it fast enough?

Of course there is not much sense in an implementation that is so slow that actually nobody uses it. But for 90% of nowadays software it is rather irrelevant which programming language you use - what is important is that your algorithms are good and your implementation does not make serious mistake in their implementation (IBM research showed that an average implementation can be speeded up by up to 20% by looking for string concatenation and replace the code with one that uses string buffers).

I still say that it does not make much sense to learn C as your first programming language unless you want to do something at driver or kernel level. 
That does not mean that C is irrelevant (that is highly untrue), it just means it is not suited for a modern approach to learn how to program.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]But that's not relevant to algorithm study, in the manner you're thinking.[/quote]
No, but it's relevant when it comes to the point of choosing a programming language to learn, isn't it?

---

### Post by Christmas on 2006-08-08
[quote=ember]Actually it is not the most important. The most important factors are:[/quote]
I only said it's **one** of the most important... They are not programming languages in the truly meaning, they are most likely known as scripting languages, their scope is to be used for small tasks, to extend another program.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> No, but it's relevant when it comes to the point of choosing a programming language to learn, isn't it?Not especially. Doubly-so if the purpose is to study algorithms.  Mostly because learning languages is easy.  Learning things like computational theory, data structures and alogrithms, and how to design programs aren't easy, but they can be accomplished in any language.

---

### Post by ember on 2006-08-08
> **Christmas said:**
> I only said it's **one** of the most important... They are not programming languages in the truly meaning, they are most likely known as scripting languages, their scope is to be used for small tasks, to extend another program.

Well - that's where we disagree. To my mind, the reason for the increasing popularity of Ruby or Python is their high productivity. Of course there are limitations, yet I'd say scripting language (with solid frameworks) scale up to medium sized projects.

---

### Post by jordilin on 2006-08-08
> **ember said:**
> Well - that's where we disagree. To my mind, the reason for the increasing popularity of Ruby or Python is their high productivity. Of course there are limitations, yet I'd say scripting language (with solid frameworks) scale up to medium sized projects.

Python is not an scripting language. It's a complete full-featured programming language suitable for many tasks, one of them scripting. And it can be used for large and complex projects.
Taken from python.org:
> Python® is a dynamic object-oriented programming language that can be used for many kinds of software development. 

---

### Post by forrestcupp on 2006-08-08
> **Christmas said:**
> The programmer's time is worth a lot, but not when you have to make a big application, say a game. They are all (or almost all) made in C. 

This is not necessarily true.  The standard is changing toward using a scripting or high level language for the game logic code, and using a game engine programmed in assembly or c/c++ for the low level graphics/sounds/physics, etc.  Now if you personally want to, I guess you could reinvent the wheel every time you work on a project, but you won't get a lot done that way.

Python is an easy, productive, and powerful language to use.  It is cross-platform.  You can use it to program GTK, SDL, openGL, and just about anything you would want.  I know most of these libraries are probably programmed in c, but like I said, why reinvent the wheel for every project?  And BTW, it is possible to compile Python.

---

### Post by fluffington on 2006-08-08
> **jeffc313 said:**
> I have been starting really concidering starting to learn a "real" programming language.  I am decent at shell, and am looking to learn another language.  I have been thinking C or C++, which one would be better to start with and why?? If you have any other suggestions on which language to learn, or how to start, please tell me!

C is one of the best languages to start with. It's powerful enough to do just about anything, and it doesn't try to prevent you from shooting yourself in the foot, which aids learning significantly. Also, a lot of popular languages are based on it (C++, C#, ObjC, D, Java, etc.), which will make picking up those fairly easy later on. And you will want to move on; C is great for learning, but it's rarely the best tool of the job.

My recommendation? Read [this book](http://www.amazon.com/gp/product/0131103628) cover to cover (and do all of the exercises), then pick a higher-level language (I prefer C++, but there are lots of others) and learn that too.

---

### Post by jordilin on 2006-08-08
> **fluffington said:**
> C is one of the best languages to start with.


It was some years ago, but seeing how the software market has evolved I would recommend other choices. But as always it will depend on what kind of project you are gonna deal with. If you are to work with the Linux Kernel, programming drivers, then go for C. If not, then go for Python or C#.

---

### Post by Christmas on 2006-08-08
[quote=forrestcupp]Python is an easy, productive, and powerful language to use. It is cross-platform. You can use it to program GTK, SDL, openGL, and just about anything you would want. I know most of these libraries are probably programmed in c, but like I said, why reinvent the wheel for every project?[/quote]
Why is this mentality that using C takes to reinventing the wheel? You can make your own functions for each task you want in C and then use the same functions in each project.

---

### Post by LordHunter317 on 2006-08-08
> **fluffington said:**
> C is one of the best languages to start with.None of your reasoning is compelling.

>  It's powerful enough to do just about anything,So's brianfuck but that doesn't mean you want to.  And doing a lot of simple stuff in C is very difficult.

> and it doesn't try to prevent you from shooting yourself in the foot, which aids learning significantly.Not really.  It generally IME impedes it, because it makes finding the "right" solution difficult.

> Also, a lot of popular languages are based on it (C++, C#, ObjC, D, Java, etc.),Only in syntax, which is irrelevant.

---

### Post by Christmas on 2006-08-08
Ok, I was also thinking from another point of view. Let's say you start with Perl for example and want to learn C, Python and Java after that. It'll be hard to learn C and almost as hard as learning Perl to learn Python/Java. If one goes for the 'hardest' alternative from the beginning, in this case C, then the other free (and most likely any other languages like them) will take less time to learn. If one wants only a single programming language (an idea which is bad anyway as standards change, the request for different programmers in different programming languages is growing) then C still remains the most important one by far. Most of the job offers in the IT domain here are requesting C++/C#, PHP and Java mainly, rarely Ruby/Perl/Python or whatever. It really depends on what you want to do with what you learnt.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]Only in syntax, which is irrelevant.[/quote]
Only in syntax? Hell, half of them were written in C!

---

### Post by ember on 2006-08-08
> **Christmas said:**
> Ok, I was also thinking from another point of view. Let's say you start with Perl for example and want to learn C, Python and Java after that. It'll be hard to learn C and almost as hard as learning Perl to learn Python/Java. If one goes for the 'hardest' alternative from the beginning, in this case C, then the other free (and most likely any other languages like them) will take less time to learn.

O.k. From that point of view, C makes sense. It is like learning Latin that is said to help you with other languages (I agree with that).

And well, once you know what a mess resource management in C can be, you will be happy that other languages relieve you from this pain ;)

---

### Post by simonn on 2006-08-08
> **LordHunter317 said:**
> 
Neither does C++.  More importantly, this is a non-sequitur: being OO or not OO has nothing to do with whether you have to explictly allocate or release memory or not.


True, however in practise most OO languages have garbage collection, e.g. Java, or hide the memory management from you like a lot of C++ classes, you even agree with this [http://ubuntuforums.org/showpost.php?p=1348309&postcount=20](http://ubuntuforums.org/showpost.php?p=1348309&postcount=20).

In any case, I did not suggest learning an OO language later because it had anything to do with memory management, but because it is important to learn OO programming.

> 
Even more importantly, that's a bunk reason.  Memory management is just a form of resource management, and you have to do manual resource management (for some resources) in *all* languages.  The lessons you learn there can generally be applied to memory without much trouble or modification.


And with C you have to do pretty much all of it yourself, which is my point, e.g. you are fully aware that strings are character arrays etc etc

> But it's not because manual and automatic transmissions share very little in common but the fact they have gears.

Quite right, it is because the driver has to do more work and understand why it is being done.

> Also nonsense, as that excludes a lot of functional languages.  My guess (I could be mistake) is you were trying to exclude Java and C#, but they have pointers anyway.

I was actually suggesting using a language that relies on pointers, which C pretty much does.

[http://en.wikipedia.org/wiki/Java_%28Sun%29](http://en.wikipedia.org/wiki/Java_%28Sun%29)

"Java syntax borrows heavily from C and C++ but it eliminates certain low-level constructs such as pointers and has a very simple memory model where every object is allocated on the heap and all variables of object types are references."

Which encapsulates almost everything I want to to say originally.

BTW, I do not think anyone is saying "C is the only language you should learn", far from it. However, the thread's topic is "Is C a good language to start with", not algo design or whether C is the best language in the world etc.

> **ember said:**
> From that point of view, C makes sense. It is like learning Latin that is said to help you with other languages (I agree with that).

Excellent analogy.

---

### Post by IYY on 2006-08-08
> Christmas, the programmer's time is worth a lot more then the proccessor's time. It's better to write a simple program that is slightly slower then a fast program that is much more complicated

I think the developers of StarOffice had a similar philosophy, and even a few years after, with newer and faster hardware, we're complaining about how slow Open Office is.

---

### Post by ember on 2006-08-08
I can assure you, the StarOffice Code is neither elegant nor simple ;) - and I believe because of this, it is slow.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
>  Let's say you start with Perl for example and want to learn C, Python and Java after that. It'll be hard to learn C and almost as hard as learning Perl to learn Python/Java. If one goes for the 'hardest' alternative from the beginning, in this case C, then the other free (and most likely any other languages like them) will take less time to learn.But they won't.  Either you'll understand the underlying concepts or you won't.  If you do, it won't matter which language you start with.  If you don't, you won't learn to program in any language, so order still doesn't matter.

> then C still remains the most important one by far.No, it isn't.  The industry numbers worldwide don't agree with you.

> Only in syntax? Hell, half of them were written in C!Which means *nothing*.  And most languages have as much code as possible written in the language.

[quote=simonn]True, however in practise most OO languages have garbage collection, e.g. Java, or hide the memory management from you like a lot of C++ classes,[/quote]C++ classes don't "hide" the memory management from you.  

> you even agree with this [http://ubuntuforums.org/showpost.php...9&postcount=20](http://ubuntuforums.org/showpost.php...9&postcount=20).Hiding it and handling it are two different things.  C++ still requires you to be aware of where objects are allocated.

C doesn't require that (mostly because it doesn't have private objects, but still).

> In any case, I did not suggest learning an OO language later because it had anything to do with memory management, but because it is important to learn OO programming.You should have seperated your statements then.  

> And with C you have to do pretty much all of it yourself, which is my point,But you haven't shown why that's a good thing.

> e.g. you are fully aware that strings are character arrays etc etcBut that's not necessarily true outside of C.  The storage of the bytes making up a string may be just a character array, but other languages carry far more information to compose a string, like encoding.

Most large C APIs do as well, and support things like wide character types to handle multiple encodings and locales.

So the details you learn become irrelevant.

> was actually suggesting using a language that relies on pointers, which C pretty much does.So does Java, C#, C++.

> "Java syntax borrows heavily from C and C++ but it eliminates certain low-level constructs such as pointers and has a very simple memory model where every object is allocated on the heap and all variables of object types are references."

Which encapsulates almost everything I want to to say originally.And that quote is simply **wrong**.  Java has pointers.  In fact, you can only get a pointer to a non-primative type.  What the java language calls "references" are really pointers.  References in C++, Pascal, etc. can't be reseated (made to point to another object).  Java and C# references can.  Ergo, they're pointers.

> However, the thread's topic is "Is C a good language to start with", not algo design or whether C is the best language in the world etc.Right, but the things that are important to start with C is poor at teaching, for a variety of reasons.

---

### Post by janhenderson on 2006-08-08
> **jeffc313 said:**
> I have been starting really concidering starting to learn a "real" programming language.  I am decent at shell, and am looking to learn another language.  I have been thinking C or C++, which one would be better to start with and why?? If you have any other suggestions on which language to learn, or how to start, please tell me!

Learn an interactive language. You don't need C. Chances are you'll never even need to learn C. If you want a little upgrade from shell then learn a scripting language such as perl or python. If you want a "real" language learn lisp.

---

### Post by fluffington on 2006-08-08
> **LordHunter317 said:**
> None of your reasoning is compelling.
Neither is yours, but I'm feeling argumentitive today, so I'll bite.

> So's brianfuck but that doesn't mean you want to.
BF is a good one to learn. It's not really worth attempting to implement anything meaningful in it, but it'll make you think about the problem differently, which is really the whole point of learning to program. Also, Turing-completeness is not equivalent to power.

> And doing a lot of simple stuff in C is very difficult.
Can you give an example? I personally find C one of the easiest languages out there to work with.

> Not really.  It generally IME impedes it, because it makes finding the "right" solution difficult.

There is no "right" solution, and there never will be. There are a number of, perhaps infinite, ways to approach any given problem. Part of learning is discovering several of these approaches and evaluating them based on criteria such as time to write, time to run, memory usage, etc.

And being able to shoot yourself in the foot is a very good thing when learning because making and correcting a mistake is infinitely more effective at imparting a lesson than forcing someone to use a tool that simple doesn't allow one to do certain things because they might be dangerous.

> Only in syntax, which is irrelevant.
C, ObjC, C#, C++, and D are supersets of C. Any program written in C will compile and behave normally when compiled with an ObjC compiler, for example.

Further, if syntax is irrelevant, both of us are fluent in German, which differs from English only in syntax.

---

### Post by LordHunter317 on 2006-08-08
> **fluffington said:**
> Can you give an example? I personally find C one of the easiest languages out there to work with.I'll pose the same, easy, classic challenge: write a program in C to take a string from the user (up to newline), concatenate it with another string, and write it out.  It must handle input of any length, cannot have any bugs, and must handle all error conditions gracefully.

*Most people can't even do it correctly* (In fact, no one has done it 100% correct ever sense I started posting it here).  Then, write it in any other mainstream language.  You'll find that it's eaiser.  Far eaiser, in fact.  

> There is no "right" solution, and there never will be. Utter nonsense.  The right solution is the one that solves the problem at hand.  C makes it too easy to get sidetracked on solving that problem and makes it hard to express it in a straightforward fashion.

> Part of learning is discovering several of these approaches and evaluating them based on criteria such as time to write, time to run, memory usage, etc.Not on your own. We dedicate whole mountains of classes to this on purpose, because self-exploration may not be the best method of study to this.

> And being able to shoot yourself in the foot is a very good thing when learning because making and correcting a mistake is infinitely more effective at imparting a lessonIt can be, but it isn't always.  Sometimes it's good.  It's certainly not a universal good.

> C, ObjC, C#, C++, and D are supersets of C.Wrong, right, wrong, half-right, and wrong.  They're related in syntax only.  C++ is a partial superset.  Objective-C is a strict superset, at least for now.  None of them but C++ use declaration-mimics-usage.

> Any program written in C will compile and behave normally when compiled with an ObjC compiler, for example.That's the only one.  The other four share nothing in common but syntax.  C# doesn't even support non-member functions, for example.

> Further, if syntax is irrelevant, both of us are fluent in German, which differs from English only in syntax.Nope, that doesn't follow in the least.  Just because syntax is irrelevant doesn't mean other things are.  Standard libraries are very relevant for example, which would be the vocabularly of a natural language.

---

### Post by fluffington on 2006-08-08
> **LordHunter317 said:**
> I'll pose the same, easy, classic challenge: write a program in C to take a string from the user (up to newline), concatonate it with another string, and write it out.  It must handle input of any length, cannot have any bugs, and must handle all error conditions gracefully.

*Most people can't even do it correctly* (In fact, no one has done it 100% correct ever sense I started posting it here).  Then, write it in any other mainstream language.  You'll find that it's eaiser.  Far eaiser, in fact.

Fair enough. String manipulation isn't C's strong suit, but it's rarely something I have to work with. I consider the fact that you haven't been given a correct answer a challenge, though; I'll post again later with a solution.

> Utter nonsense.  The right solution is the one that solves the problem at hand.
That's your definition, not mine; I'll rephrase to better suit your semantics: There are an infinite number of right solutions, none of which is more right than any other.

> C makes it too easy to get sidetracked on solving that problem and makes it hard to express it in a straightforward fashion.
And that teaches discipline, which is part of the reason I believe C is an excellent language for learning purposes, regardless of what it may be for production work.

> Not on your own. We dedicate whole mountains of classes to this on purpose, because self-exploration may not be the best method of study to this.
I have never seen a method of instruction more effective than self-exploration. I've taken those classes, and the only information I remember from any of them is the stuff I was forced to figure out on my own.

> It can be, but it isn't always.  Sometimes it's good.  It's certainly not a universal good.
For learning, it's good. For production work, it's usually not. Once you know what you're doing, though, it becomes a moot point.

---

### Post by Jucato on 2006-08-08
I'm also trying to learn programming, mostly on my own. I started with C because at that time it was the "in" thing, together with Pascal. From my point of view, "what programming language to start with" depends on where you want to start in the first place.

I think that if you really want to learn the very basics of programming, specially the theoretical parts, C would be a good starting point. It teaches you about basic theoretical (and practical) stuff like how character strings are actually just character arrays, how to manage memory, etc. The basics.

On the other hand, if you want to begin diving into actual programming immediately, and just learn the theories along the way, a high-level language such as Java or Python would be a better starting point.

So my point of view has nothing to do immediately with performance or features of a language, but more of where do you want to start from. Whichever starting point you choose, you could always go to the other end afterwards, from C to Java/Python and vice versa.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]And doing a lot of simple stuff in C is very difficult.[/quote]
No it isn't. It may seem difficult at the beginning, but after learning it all will make sense. I found myself making a small C plugin for XChat instead of making a simple Perl/Python/Tcl script just because I knew how to do that in C, and didn't want to waste time searching for the string functions that Perl is using for example. Again, it's not difficult, it just requires more code for the same simple task, and that will lead you to learn programming.

LE
[quote=LordHunter317]Utter nonsense. The right solution is the one that solves the problem at hand. C makes it too easy to get sidetracked on solving that problem and makes it hard to express it in a straightforward fashion.[/quote]
How can you know what's exactly the right solution? It may just seem to solve the problem, or it can be right from one point of view and wrong from another. It can be bug-free but slow or viceversa.

---

### Post by TheRingmaster on 2006-08-08
pascal is what They teach in high school.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]But this is also a non-sequitur. Just because you have a sort function doesn't mean you have to use it.[/quote]
If you don't use it you'll make things exactly how they are done in C, so what's the point then? You're contradicting yourself.

---

### Post by LordHunter317 on 2006-08-08
> **fluffington said:**
> Fair enough. String manipulation isn't C's strong suit, but it's rarely something I have to work with.But neither is any sort of error-handling or file I/O, for example.  Both of which are very common tasks.

> That's your definition, not mine; I'll rephrase to better suit your semantics: There are an infinite number of right solutions, none of which is more right than any other.But you're still missing the point: C makes it harder at arriving at any of those right solutions than it ought to be.  You haven't responded to that.

> And that teaches discipline,Not really.  What it generally teaches is that doing things the right way just isn't worth it.  Because the right way is excessively difficult.

Or are all those continuing exploits in C code my imagination.  It's not like secuina.org has gotten less busy or anything.

> I have never seen a method of instruction more effective than self-exploration.Then why do most developed countries mandate public education for children?

Clearly, there's something to it.

> I've taken those classes, and the only information I remember from any of them is the stuff I was forced to figure out on my own.I would suggest the curriculum was poor, the teachers were poor, or perhaps a combination.  I've taken both good classes and bad classes at every level of my education.  The good ones are irreplacable, and no amount of self-study will teach you what they will.

> For learning, it's good.No, it isn't.  And my string example clearly proves in some cases, it is not.  You've yet to support your position here.

[quote=Fenyx]It teaches you about basic theoretical (and practical) stuff like how character strings are actually just character arrays,[/quote][list][*]This is not theoretical.  It's as applied as you can be.[*]It's not actually true in all cases.[/list] 

[quote=Christmas]No it isn't.[/quote]Yes, it is.  Write code to properly open a file, read in data from it, open another file, and write it out.  Properly handling the error conditions is ugly and difficult.

> Again, it's not difficult, it just requires more code for the same simple task, and that will lead you to learn programming.Being able to write more code doesn't make you a better programmer.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> If you don't use it you'll make things exactly how they are done in C, so what's the point then?The point is to learn algorithms.  The accepted way to do it is to write a bubble sort, an insertion sort, a quick sort, a merge sort, etc.

Not only will several of those not look like how they're done in C (because C doesn't implement all those sorts), your quick sort may not look the standard library's sort at all.

---

### Post by mscman on 2006-08-08
> **Fenyx said:**
> From my point of view, "what programming language to start with" depends on where you want to start in the first place.

My sentiments exactly. It makes no sense to use a language such as python or perl to program a hardware controller. Likewise, you would be stupid to write a small script for string manipulation in C. Granted, both can be done, but not without difficulty.

I agree with using C to learn the basics of programming (that's how I've been taught). I also find it to be the most common language for programs in Linux.

---

### Post by Christmas on 2006-08-08
[quote=LordHunter317]Yes, it is. Write code to properly open a file, read in data from it, open another file, and write it out. Properly handling the error conditions is ugly and difficult.[/quote]
They are all routines. I can't see the difficulty in opening, writing and closing files.
[quote=LordHunter317]Being able to write more code doesn't make you a better programmer.[/quote]
It is well-known that in maths you have to make exercises a lot, even if they become routine at some point. It does make you because you can understand better what happens there. 

Ok, let me put a simple example which doesn't apply only to C. For a beginner it takes a while until he learns how to use the "while" and "for" structures. If he uses them just a couple of times, he might never find out that all that can be done with "for" can be done with "while". Then put him write the same code many more times, in different contexts, always thinking about it, always the same variables until he will observe that. He will be able to make many more connections. The same goes for C vs others mentioned in this thread, C is somehow forcing the programmer to do all that low-level stuff. My point is that more code has as a result a better programmer. Not better than a genius or a talented person, but better than him if he wouldn't code that much, I guess it's logic.

---

### Post by LordHunter317 on 2006-08-08
> **Christmas said:**
> They are all routines. I can't see the difficulty in opening, writing and closing files.Because if you encounter an error, you have to clean up resources.  And cleaning up resources in C is hard.

What this is telling me is you have little practical C experience, or you're not writing very correct code.

> It is well-known that in maths you have to make exercises a lot, even if they become routine at some point. It does make you because you can understand better what happens there. Which is  releavant to your example how?  It's not.  You're confusing number of lines written with repetition.  Repetition is generally good for learning.  Writing lots of lines of code is not necessarily.  The two are related, but not in the manner you've tried to suggest.

> If he uses them just a couple of times, he might never find out that all that can be done with "for" can be done with "while". Then put him write the same code many more times, in different contexts, always thinking about it, always the same variables until he will observe that. He will be able to make many more connections.True, but irrelevant to what you originally siad.

---

### Post by simonn on 2006-08-09
LordHunter317, what would you suggest for a first language?

---

### Post by LordHunter317 on 2006-08-09
C++ is OK, not because I think it's the best language to learn from (really, it's too complicated) but because the learning material for it is simply superb.  *Accelerated C++* is probably one of the best introductory programming texts ever.  Material to read after that is plentiful and of excellent quality.


*How to Design Programs* and *Structure and Interpretation of Computer Programs* are excellent, but are going to require a lot more dedication than other paths.  SICP has video caps of lecture online, I highly recommend you watch them.

I can't speak to any of the Python stuff as I've not read it.

My main concern is quality and availabilty for teach material.  As I said, you can learn in any language if you really want to.  

But C lacks material for teaching *introductory* programming.  At an introductory level, the language is probably the least important part.  Understanding data flow, scope, what a variable really is, the relationship between code and data, etc. is far more important.

Another concern is how easy is it to apply the knowledge learned.  For example, Python makes this very easy, making it a good learning choice.

---

### Post by jordilin on 2006-08-09
> **LordHunter317 said:**
> 

I can't speak to any of the Python stuff as I've not read it.



Python documentation is really good, and the library reference is awesome. [http://www.python.org/doc/](http://www.python.org/doc/)

---

### Post by LordHunter317 on 2006-08-09
The documentation isn't introductory programming material, though.  I was referring to things like *Dive Into Python* and *How to Think Like a Computer Scientist*.

---

### Post by Ubuntist on 2006-08-09
Here's another vote for starting with Python.  The advantage of beginning with Python is that you will learn more about programming in less time.  You'll spend more time trying out new concepts -- like OO -- and less time on the nitty gritty of getting syntax right, etc.

Once you've learned the big picture with Python, it'll be easier to pick up a language like C++.

---

### Post by jordilin on 2006-08-09
> **Ubuntist said:**
> Here's another vote for starting with Python.  The advantage of beginning with Python is that you will learn more about programming in less time.  You'll spend more time trying out new concepts -- like OO -- and less time on the nitty gritty of getting syntax right, etc.

Once you've learned the big picture with Python, it'll be easier to pick up a language like C++.

I agree, but I wouldn't take another language like C++. With Python is sufficient :D . But as always it will depend on the project you are working on.

---

### Post by Christmas on 2006-08-09
Maybe a poll would be appropiate? Something like "I have experience with programming and recommend C", "I have little experience and recommend C", "I have experience and recommend Perl", "I have little experience and recommend Perl" etc.

---

### Post by X.Cyclop on 2006-08-09
It depends on what you want to do. 

C is for cross-platform apps, low level actions (drivers, partitioners, cd burners...) and fast-apps.

I prefer C, for its power. 

;)

---

### Post by [h2o] on 2006-08-10
In comparison with the interpreted languages, wouldn't C be considered pretty "non-cross-platform"? You do compile it's code for a specific platform (as I guess you already know ;)).
Of course you can recompile it for the target platform, but that would be true for any compiled language, right?

---

### Post by LordHunter317 on 2006-08-10
> **'[h2o] said:**
> In comparison with the interpreted languages, wouldn't C be considered pretty "non-cross-platform"?Standard C is very cross-platform in the sense that it runs on a lot of platforms.  Standard C isn't very cross-platform in the sense it lets you do very little useful stuff on most platforms.  For most people, the latter is more important than the former, hence C is not actually very cross-platform.

> Of course you can recompile it for the target platform, but that would be true for any compiled language, right?That compiles to native code.

---

### Post by eukhost.com on 2006-08-10
C is a good language to start with and a great base for learning additional languages. Imo, when you start with C or C++, it's easier to pick up other languages like Java or Perl.

---

### Post by LordHunter317 on 2006-08-10
Several people have said that, but no one has given a valid reason why.  The only thing they share is syntax.  Most syntax is pretty easy to learn.

---

### Post by [h2o] on 2006-08-10
> **LordHunter317 said:**
> That compiles to native code.
Obviously, yes. :rolleyes:

---

### Post by LordHunter317 on 2006-08-10
Well given that the differences between languages that are directly compiled to native code (e.g., C, C++) and languages that are not normally compiled to native code but some form of bytecode (e.g., Python, Emacs-Lisp, Java, C#), I thought it was worth mentioning.

---

### Post by X.Cyclop on 2006-08-10
> **LordHunter317 said:**
> Several people have said that, but no one has given a valid reason why.  The only thing they share is syntax.  Most syntax is pretty easy to learn.
Here are **my** reasons:

- With C/C++ you can do WHATEVER you want. Drivers, games, operating systems (Windows and GNU/Linux are mostly written in C)...
- C/C++ have too many compilers-IDEs.
- C/C++ have a nice syntax.
- C/C++ don't depend on ANYTHING (neither interpreter, nor web servers, nor extra-libraries, obviously, if you're using ANSI. Of course, if you're using MFC, your app depends on Visual C++ DLLs).

However, i need to admit that C/C++ are a little more difficult to learn than other languages (Python, PHP, ASP, Ruby...), because you need to use libraries, or pointers and may crash your computer.

;)

---

### Post by LordHunter317 on 2006-08-10
> **X.Cyclop said:**
> - With C/C++ you can do WHATEVER you want. Drivers, games, operating systems (Windows and GNU/Linux are mostly written in C)...While that is a valid reason, I'm not sure it's a valid reason for a first language.  Very few people write operating systems or drivers, and that requires very specialized learning anyway.

> - C/C++ have too many compilers-IDEs.Many of these are of terrible quality.  I'm not sure this is a valid reason at all.  You're generally only going to use one, after all.

> - C/C++ have a nice syntax.Not really.  Declaration-mimics-use is a terrible thing: is *foo a declaration or a dereference?  C++ references overloading the meaning of &foo makes it even worse.

Templates have several major problems.  Nested templates can't be defined cleanly: '>>' is illegal, you must use '> >'.  Inherited tempates require special declartions to access their members, since specialization means they may not be there.  Lack of constraints is a real pain, assertations aren't nearly as expressive or user-friendly.

Anonymous namespaces automatically being imported is an obvious requirement but another idiosynchronously.

> - C/C++ don't depend on ANYTHING (neither interpreter, nor web servers, nor extra-libraries, obviously, if you're using ANSI.But it does require a compiler and a toolchain and a standard library. And providing a compliant C++ standard library is extremely difficult (no one has done it yet).

Practically speaking, the C++ standard library doesn't provide enough for anything but the most trival applications.  C is the worse.

---

### Post by [h2o] on 2006-08-11
> **LordHunter317 said:**
> Well given that the differences between languages that are directly compiled to native code (e.g., C, C++) and languages that are not normally compiled to native code but some form of bytecode (e.g., Python, Emacs-Lisp, Java, C#), I thought it was worth mentioning.

Yeah, you are right. What I meant was "non-interpreted languages", not compiled.

---

### Post by [h2o] on 2006-08-11
> **LordHunter317 said:**
> But it does require a compiler and a toolchain and a standard library. And providing a compliant C++ standard library is extremely difficult (no one has done it yet).


Haha, that was actually the major headache I had this summer. Working on a C/C++ program (as in some parts C, some parts C++. No, I did not write it in the first place, I'm only modifting it) it took me a few days (!) to get my program to link and then work on another machine than the one I was developing for, since they used different versions of libgcc and libdc++.
This was of course ultimately related to the fact that I am not very good C/C++ programmer, but it does show that C/C++ might not be the best of beginners languages since I am by far an inexperienced programmer in general.

---

### Post by X.Cyclop on 2006-08-11
> **LordHunter317 said:**
> Many of these are of terrible quality.  I'm not sure this is a valid reason at all.  You're generally only going to use one, after all.
Yes, you've too many choices.

> Not really. Declaration-mimics-use is a terrible thing: is *foo a declaration or a dereference? C++ references overloading the meaning of &foo makes it even worse.

Templates have several major problems. Nested templates can't be defined cleanly: '>>' is illegal, you must use '> >'. Inherited tempates require special declartions to access their members, since specialization means they may not be there. Lack of constraints is a real pain, assertations aren't nearly as expressive or user-friendly.

Anonymous namespaces automatically being imported is an obvious requirement but another idiosynchronously.
These are a few things, generally C/C++ have a nice syntax.

Well. Compare C/C++ syntax with Python, Ruby or Bash Syntax... it's very very nice, isn't it?:roll: 

> But it does require a compiler and a toolchain and a standard library. And providing a compliant C++ standard library is extremely difficult (no one has done it yet).

Practically speaking, the C++ standard library doesn't provide enough for anything but the most trival applications. C is the worse.
A compiler and toolchain for coding it, but NOT for running it.

e.g.: For running amaroK you'll need some libraries, while running GIMP you'll need the Python interpreter.

Python interpreter and other files -> Over 3400KB
C/C++ libraries -> Over 300KB

Too many dependences for non-compiled languages or compiled languages with a VM (C#, Java).

Check this: [http://www.cprogramming.com/whyc.html](http://www.cprogramming.com/whyc.html)

;)

---

### Post by LordHunter317 on 2006-08-11
> **X.Cyclop said:**
> These are a few things, generally C/C++ have a nice syntax.But they're fundamental and are riddled through the whole language.  

Calling C++ 'nice' is just ludicrious.

> Well. Compare C/C++ syntax with Python, Ruby or Bash Syntax... it's very very nice, isn't it?:roll: Not really.  All of them have their blemishes, but I can write lots of Python or Rbuy that doesn't run into them.  Not so much for C++ or Bash.

> A compiler and toolchain for coding it, but NOT for running it.No, the standard library must still be present for running it.  Not optional.

> e.g.: For running amaroK you'll need some libraries,Which is something you need for running it. Thank you for proving my point.

> while running GIMP you'll need the Python interpreter.No, you will not, seeing GIMP isn't written in Python.

> C/C++ libraries -> Over 300KBI don't know how you came to this, but it's wrong.  libstdc++ by itself is 800KiB on my system.  And that's not all that is required.

> Too many dependences for non-compiled languages or compiled languages with a VM (C#, Java).Java just needs a JVM, plus your external libraries (but you can provide those with your application, trivally, so that's not a big deal).  Which may be large, but that's it.  The JVM is required to provide the standard libraries, so you don't even have to worry about.

Same's true of C#, to a degree.

Unlike with C or C++ where you do have to worry about static vs. dynamic linking from time-to-time.

As for the article:> [Why Learn C](http://www.cprogramming.com/whyc.html)
Nevertheless, there are some good reasons to learn to program in C. First, age has its advantages: C has been around for 30 years, and there is a ton of source code available.Given the [track record](secunia.org) of a lot of C code out there, I'm not sure this is a good reason to learn C.

> Third, C is reasonably close to the machine. When you're working with pointers, bytes, and individual bits, things like optimization techniques start to make a lot more sense.This is nonsensical.  Most optimization techniques are relatively machine-independent.  And the important ones are based on algorithms and are language-independent too.

---


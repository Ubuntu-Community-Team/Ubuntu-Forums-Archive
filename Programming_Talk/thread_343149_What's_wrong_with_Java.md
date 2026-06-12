---
title: "What's wrong with Java??"
date: 2007-01-21
forum: Programming Talk
---

### Post by laxmanb on 2007-01-21
I'm learning how to program with Java & frankly, i love the language! 
The API seems comprehensive enough & the language seems easy to program in (having done C/C++ before, Java is easy enough... but i get confused the second i look at VB.Net code or python code...)

however, i've seen a lot of ppl say Java has a lot of problems... i would really like to know those people's point of view... so please, enlighten me!

---

### Post by Yarias on 2007-01-21
Things that I personally like about Java
- Built in Documentation via Javadoc
- Excellent Compiler Warning and Error Descriptions
- Portability of Code

Things that could be better
- Features that were added in recently but are not as good as possible because of the need to keep reverse compatibility (e.g. Generics)
- Speed (although for most applications, its plenty fast enough)

---

### Post by jblebrun on 2007-01-21
> **laxmanb said:**
> I'm learning how to program with Java & frankly, i love the language! 
The API seems comprehensive enough & the language seems easy to program in (having done C/C++ before, Java is easy enough... but i get confused the second i look at VB.Net code or python code...)

however, i've seen a lot of ppl say Java has a lot of problems... i would really like to know those people's point of view... so please, enlighten me!

I think Java is a pretty powerful langauge. The main reason I don't use it is that I haven't found any situations in which it made sense to use Java over Python... programming in python tends to result in much more succinct code, and more rapid development time. Java is often considerably faster, but the programs that I write are not usually compute-bound, but rather I/O bound ( meaning: most of the time in the program is spent waiting for input or reading from the network or a file ), so I prefer Python's quick coding over Java's speed.

Overall, I'd say Java is a good language, though. It's just personal taste that causes me not to care for it.

---

### Post by lnostdal on 2007-01-21
The language "wants" everything to be an object which is not true to the complexity/flexibility of the "real world". In other words, it mostly only supports a single [paradigm](http://en.wikipedia.org/wiki/Programming_paradigm) called Object Oriented Programming or OOP.

A fun/interesting blog-post about this is found here btw: [http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)

But compared with C++ I'd go for Java hands down in almost all cases. :) The benefits of GC especially helps here.

..and to continue my advocacy I'd like to mention that Lisp, as a programmable programming language (and thus "automatically" multiparadigm) - has enabled programmers to implement or add paradigms such as for instance OOP and AOP (Aspect Oriented Programming) directly using standard language features as one would do when programming libraries -- without extending the compiler. So while users of other languages are (well, mostly) only able to add libraries to their languages, Lispers add both libraries and language-extensions (or "language-libraries") to their language in a standard fashion.

---

### Post by laxmanb on 2007-01-21
Really... Speed isn't that much of an issue... or will completely cease to be in the coming year...

Windows Vista already requires 512 MB RAM and about a gig of RAM optimally... this means all computers sold will meet this req. (i live in India, where certain OEMs still sell computers with 256 MB RAM, but it'll stop soon[i think])...

...And Java was never slow... beyond a certain threshold requirement of RAM, you really can't tell much of a difference performance wise... with all computers meeting that requirement soon..( and JDK 6 has some new features for desktop integration)... Java is a very viable platform for desktop apps...

---

### Post by laxmanb on 2007-01-21
lnostdal, thank you 4 the link... but i don't get it yet... sorry!!

i guess i don't have that much experience yet... so i possibly haven't faced any problems with Java's OOP intepretation yet... perhaps later i'll be frustrated too...

btw, does C# have the same problem??

---

### Post by Quillz on 2007-01-21
> **laxmanb said:**
> I'm learning how to program with Java & frankly, i love the language! 
The API seems comprehensive enough & the language seems easy to program in (having done C/C++ before, Java is easy enough... but i get confused the second i look at VB.Net code or python code...)

however, i've seen a lot of ppl say Java has a lot of problems... i would really like to know those people's point of view... so please, enlighten me!
There is a recurring myth that Java is a system hog, and apps that rely on it, such as Azureus, are bloated and slow, but it's not true. Any modern computer will not be slowed down by 50 MB of memory usage.

---

### Post by ssavelan on 2007-01-21
I have not tried to program in Java, although object-oriented java/python are great languages to develop prototypes.... if the program is worth refining, perhaps you lower the level of the language:guitar: 

I'm looking to paste this somewhere:

biouser@reishi-tsunami:~/Desktop$ fakeroot make-jpkg jre-6-linux-i586.bin 
Creating temporary directory: /tmp/make-jpkg.rGpAwl9637
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

Any idea where?

I am really just a noob looking for help with user-end java noobishness....

---

### Post by maxamillion on 2007-01-21
I think Java is a very respectable language and that majority of the complaints you will find around the net on forums, irc channels, blogs, etc. are going to be issues that people had with older versions of Java that are no longer relevant.

---

### Post by jblebrun on 2007-01-21
> **Quillz said:**
> There is a recurring myth that Java is a system hog, and apps that rely on it, such as Azureus, are bloated and slow, but it's not true. Any modern computer will not be slowed down by 50 MB of memory usage.

This is a horrible attitude to take. It seems like everytime computing power gets cheaper, then rather than trying to take better advantage of it, we just adopt lazier programming practices!

---

### Post by laxmanb on 2007-01-21
that is true... i remember reading this cartoon on how once upon a time memory was so precious they cut off 2 digits from the year (and the entire Y2K thing emerged... )

but really... it's not just Java that is a memory hog... modern programs in any language are memory hogs... almost.

---

### Post by lnostdal on 2007-01-21
> **laxmanb said:**
> i guess i don't have that much experience yet... so i possibly haven't faced any problems with Java's OOP intepretation yet... perhaps later i'll be frustrated too...

Just make sure it is about the right things; the things that truly turn out to be more-or-less un-fixable problems with Java or your current paradigm. Your problem might be more suitable to solve in another language or paradigm then. 

..in fact; the only time a person really knows a language or paradigm is when they see and understand its potential problems and limitations (everyone has them) -- and is able to avoid them by switching language/paradigm. It's like attacking a problem from a totally different angle. Weird thing is; these (obvious when you understand them) problems and limitations often turn out to be quite hard to describe with words ("there really is a world outside my fishbowl (or above the blue sky)?") and/or small examples ("everything is turing-complete anyways!!") -- and thus leads to interesting/annoying flamewars. ;)


> **laxmanb said:**
> btw, does C# have the same problem??

Not too sure about C# -- but I think so; wikipedia mentions the same set of paradigms as Java.

---

### Post by Grey on 2007-01-21
I had to buy more memory for my laptop, due in large part to Azureus.  (I had 512MB, I upgraded to 1GB).  That does not make me fond of Java in the slightest.

From a programming point of view, I dislike Java for a couple of reasons.

1) No unsigned types.  (This is seriously a WTF in my books)
2) No default values for functions (requiring you to spend half an hour writing something that should normally take 5 minutes)
3) Too much Object Orientation.  (Not everything should be an object)

I'm sure that there's more, but those are the ones that have personally bitten me in the ***.

---

### Post by laxmanb on 2007-01-21
Grey... if it's any consolation, you can now run Microsoft(C) Windows(R) Vista Home Premium on your laptop... 

512 MB of RAM would not have been enough for that as well...

---

### Post by Grey on 2007-01-21
Oooh!  Yay!  Let me rush right out and get that.  =P

Nah, I like having a large amount of memory on my computers anyway.  But Azureus was just the most common reason I ran out of memory.  (would use somewhere between 100 and 200MB of memory)

But in all honesty, I don't think I would install Vista even if it were given to me for free at this point.

---

### Post by pmasiar on 2007-01-21
After couple years of Perl and later Python I needed to switch to Java. I was already spoiled with expectations how easy things could be and how easy you can dive in and swim when learning new language. Not with Java :-( So I compare Java with Perl/Python.

[LIST]
[*]**verbosity:** VeryLongUglyType someName = new VeryLongUglyType(); I see something typed twice :twisted: Why it cannot be just VeryLongUglyType someName = new(); I  just entered  the type?
[*]**Byzantine API**: depending on what team in Sun implemented it (and phase of the moon?), functionality is in static or object methods with slightly different names. How I am supposed to remember all that?
[*]**object ravioli:** Instead of spaghetti code, we now have hundreds of small raviolis, stuffed with raviolis. Which one hides what you want? Example: ArrayList is *not* array, nor list of arrays.
[*]**Object obsession:** why o why everything needs to be an object? I don't care about OOP religion - I have problems to solve before deadline! Why I cannot have simple print? One smart improvement I've seen was designing package P with overloaded P.rint() function to make printing simpler. Come on, WTF?
[/LIST]

OK I give up and confess: I am pythonista who became weak and spoiled :-) and cannot handle real badass strictly typed language as I was able before - my tolerance to syntax pain is   substantially decreased. I am slowly adapting to that pain again - and let me tell you *it hurts*. Somewhere I read that many languages have syntax sugar to make tasks simpler - and java invented **syntax vinegar** to enforce object religion :-)

---

### Post by Hendrixski on 2007-01-21
[SIZE="4"]THERE SHOULD BE AN EPISODE OF MYTH BUSTERS ABOUT JAVA.
[/SIZE]
When I got into college people said "Java is slow" so I wrote all of my code in C++, then they said "it's getting better" so I wrote cool applications in Java, but did C++ for all my computational mathematics and Cryptography programming.  Today, I can't tell the difference.  I use mostly Java and it's plenty fast.

---

### Post by Wybiral on 2007-01-21
I don't even want to get in the middle of this...

But, when something is either interpreted or JIT compiled... It's going to be a little slow. Not noticeably in small apps, but certainly in large ones (because it has a complex system of managing things behind the scene, any VM does)

Not all of java can be machine compiled or it wouldn't maintain it's pretty garbage collection capabilities, and the parts that are JIT compiled, are one of the big reasons java is such a cookie monster about eating CPU speeds (compiling large sections of code every runtime... SERIOUSLY??? You WANT to do that???)

One can argue that the behind the scenes stuff is what makes VM'd languages so good, because garbage collection/memory management are all taken care of for you.

Personally, I've never had a problem freeing up my old memory and allocating new memory and general program specific memory problems in compiled languages like C++ You have to be one inattentive person to really mess things up that badly or to loose track of your memory that easily.

Also, if I'm going to opt for an interpreted language, I'll at least use one that's more dynamic than java (like python/ruby)

Java's like a bulky, restrictive, CPU intensive version of C++ so I don't see why so many java users argue that C++ sucks... The language isn't that different, except java ENFORCES object oriented class structures on the user, and C++ makes it optional... And so what if C++ doesn't manage your memory for you, 99.99% of the time you don't even need that complex of a memory management system anyway... There are faster and more appropriate solutions, ones that don't lurk in the background eating your CPU and forcing your users to download a large, bulky runtime environment.

But I guess if memory management isn't your thing...

---

### Post by lnostdal on 2007-01-22
I'm no fan of neither Java or C++ .. but still gotta point out some things.

> **Wybiral said:**
> .. or JIT compiled... It's going to be a little slow.

Long running software has the potential to run faster than traditional compile-once solutions. This happens over time with run-time analysis and dynamic recompilation based on stuff a traditional compiler cannot predict or see.

> **Wybiral said:**
>  Not all of java can be machine compiled or it wouldn't maintain it's pretty garbage collection capabilities,

Uhm .. non-native code is _not_ a prerequisite for GC.

> **Wybiral said:**
>  and the parts that are JIT compiled, are one of the big reasons java is such a cookie monster about eating CPU speeds

I doubt this is true; the speed of Java has improved vastly after introduction of a JIT-compiler.

> **Wybiral said:**
> One can argue that the behind the scenes stuff is what makes VM'd languages so good, because garbage collection/memory management are all taken care of for you.

Well yeah, but a VM is not a prerequisite for GC either:
[http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29#Implementations](http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29#Implementations)


> **Wybiral said:**
> Personally, I've never had a problem freeing up my old memory and allocating new memory and general program specific memory problems in compiled languages like C++ You have to be one inattentive person to really mess things up that badly or to loose track of your memory that easily.

You must be better than most people then. You've never gotten a "weird" SIGSEGV while developing C-software? I find that very hard to believe ... 


> **Wybiral said:**
> Also, if I'm going to opt for an interpreted language, I'll at least use one that's more dynamic than java (like python/ruby)

Java's like a bulky, restrictive, CPU intensive version of C++ so I don't see why so many java users argue that C++ sucks...

Java isn't interpreted. Python/Ruby is way more dynamic than both C++ and Java though. 

If you never get SIGSEGVs (not that these are the only problems that show up when lacking GC!) then I guess Java doesn't have much to offer compared with C++.


> **Wybiral said:**
> There are faster and more appropriate solutions, ones that don't lurk in the background eating your CPU and forcing your users to download a large, bulky runtime environment.

I guess you're running your Python/Ruby-software without runtime environments too then. :} All (application)software - also C-software, has dependencies; that's why things like installers and APT exist. I also doubt Python/Ruby is faster than Java; last time I checked they where interpreted while Java is compiled to native code.

Maybe Java is closer to C++ in some ways .. a "C++ with only GC added" .. but GC is definitively not an insignificant addition IMHO.

I'm still voting for a language/implementation/environment with the dynamic features of Ruby/Python++beyond, _and_ compilation to native optimized code though.

---

### Post by runningwithscissors on 2007-01-22
> **lnostdal said:**
> Maybe Java is closer to C++ in some ways .. a "C++ with only GC added" .. but GC is definitively not an insignificant addition IMHO.
Just wanted to point out. C++ has garbage collectors available for it too. :wink:

I don't mind Java. It isn't slow, despite what people say. I am just not very comfortable with it, that's all.

---

### Post by lnostdal on 2007-01-22
> **runningwithscissors said:**
> Just wanted to point out. C++ has garbage collectors available for it too. :wink:

While I am aware of this, I wonder how well it works in practice (edit: well, looking at the site I mention below - it does mention some examples) considering it is not part of "the standard" or core of the language. 

There seem to be some potential "holes" as described here for instance: [http://www.hpl.hp.com/personal/Hans_Boehm/gc/issues.html](http://www.hpl.hp.com/personal/Hans_Boehm/gc/issues.html)  I must say I have not bothered with experimenting with this as I'm more into using standard C when really needed - combined with higher-level languages where GC usually already exists and is well supported, and things like finalization takes care of memory/resource management in stuff allocated at the C-side etc.. Does anyone have experience with this however?

---

### Post by phossal on 2007-01-22
My staff and I wrote  a replacement program (using Java) for a large commercial application originally written in C++. It has a fairly sophisticated GUI front-end, routinely opens sockets to retrieve information from the web, runs multiple threads, manages a pool of database connections (to a legacy database) via JDBC, and provides a bunch of ancillary services using add-ins. The business we wrote it for depends on it. It's significantly faster than its C++ counterpart on all of their Windows XP desktops, has a significantly *smaller* code base, and still works like magic on their Unix server.

Java is a great language. Like *most* things in life, a significant percentage of the problems people will report are the fault of the people rather than the object of their complaints.

Here is a valid downside though: From a commercial development perspective, it's very, very easy to reverse Java code. Even modern, obfuscated Java is relatively easy to revert to source. Depending on how aggressively you plan on protecting your code, with Java, you're one step closer to the courts.

---

### Post by Tomosaur on 2007-01-22
> **pmasiar said:**
> 
[*]**verbosity:** VeryLongUglyType someName = new VeryLongUglyType(); I see something typed twice :twisted: Why it cannot be just VeryLongUglyType someName = new(); I  just entered  the type?

Because the type is not the same as the instance. You can use a superclass as the type, and a subclass as the instance, such as:
Object myObject = new String("Hello!");

> 
[*]**Byzantine API**: depending on what team in Sun implemented it (and phase of the moon?), functionality is in static or object methods with slightly different names. How I am supposed to remember all that?

What? The documentation is there for you to read.

> 
[*]**object ravioli:** Instead of spaghetti code, we now have hundreds of small raviolis, stuffed with raviolis. Which one hides what you want? Example: ArrayList is *not* array, nor list of arrays.

No, but it IS an array-based list, hence the name. An ordinary List does not have the array features of an ArrayList.

> 
[*]**Object obsession:** why o why everything needs to be an object? I don't care about OOP religion - I have problems to solve before deadline! Why I cannot have simple print? One smart improvement I've seen was designing package P with overloaded P.rint() function to make printing simpler. Come on, WTF?

It's just how it's done. print itself is not an object, it's a method in a stream object. You are using the static method print. I actually prefer this way, it keeps me on my toes. Writing 'print' is faster, yes, but that's life. Speed isn't everything :)

> 
OK I give up and confess: I am pythonista who became weak and spoiled :-) and cannot handle real badass strictly typed language as I was able before - my tolerance to syntax pain is   substantially decreased. I am slowly adapting to that pain again - and let me tell you *it hurts*. Somewhere I read that many languages have syntax sugar to make tasks simpler - and java invented **syntax vinegar** to enforce object religion :-)

You like python too much :P

---

### Post by pmasiar on 2007-01-22
You asked what is wrong with java - don't whine and don't be offended now when i am telling you what exactly :-)

> **pmasiar said:**
> **verbosity:** VeryLongUglyType someName = new VeryLongUglyType(); I see something typed twice :twisted: Why it cannot be just VeryLongUglyType someName = new(); I  just entered  the type?

> **Tomosaur said:**
> Because the type is not the same as the instance. You can use a superclass as the type, and a subclass as the instance, such as:
Object myObject = new String("Hello!"); 

My feeling about java is: they tried to make language which gives you 100% of control. Control comes with price; you need to be exact of many things, which you don't care in 98% of the time, but need a way to control it in freak 2% of the cases. 

Java choose to inflict pain of total control, needed only in 2% of the cases, also in rest of 98%, because "it will allow you to have it your way in that 2%". And i am not buying it. How often you used superclass on left side? String IS-A Object and you can use it where Object is required anyway - but you defined it as String because you need it's String methods, no?

IMHO in 98% VeryLongUglyType is on both sides, mentioning it twice is syntax vinegar. Sugar would be to have it once, and special case to change it if needed. 

How often you *don't* use VeryLongUglyType on both sides? Is it more than 2%? In Python we have mantra: **special cases are not special enough to break the rules** :-)

> **pmasiar said:**
> **Byzantine API**: depending on what team in Sun implemented it (and phase of the moon?), functionality is in static or object methods with slightly different names. How I am supposed to remember all that?
**object ravioli:** Instead of spaghetti code, we now have hundreds of small raviolis, stuffed with raviolis. Which one hides what you want? 


> **Tomosaur said:**
> What? The documentation is there for you to read.

I know - all 20,000 pages of docs. That exactly what is wrong. Python pocket reference is 130 pages of pocket format - where is my "pocket java" reference?

Why number has .toString(), but not .round() method? Why local variables are initialized differently from heap? etc.

> **pmasiar said:**
> **Object obsession:** why o why everything needs to be an object? I don't care about OOP religion - I have problems to solve before deadline! 

> **Tomosaur said:**
> It's just how it's done. print itself is not an object, it's a method in a stream object. You are using the static method print. I actually prefer this way, it keeps me on my toes. Writing 'print' is faster, yes, but that's life. Speed isn't everything :)
LOL so you are slave of OO religion and you like it - it "keeps you on your toes" even if it does not makes sense and hurts productivity. 

> **Tomosaur said:**
> You like python too much :P

yes, this is one thing we can agree. :-)

Let me add: I like some features of java. I like that I can copy java bytecode from Linux to Windows and it just runs. i like that I can define a class as interface, and force it to implement fome methods. I like that there are libraries for anything under the sun - even hard-to-use library is better than none :-)

I don't care much about java speed - memory footprint is bigger concern for me, but you can solve it by just adding RAM, it's cheap solution.

My biggest concern is how everything in Java becomes static: exception, data structures, ossified program structure. If you made misake in design, it is hard to change direction. It goes on like a Titanic...

In python, i needed complex data structure, which was list of dictionaries (hashes), some elements were lists of dictionaries. Then I found that some elements of 2nd-level dicts needs be lists. No big deal in Python.

---

### Post by phossal on 2007-01-22
> **laxmanb said:**
> I'm learning how to program with Java & frankly, i love the language! 
The API seems comprehensive enough & the language seems easy to program in (having done C/C++ before, Java is easy enough... but i get confused the second i look at VB.Net code or python code...)

however, i've seen a lot of ppl say Java has a lot of problems... i would really like to know those people's point of view... so please, enlighten me!

My first language was Java. Once you've learned it thoroughly, you'll be able to proceed in any direction. Perl, Python, Javascript and PHP are what I refer to as "candy" languages. You can learn 90% of what you want to learn in a day, because 99% of what you want to learn already exists as an example in a book. They're relatively simple, and existing code is readily available and easy to manipulate. 

Plus, you'll have no trouble going in the other direction, toward C and beyond. 

Just keep plowing forward.

[edit] As for Java being slow, it's usually the result of poor configuration and/or poor programming on the part of the app developer. Bad programmers write bad programs in all languages.

---

### Post by Ben Sprinkle on 2007-01-22
```

public class NothingsWrong {
    public static void main(String[] args) {
        String s = "Nothing is wrong with Java in my eyes. :)";
        System.out.println(s);
    }
}

```

---

### Post by neoflight on 2007-01-22
disp(matlab is so easy....!)

---

### Post by phossal on 2007-01-22
> **Ben Sprinkle said:**
> ```

public class NothingsWrong {
    public static void main(String[] args) {
        String s = "Nothing is wrong with Java in my eyes. :)";
        System.out.println(s);
    }
}

```

That's *a lot* of code to print a single sentence. Almost all of my programs print just a single sentence. I should switch to Python|Perl|PHP|Javascript, because all of my one-line programs would be much easier to write. Except, if I need to change my sentence, I'll have to completely rewrite that code over again.  And if I want to copy and paste my one-liner python program into another, I'll have to make it a subroutine or a function, and that will add lines.

I guess that would be stupid after all. Never mind.

It's as ugly in C, isn't it?
```

#include <stdio.h>

int main () {
    printf("Nothing wrong with C, either!");
    return(0);
};

//Blank Line
```

Yet, almost *all* of our favorite OSes and *baddest* programs are written in C or C++. Python is sweet for, like, extracting HTML text, and one-line terminal programs. Sweet! 

As soon as Debian is written in Python, I'm converting. Until then, I'll stick with the not-so-sweet languages.

---

### Post by Ben Sprinkle on 2007-01-22
> **phossal said:**
> That's *a lot* of code to print a single sentence. Almost all of my programs print just a single sentence. I should switch to Python, because all of my one-line programs would be much easier to write. Except, if I need to change my sentence, I'll have to completely rewrite that code over again.  And if I want to copy and paste my one-liner python program into another, I'll have to make it a subroutine or a function, and that will add lines.

I guess that would be stupid after all. Never mind.

Funny, but not persuasive.

One liner. ;)
```

public class NothingsWrong { public static void main(String[] args) { System.out.println("Nothing is wrong with Java in my eyes. :)"); } }

```

---

### Post by phossal on 2007-01-22
> **Ben Sprinkle said:**
> One liner. ;)


Technically, it's a "single line". "Liner" isn't in the OED either. Good try, though. Don't you have any cheesy web scripts to write? :p  lol I'm not as politically correct as my friends in these forums. Python sucks. You use it for junk programs, as we all do for Sys Admin, web junk, and prototyping. We don't write commercial apps in Python|Perl, etc.

---

### Post by runningwithscissors on 2007-01-22
> **lnostdal said:**
> While I am aware of this, I wonder how well it works in practice (edit: well, looking at the site I mention below - it does mention some examples) considering it is not part of "the standard" or core of the language. There seem to be some potential "holes" as described here for instance: [http://www.hpl.hp.com/personal/Hans_Boehm/gc/issues.html](http://www.hpl.hp.com/personal/Hans_Boehm/gc/issues.html) 
It works fine, in fact. There is a shared pointer implementation provided by the STL, which is about as standard as you can get with C++ (which is admittedly, not much). Another one is provided by the excellent Boost C++ libraries (which too, are quite popular).
Use them wisely, and you have a working garbage collection implementation as good as any, since there is hardly any garbage generated at all.

> **lnostdal said:**
>  I must say I have not bothered with experimenting with this as I'm more into using standard C when really needed - combined with higher-level languages where GC usually already exists and is well supported, and things like finalization takes care of memory/resource management in stuff allocated at the C-side etc..

I myself use C, because I find C++ rather large and unweildy. But is is an alright language. People still remember C++ unfavourably from its pre-standardisation days.

---

### Post by Ben Sprinkle on 2007-01-22
> **phossal said:**
> Don't you have any cheesy web scripts to write?
Actually Java is not a scripting language, it's a programming language, the difference between the 2 is that one is getting compiled. ;)
I also havn't done any applets yet, I am still on the basics and plan to stay at console for a bit untill I have enough experience for Swing.

---

### Post by Wybiral on 2007-01-22
lol, lnostdal, you couldn't have possibly picked out the smallest details...

When I made the VM/GC comment I said so because *generally* they go together, and also because that is probably the #1 argument when people are trying to claim that java is the jesus of programming languages.

My main point was that most of the time, a complex garbage collection system simply isn't needed..

And as far as me using ruby/python and them still requiring a runtime environment... Theirs isn't nearly as slow or bulky as javas...

So you think that JIT compiling is faster? Not quite... The process of compiling, especially from java bytecode to machine code, is a complex process... Anyone who's ever had to compile a large C program can tell you this (wait... wait... wait...) Also, anyone who's ever had to load a large java program can tell you this (wait... wait... wait...) Also, JIT compiling doesn't happen to ALL of the code, just select parts. I don't think it's worth the wasted CPU power to have a few select parts compiled...

Saying that interpreted languages are usually faster than compiled is kindof silly... Maybe for some stuff the interpreted languages act as a fast library for the programmer offering certain routines that the language is designed for simple use... Like iterators and advanced comprehensive methods. And if that's what you mean... Then yeah, you are probably right (of course the C programmer could always write these things, or use a similar library)

But if you mean that an interpreted language is going to compute math or reference/dereference as fast as a well compiled machine code executable... Sorry, think about the logic there. Don't tell me mathematical computations aren't that big of a deal, or that blazing fast programs aren't necessary...

I've spent the past couple of weeks working on an optimizing BSP level loader/renderer for a game engine (lightmaps and all), and a MD2 model loader/animated renderer as well. I can assure you that this kind of stuff NEEDS to be compiled to machine code to reach usable speeds. And trying to JIT compile this... Well, it takes a long time for me to compile it in C, I don't want my users to go through this every time they load the program...

---

### Post by phossal on 2007-01-22
> **Ben Sprinkle said:**
> Actually Java is not a scripting language, it's a programming language, the difference between the 2 is that one is getting compiled. ;)
I also havn't done any applets yet, I am still on the basics and plan to stay at console for a bit untill I have enough experience for Swing.

Are you responding to me? That doesn't appear to be related to anything I posted. In fact, I think we're both suffering from miscommunication. Who's side are you on? What language do you *prefer?*

---

### Post by laxmanb on 2007-01-22
> **Wybiral said:**
> But if you mean that an interpreted language is going to compute math or reference/dereference as fast as a well compiled machine code executable... Sorry, think about the logic there. Don't tell me mathematical computations aren't that big of a deal, or that blazing fast programs aren't necessary...

I've spent the past couple of weeks working on an optimizing BSP level loader/renderer for a game engine (lightmaps and all), and a MD2 model loader/animated renderer as well. I can assure you that this kind of stuff NEEDS to be compiled to machine code to reach usable speeds. And trying to JIT compile this... Well, it takes a long time for me to compile it in C, I don't want my users to go through this every time they load the program...

A. Java isn't interpreted anymore... it uses JIT compilation... in theory, you could get better performance than native code... the net is full of "Java faster than C" comparisions... and you get better performance with every release of the JRE...

B. You can use Java for 3D... to see serious 2D/3D & animations, try project looking glass, an in-the-works display manager written completely in Java... that uses plently of 3d/2d widgets and animation... runs quite smoothly if you have a modern computer...

---

### Post by Wybiral on 2007-01-22
I never said java was interpreted.

And if you read my previous post (and the one before that) you will see what I mean about JIT compiling.

Not all of it is JIT compiled, from the research I've done, only small chunks. Most of it is still on top of a VM... This is what makes it's garbage collection work so well, it is in charge of referencing all of the memory.

This is all great, depending on your app... But is nothing but baggage when you don't need such a complex GC, and when you need every last inch of CPU power.

I know that there ARE games, and 3d software written in java... But they still wont be as fast as machine code... Not with the amount of math they will have to do. Intensive 3d software is touchy, you just can't afford all of the extra baggage.

---

### Post by pmasiar on 2007-01-22
> **Ben Sprinkle said:**
> Actually Java is not a scripting language, it's a programming language, the difference between the 2 is that one is getting compiled. ;)

Not sure why you excluded say perl or bash from programming languages :-) IMNSHO bash definitely *is* a programming language, thank you very much!

Meaningfull difference will be:
- statically (C/Java) vs. dynamically (Perl/Python etc) typed
- compiled only (C++/Java), interpreted only (PHP, perl), compiled optional (Lisp, Python)
- garbage collected (Java, Python, Ruby) or not (C/C++)
- exceptions checked statically (Java) dynamically (Python) or with luck (Perl)
- paradigm: OOP only (Java), procedural only (bash?), mixed (C++, Python, Perl), functional (Lisp)

And still is not as clear cut - there is implementation of C for VEX robots which is interpreted, etc.

And maybe couple more distictions - but what "scripting" means exactly for you? Do you ever used any dynamically typed language? From your comment is hard to guess your level of experience beyond Java.

---

### Post by hod139 on 2007-01-22
Speaking of Java and OpenGL, have you seen the [jogl demos]("https://jogl-demos.dev.java.net/").  And the no arch dependencies, just click and it runs!!!

---

### Post by laxmanb on 2007-01-22
> **Wybiral said:**
> I never said java was interpreted.

And if you read my previous post (and the one before that) you will see what I mean about JIT compiling.

Not all of it is JIT compiled, from the research I've done, only small chunks. Most of it is still on top of a VM... This is what makes it's garbage collection work so well, it is in charge of referencing all of the memory.

This is all great, depending on your app... But is nothing but baggage when you don't need such a complex GC, and when you need every last inch of CPU power.


So... there are GC facilities for C/C++... what VM do they run on??

advantages of JIT code over native code(Copied from Wikipedia):

> On the other hand, a JIT runtime system is able to collect statistics about how the program is actually running in the environment it is in, and it can rearrange and recompile for optimum performance. This data is normally difficult or even impossible to obtain for conventional compilers,

Neverthless, JIT compilation is still considered advantageous in many scenarios because of its portability, flexibility and performance.

---

### Post by Wybiral on 2007-01-22
> **laxmanb said:**
> So... there are GC facilities for C/C++... what VM do they run on??

advantages of JIT code over native code(Copied from Wikipedia):

C/C++ don't have GC, but I mentioned this in one of my previous post's and how it generally wasn't even necessary and in stead, gives you the added benefit of some sweet sweet overhead baggage.

BTW, I have read a lot about JIT compiling... And about the JVM and JRE, I'm not sure how reliable a wikipedia article is, lol, but that's not the point...

Show me one article from sun about the JIT compiler being so advanced it can actually rearrange program parts to fit the machine state when it JIT compiles... I've seen people argue this before, but I have yet to find any proof. Toss me some?

I don't see how machine code could be rearranged in that sort of way. Plus, as I mentioned before... The JIT compiler does not compile all of the program, certain chunks of it are deemed compilable and those get "compiled" during program execution...

---

### Post by lnostdal on 2007-01-23
> **Wybiral said:**
> Saying that interpreted languages are usually faster than compiled is kindof silly... Maybe for some stuff the interpreted languages act as a fast library for the programmer offering certain routines that the language is designed for simple use... Like iterators and advanced comprehensive methods. And if that's what you mean... Then yeah, you are probably right (of course the C programmer could always write these things, or use a similar library)

I really have no idea what you're talking about. Are you commenting on something I've said? 

In general -- I can't seem to make much sense of parts of your posts. They contradict themselves (not just isolated; but cross-post-wise) in several places. Yes, mostly I ignore what you say when I respond and just point out the isolated things that are wrong "fact-wise". But I'd best not bother with responding at all I think.

Hm, well, no worries -- don't really matter to me; just slow down on the sugar/drugs .... :}

edit:
Some other comments:

> My main point was that most of the time, a complex garbage collection system simply isn't needed..

That depends on what you're doing most of the time. Is this still a surprise to you, or are you starting to realize it without stating it by old habit or by a bias towards your own current dabblings? :P 

You mention the inner workings of a real-time graphics engine as a (valid; I agree) example but seem to forget that that's just one isolated part of a game-engine. Software in general usually has isolated spots like these. Describing how to push data down bus-pipes fast is something C is suitable for, but there are other problems to be solved that turn out to be very hard to describe and handle (not for you; but for the language itself) with C and/or without GC.

> And as far as me using ruby/python and them still requiring a runtime environment... Theirs isn't nearly as slow or bulky as javas...

As stated by others, and me - several times (I think); Java is compiled which means it usually runs faster than Ruby/Python.

---

### Post by Wybiral on 2007-01-23
Ok, Well said... Then show me some practical examples of times when garbage collection is unmanageable in C/C++

Particularly C++ because it shares some of the OOP features that java has. And also because C++ has classes with destructors, a nice time to clean things up.

So far, I haven't seen a need for GC, but maybe I am missing out...

You seem kind-of huffy because I'm not a Java fan... Saying you're ignoring someone doesn't make you look like a very reasonable person, it makes you look like another evangelist.

> ...Yes, mostly I ignore what you say when I respond...

Especially with the 2-year-old comments...

> ...just slow down on the sugar/drugs...

I am trying to explain to people the downsides of software running from VM's, the CPU usage involved in JIT compiling, and the extra overhead as a result of GC. I don't think I've contradicted myself... I may have learned a little more about Java's internals since the last time I talked about this subject...

How about trying to show me some research results or some links? My posts have been based off of what I've been reading from various resources (including sun) about the JVM, JIT, and Java bytecode format. I don't see where you're coming from claiming that I am wrong "fact-wise"

What have I been wrong about?

---

### Post by lnostdal on 2007-01-23
> **Wybiral said:**
> ..show me some practical examples of times when garbage collection is unmanageable in C/C++

I think you'll have to discover them yourself as I have no handy examples hanging around for you to break down.

  [http://www.memorymanagement.org/articles/begin.html](http://www.memorymanagement.org/articles/begin.html)
  [http://en.wikipedia.org/wiki/Manual_memory_management#Criticism](http://en.wikipedia.org/wiki/Manual_memory_management#Criticism)

Problems with memory/resource-management escalate quickly as design-problems start to show up. GC was invented for perfectly good reasons by programmers who knew what they where doing. 

Note that I have no problems with "avoiding" your question like this.


> **Wybiral said:**
> You seem kind-of huffy because I'm not a Java fan...

Not at all; I've already stated that I'm not a Java fan. But that does not mean I'm "OK" with false statements about Java -- or any language really.


> **Wybiral said:**
> Saying you're ignoring someone doesn't make you look like a very reasonable person, it makes you look like another evangelist.

I'm ignoring stuff that make no sense -- if that makes me an evangelist or a "bad person" I'm more than fine with people believing that.


> **Wybiral said:**
> What have I been wrong about?

See my previous posts where I mention some points. 

If you want a "model"; in general you state something that is perfectly true -- then turn around and contradict your first point to make another point "seem true" .. or something like that. 

I'm not going to comment any further if you can't see this based on what I've already said -- I think.

---

### Post by runningwithscissors on 2007-01-23
> **lnostdal said:**
> I think you'll have to discover them yourself as I have no handy examples hanging around for you to break down.

  [http://www.memorymanagement.org/articles/begin.html](http://www.memorymanagement.org/articles/begin.html)
  [http://en.wikipedia.org/wiki/Manual_memory_management#Criticism](http://en.wikipedia.org/wiki/Manual_memory_management#Criticism)

Erm... In modern C++ you don't _have_ to manage memory manually. You can do so if you like, but it isn't required of you.

---

### Post by lnostdal on 2007-01-23
> **runningwithscissors said:**
> Erm... In modern C++ you don't _have_ to manage memory manually. You can do so if you like, but it isn't required of you.

You're not required to delete or delete[] your objects in C++?

---

### Post by Magnes on 2007-01-23
> **runningwithscissors said:**
> Erm... In modern C++ you don't _have_ to manage memory manually. You can do so if you like, but it isn't required of you.

You HAVE to manage memory manually. Of course it could be hidden in some class constructors and destructors (as in STL) but it's still there.

---

### Post by Tomosaur on 2007-01-23
Lay off the personal stuff guys, it's all just a matter of opinion. It's just not worth getting worked up over.

Wybiral - yes, the VM reliance does present problems - but with the power of today's computers, it really isn't anything that serious. Most programs are not particularly intensive. With the exception of programs like games and editing software which require lots of memory and processing ability, most software can make do with **lots** of room to spare. The web is littered with examples of Java running faster (in some cases) than C/C++, or at least comparable to. The natue of the Java language means performance issues are largely down to poor programming than then JVM, and thus, it's not really a 'Java issue'. Java typically tries to enforce good programming techniques (whether it achieves that is a matter of opinion :P), but if the programmer still writes bad software, then the execution is penalised. C/C++ and other languages suffer the same problems, but the crux of the matter is that compiled languages do what they're told to. JVM / JIT compiled languages are examined to make sure what they're doing is acceptable. Errors are caught and handled by the JVM rather than propogating through the system and causing damage elsewhere. I find it perfectly reasonable. I prefer C over C++ (although I wouldn't say I'm a guru in either, at all), but I find the way Java works to be extremely beneficial. JIT compilation also allows a speed increase, but the JVM itself has undergone massive improvements since its first few appearances, and, particularly with computers today, performance problems are pretty much a thing of the past. Many of the arguments about Java's speed issues are either unfounded, or irrelevant today. The end user is unlikely to notice a performance drop between an application in C/C++ (or any other language) and a clone in Java. Java's real issue is the web start, which is, frankly, painful to watch. Although it can only be expected (the software still needs to be downloaded etc), I think most people expect web content to be 'on demand'. The idea of a Java Web Start is a misnomer - it neither starts instantly, nor does it run from the web. It's just a different way of installing stuff, and one which I personally find to be pretty damn annoying.

---

### Post by lnostdal on 2007-01-23
> **Magnes said:**
> You HAVE to manage memory manually. Of course it could be hidden in some class constructors and destructors (as in STL) but it's still there.

..and these "outer object wrappers" will themselves need to be managed at some point. The lifetime of objects is not always predictable by scope only and must be "(de)allocated at runtime" at "random" (hoping I'm wording this right now ..).

---

### Post by runningwithscissors on 2007-01-23
> **Magnes said:**
> You HAVE to manage memory manually. Of course it could be hidden in some class constructors and destructors (as in STL) but it's still there.
Nope. You don't have to hide stuff in constructors and destructors either.
Dynamically allocated memory ought to be handled using smart pointers.
[Smart pointers](http://en.wikipedia.org/wiki/Smart_pointers)

---

### Post by lnostdal on 2007-01-23
> **runningwithscissors said:**
> Dynamically allocated memory ought to be handled using smart pointers.

Smart pointers is a form of automatic memory management or GC. But they are not the "real thing" IMHO.

---

### Post by runningwithscissors on 2007-01-23
> **lnostdal said:**
> Smart pointers is a form of automatic memory management or GC. But they are not the "real thing" IMHO.
Why not? If you are generating minimal garbage, why is there need for a garbage collector?

---

### Post by lnostdal on 2007-01-23
> **runningwithscissors said:**
> 
[quote=lnostdal]Smart pointers is a form of automatic memory management or GC. But they are not the "real thing" IMHO.
Why not?[/QUOTE]

They do not work because as soon as I've gotten to a level where they where really required other things at just about the same level has started interfering and cluttering things up so badly that a mix of both non-standard ad hoc smart-pointers, static typing restrictions, thread safety, lack of proper meta-programming features and other things has started to collapse in on themselves .. uhm .. well; leading _both_ smart-pointers and C++ itself as less desirable choices at that point. Things mix together and create incompatibilities and problems because they are not part of the "core".

They are like Boost as a whole; lots of good ideas and intentions borrowed from other places -- which sadly in practice turn out buggy or hard to maintain (stuff leak to your app-code) and just plain ugly (code-wise) real fast because they are features padded onto a core that was not designed to maintain these things properly.

These things might work in simple cases (which is why I almost never post examples; they are too easy to break down - almost like the "turing-complete" argument) but I've had them break down to many times (the times when they where really needed) for me to call them the "real thing".

I'm not sure if you're content with this answer, but it's not really possible to attribute to an isolated example or at least within the smart-pointer concept itself --  I think. It's the dependencies or concerns between them that break things down at this level.

edit: ..or maybe it's just because C++ isn't how my brain is wired at all; after switching to Lisp I'm many steps closer.  But I somehow doubt any brain is wired for C++ natively; it's not a matter of logical understanding and agreement between the _thinking_ brain, problem and the language -- it's more like the _remembering brain_  has to work overtime enforcing upon oneself that things in the limiting language are the way they are because of some external, vague, unrelated reason to what you're doing here right now. You know -- the problem at hand? The thing you where trying to solve in the first place?

When I hear C++ I'm hearing things like "why?!" and "why not?!" being repeated internally without ever finding good answers - or alternatively _proper_ ways to work around the issues.

*sheez* .. turned into another rant yes :}

---

### Post by runningwithscissors on 2007-01-23
> **lnostdal said:**
> edit: ..or maybe it's just because C++ isn't how my brain is wired at all; after switching to Lisp I'm many steps closer.  But I somehow doubt any brain is wired for C++ natively; it's not a matter of logical understanding and agreement between the _thinking_ brain, problem and the language -- it's more like the _remembering brain_  has to work overtime enforcing upon oneself that things in the limiting language are the way they are because of some external, vague, unrelated reason to what you're doing here right now. You know -- the problem at hand? The thing you where trying to solve in the first place?

When I hear C++ I'm hearing things like "why?!" and "why not?!" being repeated internally without ever finding good answers - or alternatively _proper_ ways to work around the issues.

*sheez* .. turned into another rant yes :}
That would be it, I think.
I am no big fan of C++ either. Or OOP (that is another discussion).
Java is quite similar, in fact.
I just wanted to clear up some of the long-held beliefs about C++.

---

### Post by laxmanb on 2007-01-23
Thank you everybody! it's very informative to know your opinions on Java!

have fun programming in your preferred programming language...

now... how do you close a Topic??

---

### Post by lnostdal on 2007-01-23
> **laxmanb said:**
> now... how do you close a Topic??

Luckily, that's not possible (edit: by random users themselves). It'll die out and meanwhile, well -- people will be enable to have _one_ single thread to avoid/ignore instead of a myriad of threads referring to each other. 

..and hey -- who says anyone "owns" a thread in a public forum in the first place? 'Twas makes the "Wild Wild Web" cool in the first place IMHO. :)

In the "old days" of [USENET](http://groups.google.com/groups/dir?sel=33583294) - well, I still use it, people could create sub-discussions seeing as all threads or topics where based on a tree-structure by default. Stuff sometimes goes on for months; pretty interesting and intense some of it. :)

..but do as you please; easiest way to close a topic here is probably by contacting some mod/admin.

---

### Post by Wybiral on 2007-01-23
Well, anyone who know's the C++ STL well enough know's about: Lists, Deques, Queues, Stacks, Maps, Priority Queues, and my all time personal favorite, Vectors. These allow you to easily manage dynamic memory without any risk of failure.

Also, the use of constructors and deconstructors in classes does make it exceedingly easy to manage your memory...

```

class example {
   int* myMemory;
   example(){}

   ~example(){
      delete [] myMemory;
   }

   void create(int size){
      myMemory = new int (size);
   }
}

```

So, no, I still don't see a point in sophisticated GC systems that are only going to add to the overhead.

Also, you haven't showed me any times that I've made "no sense" or "contradicted myself" or put more clearly by you...

> If you want a "model"; in general you state something that is perfectly true -- then turn around and contradict your first point to make another point "seem true" .. or something like that.

You are the one who is not making sense...

---

### Post by phossal on 2007-01-23
For the record, I like all languages.

---

### Post by pmasiar on 2007-01-23
I tried to trimm out non-relevant parts

> **phossal said:**
> I apologize for making this post i (...)I'm sorry.

I am really confused why this rant about me and Python is here in thread about Java. I like python too. I will try to get just the facts:

You seems to suggest that Python is not good choice for commercial programs:

> **phossal said:**
> Python sucks. (...)  We don't write commercial apps in Python.

I disagree with a link: [Commercial success in Python]("http://www.python.org/about/success/"). Looks like you underestimate Python. I might be wrong.

Why it is here in thread on java? I don't know. This was the only relevant fact I was able to respond to. I guess I should not.

I would expect someone flaming me for what I [dislike on Java]("http://ubuntuforums.org/showpost.php?p=2047145&postcount=16") but it was forgotten. Oh well.

---

### Post by phossal on 2007-01-23
I apologized in response to your comment that I was engaged in Drive-by smear. I thought you would understand why my apology was here given this [tempertantrum]("http://ubuntuforums.org/showthread.php?t=342875")

---

### Post by pmasiar on 2007-01-23
I am sorry. I should say I accept apology although I am not sure why you feel need to apologize (and why in this thread). I also should not say "rant" for an apology. I will be much more carefull to responding to you. I know I promised that before. :-(

I am also not sure where I suggested I feel you attacked (smeared) *me personally*. In the link you mentioned I said "smear against Python" when you suggested that Python is fad (I also tried explain why I believe it is not). I did not realized that I am embodiment of Python for you :-) Of course it was joke, I know I am not. I am missing some libraries :-)

Looks like you disabled PM or something, I could not apologize and try clear this misunderstanding via PM.

If only someone linked me to a way how to comprehend enormous Java's API.

---

### Post by lnostdal on 2007-01-23
> **Wybiral said:**
> Well, anyone who know's the C++ STL well enough know's about: Lists, Deques, Queues, Stacks, Maps, Priority Queues, and my all time personal favorite, Vectors. These allow you to easily manage dynamic memory without any risk of failure.
...
So, no, I still don't see a point in sophisticated GC systems that are only going to add to the overhead.

Heh; I don't think you really know what GC means. Here's a single simple example of one amongst the many things that can go wrong:

```

#include <iostream>
#include <vector>
#include <cassert>

using namespace std;


class A{
public:
  static unsigned int num_alive;
  A(){
    num_alive++;
    cout << "A:A()" << endl;}

  ~A(){
    num_alive--;
    cout << "A:~A()" << endl;}

  static void printNumAlive(){
    cout << "A::num_alive -> " << num_alive << endl;
  }
};


unsigned int A::num_alive = 0;


void next(){
  cout << endl << "===================================" << endl << endl;}


int main(){
  // All good and well:
  {A a1; A a2;
    A::printNumAlive(); assert(A::num_alive == 2);}
  A::printNumAlive(); assert(A::num_alive == 0);
 

  next();
  vector<A*> av;
  av.push_back(new A);
  av.push_back(new A);
  A::printNumAlive();
  cout << "av.size() -> " << av.size() << endl;

  next();
  av.erase(av.begin()); // erase first element.
  A::printNumAlive();
  cout << "av.size() -> " << av.size() << endl;
  
  assert(av.size() != A::num_alive); // == fails; which mean we now have a leak.
  return(0);}


/*
  lars@ibmr52:~/programming/c$ g++ -Wall -g c.cpp -o c && ./c
  A:A()
  A:A()
  A::num_alive -> 2
  A:~A()
  A:~A()
  A::num_alive -> 0
  
  ===================================
  
  A:A()
  A:A()
  A::num_alive -> 2
  av.size() -> 2
  
  ===================================
  
  A::num_alive -> 2
  av.size() -> 1
*/

```

Feel free to dispute this as irrelevant or a "minor issue". I've gone and broke my own promise of never posting simple, understandable examples anyways. edit: Well, let's imagine some of the instances are referred to via other places (and another thread?) than `av'. It should be possible to solve; but keep building on this .. there will eventually be so much cruft it'll start breaking down on itself. Oh; and let's say you store pointers to some static data in there as well; that should give some "weird errors" in your manual cleanup code.

edit: To keep this somewhat on track; point is that Java has GC which makes Java avoid these problems while C/C++ (in general) does not.

---

### Post by nick.inspiron6400 on 2007-01-23
I went to Java because i had loads of problems with Anjuta. I could never ever get it to work! A plug-in for everything! And that still didn't get it to work. My biggest problem was the Glade plug-in!

Nick,

---

### Post by Wybiral on 2007-01-23
I see your point... I'm not trying to be disagreeable, Its just... This is a thread about what it wrong with Java, and I am asserting that it has some unnecessary overhead as one of my points. You can always find a flaw, C++ has them... Java has them.

And that source code... I don't know why you are combining dynamically allocated memory with "new" AND STL vectors... The point of the STL containers are to avoid using unsafe memory like "new" and "malloc"

The main problem with your code is that you are checking the size of av (a vector of type "A") against the total number of "A" objects... That's obviously going to cause an error. The easiest way to solve it would be to use local and global counts.

If you use a vector of type "A" instead of a vector of type "A*" you won't have those memory leaks even with the assertion error (which wouldn't cause a memory leak had you put "delete" in the class "A" deconstructor... It would still report an error because you are checking to see if the vector size is the global count of "A" objects)

But, you are right... There probably are times when GC is needed, but I still haven't found any that I can't solve with the STL and strategic memory management. Constructors and deconstructors are a really big help if you use them right.

---

### Post by lnostdal on 2007-01-23
> **Wybiral said:**
> I see your point... I'm not trying to be disagreeable, Its just... This is a thread about what it wrong with Java, and I am asserting that it has some unnecessary overhead as one of my points. 

Of course; but do try to mention "..some unnecessary overhead /in some cases/.." as GC is indeed _very_ handy and is _not_ unnecessary in other contexts. You _do_ get something viable in return from the investment in (possibly) extra overhead; it was invented and is used for very good reasons. :)

> **Wybiral said:**
> And that source code... I don't know why you are combining dynamically allocated memory with "new" AND STL vectors... The point of the STL containers are to avoid using unsafe memory like "new" and "malloc"

Just trust me on this; you need to allocate stuff with new/malloc (on the heap) for various reasons.

> The main problem with your code is that you are checking the size of av (a vector of type "A") against the total number of "A" objects... That's obviously going to cause an error. The easiest way to solve it would be to use local and global counts.

Uhm, what?

> If you use a vector of type "A" instead of a vector of type "A*" you won't have those memory leaks even with the assertion error (which wouldn't cause a memory leak had you put "delete" in the class "A" deconstructor... It would still report an error because you are checking to see if the vector size is the global count of "A" objects)

Dude, the destructor is never called in the first place? That's why I've put a `cout' call in the destructor to show that it actually isn't called at all.

The "problem", in this very simplified example - is that I've forgotten to iterate (yes; manual memory management -- which kind of was my point here) over each element and call `delete' on them. In the "real world" it probably would not be as simple as this because it might not be certain that the instances aren't still used elsewhere. Which should lead you --- right to smart pointers which I've already ranted about in this thread. :}

---

### Post by Wybiral on 2007-01-23
> as GC is indeed _very_ handy and is _not_ unnecessary in other contexts. You _do_ get something viable in return from the investment in (possibly) extra overhead; it was invented and is used for very good reasons. :)
As I said... There _may_ be cases where it is useful... But you do not _need_ it. And in the cases where it is _not_ used, it's just extra _overhead_

> Just trust me on this; you need to allocate stuff with new/malloc (on the heap) for various reasons.
Sometimes... But not always. It depends on how fast you want something to do... In C++ vectors are almost always better than new/malloc, and MUCH MUCH safer. Most situations can be 100% eliminated with STL containers. I only use new when I need to implement a insert/lookup quickly in a program... And thats when I need maximum speed, STL vectors are actually pretty fast in the first place... And without the overhead of GC.

> Uhm, what?
I will reiterate... You were checking the GLOBAL count of "A" objects because it was static in the class... Against the size of the "A" vector... They were NOT going to be the same size and will certainly raise an error with that assertion...

> The "problem", in this very simplified example - is that I've forgotten to iterate (yes; manual memory management -- which kind of was my point here) over each element and call `delete' on them. In the "real world" it probably would not be as simple as this because it might not be certain that the instances aren't still used elsewhere.

No need to iterate over anything... Had you used a class with a dynamically allocated element, you could delete it in the destructor.

Had you done that properly and used vectors as they were meant, you wouldn't need to delete anything... Next time try "vector<A> av;" instead of "vector<A*> av;" and use "av.push_back(A());" instead of "av.push_back(new A)" and you can eliminate  your memory errors 100% AND... Not require the overhead of GC.

I'm just saying... People often argue that Java is better than C++ because of GC... I don't understand... C++ handles dynamic memory beautifully if you know the STL and what you are doing.

---

### Post by lnostdal on 2007-01-23
Right, discussing this with you has finally turned out to be a total waste of time. I have nothing further to add about what I've already explained because you are obviously unable to understand any of it (as I expected when I regrettably posted the example).

---

### Post by Wybiral on 2007-01-23
No... I actually want to know... What are the practical situations where it would be too hard to clean up the garbage and old references in C++?

Once again... I'm not *trying* to be disagreeable here, but the topic was "What's wrong with Java??" and I am saying "Overhead is wrong with Java"

And I don't understand why you have taken such low blows as to claim that I am contradicting myself or that I don't make sense... If I don't make sense, enlighten me or point out where I am wrong...

That's all I am trying to do. You say that GC is important. I say there are other ways, ones which avoid the overhead of a complex GC system like Java has.

I'm not trying to stubbornly disagree with you, I just don't see your point... If you try to explain rather than trying to put me down, then maybe I would understand where you are coming from...

---

### Post by phossal on 2007-01-23
You two have been going at this a long time. Some of us would have liked to follow along and learn something, but it has been tough to do. You've both abused English punctuation so badly that it's very difficult to read it all and understand it. Keep the rest of us in mind, too. :)

---

### Post by jblebrun on 2007-01-23
Wybiral, the point of GC is to NOT think about memory allocation when it's not an important part of your programming task. When you say "GC is not necessary with a memory managment strategy",  you are not directly addressing Inos's point, because you have suddenly re-introduced the need to think about memory at ALL. 

By the way, your counter-example won't always work as intended... If you need to pass the vector on to another function to modify it, then if you use v.push_back(A()), then the A that gets created is destroyed when the function exits. So, you still need to use dynamic memory management in those cases.

You're completely missing his point. You don't NEED math libraries, either. You can re-implement exponentiation functions every time you need them. But why waste time? 

It doesn't matter how good you are with thinking about memory management... if it's not a core part of your programming task, then you're just needlessly introducing another source of errors.

---

### Post by lloyd mcclendon on 2007-01-23
> **Wybiral said:**
> Once again... I'm not *trying* to be disagreeable here, but the topic was "What's wrong with Java??" and I am saying "Overhead is wrong with Java"

you're right, but practically it's not a big deal at all.  the GC only runs when necessary, it's not a continuous real time thread.  it just pops up when the heap gets to a certain point and makes the program unresponsive for .1 seconds.  if you ever stumble upon a program that abuses the gc you can always fall back to object pooling.  the minimal overhead is more than worth it.

and i personally loathe the "c programmers are better because they know how to use malloc & free" argument.  i'd compare it to snobby porsche owners thinking they are good drivers just cause they know how to shift.  

understanding the concept of the heap is one thing, but having to actually manage it yourself is just tedious and a distraction from the real problem at hand.  have fun chasing memory leaks and dangling pointers, i'll focus on delivering the solution.  and i don't care how good you are at this, you WILL make mistakes and find yourself wasting time in the debugger.

> That's all I am trying to do. You say that GC is important. I say there are other ways, ones which avoid the overhead of a complex GC system like Java has.

again i'd argue that the total cost of memory management errors will always be far greater than the minimal overhead of gc.

---

### Post by runningwithscissors on 2007-01-23
> **jblebrun said:**
> 
You're completely missing his point. You don't NEED math libraries, either. You can re-implement exponentiation functions every time you need them. But why waste time? 

It doesn't matter how good you are with thinking about memory management... if it's not a core part of your programming task, then you're just needlessly introducing another source of errors.
Which is what you are missing too. Programming with modern C++ does not need to have manual memory management. At all. Just like Java. So the argument that C++ does not have a formal garbage collector is irrelevant.

You don't need to reimplement _anything_. At all.

---

### Post by lloyd mcclendon on 2007-01-23
> **jblebrun said:**
> You're completely missing his point. You don't NEED math libraries, either. You can re-implement exponentiation functions every time you need them. But why waste time? 

It doesn't matter how good you are with thinking about memory management... if it's not a core part of your programming task, then you're just needlessly introducing another source of errors.

damn you beat me to it, i agree 100%.  focus on the real problem, the fun stuff you have to solve.  worrying about having to make sure everything is straight on the heap is just a waste of a developers expensive time - cpu cycles are practically free these days

---

### Post by Wybiral on 2007-01-23
You guys are missing MY point...

I've been programming for a while, from 3d games, game engines, interpreters, compilers... I like to think quite a range of situations, where I haven't ran into a memory management problems. No, I'm not trying to be snooty and say that I know more than you, I'm actually trying to say that I haven't encountered many situations when it was that big of an issue.

I don't see what you mean with all this "why think about it?" stuff... You don't have to think about it for very long when you do... But half the time you don't even NEED GC, as I said... Go look up the C++ STL container objects, they are more than willing to lend you a hand.

I'm not at all saying that everyone should use C++... But, correct me if I'm wrong, the question this title raised was "What's wrong with Java??" even if the GC only pops up every now and then... Even if it's only ".1" second... It's still an extra process, and I find that wrong with Java.

Maybe not for everybody's task's, maybe that small CPU difference doesn't change your world... But I work on a lot of projects that require 100% maximum speed and minimum overhead, so for me, it IS something wrong with Java. You can only render so many polygons/check so many faces for collision before speed becomes ABSOLUTELY critical and the overhead of Java is simple not possible to work around.

I've seen small, simple 3d stuff in Java... A number of game even... But none of them are capable of reaching the maximum efficiency of ones written in C++ (or better yet, C)

I am not saying everyone needs to stop using Java... Someone asked what I had wrong with it, I was just letting them know.

Anyway... Guess what... I don't THINK about memory management, I allocate it, I write maybe 2-3 lines more to destroy it... I don't think it makes me snooty to say that it's easy, and I don't put much more thought into it than that. Yes, I've ran checks on my programs for memory leaks, NO, I have not found any. You can say what you'd like, but I will take my lack of overhead any day, even if it means I write an extra "delete [] vertex;" in a class destructor...

EDIT:

BTW, the av vector doesn't HAVE to disappear, you can always pass it to/from a function thats using it.

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> You guys are missing MY point...

I've been programming for a while, from 3d games, game engines, interpreters, compilers... I like to think quite a range of situations, where I haven't ran into a memory management problems. No, I'm not trying to be snooty and say that I know more than you, I'm actually trying to say that I haven't encountered many situations when it was that big of an issue.

I don't see what you mean with all this "why think about it?" stuff... You don't have to think about it for very long when you do... But half the time you don't even NEED GC, as I said... Go look up the C++ STL container objects, they are more than willing to lend you a hand.

I'm not at all saying that everyone should use C++... But, correct me if I'm wrong, the question this title raised was "What's wrong with Java??" even if the GC only pops up every now and then... Even if it's only ".1" second... It's still an extra process, and I find that wrong with Java.

Maybe not for everybody's task's, maybe that small CPU difference doesn't change your world... But I work on a lot of projects that require 100% maximum speed and minimum overhead, so for me, it IS something wrong with Java. You can only render so many polygons/check so many faces for collision before speed becomes ABSOLUTELY critical and the overhead of Java is simple not possible to work around.

I've seen small, simple 3d stuff in Java... A number of game even... But none of them are capable of reaching the maximum efficiency of ones written in C++ (or better yet, C)

I am not saying everyone needs to stop using Java... Someone asked what I had wrong with it, I was just letting them know.

Anyway... Guess what... I don't THINK about memory management, I allocate it, I write maybe 2-3 lines more to destroy it... I don't think it makes me snooty to say that it's easy, and I don't put much more thought into it than that. Yes, I've ran checks on my programs for memory leaks, NO, I have not found any. You can say what you'd like, but I will take my lack of overhead any day, even if it means I write an extra "delete [] vertex;" in a class destructor...

EDIT:

BTW, the av vector doesn't HAVE to disappear, you can always pass it to/from a function thats using it.

So, what you're saying is that Java sucks because it's not fast enough to write tightly optimized polygon-pushing code. Well, great. That's one use case. If that's ALL you do when you program, then don't use Java.  But you made a much broader-sweeping claim in your original post, making it sound as if GC was completely useless. If you don't understand why someone shouldn't have to think about memory management every time they program, I don't know how else to explain it to you. 

By the way, have you ever benchmarked Java OpenGL code vs. C++ openGL code? I don't doubt that C++ is faster than Java wit intensive polygon pushing code, i'm just wondering by how much. I can't find any comparisons on Google, but for some other mathematically intensive operations, there's about a 10-fold decrease in performance with Java. 

As for your "EDIT", please **re-read** my post. At no point did I say the vector disappeared. Furthermore, my example was a case in which I passed a vector to/from the function! What I said was that the OBJECT placed in the vector was destroyed when the function exited.

Your arguments go all over the place, and you ignore/misinterpret what people say. I see why Inost got frustrated and gave up. 

> **Wybiral]
And as far as me using ruby/python and them still requiring a runtime environment... Theirs isn't nearly as slow or bulky as javas...
[/QUOTE]
Um, what? Do you have evidence to back that up, or is this just again, "in your experience"? Because Java tends to execute code faster than Python and Ruby.  And yes, I can provide numbers that prove it.

By the way, here's an example of you contradicting yourself:
[QUOTE=Wybiral said:**
> 
Also, if I'm going to opt for an interpreted language, I'll at least use one that's more dynamic than java (like python/ruby)

> **Wybiral said:**
> I never said java was interpreted.


---

### Post by Wybiral on 2007-01-24
Ok, that's fare... I'm not trying to argue with anyone or be stubborn.

I'm not saying that Java "SUCKS" I'm just stating what I have wrong with it.

Yes, I think *most* of the time, it's not only possible, but just as simple to get by without GC, depending on the project. I guess I've lucked out.

Also, I didn't mean to say "interpreted" I mean "non-compiled"

By that I meant if I were going to use a language that didn't output raw machine code in an executable format, if you want me to be more specific.

If you reference the vector in a function parameter, it will alter the vector given as an argument, that's what I mean... You can maintain the same vector between functions, I do it a lot.

Once again, I'm not trying to crap on Java, I'm glad you guys are so adamant about defending it, I am just explaining what *I* find wrong with it.

About the runtime environment thing... Java programs do definitely slow my computer down more than python programs... I don't have any numbers, but I don't need them, its VERY noticeable. I believe it's mostly due to the JIT compiling... But once again, no proof.

Anyway, I still haven't seen any concrete examples of when Java GC is easier/safer than minimally managed memory in C++... Especially when you can use the STL containers. I'm _NOT_ saying there is none... I'm just saying, for you guys being so adamant about arguing your side, why hasn't anyone showed me a worthy example?

---

### Post by ghostdog74 on 2007-01-24
> **jblebrun said:**
> Because Java tends to execute code faster than Python and Ruby.  And yes, I can provide numbers that prove it.
just curious, can u provide the links/numbers that prove it. thanks

---

### Post by lnostdal on 2007-01-24
My first example is "worthy" by all means, but here is another "interesting" problem:

```
#include <iostream>

using namespace std;


int open()
{
  cout << "open()" << endl;
  return 1234; // Some handle representing a resource or whatever.
}


int close(int handle_from_open)
{
  cout << "close()" << endl;
  return -1; // Some useful information about how things worked out.
}


class A{
public:
  A()
  {
    resource = open();
  }

  ~A()
  {
    // Hey; and since we're such "good programmers" we somehow always remember to close here.
    close(resource); // What about the result? You know; the useful information about how things worked out?
  }

  int resource;
};



int main()
{
  {
  A a;
  }
  cout << "The result after closing the resource in our instance `a' is: " << "'?'" << endl;  
  return(0);
}

```

..enjoy. I'd rather not soil my brain with more C++ but maybe I'll come up with a couple of more exercises that involves threading, non-deterministic life-span of objects/resources/memory for when you need to have objects last outside the scope where they where created. No; I don't always want to pass them "down" to other functions by calling from within the scope they where allocated ..etc..etc..

---

### Post by lnostdal on 2007-01-24
another example; i've probably missed something .. this was typed faster than usual:

```

#include <iostream>
#include <pthread.h>
#include <unistd.h>

using namespace std;


int myMalloc()
{
  cout << "myMalloc()" << endl;
  return 1234; // Some handle representing a resource or whatever.
}


int myFree(int handle_from_open)
{
  cout << "myFree()" << endl;
  return -1; // Some useful information about how things worked out.
}

int resource; // We cheat to illustrate a point; this is not what is done in "real life".

class A{
public:
  A()
  {
    resource = myMalloc();
  }

  ~A()
  {
    // Hey; and since we're such "good programmers" we somehow always remember to close here.
    myFree(resource); // What about the result? You know; the useful information about how things worked out?
    resource = -1; // To signify that the resource is closed.    
  }
};


void* useA(A* a)
{
  for(int i = 0; i < 5; i++){
    sleep(1);
    if(resource != -1)
      cout << "Using resource in instance `a': " << resource << endl;
    else
      cout << "Using resource in instance `a': " << resource << " *boom* err .. no" << endl;
  }
  return NULL;
}


typedef void*(*start_routine_t)(void*); // Ouh; just sexy -- lol.



int main()
{
  pthread_t thread;
  {
    A a;
    pthread_create(&thread, NULL, (start_routine_t)useA, &a);
    sleep(3);
  }
  pthread_join(thread, NULL);
  
  return(0);
}

```

lars@ibmr52:~/programming/c$ g++ -Wall -g -lpthread c.cpp -o c && ./c
myMalloc()
Using resource in instance `a': 1234
Using resource in instance `a': 1234
myFree()
Using resource in instance `a': -1 *boom* err .. no
Using resource in instance `a': -1 *boom* err .. no
Using resource in instance `a': -1 *boom* err .. no


Oh, I don't "care" if you're able to fix this; all these seemingly small problems escalates to gigantic tasks very quickly when combined in several ways.

---

### Post by lnostdal on 2007-01-24
Somewhat unrelated, but here's how this works by itself in a non-braindead language with GC and closures:

```

(let ((a 1234))
  (withThread "my-thread"
    (dotimes (i 5)
      (sleep 1)
      (format t "Using resources in instance `a': ~A~%" a)))
  (sleep 3)
  (write-line "(even though the let that binds `a' to 1234 has returned now the thread still maintains the resource!)"))

Using resources in instance `a': 1234
Using resources in instance `a': 1234
(even though the let that binds `a' to 1234 has returned now; the thread still maintains the resource!)
Using resources in instance `a': 1234
Using resources in instance `a': 1234
Using resources in instance `a': 1234

```

Oh; and this is compiled to native machine code with full control of whether to generate debug-optimized code or performance-optimized code.

---

### Post by jblebrun on 2007-01-24
> **ghostdog74 said:**
> just curious, can u provide the links/numbers that prove it. thanks

Here are the numbers I was referring to:

[http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

---

### Post by jblebrun on 2007-01-24
> **runningwithscissors said:**
> Which is what you are missing too. Programming with modern C++ does not need to have manual memory management. At all. Just like Java. So the argument that C++ does not have a formal garbage collector is irrelevant.

You don't need to reimplement _anything_. At all.

I didn't say that anyone needed to reimplement GC. He wasn't talking about using a GC library, he was talking about managing memory himself.

---

### Post by Wybiral on 2007-01-24
OK... The threading example is a good one. I'm sure it *could* be fixed, but you are right, it would require too much effort. I rarely work with multi threaded programs, so I have never encountered these problems. I will admit that in that aspect you win... But I will also admit that I rarely have a need to multi thread.

But still... You have to admit, *most* of the time, not in isolated multi threaded examples such as that, GC is easily avoidable. Whether you agree or disagree, I can just say that people have been using C/C++ without it for years and if you are efficient without it... The loss of overhead is worth the extra work. I know because I often have to write very tedious code, sometimes hand optimized with assembly to reach the execution speeds I desire. As I said earlier, you can only achieve a certain polygon count in a program if you employ some dirty stuff.

For a lot of applications, maybe GC is nice, probably even comforting... But it is one thing about java that I, personally, could do without. And you can't deny the fact that an extra process babysitting your allocated memory is only going to slow things down...

Especially when you are rapidly allocating/deleting LARGE pools of memory, such as in the case with 3d games, where levels and models can create some massive sums of memory! (thousands of vertices's each containing three floating point values (when you factor in vertex normals thats an extra 3 floats per vertex)... Linked by a list of thousands of faces, each containing three (or four) integer values (factor in face normals, three more floats)... Filled in with dozens of textures with decent resolutions (amounting to width*height*3 bytes per texture)).

It shouldn't be hard to see why I say that in some cases, losing the overhead is an absolute MUST.

But, I'm not too stubborn to see what you mean now... I can see how trying to manage multi threading and dynamic memory with constructors/destructors would definitely become a challenge. So, thank you for enlightening me on that.

Unfortunately, most of the benchmarks for mathematical comparison between Java and C++ have C++ in the lead. I have to assume that it's the same when it comes to rendering.

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> 

By that I meant if I were going to use a language that didn't output raw machine code in an executable format, if you want me to be more specific.

If you reference the vector in a function parameter, it will alter the vector given as an argument, that's what I mean... You can maintain the same vector between functions, I do it a lot.



If you use v.push_back(A()) and a vector<A> (as you suggested), it pushes a stack variable onto the vector, right? The stack variable is destroyed when the function exits. How can you modify a vector in a function WITHOUT using dynamic memory? 

> 
About the runtime environment thing... Java programs do definitely slow my computer down more than python programs... I don't have any numbers, but I don't need them, its VERY noticeable. I believe it's mostly due to the JIT compiling... But once again, no proof.

Can you give me examples of two comparable programs implemented in both Java and Python that show this? 

Try something like the calendaring app Chandler, written in Python by OSAF. It's slow as hell!

> 
Anyway, I still haven't seen any concrete examples of when Java GC is easier/safer than minimally managed memory in C++... Especially when you can use the STL containers. I'm _NOT_ saying there is none... I'm just saying, for you guys being so adamant about arguing your side, why hasn't anyone showed me a worthy example?

Ok, show me an example of something where you can completely avoid the need for new/delete by using STL, but still achieve the benefits of dynamic memory management. I guess part of the problem is that I just can't imagine this example. A concrete example would help your argument a lot, and help the rest of us understand what you're saying.

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> OK... The threading example is a good one. I'm sure it *could* be fixed, but you are right, it would require too much effort. I rarely work with multi threaded programs, so I have never encountered these problems. I will admit that in that aspect you win... But I will also admit that I rarely have a need to multi thread.

But still... You have to admit, *most* of the time, not in isolated multi threaded examples such as that, GC is easily avoidable. Whether you agree or disagree, I can just say that people have been using C/C++ without it for years and if you are efficient without it... The loss of overhead is worth the extra work. I know because I often have to write very tedious code, sometimes hand optimized with assembly to reach the execution speeds I desire. As I said earlier, you can only achieve a certain polygon count in a program if you employ some dirty stuff.


Here you go again, confusing YOUR common experience with everyone else's common experience, while completely dismissing someone else's experience as a rare corner case!!! Stop that!

 You *are* aware that it's quite likely that multi-threaded programming is going to be the only way to take full advantage of commodity hardware, in a few years, right?

---

### Post by jblebrun on 2007-01-24
By the way, for the record, I'm not trying to 'adamantly defend Java'; I agree with you about some of its problems.  I'm just debating the claims you make, which seem to often be unfounded or strongly biased, or just plain rushed and undeveloped.

---

### Post by Wybiral on 2007-01-24
> Here you go again, confusing YOUR common experience with everyone else's common experience, while completely dismissing someone else's experience as a rare corner case!!! Stop that!

You're right.

I thought I clarified that it depends on the project... I guess not. I know that I said MOST of the time, it isn't needed... And I still insist that in a lot of cases, it really isn't. Anyway, you guys are both right, that's what I was saying in my last post... I also thought I summed up my point by saying that *sometimes* GC is a comforting and handy tool, and *sometimes* it's not necessary and you will benefit from the lack of baggage.

You can modify a vector passed to a function, if you pass it as a reference. I hope I'm not missing something here, you were insisting that you can't modify a vector from within a function, right?

```

#include <iostream>
#include <string>
#include <vector>

using namespace std;

class someClass {
   public:
   string someValue;
   someClass(string value){
      someValue = value;
   }
};

void screwWithVector(vector<someClass> &myVec){
   myVec.push_back(someClass("I'm screwing with your vector!"));
}

void screwWithVector2(vector<someClass> &myVec){
   myVec.push_back(someClass("I'm screwing with your vector too!"));
}

int main(){
   vector<someClass> myVec;
   myVec.push_back(someClass("I am the original vector!"));

   screwWithVector(myVec);
   screwWithVector2(myVec);
   cout << "Vector after returning..." << endl;
   for(int i=0; i<myVec.size(); i++){
      cout << myVec[i].someValue << endl;
   }

   myVec.back().someValue = "NOW " + myVec.back().someValue;
   cout << "Vector after modifying..." << endl;
   for(int i=0; i<myVec.size(); i++){
      cout << myVec[i].someValue << endl;
   }

}

```

This is an over complicated version because I wanted to show that it would maintain the classes too... A simple string would obviously have worked in this case.

---

### Post by MattKemp on 2007-01-24
> **Ben Sprinkle said:**
> One liner. ;)
```

public class NothingsWrong { public static void main(String[] args) { System.out.println("Nothing is wrong with Java in my eyes. :)"); } }

```

```

java -jar NothingsWrong.jar |sed -e "s\wrong\right\g"

```

Now that's a one-liner.

As a student that's being made to learn Java, I feel that it's a good starting point. It's a good way to help people learn OO principles and get the idea of programming. However, like others have said, the annoyance of having to do everything in OO form can be very, very annoying. There's nothing like having to import up to twenty java.swing objects for a GUI, because you need to put all their exceptions in too. Yes, you can just import java.swing.*, but where's the efficiency?

Personally, I like to write efficient code. I've found lots of things that I've wanted to do in Java that's taken the long way around because of a lack of one thing or the other. There are bonuses to it as well, though - I wouldn't say that Java's a really poor language, but I can't see me using it much once I'm not made to.

[This]("http://www.jwz.org/doc/java.html") page sums up a lot of the things that bug me.

---

### Post by phossal on 2007-01-24
> **MattKemp said:**
> [This]("http://www.jwz.org/doc/java.html") page sums up a lot of the things that bug me.

Don't you wonder how people have so much time? Who would waste any energy creating such a thing? Even if it all made sense, it has little practical value. How lame. It seems like a person could think of at least *one* better way to spend their time than creating that. lol For example, *replying* to a post about it, which is (only marginally) better.

---

### Post by Ragazzo on 2007-01-24
> **MattKemp said:**
> 
There's nothing like having to import up to twenty java.swing objects for a GUI, because you need to put all their exceptions in too. Yes, you can just import java.swing.*, but where's the efficiency?


How does import-statement affect efficiency?

---

### Post by pmasiar on 2007-01-24
> **jblebrun said:**
> Here are the numbers I was referring to:

[http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

Thanks for the link, these debian guys are genius! I would never guess that Python can beat Java in some benchmarks, but it does! Awesome. Of course sometimes it suck, badly. Good to know where, too. :-)

---

### Post by MattKemp on 2007-01-24
> **phossal said:**
> Don't you wonder how people have so much time? Who would waste any energy creating such a thing? Even if it all made sense, it has little practical value. How lame. It seems like a person could think of at least *one* better way to spend their time than creating that. lol For example, *replying* to a post about it, which is (only marginally) better.

I didn't actually create that, it just has a lot of things on it that could do with improvement.

If you actually read what I said, you'd notice I don't think that Java is an overly bad language. It's a very good way to teach people OO programming, and it's generally not as slow as people make out. I just can't see myself using it once I'm not forced to by my course.

> **Ragazzo said:**
> How does import-statement affect efficiency?

More that if you import every single swing library when you're only using say, twenty components, you're importing things you don't need - which will obviously increase its resource needs.

---

### Post by pmasiar on 2007-01-24
> **MattKemp said:**
> [This]("http://www.jwz.org/doc/java.html") page sums up a lot of the things that bug me.

Thanks for the link. I found couple more ways how java sucks I was not aware yet. :-(

> **phossal said:**
> Don't you wonder how people have so much time? Who would waste any energy creating such a thing? Even if it all made sense, it has little practical value. How lame. It seems like a person could think of at least *one* better way to spend their time than creating that. lol For example, *replying* to a post about it, which is (only marginally) better.

If "lame person" is Jamie Zawinski: IMNSHO Zawinski *earned* the right to have his opinion at least listened to, in old-fashioned way: [http://en.wikipedia.org/wiki/Jamie_Zawinski](http://en.wikipedia.org/wiki/Jamie_Zawinski)

If "lame person" is MattKemp: IMNSHO Matt added his own 2 cents about what he thinks is wrong in java, which is exactly on topic in this thread. Even if you prefer Matt spending his time differently.

And of course you have full right to continue thinking that Jamie, Matt, both, me, or anyone else is lame. 

What would *you* reply in response to the post Matt did not replied? Ben's post was not very thoughtfull IMHO - Matt's response was as smart as you can get for such a dumb post IMHO. :-)

Of course I might misundertood you again - in this case I apologize preemptively.

---

### Post by phossal on 2007-01-24
> **pmasiar said:**
> blah blah blah, phossal, blah blah blah, I want to debate and win *just once*

You bore me. I'm tired of you. I don't feel I have any unique skills to offer to help anyone beyond the two stupid tutorials I've written. I don't want to degenerate into an ineffectual, humble opinion giver. And I'm busy. New projects. Zaijian to the forums for now!

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> You're right.
You can modify a vector passed to a function, if you pass it as a reference. I hope I'm not missing something here, you were insisting that you can't modify a vector from within a function, right?
This is an over complicated version because I wanted to show that it would maintain the classes too... A simple string would obviously have worked in this case.


Not exactly, I was saying that if you put a local stack variable into a vector, it will disappear. But anyway, I was wrong. Clearly I shouldn't make arguments when I've been up for 16 hours after 4 hours of sleep, since obviously when you pass a stack variable by value, a copy is made. D'oh. 

When I was writing a program to test, I was passing my vector by value instead of by reference. Oops ;-)

Anyway, your example solidified your argument for me a bit. I can see how as long as you can do your work using statically declared STL containers, you can avoid having to do memory management.

---

### Post by Ragazzo on 2007-01-24
> **MattKemp said:**
> 
More that if you import every single swing library when you're only using say, twenty components, you're importing things you don't need - which will obviously increase its resource needs.

Nope. Import statements aren't saved in the class file which you can easily verify by importing extra packages and comparing the class file size to one that has no imports.

---

### Post by MattKemp on 2007-01-24
> **Ragazzo said:**
> Nope. Import statements aren't saved in the class file which you can easily verify by importing extra packages and comparing the class file size to one that has no imports.

Oh, nice. Learn something new every day!

---


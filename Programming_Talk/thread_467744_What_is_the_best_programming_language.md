---
title: "What is the best programming language"
date: 2007-06-08
forum: Programming Talk
---

### Post by md5hash on 2007-06-08
im currently on php and planning to study another PL, which is better?

---

### Post by madmetal on 2007-06-08
> **md5hash said:**
> im currently on php and planning to study another PL, which is better?

better is what fills your needs and interests.. ;)

---

### Post by loell on 2007-06-08
lol, can anybody smell a language battle again ;)

usually this doesn't end up well.

---

### Post by amo-ej1 on 2007-06-08
It seems you have forgotten a couple hundred alternative choices ;)

Edit: it might help if you  gave a reason for the type of programs you'd want to write ... database apps, games, webpages, devices drivers, ...

---

### Post by daxumaming on 2007-06-08
This question is a flame bait.... you'll get a lot of opinions, but there won't be one (or even two or three) answer for your question. I guess this is a personal preference since we're the one coding, not the language. To each his own.

---

### Post by cunawarit on 2007-06-08
None of the above ASP.NET with C#. :D

Ruby on rails seems quite interesting, and powerful. Will give it a go when I have the time.

---

### Post by pmasiar on 2007-06-08
I need to buy a motor vehicle, which one is better? Toyota Prius, Honda Odyssey, Lamborghini, RV, or 18 wheeler truck?

LOL

---

### Post by shijirou on 2007-06-08
> **md5hash said:**
> im currently on php and planning to study another PL, which is better?

Programming language? Isn't PHP scripting? Correct me if I'm wrong.

---

### Post by WW on 2007-06-08
> **shijirou said:**
> Programming language? Isn't PHP scripting? Correct me if I'm wrong.
It has variables, loops, conditional statements, etc.  Of course it is a programming language.

---

### Post by pmasiar on 2007-06-08
> **shijirou said:**
> Programming language? Isn't PHP scripting? Correct me if I'm wrong.

[Scripting](http://en.wikipedia.org/wiki/Scripting) is kind of programming where your programs calls other  system utilities. It is very artificial and misleading label invented by C++ programmers to make them fell superior over other ("scripting") languages which can handle task hard or awkward in C++ :-)

---

### Post by veerakumar on 2007-06-08
Everything present in the world!
Each programming language is developed for specific purpose.
It's so obvious.
One Language for all has too many limitations
just like our eyes seeing everything around - so many limitations!

---

### Post by jespdj on 2007-06-08
This poll is nonsense.

It is like asking "Which is the best tool? A hammer, screwdriver or a wrench?" :roll:

Every programming language has its own strengths and weaknesses. Which is best depends on the job you need to do.

---

### Post by steve.horsley on 2007-06-08
INTERCAL

No contest.

---

### Post by tturrisi on 2007-06-09
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<title>Code Wars</title>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
</head>
<body>
<h1>Code Wars</h1>
<?php
if ($_POST['submit'] == TRUE) {
$my_lang = $_POST['lang'];
if(empty($my_lang)) {
echo "<h2>You Win!</h2>";
}
else {
echo "<h2>I Know You Are But What Am I?</h2>";
}
}
else {
?>
<form method="post" name="moot" action="">
php: <input type="radio" name="lang"  value="1"><br>
perl: <input type="radio" name="lang"  value=2"><br>
python: <input type="radio" name="lang"  value="3"><br>
ruby: <input type="radio" name="lang" value="4"><br>
<input type="submit" name="submit" value="so you think your vote counts!">
</form>
</body>
</html>
<?php
} ?>
```

---

### Post by Sockerdrickan on 2007-06-09
Add C/++!

---

### Post by Dylnuge on 2007-06-09
And what if I said Java? C? C++?

I do have a prefrence from that list. My personal prefrence may or may not be in that list. I'm not going to say, because that would be a flamebait. Instead, I will give you some advice: you will hear a lot about which programming languages are good, bad, etc. The only way you can decided is to see for yourself. Try some quick tutorials and use a universal editor like xEmacs or jEdit. However, of the four, I can tell you some basic strengths and weaknesses:

PHP: As a portion of the W3C Standards and a part of the Internet, this language shows some great strength in Website Programming. Although frameworks exist for Python and Ruby (and probably Perl) to do the same, PHP has a strong following, and does not require a framework (though if making a large project by god please use one).

Perl: I have seen it run very fast. In more complex applications, some more advanced work is required to optimize the code, but still, probably the fastest of these four. It has some complex code in it, which may require a bit more time to create.

Python: It is included with Ubuntu and is popular among Ubuntu programmers. Regardless of what others say, don't listen to it being the "Ubuntu choice" or preference, since I know tons of Perl, Ruby, Java, C, and C++ programmers on here. It has a nice speed, fast to program in. Its library support is extensive.

Ruby: Don't really know much about Ruby.  From what I have heard and read, Ruby is much closer to Perl then Python in a lot of ways.

Conclusion: For ease and speed of programming, go Python. For speed of execution, go Perl. Don't know enough about Ruby to recommend. Java is faster then all of these, but extremly verbose-so much that unless many people will use your product or you need it to be megafast, you will lose more time programming then the customers/clients/end users gain. If you are not your own end user, take speed of execuion into account. There are a lot of great resources out there, regardless of what you choose. Good luck.

---

### Post by nix4me on 2007-06-09
Most of those are not programming languages at all.  They are scripting languages.

Use C.

nix4me

---

### Post by Modred on 2007-06-09
Simple solution: *learn as many as you can.  It will do you good.*

Most of my "for-fun" programming is done in Python, but I'm also doing some work this summer using Ruby (on Rails, no less) and I'm fairly well versed in C++ and Java.  If you're just throwing little things together for fun, then you'll be able to get a good deal more done in less time with languages such as Perl, Python, or Ruby (or any of their brethren).

A compiled language will always give you some speed boost over interpreted languages (which it seems quite a few here are erroneously calling "scripting" languages...fully object oriented languages such as Python and Ruby hardly seem limited to "scripting").  For example, I had a project to implement several different types of sort algorithms in the language of my choosing.  I chose Ruby; for large input (16468 elements to sort), some of the Ruby programs took around 10-20 minutes to complete (NOTE: This was on the particularly poor algorithms, such as bubble sort.  For better algorithms, Ruby completed in a more reasonable time).  A comparable C/C++/Java program could get the same job done within a minute or so, if that long.  But chances are you won't be doing anything like that, so don't let the potential performance hit derail you from learning an interpreted language.  Ruby, Python, Perl, etc., make some tasks that would take hours or days to implement in C/C++/Java a simple matter of knowing what functions to call (especially Ruby...I just keep finding nice little surprises).

So give them all a try.

Heh, over two years as a member here and I just now posted.  Woo.

---

### Post by pmasiar on 2007-06-09
> **nix4me said:**
> Most of those are not programming languages at all.  They are scripting languages.

What are qualitative differences in scripting languages that is not possible to program in them? What they lack? I used Perl and Python to write websites for last 7 years, so it looks I did not programmed at all? What I was doing then?

---

### Post by montgoej on 2007-06-10
I'm gonna have to go with C, right now. I've used Python, PHP, Visual Basic, TI-Basic, Z80 Assembly, LOLCODE and C++ in the past, but right now I'm on C. In a year that could be completely different, but for now, C.
~Jordan "The Stash" Montgomery

---

### Post by diafanos on 2007-06-10
> **jespdj said:**
> 
It is like asking "Which is the best tool? A hammer, screwdriver or a wrench?" :roll:


I think screwdriver is the best. 
Lack of hammer?  Use a stone....
Lack of wrench? Use your strong fingers...
Lack of screwdriver? ....
After all, we live in a world full of screws...







BTW, Java???? Where is my lovely Java?????:lol:

---

### Post by Dylnuge on 2007-06-10
> **nix4me said:**
> Most of those are not programming languages at all.  They are scripting languages.

A so called scripting language is a programming lanugage. JavaScript is not a programming language, python is.

Scripting language is just a term invented to make C/++ programmers look so much better then the rest of us. I have used C/++, and just because I need 30 lines of code to do in C++ what I could do in python in 1 does not make it a better language. That's like saying that a long boring lecture is better then a quick fun activity in regards to learning. In reality it depends on how you learn (program). People who learn kinesthetically will prefer the activity, people who learn auditory and want a comprehensive knowledge prefer the lecture. C/++ is the lecture. Its complex and verbose, but by the end you know what you are doing and can do it well.

I learned from the ground up (C++ first, then Java, now Python), but that does not mean that I should use C++ because I know it. I prefer Python, because everything I do only requires the short and simple version.

---

### Post by pmasiar on 2007-06-10
I agree with you with almost everything, can you explain this bit?

> **Dylnuge said:**
> JavaScript is not a programming language, python is.

Why JS is *not* a programming language? what kind of language is it then?

I understand when people laugh at "programming in HTML" -- HTML is just a markup notation, not a programming language. But IIUC, JS is very specific programming language (rather brain-dead one, but that's beyond the point now), what would be the reasoning to question it?

---

### Post by slavik on 2007-06-10
perl because I know it will be there on an old unix system which was installed before anyone thought of python. :)

and for scripting languages for admin stuff, OO is unneeded.

---

### Post by kevinlyfellow on 2007-06-10
> **diafanos said:**
> I think screwdriver is the best. 
Lack of hammer?  Use a stone....
Lack of wrench? Use your strong fingers...
Lack of screwdriver? ....
After all, we live in a world full of screws...


For a screwdriver, use a knife, flaked stone, fingernails...

Wrench is clearly the winner.  The wrench can also be used as a hammer (I know I've used 'em that way before)...  Its like killing two birds with one sto... errrr... wrench

---

### Post by information_entropy on 2007-06-10
My all time favorite programming language is FIFTH.  It is a derivative of FORTH with the additional requirement that when a programmer starts working on a program he begins with an empty shot glass an a full bottle of his favorite whiskey (at least 10 years old).  Every time you get a stack overflow you fill the glass from the bottle and drink it.  

Obviously, this language is not approved for use on medical equipment or in anything even remotely related to a nuclear power plant.   The prohibition is purely academic however, because only a handful of programmers have actually finished even the obligatory “Hello World” first program. 

The history of the FORTH programming language can be found here:

[http://en.wikipedia.org/wiki/Forth_(programming_language)]("http://en.wikipedia.org/wiki/Forth_(programming_language)")

---

### Post by bl3s5in on 2007-06-10
"No programming language is perfect. There is not even a single best language; there are only languages well suited or perhaps poorly suited for particular purposes."
                                                                                                             Herbert Mayer

---

### Post by loell on 2007-06-11
can i get an amen? 

 **_ LoLcode _**is the bestest programming language, ever... :lolflag:

---

### Post by kevinlyfellow on 2007-06-11
> **loell said:**
> can i get an amen? 

 **_ LoLcode _**is the bestest programming language, ever... :lolflag:

I prefer [whitespace]("http://compsoc.dur.ac.uk/whitespace/")

---

### Post by md5hash on 2007-06-12
> **Dylnuge said:**
> And what if I said Java? C? C++?

I do have a prefrence from that list. My personal prefrence may or may not be in that list. I'm not going to say, because that would be a flamebait. Instead, I will give you some advice: you will hear a lot about which programming languages are good, bad, etc. The only way you can decided is to see for yourself. Try some quick tutorials and use a universal editor like xEmacs or jEdit. However, of the four, I can tell you some basic strengths and weaknesses:

PHP: As a portion of the W3C Standards and a part of the Internet, this language shows some great strength in Website Programming. Although frameworks exist for Python and Ruby (and probably Perl) to do the same, PHP has a strong following, and does not require a framework (though if making a large project by god please use one).

Perl: I have seen it run very fast. In more complex applications, some more advanced work is required to optimize the code, but still, probably the fastest of these four. It has some complex code in it, which may require a bit more time to create.

Python: It is included with Ubuntu and is popular among Ubuntu programmers. Regardless of what others say, don't listen to it being the "Ubuntu choice" or preference, since I know tons of Perl, Ruby, Java, C, and C++ programmers on here. It has a nice speed, fast to program in. Its library support is extensive.

Ruby: Don't really know much about Ruby.  From what I have heard and read, Ruby is much closer to Perl then Python in a lot of ways.

Conclusion: For ease and speed of programming, go Python. For speed of execution, go Perl. Don't know enough about Ruby to recommend. Java is faster then all of these, but extremly verbose-so much that unless many people will use your product or you need it to be megafast, you will lose more time programming then the customers/clients/end users gain. If you are not your own end user, take speed of execuion into account. There are a lot of great resources out there, regardless of what you choose. Good luck.

Thanks alot.. :D  im already starting with ruby... but i'll try python

---

### Post by Tundro Walker on 2007-06-12
> OMG!  You didn't include ____________?!  And you call yourself a programmer!?  Pfffttt!

Fill in the blank...
[LIST]
[*]Apple ][e programming language
[*]Texas Instruments TI-30X pocket calculator programming
[*]BASIC
[*]VBScript
[*]QuakeC
[*]World of Warcraft Macros[/LIST]:D

---

### Post by Dylnuge on 2007-06-17
[QUOTE=pmasiar;2819039]
Why JS is *not* a programming language? what kind of language is it then?
/QUOTE]

JavaScript is a programming language. Sorry for that, I meant HTML.

Also, the definition of script is a set of instructions. How is C/++ not a scripting language? I can create a set of instructions with it. So stop calling python a scripting language-Every language is a a scripting language. After all, large programs are just collections of scripts. Actors in large movies don't say "Oh, well since this is a huge Hollywood production, we can't use a script." 

Don't ever choose a language because of how many people use it. While it may be more useful for a job, it would be like speaking Chinese just because it is the worlds most spoken language.

---

### Post by pmasiar on 2007-06-17
> **Dylnuge said:**
> Also, the definition of script is a set of instructions. How is C/++ not a scripting language? 

No, C definitely is *not* a scripting language in common understanding what [scripting language](http://en.wikipedia.org/wiki/Scripting) is.

"One way of looking at scripts is as "glue" that puts several components together;". Doing that from bash or perl or python is just much more common than using C for that.

> I can create a set of instructions with it. 

Set of instructions is called "program". As wikipedia clarifies, scripting is specific kind of programming. BTW Python is compiled to bytecode, so it does not fit above definition 100%.

> So stop calling python a scripting language

When you will be longer around this forum, you will notice that it is *me* who argues against people who dismiss Python as mere "scripting" language. :-)

> Every language is a a scripting language. After all, large programs are just collections of scripts.

Not exactly. Is Linux kernal just a collections of scripts? You may need to modify definition of a script slightly to fit to your theory :-)

---

### Post by 5-HT on 2007-06-17
Depends on the task IMHO. Though I'm really diggin' Python right now, just started to get into it (yay dynamically typed)!

---

### Post by gnirts on 2007-06-18
If you're going to be doing web development I would stick with PHP. Anything but web, go with Python.

---

### Post by pmasiar on 2007-06-18
PHP was main player on web couple years before, but not any more. TurboGears and Django are seriosly cool technologies.

Install turbogears and follow "20 minute wiki" to see how little code (and how clean and obvious it is) can get you up and running.

Database with CRUD methods is generated from your model, dev table updates is inspected out of model (not even generated), and everything is neatly separated to model 9data), viet (templates) and controller (business logic). Compare that with PHP - and cry.

---

### Post by RedSquirrel on 2007-06-18
> **pmasiar said:**
> But IIUC, JS is very specific programming language (rather brain-dead one, but that's beyond the point now), 

JavaScript is actually a general-purpose language. It is used so much for web programming that most people think of it in those terms exclusively.

Just out of curiosity, why do you think it is "brain-dead"? (And no, I'm not a JavaScript *fanboy*. :))

---

### Post by LaRoza on 2007-06-18
> **RedSquirrel said:**
> JavaScript is actually a general-purpose language. It is used so much for web programming that most people think of it in those terms exclusively.

Just out of curiosity, why do you think it is "brain-dead"? (And no, I'm not a JavaScript *fanboy*. :))

JavaScript is very limited, although it is a programming language. It is very much tied to a browser.

I realize it can be used elsewhere, but other languages would be more useful in those cases.

---

### Post by Dylnuge on 2007-06-19
My definition of a script is a set of instructions. pmsair, my comments were directed to the people who were calling Python/Perl/Ruby/PHP "scripting languages". Only the Javascript comment which follows the quote was related to your post, sorry if that was confusing.

A script is really just defined as a set of instructions, although it has come to mean in the programming vernacular a small set of instructions, with either:
1. A limited range of functionality, ie, a very small program, minimal code.
2. A program with limited use of logic.
3. A program with no interactivity with the user.

Using any of these terms, Python is by all means not a scripting language. Using the set of instructions definition, binary is a scripting language. I usually use the limited range definition: ie, I would call the languages used in most game editors a scripting language (they usually call themselves that).

Also, I don't think that it is a proper definition to say that anything which does not compile straight to binary or assembly is not a scripting language. Few people would say that C++ code that uses the Microsoft .NET framework or open Mono framework is considered a scripting language.

The real question is of course not whether the language you are going to learn will be powerful, but if it would be powerful enough. I learned programming backwards (I still don't get C++ very well, since I read the books when I was 8), with C++, then Java, and then Python and some Perl. Once I tried to learn a variant of Basic, but I hated it. I don't use C++ or Java for most tasks because they are verbose, complex, and the speed is not worth the small task. Instead, I use a small language, because it is powerful enough. If I wanted the most powerful language, I would go and learn x86 and 64x assembly.

---

### Post by ichiban on 2007-06-19
As many already said there is no perfect language. But here is my personal preference:
Learn Python and C/C++.  With that combination you can do almost anything. 

What I do when I make a project is this:

[LIST=1]
[*]Make the program in Python.
[*]Make a statistical review of your code.
[*]Where speed matters recode those modules in C++.
[/LIST]

With that combination you get the fast development with Python and the speed of C++. ;)
That is the solution that works for me.

---

### Post by Smygis on 2007-06-19
I must say that as a hobby-programmer, I have more fun with Python then with languages like C/C++. Its more fun to see something happen quickly then fight with the code.
I can prototype a app in about a day. Where in C++ it take me a week.

And the past couple of days i have been trying to learn Haskell. And its... Diffrent.

---

### Post by glowplug61 on 2007-06-21
There is no *Other which I'd select

From my perspective each have equal merits in regard to each other.
Each cover facets that we need from time to time.

Overall they are generally overused in mainstream.

We preached 'Get closer to the hardware' last century and now it is 'Get closer to the O/S you fool' - hehe

---

### Post by pmasiar on 2007-06-21
> **glowplug61 said:**
> We preached 'Get closer to the hardware' last century and now it is 'Get closer to the O/S you fool' - hehe

I think it should be "get closer to the user" - get closer to the way user thinks about the problem, use language which allows you to map user's mental model of the problem area to your code with least amount of mind-bending gymnastic contortions.

The only thing which improved only marginally (and not by couple of orders of magnitude like CPU speed, RAM and disk space) in past 50 years of computing is programmer's productivity: number of debugged, production-ready lines written per hour. :-)

---


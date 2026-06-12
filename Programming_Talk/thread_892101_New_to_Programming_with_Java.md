---
title: "New to Programming with Java"
date: 2008-08-16
forum: Programming Talk
---

### Post by coderJ on 2008-08-16
Well I'm new to all of this actually (Linux). But I will be taking up Computer Science at my college and they teach Programming with Java under the Linux OS (idk which one).

I was wondering if anyone could point me in the right direction just to get my feet wet in the Prog. w/ Java world...this can be:

>>Which software should I use (compatible with Ubuntu 8.04).
>>Any tips/advice would be nice too.

If there is a thread relating to this then please post link and lock (If it's the same and I apologize if there is)

Thanks

~Coderj

---

### Post by badperson on 2008-08-16
I don't know if you mean an IDE; but I use Eclipse, although if I had to do it all over again, I might start with netbeans. Both are free downloads...

I'm happy with eclipse, though. 

not sure if that's what you meant.
bp

---

### Post by coderJ on 2008-08-16
Yea, I've heard of those programs but I don't know which is better, etc... 

I'm new to the whole programming world, so I don't know much of anything about it. So which is better to use Eclipse or netbeans?

---

### Post by pmasiar on 2008-08-16
Quite a few people will be mad about me, because they have feeling what I am going to propose... but you asked for my best professional opinion based on my experience, right? So you'll get exactly what you asked, torpedoes be damned. :-)

Java is quite complicated language, starting from the very beginning with OOP (Object-oriented programming). Also, as statically typed, and with static exception checking, it is quite a pain to write simple training programs. It pays off when you can compile more efficient code afterwards, but it's PITA to get started.

I read about some comparison where two groups of student beginners were taught, one pure Java from the start for 10 months, another 3 months of Python then 7 of Java. Author claimed that because Python is so much simpler, he was able to cover quickly basics of Python, then when showing students comparable Java concepts (which are of course more wordy) they were able to see common principles, to see 'computer engineering' beyond the plain syntax.

Of course you may dismiss this as BS (and you will have plenty of company of people encouraging you just that), it's up to you. You have about month before Java classes seriously start, you can cover plenty of Python by then, if you care (see wiki in my sig for links). 

Remember advice is as valuable as much **you** will make of it. I use Java daily but when I shown it to my son, he said: "I pity the fools who use this language".

Check for yourself: Simple code to kick tires in Python, I hope some real Java enthusiast will provide Java equivalent, feature by feature (hint: it will be much longer to write and test, I cannot force myself to do Java over weekend :-) )

[php]
# program to test basic language features:
# 1) importing standard library module
# 2) defining function with default argument
# 3) string substitution
# 4) conditional code to manipulate runtime parameters
# 5) simple print output

import sys

def hello(name="World"):
    """return hello response for given name"""
    return 'Hello %s!' % name

# sys.argv[0] is this program name, [1] is argument provided by shell
if len(sys.argv) < 2:
    # no name provided: add 'unknown'
    sys.argv.append('unknown')
    
print hello()
print hello(sys.argv[1])
[/php]

To test it, save it as hello.py, and run in terminal window

```

python hello.py 
python hello.py <yourname>

```

Compare this Python snippet with Java, and tell me what you think! :-)

---

### Post by dwhitney67 on 2008-08-16
> **pmasiar said:**
> ...
Compare this Python snippet with Java, and tell me what you think! :-)
Great challenge, unfortunately you picked a Python example that cannot be implemented in Java because of Java's limitation of not allowing function (method) parameters to be defaulted to an initial value.

This issue does not prove that Python is better than Java.  All it proves is that it has different, and in this particular case, more capabilities.

In C++, the code above could be translated to be:
[PHP]#include <string>
#include <iostream>

std::string hello( std::string name = "World" )
{
  return "Hello " + name;
}

int main( int argc, char **argv )
{
  std::cout << hello()        << std::endl;
  std::cout << hello(argc > 1 ? argv[1] : "unknown") << std::endl;

  return 0;
}[/PHP]
Woo hoo!  This example doesn't look any more complicated than the Python example.

But oops, this thread is about Java... not Python or C++.

---

### Post by slavik on 2008-08-16
obligatory Perl :)
```

#!/usr/bin/perl -w

use string;
use warnings;

sub hello {
  my $str = shift or "unknown";
  return "Hello ".$str;
}

print hello();
print hello($ARGV[0]); #in Perl, the name of the script does not go into ARGV

```

EDIT: appending to ARGV is not a very good idea, because you might be sending argv to a library for parsing its own specific options and whatever you might append, might cause the library to act differently.

---

### Post by pmasiar on 2008-08-16
> **dwhitney67 said:**
> Great challenge, unfortunately you picked a Python example that cannot be implemented in Java because of Java's limitation of not allowing function (method) parameters to be defaulted to an initial value.

Well then copy arguments somewhere and use that copy  for the same goal. That's common in programs: to have different sets of parameters for different usecases, and handle them accordingly, IMHO.

> This issue does not prove that Python is better than Java.  All it proves is that it has different, and in this particular case, more capabilities.

It shows OP that even such seemingly trivial task is rather complicated (or as you said impossible - which I doubt, Java is after all Turing-complete :-) ) in Java, because of the static character of the Java language. I picked that feature (with some luck) with intention to show the difference between programming in static and dynamic languages.

> 
  return "Hello " + name;


This is cheating. 
1) I used default argument "world" if not provided to hello(), different from 'unknown' if not as input parameter. That's by design, to force you to show us  if () :-)
2) I used string substitution, not concatenation: much more flexible for real-life output.


> Woo hoo!  This example doesn't look any more complicated than the Python example.

I'll let OP to decide that :-)

> But oops, this thread is about Java... not Python or C++.

No, this thread is (IMHO of course) about how to learn programming, and my point is that Python is easier for beginners - even if these beginners will start with Java soon enough.

And let's hope that other people quoting me will trim - I hate all those electrons being wasted :-)

---

### Post by kool_kat_os on 2008-08-16
i use netbeans... in leopard(hey...it has unix :-))

---

### Post by badperson on 2008-08-16
I should also point out, that I think you're very first programming experience should be with a text editor and a command prompt; I spent a lot of time doing that and it paid big dividends. 

It's free, it's basic, and you don't confuse the functionality of an ide with the language itself.

I knew a little perl before I started java, and I think that did help some, although I wouldn't agonize over which language to begin with; I think if you're motivated, you can learn any language. (the argument about python is a good one, though: 

perl: ```

open (FILE, ">file.txt");
print FILE "Writing a line to a text file.\n";

```


java:```


BufferedWriter br= new BufferedWriter(new FileWriter(new File("file.txt")));
   try{
  
   br.write("Writing a line to a text file.");
   br.close();
   } catch (IOException e){
   e.printStackTrace();
   } 



```

(I actually didn't compile that, but I think it's right)
The point is, it's true that this kind of stuff takes awhile to get your head around (at least it did for me)

bp

---

### Post by NovaAesa on 2008-08-16
Okay, so when it comes to Java, this is my suggestion. Rather than relying on a IDE, use a plain text editor (such as gedit) and a terminal window for compilation. This way you will get to know the language much better. You will end up memorising some of the more commonly used libraries and also know the exact file structure/hierarchy.

As for if you should learn Python first or not... here is my suggestion. It is somewhat based on the experience of me and some of my friends, as we were in your exact position at the start of this year (entering CS, EE, CE, and SE, doing a first semester software Java course). For the 3 months prior to the start of uni I had been learning Python. I already know Visual Basic from high school. Some of my friends also had done lots of Visual Basic in high school. They know how to do most of the things that VB offered. Some of my *other* friends hadn't had any programming experience. Keep in my that we all had about the same level of interest in our fields, none of us were slackers or anything like that.

Anyway, I ended up getting high distinction. I found the work very easy. My two friends that know the ins and outs of Visual Basic also got high distinctions. Out of my other friends, 2 changed degree programmes. I have a feeling that Java was one thing that put them off. Another friend barely scraped a pass, another failed, and another dropped out of that subject just before the withdraw-without-academic-penalty date. These were the ones that had no previous programming experience.

So I really do think that you need to make something *apart* from Java your first language. Java is easy if you already know how to programme, but learning Java *and* programming at the same time is a very difficult task. Give Python a whirl. Maybe give Visual Basic a whirle. These two are both excellent first languages IMO.

---

### Post by tinny on 2008-08-17
> 
Computer Science at my college and they teach Programming with Java


The OP is going to learn Java and they want us to help them with this

@OP

If you work hard and focus on your studies (getting good at Java along the way) you really cant go wrong. There are lots of jobs in Java. Get your foundations in place first and then you can branch out and do whatever you want later. Its never to late to learn another skill, ive been coding for nearly 10 years in Java and are now learning Python.

I would strongly suggest you have a look at [BlueJ]("http://www.bluej.org/").

> 
The aim of BlueJ is to provide an easy-to-use teaching environment for the Java language that facilitates the teaching of Java to first year students. Special emphasis has been placed on visualisation and interaction techniques to create a highly interactive environment that encourages experimentation and exploration.


---

### Post by LaRoza on 2008-08-17
> **coderJ said:**
> Well I'm new to all of this actually (Linux). But I will be taking up Computer Science at my college and they teach Programming with Java under the Linux OS (idk which one).

I was wondering if anyone could point me in the right direction just to get my feet wet in the Prog. w/ Java world...this can be:

>>Which software should I use (compatible with Ubuntu 8.04).
>>Any tips/advice would be nice too.


Java is pretty well documented on the web. My wiki should be a good start (the official Java site is very complete, last time I looked)

Java is Java no matter where you are, so it doesn't matter if you use Linux. See the sticky on how to install and test compile with Java.

For IDE's, you can use whatever you want, see the sticky for various options. I suggest in the beginning to use a plain editor (Gedit).

---

### Post by tinny on 2008-08-17
> 
I suggest in the beginning to use a plain editor (Gedit).


Yeah, I must say that when I was learning I found that using a text editor did help train my eye (you have to pay a bit more attention to your code when using a text editor, not sure if what I just wrote makes sense...?).

---

### Post by LaRoza on 2008-08-17
> **tinny said:**
> Yeah, I must say that when I was learning I found that using a text editor did help train my eye (you have to pay a bit more attention to your code when using a text editor, not sure if what I just wrote makes sense...?).

Not only that (it made sense), but we get a lot of people that use VS or whatever who can't code without that IDE. An IDE should help the programmer, not make the programmer.

---

### Post by tinny on 2008-08-17
> **LaRoza said:**
> Not only that (it made sense), but we get a lot of people that use VS or whatever who can't code without that IDE. An IDE should help the programmer, not make the programmer.

Yeah bang on.

The old VS programmer ](*,)

---

### Post by coderJ on 2008-08-17
Woah a bunch of stuff all at once. But I get the gist. I'll try familiarizing myself with python in the few weeks I have before school starts. 

What is the name of the python that comes with Ubuntu? (Is it Python?)....if so how come its not running when I type it in...(Not only am I new to prgramming but Linux as well...LOL)

---

### Post by LaRoza on 2008-08-17
> **coderJ said:**
> Woah a bunch of stuff all at once. But I get the gist. I'll try familiarizing myself with python in the few weeks I have before school starts. 

What is the name of the python that comes with Ubuntu? (Is it Python?)....if so how come its not running when I type it in...(Not only am I new to prgramming but Linux as well...LOL)

```

~$python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print "Hello world"
Hello world
>>> 

```

The implementation is called "CPython" though.

---

### Post by Reiger on 2008-08-17
> **pmasiar said:**
> 
Compare this Python snippet with Java, and tell me what you think! :-)

I think that is a *really* poor example of the assumed cumbersome Java compared to the assumed versatile Python:


*With* interactive prompt [which you sample doesn't have]:
```

import java.io.*;

public class Hello {

	public static void main(String[] args) {
		System.out.println( "Simple, interactive greeting program.\n" +
				"Supply a commandline argument or type your name at the prompt " +
				"if you wish your name to be known; " +
				"or just hit enter at the prompt to remain unknown.");
		String me;
		if(args.length==0) {
		me="";
		try {
			System.out.println("Please type your name at the prompt.");
			System.out.print("> ");
			BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
			me=br.readLine();
		br.close();
		} catch (Exception e) {	}
		} else {
			me=args[0];
		}
		
		me= me.equals("") ? "world!" : (me+"!");
		
		System.out.println("Hello "+me);
		System.out.close();
		System.exit(0);
	}

}

```

And without; conceptually equivalent to your Python code (although it does take care to close the output stream and exit properly, whereas...).

```

public class Hello {

	public static void main(String[] args) {
		
		String me;
		if(args.length==0) {
		        me="";
		else {
			me=args[0];
		}
		
		me= me.equals("") ? "world!" : (me+"!");
		
		System.out.println("Hello "+me);
		System.out.close();
		System.exit(0);
	}

}

```

That isn't too hairy, now is it? :D

---

### Post by pmasiar on 2008-08-17
> **coderJ said:**
> What is the name of the python that comes with Ubuntu? (Is it Python?)....if so how come its not running when I type it in...(Not only am I new to prgramming but Linux as well...LOL)

Maybe don't try to learn too many things at once... ActiveState Python Windows installer is excellent, and includes decent IDE, called IDLE, use it. It works also on Linux, it's just looks not as pretty. Om Linux, Python is installed but IDLE is separate install (Synaptic will fetch it for you).

IDLE will run your code for you, and also shell has syntax highlighting - nicer than standard terminal shell.

Try to solve as many problems as you can, to get feeling what programming is: ProjectEuler (low numbers) is excellent source. Programming is like learning human language: you may read all you can, but real test is when you try to express yourself.

---

### Post by pmasiar on 2008-08-17
> **Reiger said:**
> 
That isn't too hairy, now is it? :D

No it is not, because it skips over all the hairyness of java :-) by ignoring the task which example was supposed to show:

[quote=pmasiar]
# 1) importing standard library module
# 2) defining function with default argument
# 3) string substitution
# 4) conditional code to manipulate runtime parameters
# 5) simple print output
[/quote]

- You don't have (2) at all. Defining functions is important for modularization, especially defining functions which can work in a flexible way. This is exactly IMHO strong point of Python and weak point of Java, but let's see. 
- for (3) you used basic string operations, because that part of Java really sucks. Python allows me not only concatenate string values, but substitute them in format. I made it little harder for you (again to show off Python's flexibility)
- you have only one runtime parameter, not array.

OK, if you are still game, let's continue: User liked our program, so (are you surprised? :-) ) wants to change it: let's provide also age, and for fun, add 4 years to get age at graduation.

And let's have copy of runtime arguments (any kind of collection, not scalars), and manipulate it. Slavik is right, we should not mess with system args :-)

[php]
# program to test basic language features:
# 1) importing standard library module
# 2) defining function with default argument
# 3) formatted string substitution
# 4) conditional code to manipulate runtime parameters
# 5) simple print output
# 6) String with both kind of quotes
# 7) string->integer conversion
# 8) arrays of parameters

import sys

def hello(name="World", age=0):
    """return hello response for given name"""
    format = """Hello my name is "%(name)s" and I'll be %(grad)i when I'll graduate!"""
    return format % dict(name=name, grad= age+4)

params = sys.argv[:] # my own copy of arguments
if len(params) < 2:
    params.append('prodigy')
    params.append('12')
    
print hello()
print hello(params[1], int(params[2]))
[/php]

Please see 2 new requirements.
I needed IIRC add 3 lines, and change 4, of those 2 changes were cause by renaming variable. 

And honest, I did not planned for this change in requirements :-) It is just example to show OP (and any reader) what it is to program in Java and compare it to Python.

In Java, you will probably throw old code away and start anew? :-)

---

### Post by LaRoza on 2008-08-17
> **pmasiar said:**
> 
In Java, you will probably throw old code away and start anew? :-)

Well, those hours are billable right?

---

### Post by pmasiar on 2008-08-17
> **LaRoza said:**
> Not only that (it made sense), but we get a lot of people that use VS or whatever who can't code without that IDE. An IDE should help the programmer, not make the programmer.

I agree in general (it's safer to know how to walk by yourself, without relying on a crutch), but disagree when applied to Java:

Java's syntax and semantics are so convoluted and library so vast, IMHO it is too much to require beginner to fight that monster with bare editor only. Java is one of the languages which requires IDE. Sure learn how to go without IDE, but it is **so** much more pain - it is not worth my time. I use eclipse all the time, and would have hard time to edit Java without it. I could do it but my productivity would drop 90% and it would not make any sense - Eclipse is free and available for any system where I can reasonably be expected to code in Java, so what is the hidden higher enlightenment in doing it by bare hands? What the heck, I need to job get done!

Say, I added library call. IDE found it throws exception, and suggest either surround by try/catch or add throws to function signature. Doing either manually would disrupt my 'flow': I was writing the code and could not care less about exception right now! So let's add signature and finish function. Now I need to find the code calling my function and add try/catch there. Luckily, Eclipse shows (red spots on scroll bar) where broken code is, I can go there by single click and fix it. Why suffer through this without the IDE?

Same with library calls and object methods: no human can remember than all, and IDE can help to pick one (and even prompts for arguments). Why reject helping hand?

Python fits my brain without help of IDE (mostly - I can program effectively without IDE, but when free IDE will have support for library lookup I'll use it), but Java does not, and I am not elitist enough to ignore productivity gain from IDE. I don't care it it makes me lesser Java expert, I program Java for my daytime job and have deadline.

---

### Post by LaRoza on 2008-08-17
> **pmasiar said:**
> I agree in general (it's safer to know how to walk by yourself, without relying on a crutch), but disagree when applied to Java:

I know about that, but for **learning Java** one should do it by hand. I doubt a beginner is going to find use for those features.

---

### Post by ghostdog74 on 2008-08-17
OP is asking about Java, and its part of his curriculum in his studies. I don't understand the relevance of Python or Perl in this thread.

---

### Post by LaRoza on 2008-08-17
> **ghostdog74 said:**
> OP is asking about Java, and its part of his curriculum in his studies. I don't understand the relevance of Python or Perl in this thread.

My involvement for Python was someone (presumably the OP) asked about Python (page 2).

---

### Post by Reiger on 2008-08-17
> **pmasiar said:**
> - You don't have (2) at all. Defining functions is important for modularization, especially defining functions which can work in a flexible way. This is exactly IMHO strong point of Python and weak point of Java, but let's see.

Yes I do; no I don't. Reconsider the line:
```

me = me.equals("") ? me="world!" : (me+"!");

```

This is one simple line which subsitutes the default for the empty (== non supply) param. Essentially it depends on coding conventions (how do you interpret the defaulting case?) -- in this instance it made a lot of sense to use ""; but other instance may make more sense with null and direct testing using the == operator.

It was the most interesting line of the entire program also; because, as you alluded to, the rest is all trivial. ;) My example was just to show you can essentially do that stuff in Java as well. Of course, you still have the duty of explicitly define what Python does for you implicitly; but that doesn't make it *impossible*.

I do not deny Python or PHP or for that matter any language which is geared towards 'scripting' beats Java or any other more formal language when it comes to quickly hacking together some stuff. That's what those languages are for.

---

### Post by pmasiar on 2008-08-17
> **ghostdog74 said:**
> OP is asking about Java, and its part of his curriculum in his studies. I don't understand the relevance of Python or Perl in this thread.

IIUC, OP is interested in learning CompSci in general. Java is something he will learn in school, and asked how to get started about it. In my **opinion** Python is better intro language to CompSci than Java, and NovaAesa has pretty scary battlefield story about people who started with Java.

So is your opinion that if OP wants to become competent CompSci, best way is to learn Java and ignore every other language?

Or is there some secret society which want to suppress my opinions? 50% of the time I mention my **opinion** (that Python is the best intro language for beginners), somebody jumps on my and tries to silence my **opinion**? 

Of course I know there is not, but sometimes I have such strange feeling :-)

BTW if you think Java is so good for beginners, will you bother to solve the task I did in Python? Just to let OP compare the languages?

---

### Post by LaRoza on 2008-08-17
> **pmasiar said:**
> 
Or is there some secret society which want to suppress my opinions? 50% of the time I mention my **opinion** (that Python is the best intro language for beginners), somebody jumps on my and tries to silence my **opinion**? 

Of course I know there is not, but sometimes I have such strange feeling :-)


A secret society is in the works. Out newletters has been sent out...to nobody, but it was sent out.

---

### Post by Reiger on 2008-08-17
> **coderJ said:**
> Well I'm new to all of this actually (Linux). But I will be taking up Computer Science at my college and they teach Programming with Java under the Linux OS (idk which one).

I was wondering if anyone could point me in the right direction just to get my feet wet in the Prog. w/ Java world...this can be:

>>Which software should I use (compatible with Ubuntu 8.04).
>>Any tips/advice would be nice too.

If there is a thread relating to this then please post link and lock (If it's the same and I apologize if there is)

Thanks

~Coderj

Haven't answered to the OP's call yet:
Software:
Personally I find Eclipse to be a good choice. Of course the hardcore KISS texteditor fan might disagree but I do think that worrying about such things as duplicate variable names, or wrong types is something which doesn't neccesarily indicate routine... If anything it indicates the coder refuses to use a proper IDE. But that's just me.
Tips:
Stay well away from code examples that teach you event listeners with a Swing applet. Try to find sources which begin with baby-steps first; only digest larger chunks later; preferably sources which *only* provide you with strictly required code. 
Java has its ways & quirks; and it is a vast language. However, if in doubt you can always try a google search. Always use Java as one of your keywords; that'll help to bring up a SUN API web page. Incredibly useful stuff there.
Start with applets before moving on to full apps. Applets can be executed within a browser (make sure your browser of choice has got a Java plugin!), and this is really useful for creating your first graphical programs without having to worry [much] about a complete GUI yet.

---

### Post by CptPicard on 2008-08-17
> **NovaAesa said:**
> Okay, so when it comes to Java, this is my suggestion. Rather than relying on a IDE, use a plain text editor (such as gedit) and a terminal window for compilation. This way you will get to know the language much better. You will end up memorising some of the more commonly used libraries and also know the exact file structure/hierarchy.

Ok, opinion warning.. :)

I would take a totally different tack to this, in particular because we are discussing Java which is a very verbose language and has a somewhat complicated toolset. I might advice using a text editor and terminal in the case of something like C which is pretty terse and compiles easily from command line, but anything nontrivial (which of course is relative...) essentially requires an ant script that sets classpaths for javac etc.

Having a code-completing, autohinting and auto-correcting IDE is a total godsend in Java, and I don't understand why a beginner should avoid using it just so that he can go through some "pain" in the beginning  -- this is the same reason why learning Python is better for a beginner than learning a "harder" language so that he can then easily "move down"... it's doing stuff backwards and avoiding a learning aid. :)

I believe easy repetition and seeing lots of models of correct code are good for learning, and an IDE makes this fast. Getting up to speed is so much slower if you go through the normal edit-compile-run-correct cycle while manually browsing the humongous Java API, without even initially having much clue what you're looking for. You'll memorize stuff better and in a more natural manner when you've got a codecompletion system showing you your options at the start.

---

### Post by LaRoza on 2008-08-17
> **CptPicard said:**
> 
Having a code-completing, autohinting and auto-correcting IDE is a total godsend in Java, and I don't understand why a beginner should avoid using it just so that he can go through some "pain" in the beginning  -- this is the same reason why learning Python is better for a beginner than learning a "harder" language so that he can then easily "move down"... it's doing stuff backwards and avoiding a learning aid. :)

I only advise it when first learning the basics. Some people get totally lost and can't write/compile/run "Hello world" without their pet IDE.

---

### Post by CptPicard on 2008-08-17
> **LaRoza said:**
> I only advise it when first learning the basics. Some people get totally lost and can't write/compile/run "Hello world" without their pet IDE.

IMHO this total-noob phase is very brief, hopefully :) At the point where you're able to write a couple of classes, use IDE. (And it's so short I am not sure it's worth skipping the IDE at all)

I mean, I wish I had had the good sense at university to write my assignments in a proper IDE instead of Emacs because I wanted to feel like a Real Man. Would have saved a lot of time and probably become a better Java coder faster, because IDEs let you discover better ways to model things quicker than just manging something as verbose as Java by hand -- refactorings produce huge amounts of errors, which you really need an IDE to keep track of. :)

---

### Post by ghostdog74 on 2008-08-17
> **pmasiar said:**
> IIUC, OP is interested in learning CompSci in general. Java is something he will learn in school, and asked how to get started about it. In my **opinion** Python is better intro language to CompSci than Java, and NovaAesa has pretty scary battlefield story about people who started with Java.

Precisely. OP asked how to get started in Java , and not Python/Perl or whatever. Are you suggesting OP to ask his school to change his curriculum  just because Java is not better than your language (in your opinion) or for whatever reasons?

> 
So is your opinion that if OP wants to become competent CompSci, best way is to learn Java and ignore every other language?

Since when did i imply that? besides, to be competent in compsci requires not just programming languages, but alot of other areas as well. 

> 
Or is there some secret society which want to suppress my opinions? 50% of the time I mention my **opinion** (that Python is the best intro language for beginners), somebody jumps on my and tries to silence my **opinion**? 

nobody doubt your opinions (at least not me, because I am a Python fan like you myself) , but sometimes i think you go overboard. If you think Python is good intro to beginners, how about i say awk ? For a beginner, languages that provide basic concepts in programming eg functions, loops, conditionals etc can be used, not just Python. 

> 
BTW if you think Java is so good for beginners, will you bother to solve the task I did in Python? Just to let OP compare the languages?

i think somebody already did?

---

### Post by pmasiar on 2008-08-17
> **ghostdog74 said:**
> Precisely. OP asked how to get started in Java , and not Python/Perl or whatever. 

OP **already** said that my suggestions seems to make sense, are you saying that he was wrong and you know better what is his original goal?

> Are you suggesting OP to ask his school to change his curriculum  just because Java is not better than your language (in your opinion) or for whatever reasons?

I never said that. Again, creating a strawman argument than refuting it, because you have hard time argue against what I really said.

> Since when did i imply that? 

See how it is if someone suggests something you never said?

> besides, to be competent in compsci requires not just programming languages, but alot of other areas as well. 

... including scripting languages like Python, right? Did I ever suggested that Python is enough for a competent CompSci?

> nobody doubt your opinions (at least not me, because I am a Python fan like you myself) , but sometimes i think you go overboard. 

But some people think I have no right to express my opinion, because they disagree with it?

> If you think Python is good intro to beginners, how about i say awk ? 

No, and I do not see how it is related to anything I said. Do you think awk is good?

> For a beginner, languages that provide basic concepts in programming eg functions, loops, conditionals etc can be used, not just Python. 

but **in my opinion** Python is the best of them. Do you have any problem with that? Do you agree with my opinion? If you disagree, what is better? Awk? :-)

> i think somebody already did?

I am not sure how fully you read whole thread, or if you just jumped to some of my posts to start 'heated arguments'. FYI: Reiger solved first version, with cutting (IMHO) important corners, so I put more emphasis on those in second version, so far no takers. IMHO: because this second fuller version would be even more convincing about superiority of Python (but that's just MHO) :-)

---

### Post by ghostdog74 on 2008-08-17
> **pmasiar said:**
> OP **already** said that my suggestions seems to make sense, are you saying that he was wrong and you know better what is his original goal?
your suggestion totally doesn't make sense. Please read his very first post. Are you saying that after he tried Python, he is going to use it for his Java class in school? Instead you should give him some tips on how to cope with Java in school, since you are an expert in Java too, right? 

> 
I never said that. Again, creating a strawman argument than refuting it, because you have hard time argue against what I really said.

but your very first post implies that. OP is asking for directions in Java to prepare for his school, but straight away you direct him to Python and how good it is against Java. That's why i said, is your suggestion going to change how the school will teach Compsci using Java? 


> 
But some people think I have no right to express my opinion, because they disagree with it?

of course you have your right, but like i said, sometimes you go overboard, like in this thread. 

> If you think Python is good intro to beginners, how about i say awk ? 
> 
No, and I do not see how it is related to anything I said. Do you think awk is good?

why not? just because you are not familiar with it doesn't mean its no good. Moreover, its just for a beginner, so awk is definitely viable alternative to Python. (and others as well).  I can give you an awk solution for that Python piece you posted, but i am not going to do that. Whatever it is, any programming language that supports basic programming concepts for beginners can be used, not just Python.

> 
but **in my opinion** Python is the best of them. Do you have any problem with that? Do you agree with my opinion? If you disagree, what is better? Awk? :-)

I do not have any problem with your opinion. You are free to voice it. Here's a fact and not an opinion: NO ONE LANGAUGE IS THE BEST.

---

### Post by slavik on 2008-08-17
Java as a first language is really not good. Universities emphisize Java because that is the language that is used more than any other in the financial industry right now.

pmasiar: your opinion that Java requires an IDE stems from the fact that you believe that the better way to learn CS is from higher level to lower level, correct?

My Perl post only exists because there was a Python post and I don't really like it when people say "You're a beginner? Learn language X!", it should be more like "You're a beginner? You might want to look into languages A, B, C." (where languages A, B, C follow a different paradigm).

Java is not a bad language, it is bad when being taught as the first programming language.

MIT used to teach Scheme, now they teach Python. Carnegie Mellon (pmasiar, I hope you won't say that the professors at Carnegie Mellon don't know what they are talking about) developed their own program called Alice which teaches you object orientation by providing objects (visual objects) and allows you to connect them in various ways. (I have never used Alice, so I might be wrong in how it actually does things, but that is the idea). Keep in mind, this is something Carnegie Mellon developed on their own, in my opinion, it's like them saying "Nothing out there is good for a beginner."

---

### Post by pmasiar on 2008-08-17
> **ghostdog74 said:**
> your suggestion totally doesn't make sense. Please read his very first post.
Please read comment #16 from OP (and post #10). Do you still think that learning Python before school, before diving into Java, does not make sense?

> Are you saying that after he tried Python, he is going to use it for his Java class in school? 

No, I suggested learning basics of Python before learning Java in school. Why you think otherwise?

> Instead you should give him some tips on how to cope with Java in school, since you are an expert in Java too, right? 

No, sadly I am far from Java expert - I just use it in my day job. And AFAICT I **did** give him tips (see my post #22: why to use Eclipse) and also learn 3 months of Python before starting java, and even why I think IDE with Java is a must. Why you choose to ignore what I said? Did you read all thread, or just this one post you replied?

> you direct him to Python and how good it is against Java. 

Well, is it my fault that (IMHO) Python is better than Java? :-)

> is your suggestion going to change how the school will teach Compsci using Java? 

I never said that. Don;t be ridiculous.

> of course you have your right, but like i said, sometimes you go overboard, like in this thread. 

Why it is wrong to say learner who is going to learn Java anyway to learn quickly Python on the side by himself, if **in opinion of many people** it's better than embarking on Java as total beginner?

> If you think Python is good intro to beginners, how about i say awk ? 

Sure, show us why awk is better than Python. Talk is cheap, show us the code!

> why not? just because you are not familiar with it doesn't mean its no good. 

I looked at awk and I was not impressed, so I am not promoting it - but you do.

> its just for a beginner, so awk is definitely viable alternative to Python. 

Do you care to substantiate your opinion in any way? Or I just have to believe you because you say so? Do you have any arguments?  

> I can give you an awk solution for that Python piece you posted, but i am not going to do that. 

Exactly! This will teach me a lesson! I dared to disagree, so no awk code for me! :-)

Do you see how ridiculous your arguments are? How you want to persuade me, or anyone, that you are right?

Awk is not a language wide suggested as intro. Maybe if you are serious about awk, you want to start thread 'why I love/hate awk' to not pollute this thread? 

> Whatever it is, any programming language that supports basic programming concepts for beginners can be used, not just Python.

... because they are all Turing-complete, blahblah. Show me the code, and I'll will make my mind.

> I do not have any problem with your opinion. You are free to voice it. Here's a fact and not an opinion: NO ONE LANGAUGE IS THE BEST.

While I agree with you that in general, no language is the best (and can do it without shouting), things look differently when we are talking about specific usage of languages for specific goals:

We can agree that C is better for kernel than Lisp, right? That writing web apps in Fortran is not the best, right?

So, **IMHO** for beginners, Python is better introductory language than Java. And I can substantiate that with snippet of Python code, which solves couple of trivial problems. And all you did so far is shouted at me that all languages (and opinions) are created equal. So, where is the code? Where is the beef?

---

### Post by LaRoza on 2008-08-17
> **pmasiar said:**
> Where is the beef?

Check synaptic. It is my brainfuck interpreter of choice.

---

### Post by pmasiar on 2008-08-17
> **slavik said:**
> pmasiar: your opinion that Java requires an IDE stems from the fact that you believe that the better way to learn CS is from higher level to lower level, correct?

No. IDE is required because (see #22) Java is so huge and complicated. 

> I don't really like it when people say "You're a beginner? Learn language X!", it should be more like "You're a beginner? You might want to look into languages A, B, C." (where languages A, B, C follow a different paradigm).

I considered that, but Python is the best in my opinion, and I leave it to proponents of other opinions to defend their choices :-)

> Carnegie Mellon (pmasiar, I hope you won't say that the professors at Carnegie Mellon don't know what they are talking about) 

Why you felt that this attack was appropriate? Everybody knows that CMU is one of top CompSci school in the world.

> developed their own program called Alice which teaches you object orientation ...(I have never used Alice, so I might be wrong in how it actually does things, but that is the idea). 

I looked at [Alice](http://en.wikipedia.org/wiki/Alice_%28software%29), it is JVM successor of [SmallTalk](http://en.wikipedia.org/wiki/Smalltalk_(programming_language)) -> [Squeak](http://en.wikipedia.org/wiki/Squeak) --> [Scratch](http://en.wikipedia.org/wiki/Scratch_%28programming_language%29) --> Alice 

One reason, I am not that obsessed about teaching OOP to green beginners: let them make sense from  procedural programming first, and do OOP later. This is one particular reason why I like Python: because it is not as obsessed about OOP as Java is.

> Keep in mind, this is something Carnegie Mellon developed on their own, in my opinion, it's like them saying "Nothing out there is good for a beginner."

CompCsi department has to develop new languages to get new PhDs :-) but IMHO real language like Python usable later in real life is better that something make up to make Java more palatable for beginners. You are free to disagree :-)

---

### Post by tinny on 2008-08-17
> 
> of course you have your right, but like i said, sometimes you go overboard, like in this thread.


1+ 

Sometimes our approach comes across as being a little too aggressive (hammering home Python straight off the bat). Please dont take that as me trying to silence you :). I personal would like to see a little more tact shown when trying to state that there is another way. E.g. "welcome to the world of programming and Java, during your journey you will learn lots of different things including languages other than Java, hopefully : )"

> 
Please read comment #16 from OP (and post #10). Do you still think that learning Python before school, before diving into Java, does not make sense?


Could have gone either way. I think that was a fluke personally :lolflag:

---

### Post by pmasiar on 2008-08-17
> **tinny said:**
> I personal would like to see a little more tact shown when trying to state that there is another way. E.g. "welcome to the world of programming and Java, during your journey you will learn lots of different things including languages other than Java, hopefully : )"

Nah, too subtle, and life is short to type such long sentences. Where is fun in that?

---

### Post by CptPicard on 2008-08-17
Tinny, did you see that Simpsons episode where they removed all the violence from Itchy and Scratchy and they were just hugging each other and handing each other presents?

Now... where was the fun in that? :confused: Reflect. :)

---

### Post by ghostdog74 on 2008-08-17
> **pmasiar said:**
> 
> If you think Python is good intro to beginners, how about i say awk ? 

Sure, show us why awk is better than Python. Talk is cheap, show us the code!

i did not say awk is BETTER than Python. don't put words in my mouth. If talking about beginner, any language that supports programming concepts can take up the job. I blurted out awk just for an example. I could have said Java too. 

> 
> why not? just because you are not familiar with it doesn't mean its no good. 

I looked at awk and I was not impressed, so I am not promoting it - but you do.

its not my fault you can't appreciate awk :)

> 
> its just for a beginner, so awk is definitely viable alternative to Python. 

Do you care to substantiate your opinion in any way? Or I just have to believe you because you say so? Do you have any arguments?  

will it be an insult to you if i ask you to RTFM.? If you do RTFM, you will find it covers basic programming concepts quite adequately.(except OO). Need I say more.?

> 
> I can give you an awk solution for that Python piece you posted, but i am not going to do that. 

Exactly! This will teach me a lesson! I dared to disagree, so no awk code for me! :-)

since you need that badly, here you are:
```

awk 'BEGIN{ 
  print ARGV[ARGC-1]?hello(ARGV[ARGC-1]):hello()
}
func hello(name) {
 return (name=="")?name="World":name
}'  myname

```

> 
Awk is not a language wide suggested as intro. Maybe if you are serious about awk, you want to start thread 'why I love/hate awk' to not pollute this thread? 

No i am not going to. I do love awk, but i also don't hate others.

> 
> Whatever it is, any programming language that supports basic programming concepts for beginners can be used, not just Python.

... because they are all Turing-complete, blahblah. Show me the code, and I'll will make my mind.

i am sure i do not need to elaborate to you what are basic programming concepts. 

> 
 And all you did so far is shouted at me that all languages (and opinions) are created equal. So, where is the code? Where is the beef?

If you were to post your python snippet to a Java forum where Java experts
lurch, i am sure they can give you a solution easily. I am no Java expert.

---

### Post by tinny on 2008-08-17
> **CptPicard said:**
> Tinny, did you see that Simpsons episode where they removed all the violence from Itchy and Scratchy and they were just hugging each other and handing each other presents?

Now... where was the fun in that? :confused: Reflect. :)

Yeah ok.

Now can I have a cuddle?

---

### Post by pmasiar on 2008-08-17
> **ghostdog74 said:**
> i did not say awk is BETTER than Python. don't put words in my mouth. If talking about beginner, any language that supports programming concepts can take up the job. I blurted out awk just for an example. I could have said Java too. 

don't pull lawyer's logic on me. We were talking about languages for beginners, so do you seriously claim that awk is suitable for beginner or not?

I was trying to give my best answer for the assumed question which would OP asked if he would not (IMHO mistakenly) assumed that Java is good language for beginners. Are you trying to solve OP's problem, or just create endless arguments?

> its not my fault you can't appreciate awk :)

I don't see your point. Do you suggest that there is a reason to appreciate awk? I don't see reason, and if you like awk so badly, then YES, it is your fault that you cannot communicate why awk is so awesome. Who else?


> will it be an insult to you if i ask you to RTFM.? If you do RTFM, you will find it covers basic programming concepts quite adequately.(except OO). Need I say more.?

Yes please

> since you need that badly, here you are:
```

awk 'BEGIN{ 
  print ARGV[ARGC-1]?hello(ARGV[ARGC-1]):hello()
}
func hello(name) {
 return (name=="")?name="World":name
}'  myname

```


finally. it was like waiting at the dentist, but thanks.

Now I let OP to decide if he likes awk more than Python for introduction to programming.

Would you care to complete also second challenge?

> No i am not going to. I do love awk, but i also don't hate others.

I don't hate other languages... except Java makes me sooo frustrated soo often. 

> i am sure i do not need to elaborate to you what are basic programming concepts. 

but it would help if language you promote for beginners could do OOP, right? 

> If you were to post your python snippet to a Java forum where Java experts lurch, i am sure they can give you a solution easily. I am no Java expert.

Neither am I. I would expect that it is responsibility of people who like Java to defend their favorite language. If Java disappeared tomorrow (and I still could keep my job programming same task in Python, which would be more productive), I would not care - not a bit.

---

### Post by hod139 on 2008-08-17
@OP
If your intro class uses Java, I suggest you spend some time learning the Java syntax (you can learn other languages in your own time) since the goal is to get a passing grade in the course, and another languages syntax won't help too much with that goal.  As for tutorials, Sun has entire page devoted to them: [http://java.sun.com/developer/onlineTraining/](http://java.sun.com/developer/onlineTraining/)
Also, the course page for the class might already be up, and you can see what book the course is using.  You can then start reading the book and doing some of the exercises in there.  Also, previous years course notes might be available on the professor's website.

> **pmasiar said:**
> 
OK, if you are still game, let's continue: User liked our program, so (are you surprised? :-) ) wants to change it: let's provide also age, and for fun, add 4 years to get age at graduation.

I'm no Java pro, but I'll bite.

[php]
// program to test basic language features:
// 1) importing standard library module
// 2) defining function with default argument (not possible by design in JAVA)
// 3) formatted string substitution
// 4) conditional code to manipulate runtime parameters
// 5) simple print output
// 6) String with both kind of quotes
// 7) string->integer conversion
// 8) arrays of parameters 


import java.text.MessageFormat; // (1)

public class Demo {    

    ///
    public void hello(String name, int age){ // (2, without defaults explicitly)
        
       MessageFormat format = new MessageFormat(
           "Hello my name is \"{1}\" and Ill be {0} when I graduate!"); 
       
       Object[] testArgs = {new Integer(age+4), name}; // (3), (8)

       System.out.println(format.format(testArgs));    //(5)
    }
    
    ///
    public static void main(String[] args) {
        Demo myJavaDemo = new Demo();
    
        // default values
        String name = "prodigy";
        int age = 12;
        
        if(args.length==2) { // (4)
            name = args[0];
            age = Integer.parseInt(args[1]); // (7)
        }
        
        myJavaDemo.hello(name, age);
    }
}
[/php]I don't know enough Java to figure out how to use a single quote in a MessageFormat (it is a special character used for substitution), but maybe a java guru knows how (or a better way).  Also, the Java language by design does not allow for default values in arguments, so that will be impossible.  I added a simple if statement though that mimicks the same behavior.

---

### Post by pmasiar on 2008-08-17
> **hod139 said:**
> I'm no Java pro, but I'll bite.

Thanks for that.

> // 2) defining function with default argument (not possible by design in JAVA)

I thought there is possible to have multiple functions with different signatures, and Java is smart enough to pick right one? It would not be fair to stack test so heavy against Java :-)

> // 3) formatted string substitution

Thanks, I did not know about java.text.MessageFormat - looks really useful.

> // 4) conditional code to manipulate runtime parameters
> // 8 ) arrays of parameters 

Slavik suggested that more kosher is to make your own copy of args as I did in take (2) but you did not...

Anyway, good job, thanks. 

I hope now OP has better idea what awaits him, and has better chance to succeed.

---

### Post by ghostdog74 on 2008-08-17
> **pmasiar said:**
> don't pull lawyer's logic on me. We were talking about languages for beginners, so do you seriously claim that awk is suitable for beginner or not?

If you insist, then YES, why not? Except OO and memory management, awk supports loops, conditionals, arithmetic, operators, arrays, functions, control statements etc. Just good enough for a beginner. What Python can do for a beginner, I can say awk can do the job too. The point is, not just awk, but other languages that does these basic things can be used, even Java.


> 
> its not my fault you can't appreciate awk :)

I don't see your point. Do you suggest that there is a reason to appreciate awk? I don't see reason, and if you like awk so badly, then YES, it is your fault that you cannot communicate why awk is so awesome. Who else?

You keep telling people that if you don't know enough about a language, then there's no point comparing it with others. But you don't practice what you preach. You don't appreciate awk because you have not gone in depth. I can't force you though. Who or what else can communicate awk better than me other than the manuals? the main thing is not about languages for beginners, but whether we are showing the OP the right/best way according to his situation. Lastly, you can show him that learning about Python before diving into Java but its also not wrong for me to say that not only Python can be used to show him basic programming concepts, right? 


> 
Now I let OP to decide if he likes awk more than Python for introduction to programming.

seriously, i did not even coax OP to use awk before he learns Java. If i want to help OP besides his technical problems, i would just say make the best use of his time before school starts to learn Java, after all, he can't escape it. 

> 
Would you care to complete also second challenge?

so what is your point for me to complete the second challenge? Are you wanting me to prove awk is better than Java for beginner, or wanting me to prove just some basic programming concepts that can accomplish the task just as well?
 

> 
> No i am not going to. I do love awk, but i also don't hate others.

I don't hate other languages... except Java makes me sooo frustrated soo often. 

I understand your frustration. But that's not the point. Because you are standing on a viewpoint of a professional. But OP is just a student wanting to learn Java. Imagine if he is in class now, and he is feeling frustrated just like you, what do you suggest he do ? skip class ? ask the school to change curriculum? I would rather he use his time now to really get into it since its a subject he can't escape. He can use Python(or others) to complement his knowledge, that i agree with you, but that's only to certain extent. 
> 
> i am sure i do not need to elaborate to you what are basic programming concepts. 

but it would help if language you promote for beginners could do OOP, right? 

First of all, if you still don't get it, I am not a promoter of languages.
I could also say C++ or even Java can be used for OOP concepts. Just that OOP doesn't come to my mind as a beginner concept. PLease treat that as an opinion of mine.

---

### Post by pmasiar on 2008-08-18
> **ghostdog74 said:**
> You keep telling people that if you don't know enough about a language, then there's no point comparing it with others.

That's true: but most of those people are expressing opinion about languages while having experience in Java or C/C++ only, so they are hardly in position to compare anything beyond syntax sugar.

However, I do have first-hand experience in more than dozen languages, so I don't think I need to spend a year learning awk just to understand that it does nothing what Perl also has.

> But you don't practice what you preach. You don't appreciate awk because you have not gone in depth. I can't force you though. 

Show me some killer awk features so I would be interested. I looked at awk briefly, it looked like Perl (which I do have experience with), and I did not see any reason to learn more about awk. After your promotion, I still do not see anything - Perl at least has some awkward OOP. Why would someone prefer awk over Perl or Python?

> the main thing is not about languages for beginners, but whether we are showing the OP the right/best way according to his situation. 

Exactly. And according to what I know, learning little Python before Java increases ability to understand Java. And you are vehemently trying to prove me wrong, and I am not sure why.

> Lastly, you can show him that learning about Python before diving into Java but its also not wrong for me to say that not only Python can be used to show him basic programming concepts, right? 

Yes, not only Python, but IMHO Python is better than others. More intuitive than both Java and awk.

> seriously, i did not even coax OP to use awk before he learns Java. 

that would be tough sell IMHO :-)

> If i want to help OP besides his technical problems, i would just say make the best use of his time before school starts to learn Java, after all, he can't escape it. 

That's true. But seemingly smart and forward-planning person like OP will be just fine (if he will not start partying all night or playing bridge. Seriously, I know a student who repeated year because of bridge. OP, you were warned! No bridge! :-) ) 

> so what is your point for me to complete the second challenge? Are you wanting me to prove awk is better than Java for beginner, or wanting me to prove just some basic programming concepts that can accomplish the task just as well?

No, think about what YOU want to prove about awk. I still don't see any reason to even consider learning more about it, and you did not gave me any.
 
> I understand your frustration. But that's not the point. Because you are standing on a viewpoint of a professional. But OP is just a student wanting to learn Java. Imagine if he is in class now, and he is feeling frustrated just like you, what do you suggest he do ? 

Hack Python project over the weekend to relieve frustration and prove yourself that it's Java what sucks, not his programming skills?

Couple forum members mentioned that they started in C++ and decided that programming is not viable career for them, only to return to programming later, with non-C++ language. Java is little better, but just a little, IMHO. So I promote Python to get them chance to feel what programming fun is, before Java or C++ will make then feel stupid. To save them for programming. And you for some reason are against this - are you afraid of competition? The less programmers the higher salaries? :-)

---

### Post by imdano on 2008-08-18
> **pmasiar said:**
> Thanks for that.

> // 2) defining function with default argument (not possible by design in JAVA)

I thought there is possible to have multiple functions with different signatures, and Java is smart enough to pick right one? It would not be fair to stack test so heavy against Java :-)
It is, here's how it would look (using hod139's code as a base)...[php]import java.text.MessageFormat;

public class Demo {    
    private static final int defAge = 12;
    private static final String defName = "prodigy";
    ///
    public void hello(String name, int age){
        
       MessageFormat format = new MessageFormat(
           "Hello my name is \"{1}\" and Ill be {0} when I graduate!"); 
       
       Object[] testArgs = {new Integer(age+4), name};

       System.out.println(format.format(testArgs));
    }
    
    public void hello() {
        hello(defName, defAge);
    }
    
    public void hello(String name) {
        hello(name, defAge);
    }
    
    public void hello(int age) {
        hello(defName, age);
    }
    
    ///
    public static void main(String[] args) {
        Demo myJavaDemo = new Demo();
        String name = new String();
        int age;
        
        if(args.length == 2) {
            name = args[0];
            age = Integer.parseInt(args[1]);
            myJavaDemo.hello(name, age);
        }
        
        else if (args.length == 1){
            try {
                age = Integer.parseInt(args[0]);
                myJavaDemo.hello(age);
            } catch(NumberFormatException e) {
                name = args[0];
                myJavaDemo.hello(name);
            }
        }
    }
}[/php]In my experience (4 years of it in school) and from what I've seen in the Java standard library, the more common way to handle that kind of situation is to just have one implementation of the "hello" method, and have the user explicitly pass "null" in for the unused argument.  The "hello" method would then run a check for null values and substitute the default value when needed.

---

### Post by tinny on 2008-08-18
Here is my attempt

[PHP]
// program to test basic language features:
// 1) importing standard library module
// 2) defining function with default argument (not possible by design in JAVA)
// 3) formatted string substitution
// 4) conditional code to manipulate runtime parameters
// 5) simple print output
// 6) String with both kind of quotes
// 7) string->integer conversion
// 8) arrays of parameters


import java.text.MessageFormat;//#1 (dont need to import lang)

public class Hello {

    public static void main(String args[]) { //wink
        // default values
        String name = "prodigy";
        Integer age = 12;
        //#4
        if (args.length == 2) {
            name = args[0];
            age = Integer.parseInt(args[1]); //#7
        }
        //#5
        System.out.println(hello(name, age));
        System.out.println(hello());
    }

    public static String hello(String name, Integer age) {
        return formatMessage(name, age);
    }

    //#2 (sort of)
    public static String hello() {
        return formatMessage("World", 0);
    }

    private static String formatMessage(String name, Integer age) {
        //#3 #8
       return MessageFormat.format("Hello my name is \"{0}\" and I''ll be {1} when I''ll graduate!",
               new Object[]{name, age + 4});
    }
}
[/PHP]

I was in a hurry (at work) when I wrote this so be gentle.

---

### Post by pmasiar on 2008-08-18
> **imdano said:**
> In my experience (4 years of it in school) and from what I've seen in the Java standard library, the more common way to handle that kind of situation is to just have one implementation of the "hello" method, and have the user explicitly pass "null" in for the unused argument.  The "hello" method would then run a check for null values and substitute the default value when needed.

Thanks. Good way in Java to handle defaults I guess.

And your code is little safer because I did not bother to handle exception on integer conversion failure, while Java will force you to do it. Which is good in general, but quite annoying for 'quick and dirty test' code - and good reason to have IDE handle it for you.

Is there some quick way to copy args[] to params[]? Do I have to loop through all?

---

### Post by slavik on 2008-08-18
> **pmasiar said:**
> snip ...

CompCsi department has to develop new languages to get new PhDs :-) but IMHO real language like Python usable later in real life is better that something make up to make Java more palatable for beginners. You are free to disagree :-)
IMO, beginners need to learn to think in functions (as in, do X with the result from Y which will take the result of Z as input).

EDIT: <devils' advocate> Java is useful later on in life. </devils' advocate>

---

### Post by tinny on 2008-08-18
> **pmasiar said:**
> 
Is there some quick way to copy args[] to params[]? Do I have to loop through all?

[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/System.html#arraycopy(java.lang.Object,%20int,%20java.lang.Object,%20int,%20int)](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/System.html#arraycopy(java.lang.Object,%20int,%20java.lang.Object,%20int,%20int))

---

### Post by tinny on 2008-08-18
> 
And your code is little safer because I did not bother to handle exception on integer conversion failure



Integer.parseInt has a runtime exception that I didnt catch :oops:

---

### Post by tinny on 2008-08-18
> 
Just that OOP doesn't come to my mind as a beginner concept. Please treat that as an opinion of mine. 


OOP can be an intimidating subject.

I believe it is good to get the student involved in OOP early. Object decomposition is great skill that helps coders with the black art of transferring requirements from the real world into code.

This is also why I am a fan of Java. Java forces you to use Object decomposition, however this is not always appropriate.

---

### Post by slavik on 2008-08-18
> **tinny said:**
> OOP can be an intimidating subject.

I believe it is good to get the student involved in OOP early. Object decomposition is great skill that helps coders with the black art of transferring requirements from the real world into code.

This is also why I am a fan of Java. Java forces you to use Object decomposition, however this is not always appropriate.
objects are things, things interact with each other. things have actions. the actions can be given information.

example:
syntax: thing.action(data)
question: make the dog jump 5 feet
answer: dog.jump(5)

There, I just explained to you what OO is, just need more practice, and you will really get it.

---

### Post by tinny on 2008-08-18
> There, I just explained to you what OO is, just need more practice, and you will really get it.

@OP right? Hope so, or am I coming across like a noob?

---

### Post by slavik on 2008-08-18
> **tinny said:**
> @OP right? Hope so, or am I coming across like a noob?
"you" was more of a generic term for a person, sorry if I made it look like I was referring specifically to you.

---

### Post by tinny on 2008-08-18
> **tinny said:**
> :confused:

Integer.parseInt has a runtime exception that I didnt catch :oops:

NumberFormatException inherits from [RuntimeException]("http://java.sun.com/j2se/1.4.2/docs/api/java/lang/RuntimeException.html"). These types of exceptions are not compulsory to catch.

---

### Post by CptPicard on 2008-08-18
> **tinny said:**
> OOP can be an intimidating subject.

Yeah, because it's mostly a bunch of contrivances especially in statically typed languages ... essentially tricks around the type system to make "everything object-oriented". IMO the GoF book is a symptom, not a solution :)

> 
I believe it is good to get the student involved in OOP early. Object decomposition is great skill that helps coders with the black art of transferring requirements from the real world into code.

Yeah, the black art in the middle is OOP ;) Object decomposition on the other hand is OK and pretty natural when analysing problems but the really sucking part starts when one gets to encapsulation (it really is just unneccessary restriction for questionable gain), plus the problems of happily using general supertype with lost type information, until you can't, and you need to start tracking down wtf this object actually IS... :mad: (even worse if you don't have RTTI, ugly hack even when you do)

Check out Common Lisp's CLOS, that is object system done right. Objects should really be just a bunch of "structs" with a type hierarchy plus preferably multiple-dispatched functions operating on them.

> 
This is also why I am a fan of Java. Java forces you to use Object decomposition, however this is not always appropriate.

I am very sceptical of an argument that says that "learning this the hard way is good for you because you're forced to do stuff even when not appropriate"...

It really held back my evolution as a programmer that I started "properly" with Java at uni and had to first learn the "tricks" that is called "OOP design" to get anything interesting actually done. Now I do have enough stuff in my design toolbox, but with a language like Python or a Lisp I would have been really *coding**a lot of complex things much earlier than I actually was able to, simply because the stupid pieces never fit together in a reasonable way, and I was just bored of trying to fit a square peg into a round hole because of the language, although I was always *algorithmically* etc competent...

---

### Post by ghostdog74 on 2008-08-18
> **pmasiar said:**
> 

Show me some killer awk features so I would be interested. 
what do you want to see?

> 
I looked at awk briefly, it looked like Perl (which I do have experience with), and I did not see any reason to learn more about awk. After your promotion, I still do not see anything - Perl at least has some awkward OOP. Why would someone prefer awk over Perl or Python?

i am not turning this into a awk vs perl vs python language debate. I just want to make my point that for a beginner, any language that supports basic programming  concepts can be used. I just took awk as an example. I could have chosen C++ too. Also, remember, in compsci, you not only need to understand algorithms on a higher level, depending on the subjects OP takes, knowledge on the lower levels are also important. Do you agree with me on this respect that C++ can also be used too? 

> 
Yes, not only Python, but IMHO Python is better than others. More intuitive than both Java and awk.

care to show what you mean by intuitive? Easy to read? less words? less noise? 

> 
No, think about what YOU want to prove about awk. I still don't see any reason to even consider learning more about it, and you did not gave me any.

I am not trying to prove awk is superior than any other. Like i said above i am just showing you other languages can perform the same tasks for a beginner, besides Python. If you insist, i can finish up the second challenge for you using awk (Its not my fav language take note) but you must tell me WHAT YOU want me to prove.

---

### Post by hod139 on 2008-08-18
> **pmasiar said:**
> 
> // 2) defining function with default argument (not possible by design in JAVA)

I thought there is possible to have multiple functions with different signatures, and Java is smart enough to pick right one? It would not be fair to stack test so heavy against Java :-)

Yes it's possible (as later posts showed).  But functions with default values for arguments are not allowed by design.

> 
Slavik suggested that more kosher is to make your own copy of args as I did in take (2) but you did not...

He suggested that you don't alter the args by appending new values. I didn't alter the values of the runtime arguments in my solution;  I pass the age arg by value to the method, which alters a copy of one the args, not the arg itself.

---

### Post by pmasiar on 2008-08-18
> **pmasiar]
Is there some quick way to copy args[] to params[]? Do I have to loop through all?[/quote]

[QUOTE=tinny said:**
> [http://java.sun.com/j2se/1.5.0/docs/api/java/lang/System.html#arraycopy(java.lang.Object,%20int,%20java.lang.Object,%20int,%20int)](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/System.html#arraycopy(java.lang.Object,%20int,%20java.lang.Object,%20int,%20int))

Thanks. Example of use, please? What I need to import?

I guess it's time I'll read some more current book about java than those old books I had around forever...

---

### Post by pmasiar on 2008-08-18
> **hod139 said:**
> I didn't alter the values of the runtime arguments in my solution;  I pass the age arg by value to the method, which alters a copy of one the args, not the arg itself.

But goal of the exercise was to show learner some simple way to bundle parameters together, so you can pass them as single unit. I could used tuple or dict in Python. You could used POJO with getters and setters :-)

---

### Post by nvteighen on 2008-08-18
What I think is that the OP (btw, are you still there, coderJ?) or anyone in the situation: "in my college we will be taught <X> as intro language but I'd like to learn how to program first" should attempt to learn how to program with whatever language that supports the paradigms used in that X language he will be taught after.

It's just pragmatical. He'll be graded in Java, in order to pass the course he will have to know Java and even if he's a great Assembly-hacker, if he doesn't know what a class is, he'll fail.

Python seems to me very useful spaecially in this particular case. It's simple enough to teach you the very basics of programming and also stuff that you'll see in Java, like OOP.

---

### Post by pmasiar on 2008-08-18
> **ghostdog74 said:**
> what do you want to see?

I am not sure why you pretend you do not understand. Show me killer feature of awk as you promised. Show me why I should waste time learning it. Please stop answering by questions on my questions, or i would consider you a troll. It stopped being funny 2 posts ago.

> i am not turning this into a awk vs perl vs python language debate. 

Just reminder: It was **you** who muddled the picture with awk :-)

> I just want to make my point that for a beginner, any language that supports basic programming  concepts can be used. 

Yes, it **can**, but should? Should learner pick language randomly?

I would like to make my point that (IMNSHO) even if languages are Turing-complete, they are not equally suitable to teach beginners basics of programming. 

> I just took awk as an example. I could have chosen C++ too. 

Why? Are you serious? C++ would be even worse for a beginner than Java, IMHO! Plain old C would be better.

> Also, remember, in compsci, you not only need to understand algorithms on a higher level, depending on the subjects OP takes, knowledge on the lower levels are also important. 

yes, but this understanding is language independent.

> Do you agree with me on this respect that C++ can also be used too? 

For beginners? maybe for juvenile offenders, to make then suffer? :-)

> care to show what you mean by intuitive? Easy to read? less words? less noise? 

yes, and also: easier to understand. Code which work as it looks. Easier to "guess" what code does even if not exactly sure. Easier to write valid code, and less fragile code. No type terror squad blowing your code because you possibly might not have right types - big frustration for beginners. having easy to use basic library.

All this are components of being 'easy' and 'intuitive'.

> I am not trying to prove awk is superior than any other. Like i said above i am just showing you other languages can perform the same tasks for a beginner, besides Python. 

Yes, they can, but beginner can use only **one** language as first - and IMNSHO Python is better choice than awk, Java or C++. And if you don't believe me, check poll in sticky FAQ - it is majority opinion (even if such self-selected online polls are almost worthless).

So you are trying to imprint on me that most languages are Turing-complete (which I know for decades), and I am to try to make you to think which of many Turing-complete languages might be best choice for first language for a beginner, and why.

> If you insist, i can finish up the second challenge for you using awk (Its not my fav language take note)

Well don't do it if you don't like awk then. But why to discuss awk if you don't care about it?

> but you must tell me WHAT YOU want me to prove.

it was **you** who volunteered :-) for two tasks:

1) show me why you consider awk interesting language and worth to know to person like me, who already knows Perl and Python. Show me reason beyond "because it is out there". many **more interesting** languages are out there: Erlang, Factor, Scala etc, and I already know why I should learn those. So why awk?

Or was awk just a troll to start endless discussion? What was your reason to add awk to discussion between Java and Python? I considered you smart person, don't invalidate my opinion about you.

2) Show OP why he (as beginner) might consider awk, if you believe he should. (I would advice against awk: as you know, i prefer Python for beginners).

---

### Post by ghostdog74 on 2008-08-18
> **pmasiar said:**
> 
Or was awk just a troll to start endless discussion? What was your reason to add awk to discussion between Java and Python? I considered you smart person, don't invalidate my opinion about you.

Well, you brought Python into a Java discussion first, dare you say not? :) Seriously, i don't really care about your opinion on me. 

> 
2) Show OP why he (as beginner) might consider awk, if you believe he should.

Sigh, its strange that you still ask me this when I already referred you to [RTFM](http://www.gnu.org/software/gawk/manual/gawk.html)
```

awk ' BEGIN {
 #-------------------
 #for loop 
 for(i=1;i<=10;i++) {
   print i
 }
 
 i=1
 # ------------------
 # while loop
 while ( i <= 10 ){
   print i
   i++ #or i=i+1
 } 
 
 #-----------------
 # arrays
 a[1]="one"
 a[2]=2
 print a[1],a[2]
 
 #------------------
 # control flow
 j=10
 if ( j ==10 ) {
  print "j is 10"
 }else {
  print "j is not 10"
 }
 
 #-----------------
 # arithmetic
 print m=m+1
 print 2^10
 print 2*10
 print 2/3
 
 #------------------
 # Operators
 k=1
 y=2
 if ( k < y ) { # comparison operators
  print "k is less than y"
 }else if ( k == 1 ){ # relational operators
  print "k is equal 1"
 }
 
 # ----------------
 # function
 print myfunc("test")
 
} 

function myfunc(argument) {
  return argument
}'

```
What else for beginners? Any of these basic concepts are also covered in other languages. Also, variable declaration doesn't need $,@ or those funny characters that Perl uses, looks much more like C, Python declarations. Easy to read and intuitive? you tell me.

> 
 (I would advice against awk: as you know, i prefer Python for beginners).
my advice, no preference for a particular language. Any that can support beginner concepts will do.

---

### Post by pmasiar on 2008-08-18
> **ghostdog74 said:**
> Well, you brought Python into a Java discussion first, dare you say not? :) 

Yes, I brought Python for a reason: because I believe it is better intro language for beginners than Java. 

So you admit you mentioned awk as just yet another language, with no real preferences over either Java or Python. 

And you think that having more equal languages to choose from, you make some service to the beginner, right?

You might not be aware about another trick which our brain plays on us: [The Paradox of Choice: Why More Is Less](http://en.wikipedia.org/wiki/The_Paradox_of_Choice:_Why_More_Is_Less). If you have too many equal choices with no clear preferences, task to choose is becoming **harder** not easier.

> Seriously, i don't really care about your opinion on me. 

You should. And I do care about your opinion - that's why I try to explain myself and dig all those links supporting my opinion, so my opinion could be distinguished from random noise. 

> Sigh, its strange that you still ask me this when I already referred you to [RTFM](http://www.gnu.org/software/gawk/manual/gawk.html)

RTFM is too much work - I already looked at awk, and you just shown me bland common syntax, nothing to get excited about, or give awk preferences to Perl or Python which I already know. So you did not made a sale today. :-)

> variable declaration doesn't need $,@ or those funny characters that Perl uses, looks much more like C, Python declarations. Easy to read and intuitive? you tell me.

Yes, but that's not enough: I have that in Python already. 

> my advice, no preference for a particular language. Any that can support beginner concepts will do.

This leaves beginner to pick language at random - which guarantees frustration, see link above. So in your opinion, python is no worse than awk. But in opinion of many others, Python is **better** than say the same awk or Java. So why you would object if beginner learns Python first, if, in your own opinion, Python is no worse? What is the gain? Why to get involved in this endless discussion?

I am here because OP asked question (how to learn basics of programming) and I have preference about which language should beginner learn first. 

You seemingly do no have preference: would you prefer us here in forum just recommend a language in random? Every language will have own day? C++ on Mondays, awk on Sundays? I still do not see how we can implement your suggestion.

If I do not have any preference in forum discussion, I do not get involved. So I am puzzled why you decided to get involved to prove that we should not care. And how it helps beginner to solve the task of selecting the first language to learn.

---

### Post by hod139 on 2008-08-18
> **pmasiar said:**
> 
I am here because OP asked question (how to learn basics of programming) and I have preference about which language should beginner learn first. 

I don't mind you telling posters to use Python when this (your quote) is the question they are asking.  However, in this particular thread, this is not what the OP asked.  The OP asked:
> **coderJ said:**
> ...I will be taking up Computer Science at my college and they teach Programming with Java under the Linux OS (idk which one).
<snip>


In this situation, the OP does not have a choice about which language he or she can use, the school has already made that decision.  That is why I spoke up in this thread, because I'm not sure how spending 1-2 weeks time learning Python before the semester starts will help the OP learn Java (you claim it will but don't give any real evidence).  You are entitled to this opinion (I didn't challenge it) and I stated my opinion that it might be more beneficial for the OP to find the Java book the class will use and start reading.  You didn't challenge my opinion so all things are good between us.  

What I don't understand is that when ghostdog asks you to defend your opinion by asking the same question that I was thinking (ghostdog and I chose different routes, I offered an alternative s/he asked you to explain your opinion)
> **ghostdog74 said:**
> OP is asking about Java, and its part of his curriculum in his studies. I don't understand the relevance of Python or Perl in this thread.
why the discussion deteriorated so quickly between you two.

Looking back at your answer to this question, you didn't answer it very well
> **pmasiar said:**
> 
IIUC, OP is interested in learning CompSci in general. Java is something he will learn in school, and asked how to get started about it. In my **opinion** Python is better intro language to CompSci than Java, and NovaAesa has pretty scary battlefield story about people who started with Java.  

So is your opinion that if OP wants to become competent CompSci, best way is to learn Java and ignore every other language?

Or is there some secret society which want to suppress my opinions? 50% of the time I mention my **opinion** (that Python is the best intro language for beginners), somebody jumps on my and tries to silence my **opinion**? 

Of course I know there is not, but sometimes I have such strange feeling :smile:

BTW if you think Java is so good for beginners, will you bother to solve the task I did in Python? Just to let OP compare the languages?

IIUC, OP is interested in learning CompSci in general; but is not free to pick any language.   Python may very well be a better language to use for an intro (more and more schools are), but it isn't an option here.  Also, the question wasn't if Python is a better introductory language, the question is why you suggested python when it isn't a choice.  You then got unnecessarily defensive, put words in ghostdog's mouth, "BTW if you think Java is so good for beginners", and later charged him/her with trolling behavior for answering questions with questions (even though you answered his initial question with three questions).
> **pmasiar said:**
> Please stop answering by questions on my questions, or i would consider you a troll. It stopped being funny 2 posts ago.

 
Since the discussion has gone downhill between you two, I will now ask the same question that I originally avoided.  Why do you suggested the OP spend 1-2 weeks learning Python (instead of Java which s/he will be forced to use) when they will be forced to learn and use Java in the course?  What benefit will this give the OP over finding the course's book and beginning to read it and doing some of the questions from the book?

---

### Post by pmasiar on 2008-08-18
> **hod139 said:**
> OP does not have a choice about which language he or she can use, the school has already made that decision. 

I answered this in #37 and #45, and OP agreed that it makes sense (so I anwsered his unstated deeper question), see #16. Also see #10 for anecdote how some people who jumped directly to Java failed CompSci.

> I'm not sure how spending 1-2 weeks time learning Python before the semester starts will help the OP learn Java (you claim it will but don't give any real evidence).  

It's up to OP to decide, and s/he did, so I don't see where is your beef. Was OP wrong?

> What I don't understand is that when ghostdog asks you to defend your opinion 

It was a talk on some Pycon, I have hard time to find that link. If I will find it, will it change your mind? Will you at least consider it?

> why the discussion deteriorated so quickly between you two.

because of irrelevant awk?

> the question is why you suggested python when it isn't a choice.  

See #49 towards the end

> You then got unnecessarily defensive, put words in ghostdog's mouth, "BTW if you think Java is so good for beginners", and later charged him/her with trolling behavior 

Yes, why we need to talk about awk if nobody cares about it? If it is not trolling, why to mix awk there?

> I will now ask the same question that I originally avoided.  Why do you suggested the OP spend 1-2 weeks learning Python (instead of Java which s/he will be forced to use) when they will be forced to learn and use Java in the course?  What benefit will this give the OP over finding the course's book and beginning to read it and doing some of the questions from the book?

See #10, and #49 (bottom)
[so, if frustrated about java, OP can]
"Hack Python project over the weekend to relieve frustration and prove yourself that it's Java what sucks, not his programming skills?"

"Couple forum members mentioned that they started in C++ and decided that programming is not viable career for them, only to return to programming later, with non-C++ language. Java is little better, but just a little, IMHO. So I promote Python to get them chance to feel what programming fun is, before Java or C++ will make then feel stupid. To save them for programming."

Obviously, looking into book is OK, and forward-looking student like OP will do it.

But IMHO, OP can learn substantially more basic programming skills in 2 weeks in Python - and when learning Java, he can compare and see what are just syntax differences, verbosity and clunkiness of Java.

Or maybe not, I cannot see what will happen. I just gave my honest **opinion**. And looks like some people share it, I am not fringe lunatic.

BTW I appreciate your directing discussion back to topic, and asking relevant questions. I thought I already answered them, but maybe not clearly enough.

---

### Post by pmasiar on 2008-08-18
Bonus link:
[http://pthree.org/2007/05/24/good-advice-for-computer-science-students/](http://pthree.org/2007/05/24/good-advice-for-computer-science-students/) with hardly Python mentioned

OK, bunch of links (but I cannot find that article :-(

[http://oreilly.com/pub/a/oreilly/frank/elkner_0300.html](http://oreilly.com/pub/a/oreilly/frank/elkner_0300.html)
I was having a great deal of difficulty with C++. I was turning off 50 percent of my students.

[http://tech.canterburyschool.org/pycon/teaching_pygame.pdf](http://tech.canterburyschool.org/pycon/teaching_pygame.pdf)
Overall, Python is the best language we have found for introducing programming to
absolute beginners. After our initial trial on one section, we immediately switched the
remainder of our Intro sections to Python with equally positive results. In addition, we
were impressed enough with Python as a teaching language that we immediately started
considering other places in the curriculum where Python would useful.

[http://portal.acm.org/citation.cfm?id=1151869.1151880&coll=GUIDE&dl=GUIDE](http://portal.acm.org/citation.cfm?id=1151869.1151880&coll=GUIDE&dl=GUIDE)
many features of Python facilitated both teaching and learning (for instance, a simple and flexible syntax, immediate feedback, easy-to-use modules and strict requirements on proper indentation).Our findings support results from previous studies in that students have difficulties in dealing with abstract concepts

[http://portal.acm.org/citation.cfm?id=1047887](http://portal.acm.org/citation.cfm?id=1047887)
(Journal of Computing Sciences in Colleges)
discusses Python and its suitability to CS1, CS2 and other advanced computer science courses. As compared to other computing languages, Python has a simpler and more elegant syntax

[http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.12.9253](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.12.9253)
Python, with its high level of abstraction and judicious balance of simplicity, conciseness and versatility, is an excellent choice to introduce the fundamental ideas of the art of programming.

[http://www.ariel.com.au/a/teaching-programming.html](http://www.ariel.com.au/a/teaching-programming.html)
Java enforces Object Orientation, exception checking and strict typing - these are all (arguably) good things - they make it easier for a group of programmers to robustly create large systems. But for small problems (such as those faced in introductory programming classes) these things become nothing more than a complicated, time-sucking burden.

The employment reason alone is sufficient to make Java a "must teach" lanaguage, but I believe we do our students a disservice if this is the best language we show them. 

[http://www.pythonthreads.com/news/latest/python-is-very-powerful,-very-clear-and-easy-to-learn-for-students.html](http://www.pythonthreads.com/news/latest/python-is-very-powerful,-very-clear-and-easy-to-learn-for-students.html)
John Zelle, "languages like Java and C++ were unnecessarily complex for the kind of programming the computer science department wanted to do for beginner-level classes. Something in Java that might take 100 lines to do, I can do in 20-30 lines in Python. Because it takes a lot less writing, it means we can do more.

[http://www.stanford.edu/~pgbovine/python-teaching.htm](http://www.stanford.edu/~pgbovine/python-teaching.htm)
most beginner programmers don't care at all about Computer Science or programming language theory, but rather simply want to get the computer to do what they say with as little overhead and boilerplate code as possible. The less code they need to write, the less errors and bugs they might encounter; the less errors and bugs they encounter, the less likely they are to become frustrated in those crucial early days and give up on programming altogether.

[http://www.stanford.edu/~pgbovine/prog-curriculum.htm](http://www.stanford.edu/~pgbovine/prog-curriculum.htm)
I strongly believe in teaching Python to students as a first language (see here for some reasons) because it's so easy to get started solving small but useful problems with minimal overhead.

---

### Post by slavik on 2008-08-18
stop walking the flaming line, get back to the safe side, or ELSE! ;)

NOTE: not looking for a fight in this one, because Java as a first language is ... a tricky issue.
As for first languages and such. My college recently switched from doing C to C++ in the introductory classes, because they wanted to give students OO later on without switching languages (I remember having to do linked lists in C, then in C++ using pointers and then classes in C++, which IMO was not bad). If that is the college's choice, then I cannot blame them for that.

But then there is another problem. The intro class has formatting as a topic ... trust you me, I would not wish upon anyone to do formatted output in proper C++ using setprec and whatnot (printf is clearly easier in this regard).

IMHO, using Perl/Python/Ruby for a first language is better than C++ or especially Java. Since with the first input program in Java, you have to explain at least 3 things: 1. classes and OO, 2. exceptions, 3. BufferedReader input = new BufferedReader(new InputStreamReader(System.in));

As for the awk code presented in this thread, it is not what awk is meant to do.

For CompSci in general (pmasiar, we've discussed this and I will still disagree on this issue):
teaching C++ first is better than teaching Java first
teaching C first is better than teach C++ first.

For CompSci to get students onto OO ASAP:
Perl/Python/Ruby

---

### Post by CptPicard on 2008-08-18
> **slavik said:**
> 
NOTE: not looking for a fight in this one, because Java as a first language is ... a tricky issue.

Me neither... but it's interesting to see how people feel about the first language issue.

> Since with the first input program in Java, you have to explain at least 3 things:

For the first input program, you read the command line args :)

I have a feeling that we were actually never even specifically taught how to read System.in, you were supposed to figure that out on your own at some point.

> 
teaching C++ first is better than teaching Java first

I wouldn't start with C++ if the intention is not to actually also learn C++ all the way, which is not something I would necessarily aim for as part of a proper Computer *Science* curriculum. Too much "language" there.

Java > C++ in this simply because of resource management and a more minimal, forgiving language. You don't want to force a noob into a debugger, because you actually have stuff to *teach* them that they're supposed to formulate in the language. IMO having a garbage collector and proper stacktraces is a must.

> 
teaching C first is better than teach C++ first.


Okay... teaching C first and not teaching C++ unless as an elective, ok ;)

> 
For CompSci to get students onto OO ASAP:
Perl/Python/Ruby

Why do they need to get to OOP? It sucks... :(

---

### Post by pmasiar on 2008-08-18
First, I want to apologize to ghostdog74. I was completely confused by his offhand 'awk' suggestion, and it took me quite a while to understand that in discussion about what is better first language for a beginner, his opinion is that we should not be concerned so much about what language to begin, his opinion is it does not matter much.

I still disagree with his opinion, but now at least understand it :-)

So awk makes perfectly sense: from POV of ghostdog74, is not better or worse that any other language. So it was more useful to guide me towards his POV than it would be suggesting C++: because awk is so totally non-mainstream and random.

Other thing what confused me is why be even debates about preferences if he does not have any. My guess is that it is to defend evenhandedness of the discussion (as he sees it), but I'll let him to explain himself.

Thanks to hod139 for breaking the cycle of misunderstanding when probably most people just ignored the thread. 

All this allowed me to find out 
- one trick (obvious to most, including me) that is important to state explicitly the unstated assumptions ("explicit is better than implicit", Zen of Python), to make sure we argue about the same thing

- I knew but forgot for a bit, and many, possibly most people are not aware about [The Paradox of Choice: Why More Is Less](http://en.wikipedia.org/wiki/The_Paradox_of_Choice:_Why_More_Is_Less) that giving more choice to someone who has no clear criteria to make selection is counterproductive.

So now I made that part also explicit, and let's consider consequences of that.

**Edit**
I like to express opinions in edgy way, but I am not afraid to say 'sorry' if I believe was too edgy.

So, my apologies to everyone who feels offended.

---

### Post by ghostdog74 on 2008-08-18
> **pmasiar said:**
> Yes, I brought Python for a reason: because I believe it is better intro language for beginners than Java. 

So you admit you mentioned awk as just yet another language, with no real preferences over either Java or Python. 

And you think that having more equal languages to choose from, you make some service to the beginner, right?

and you do seem to forget this that i mentioned in my previous posts that besides OP's technical problems which i can't solve for him, he should concentrate on getting Java into his head. The debate afterwards is when you suggested learning Python before his Java course. I then did not agree with you because IMNSHO ANY language that teaches basic programming concepts can be used. That's why even awk can be used, which i have showed you. 

> 
You might not be aware about another trick which our brain plays on us: [The Paradox of Choice: Why More Is Less](http://en.wikipedia.org/wiki/The_Paradox_of_Choice:_Why_More_Is_Less). If you have too many equal choices with no clear preferences, task to choose is becoming **harder** not easier.

obviously,, we do have a choice here right ? its Java remember? And its not a choice OP can ignore?

> 
> Seriously, i don't really care about your opinion on me. 

You should. And I do care about your opinion - that's why I try to explain myself and dig all those links supporting my opinion, so my opinion could be distinguished from random noise. 

I value your opinion too you know. Just that we think differently. Just take it that I have a broader view on things that i observed.

> 
> Sigh, its strange that you still ask me this when I already referred you to [RTFM](http://www.gnu.org/software/gawk/manual/gawk.html)

RTFM is too much work - I already looked at awk, and you just shown me bland common syntax, nothing to get excited about, or give awk preferences to Perl or Python which I already know. So you did not made a sale today. :-)

so this will the last time i will say to you. those are basic concepts that serves the same purpose and supported in most languages C,Perl,C++,Ruby,Java etc...., not just in Python.  Do you agree with me on this? ( Besides you are not a beginner and nobody is forcing you to learn awk, so i have no obligation to show you what you want. )

> 
> variable declaration doesn't need $,@ or those funny characters that Perl uses, looks much more like C, Python declarations. Easy to read and intuitive? you tell me.

Yes, but that's not enough: I have that in Python already. 


so why is it "wrong" to you that i suggest such as simple language like awk for beginning programming ? Remember, the main character is NOT you. So what comments have you got for me now , since i have shown you how awk(or others) can be used as a beginner programming language?

> 
> my advice, no preference for a particular language. Any that can support beginner concepts will do.

This leaves beginner to pick language at random - which guarantees frustration, 

you seem to forget OP (beginner) has a choice. Its JAva. Python comes in only after you mentioned it. so why is it NOT a problem when Python is mentioned instead of others? Is it "RANDOM"?

> 
See link above. So in your opinion, python is no worse than awk. But in opinion of many others, Python is **better** than say the same awk or Java. So why you would object if beginner learns Python first, if, in your own opinion, Python is no worse? What is the gain? Why to get involved in this endless discussion?

Since when did i say Python is worse than awk ? You are always doing that, putting words in my mouth. We have this endless discussion because you cannot accept the fact that ANY other languages that supports programming concepts for beginner are also suitable to learn before taking up Java. 



> 
You seemingly do no have preference: would you prefer us here in forum just recommend a language in random? .

this is a repeat. I have suggested OP to learn Java, since its not a choice. 
> 
Every language will have own day? C++ on Mondays, awk on Sundays? I still do not see how we can implement your suggestion

Again , putting words in my mouth. If beginner chooses C++, then he can jolly well carry on learning programing with it because all he needs for a beginner is already cater for. Why do you even suggests such an idea of switching languages every other day?

> 
If I do not have any preference in forum discussion, I do not get involved. So I am puzzled why you decided to get involved to prove that we should not care. And how it helps beginner to solve the task of selecting the first language to learn.
i get involved because I have an alternative suggestion to yours. Is that wrong?

---

### Post by LaRoza on 2008-08-18
> **pmasiar said:**
> First, I want to apologize to ghostdog74. I was completely confused by his offhand 'awk' suggestion, and it took me quite a while to understand that in discussion about what is better first language for a beginner, his opinion is that we should not be concerned so much about what language to begin, his opinion is it does not matter much.

So awk makes perfectly sense: from POV of ghostdog74, is not better or worse that any other language. So it was more useful to guide me towards his POV than it would be suggesting C++: because awk is so totally non-mainstream and random.


That is almost my opinion also, but I cannot in my right mind recommend anything but I feel is the swiftest path to getting started. So I don't think there is permanent damage from learning any language as the first for a well motivated person, but I can't use that as an excuse for recommending a non optimal path. Java may be simple to grasp if you know "programming", but it is very difficult and slow to get started with.

---

### Post by ghostdog74 on 2008-08-18
> **slavik said:**
> 
As for the awk code presented in this thread, it is not what awk is meant to do.

so what is awk meant to be? you have to substantiate it.

---

### Post by pmasiar on 2008-08-18
I think that big part of misunderstanding is cleared now, so I'll just ignore most of this. Feel free to reopen anything you want to be cleared

> **ghostdog74 said:**
> you seem to forget OP (beginner) has a choice. Its JAva.

You wanted to say "no choice" I assume

But OP still has choice what to do for next month before classes will start in real. 

And in my opinion that time is best used learning basic of programming in simple language like Python, and I explained why.

> Why do you even suggests such an idea of switching languages every other day?

I was confused that you have no preference for best first language. My question was, what to do next if someone else ask for best first language. Will we start flamewars again? Or, as joke, will we settle that Monday is the Java day?

> i get involved because I have an alternative suggestion to yours. Is that wrong?

No, it is not wrong. It was confusing as hell why you suggested language you do not care about, like awk. I explained it fuller in my other comment.

---

### Post by ghostdog74 on 2008-08-18
> **pmasiar said:**
> 
I still disagree with his opinion, but now at least understand it :-)

Maybe my english is REALLY BAD such that you don't understand. :) however you don't have to apologize you know.:) Nobody is wrong. Just different opinions. Since i can't write any better for you to understand, i will stop here.

---

### Post by ghostdog74 on 2008-08-18
> **pmasiar said:**
> I think that big part of misunderstanding is cleared now, so I'll just ignore most of this. Feel free to reopen anything you want to be cleared
You wanted to say "no choice" I assume

my bad. this is a part of english that confuses right? :)
"no choice" means he has only one choice :)

> 
But OP still has choice what to do for next month before classes will start in real. 

And in my opinion that time is best used learning basic of programming in simple language like Python, and I explained why.

Yes i have no objections with that because that's your view. And i also explained, because its just beginners, ANY language that teaches programming concepts can be used.

> 
My question was, what to do next if someone else ask for best first language. Will we start flamewars again? Or, as joke, will we settle that Monday is the Java day?

hmmm...tell him to bookmark this thread? :) My POV stands clear. if ever anyone else ask such questions again, i will still say there's no best first language. If that language teaches you the basic concepts, then use it. The word "best" only comes in when the beginner reach a higher level of understanding.

ok i will really stop here.

---

### Post by hod139 on 2008-08-18
> **pmasiar said:**
> I answered this in #37 and #45, and OP agreed that it makes sense (so I anwsered his unstated deeper question), see #16. Also see #10 for anecdote how some people who jumped directly to Java failed CompSci.

I missed those posts in the noise; and it doesn't really answer the question.  Convincing a self professed noob to look at python is not the same as providing insight/reason that it will be beneficial (though, you did answer this later).

> 
> I'm not sure how spending 1-2 weeks time learning Python before the semester starts will help the OP learn Java (you claim it will but don't give any real evidence).  

It's up to OP to decide, and s/he did, so I don't see where is your beef. Was OP wrong?
I don't understand this.  I asked you what you think the benefits of spending 2 weeks learning python before java are, and you answer by saying it's the OP choice.  That wasn't my question.

> 
See #10, and #49 (bottom)
[so, if frustrated about java, OP can]
"Hack Python project over the weekend to relieve frustration and prove yourself that it's Java what sucks, not his programming skills?"

"Couple forum members mentioned that they started in C++ and decided that programming is not viable career for them, only to return to programming later, with non-C++ language. Java is little better, but just a little, IMHO. So I promote Python to get them chance to feel what programming fun is, before Java or C++ will make then feel stupid. To save them for programming."

Obviously, looking into book is OK, and forward-looking student like OP will do it.

But IMHO, OP can learn substantially more basic programming skills in 2 weeks in Python - and when learning Java, he can compare and see what are just syntax differences, verbosity and clunkiness of Java.

Or maybe not, I cannot see what will happen. I just gave my honest **opinion**. And looks like some people share it, I am not fringe lunatic.Thanks an answer!!! :)  , this is all the explanation I was looking for.

As an aside, I think python is a fine language, and a very good teaching language.  My only problem with your suggestion of Python in this thread was your firm stance of how a few weeks of Python would be beneficial in a course using Java.  I finally got you to answer this question, and that's all I wanted :).

---

### Post by pmasiar on 2008-08-18
> **ghostdog74 said:**
> if ever anyone else ask such questions again, i will still say there's no best first language. If that language teaches you the basic concepts, then use it. The word "best" only comes in when the beginner reach a higher level of understanding.

That's good compromise.

Now, beginner comes here, reads this thread and asks the obvious question: 

"I believe you that I cannot understand differences between languages until I get into some intermediate level above basic.

Please tell me: What is best and fastest way to get to that higher level, so I will understand that?"

Let's start now, while we are still in tempo and in context :-)

---

### Post by ghostdog74 on 2008-08-18
> **pmasiar said:**
> 

Please tell me: What is best and fastest way to get to that higher level, so I will understand that?"

Let's start now, while we are still in tempo and in context :-)

What's the best and fastest way to reach the 1st floor of a 12th storey building ? 
1) jump down from 12th storey window
2) take the elevator
3) take the stairs

Number 1) satisfy the criteria of "best" and "fastest" but you are surely going to die.
Number 2) seems like the next choice, you can reach fast but its still not the best because things might happen to the elevator that can't bring you to the 1st floor
Number 3) , what do you think ?


Same applies to programming. Btw, if you really want to continue, I think you should repost this to some other forums meant for this kind of discussion. WE should really stop here.

---

### Post by pmasiar on 2008-08-18
> **ghostdog74 said:**
> What's the best and fastest way to reach the 1st floor of a 12th storey building ? 

Those are false choices. In real life, we expect to survive, and there is no firealarm or 9/11, so just take elevator. Single choice.

> Same applies to programming. 

But you yourself admitted that there are many seemingly equivalent (for you) languages - and even if you cannot prefer any single language, most people do sugest Python in this role. 

So your suggestion leaves beginner to struggle and choose at random (which as I said at link above is source of frustration). Is it what you think is right? Or you do not believe that too much choice can be source of frustration?

---


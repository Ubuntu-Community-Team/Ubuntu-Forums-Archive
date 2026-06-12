---
title: "Code::blocks"
date: 2010-04-16
forum: Programming Talk
---

### Post by orphanlast on 2010-04-16
Okay, I've done a little research and I found out that code::blocks is the most common IDE for programming stuff with C++ while using a Linux system.

I've gone from one site after another to try and establish a basic knowledge of C++ and code::blocks.

Unfortunately, I'm poor as hell. I can't buy any books. But where do you think would be the best places where I could learn how to not only learn how to use code::blocks but also get a working knowledge of C++

---

### Post by bwhite82 on 2010-04-16
[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

[http://www.google.com/#hl=en&source=hp&q=free+programming+ebooks&aq=f&aqi=g4&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f](http://www.google.com/#hl=en&source=hp&q=free+programming+ebooks&aq=f&aqi=g4&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f)

---

### Post by lisati on 2010-04-16
Sometimes the local library is a useful resource. A few months back I picked up a copy of a book on C++ for $1 that my local library had removed from its collection. It even came with a CD! 
(Mental note to self: get back to reading it!)

Moved to "Programming talk"

---

### Post by azagaros on 2010-04-16
One I don't find code::blocks good on linux.  Codelite is better.  If I was on windows Codelite would be my choice especially for the beginner of C++.  Codelite runs on both windows and Linux platforms.

I use code::blocks on windows, and codelite on linux.

Learning C/C++ is all over the web.  cplusplus.com or org is a source for c++ programming.  There are others out there.  Hitting the development sections of this forum is a good place to start too.  Pulling up a google search might bring in a few I don't know about.

The books you can check out from most libraries if you look for them and if you have access to a campus library might be your best choice.

On the forums you might catch someone like me that can try to balance out the abstractions of C++.  I personally been doing c++ for about 17years.

Hope that puts some light to things.

---

### Post by orphanlast on 2010-04-16
Dang... I wish people could just explain this stuff in simple terms. Just the "Hello World" program doesn't make any sense, even after I read the so called explanation for it over and over again.

How about this. I remember learning HTML and then after learning it in school, the teacher showed us the web development application "Dreamweaver" which made is to that you weren't entirely required to make a website using code.

Is there anything similar to a web development application... more like a C++ development application where you work with an actual GUI instead of work with confusing code?

Or is that a program that I'm just going to have to learn because I'm so disgusted with C++?
[]("http://en.wikipedia.org/wiki/Application_software")

---

### Post by Arla on 2010-04-16
Not sure if this is the right forum for it or not, honestly if you find the normal explinations for Hello World programs confusing as hell, then your days as a programmer are severely numbered (IMHO) and please don't take that as a slight, some people just aren't cut out to be programmers.

Perhaps give us some background, what are you trying to program and why did you choose C++?

---

### Post by matthew.ball on 2010-04-16
Well, ask questions.

I'm going to assume the "Hello, World" you speak of was similar to this: (it's actually C++ despite being labelled as PHP, just ignore that for now)

[php]
#include <iostream>

using namespace std;

int main() {
  cout << "Hello World!" << endl;
  cout << "Welcome to C++ Programming" << endl;
  return 0;
}[/php]

What don't you understand about it? To be entirely honest, there's not a lot going on here...

Edit: If you're dead-set on going the C++ route, find some books (there are plenty available online) and read. If not, maybe have a look at [Python]("http://docs.python.org/tutorial/").

---

### Post by orphanlast on 2010-04-17
[COLOR=#000000][COLOR=#FF8000]#include <iostream> 

**[COLOR=Black]From what I understand, #include means open a specific folder called iostream. [/COLOR]**

[/COLOR][COLOR=#0000BB]using namespace std[/COLOR][COLOR=#007700]; 

[COLOR=Black]**From what I understand, the blue text is some key information that you're relaying to the computer... I think they're called "functions". But really, when people and every single tutorial just jumps in steeped in terminology it's really easy to get lost. From what I've researched, all these things written in blue text  can changed if you'd like to, after you tell the computer to run iostream you're telling it you want to write in it's specific coding. I have no idea what namespace is and  all I know about STD is that it's not talking about a VD.**[/COLOR]

[/COLOR][COLOR=#0000BB]int main[/COLOR][COLOR=#007700]() { 
  [/COLOR][COLOR=#0000BB]cout [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#DD0000]"Hello World!" [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#0000BB]endl[/COLOR][COLOR=#007700]; 
  [/COLOR][COLOR=#0000BB]cout [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#DD0000]"Welcome to C++ Programming" [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#0000BB]endl[/COLOR][COLOR=#007700]; 
  return [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]; 
} 

[COLOR=Black][B]All I know is that MAIN has to be in every single thing that you need to tell the computer to do.

I have no idea what int means nor what () is doing. I do however know that {}'s are somewhat like quotations. They're used to communicate to the computer what it's supposed to do.

Something you didn't type in. I know that // is used whenever you're working with a team of programmers and you want to leave some notes in the code so that they know what you're thinking about or needing to have done without effecting the program.

I think cout means compile out. I don't understand what << is all about. I know that after you establish both of those things within {} you can use "" in order to display text. In this case, you just want to show the words "Hello World"

; is used to end a specific process.

I don't understand endl and I don't know what return 0 is.

I've been told that I should probably start off with something like VB, from my research I've figured that Mono is probably the best compiler that I can use for pretty much any programming on Linux. What do you think? And where would be some good tutorials to learn how to use Mono while using VB?

[/B][/COLOR][/COLOR][/COLOR]

---

### Post by matthew.ball on 2010-04-18
So, in programming, there are *types*. These allow us to talk about a specific object as if it has some expected properties.

In standard C (and C++) there are a few basic primitive types: [FONT="Courier New"]int[/FONT], [FONT="Courier New"]float[/FONT] and [FONT="Courier New"]char[/FONT] (this list is not exhaustive). It should be fairly obvious what each type corresponds to.

Variables have a type. Functions have a type.

You are correct, every C++ program needs a [FONT="Courier New"]main[/FONT] function at some point. This tells the computer where the program starts running. The [FONT="Courier New"]int[/FONT] before the function name says what type the function is, in this case it is an integer, so we expect at some point the function to return an integer to signal it has finished (usually, one would return a 0 to indicate the program has successfully finished, while returning an integer that is not 0 would symbolise an error has occurred at some point).

Following the function name we have (in the parentheses) a list of arguments that function accepts. In this example, there are no arguments, and this is expressed by the parentheses being empty. In standard C (and I guess C++) a program's [FONT="Courier New"]main[/FONT] function implicitly takes two arguments [FONT="Courier New"]int argc[/FONT] and [FONT="Courier New"]char *argv[][/FONT]. I'm not going to explain what either of these do, there are tutorials online which explain this ([example]("http://c-faq.com/~scs/cclass/notes/sx13.html")).

The curly braces ({'s and }'s) define the "scope" of a function (and consequently a program) basically, the say everything that happens after the { block, but before the } block belongs to the function defined prior to the entire block. In our example, this says that the three executable statements (the two [FONT="Courier New"]cout[/FONT] statements and the [FONT="Courier New"]return[/FONT] statement) all belong to the [FONT="Courier New"]main[/FONT] function.

A // token is a single line comment, while an opening /* and a closing */ are used when you want to have your comment span multiple lines. Both of these are ignored entirely by the compiler but they make the job easier for us as developers.

The <<'s are used by [FONT="Courier New"]cout[/FONT], this is an object which takes an argument (a string, usually) via << and prints it to standard output. This is how we print to a terminal in C++, and this is why we [FONT="Courier New"]#include[/FONT]d [FONT="Courier New"]iostream[/FONT] at the start, indeed [FONT="Courier New"]iostream[/FONT] is actually just another C++ source file - in C++ lingo it is a "header" file. Basically, this explains to C++ how to print output and receive input. This also defines [FONT="Courier New"]endl[/FONT], which is used to denote and end of line, if we didn't print out the two [FONT="Courier New"]endl[/FONT]'s the program's output would all appear on the same line. When we declared [FONT="Courier New"]using namespace std;[/FONT] at the start, basically we said we wanted to use functions/objects defined in [FONT="Courier New"]iostream[/FONT], as if we had defined them ourselves. Had we not written this statement down, we would have to write each output statement as [FONT="Courier New"]std::cout[/FONT] and each end line character as [FONT="Courier New"]std::endl[/FONT] ([FONT="Courier New"]std[/FONT] as a shorthand for standard). I haven't explained why you would do this, and please read some of the many books available. I'm just trying to introduce you to this so you can pick it up and take it further on your own.

You use a ; at the end of each executable statement. So following from earlier, in our [FONT="Courier New"]main[/FONT] function, there are three executable statements, and a ; follows each statement.

To be honest, I would recommend starting with [Haskell]("http://en.wikipedia.org/wiki/Haskell_(programming_language)"), but it's so different to what I have just explained, and everything you will be learning, that I don't think so unless you're *very* keen for programming as a future career. In terms of an imperative language I would start with C, it provides the building blocks for C++ (technically, I only know C) and is the syntax used by many languages.

I would learn [emacs]("http://www.gnu.org/software/emacs/"), learn [gdb]("http://www.gnu.org/software/gdb/"), and learn everything about gcc you can find (don't start using an IDE until you can explain exactly why you would want to use an IDE). Honestly, programming is going to be a continual learning exercise for anyone - this is why so many people enjoy it I presume. I've been playing with C for about 6 years now, and I still find myself learning (and importantly, needing to learn!) new things constantly.

If I have just confused you even more, please ask more questions, and hopefully I (or another more experienced member) can provide a better answer. I have only summarised what I know and as I said earlier, technically I only know C, so a lot of what I have just posted could be flat out wrong. I would recommend the books ["The C Programming Language"]("http://en.wikipedia.org/wiki/The_C_Programming_Language_(book)") by Brian Kernighan and Dennis Ritchie, and if you're interested in sticking with C++, try: ["Thinking in C++"]("http://www.planetpdf.com/developer/article.asp?ContentID=6634") by Bruce Eckel (which should be available free online, but his page doesn't appear to be responding at the moment). I also said nothing about Python, which you might want to look into too.

---


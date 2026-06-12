---
title: "I want to learn C++. How?"
date: 2007-05-06
forum: Programming Talk
---

### Post by volksolwagen57 on 2007-05-06
I've been looking for references to how to learn to program in C++. I know I need a compiler for a program to run, so I downloaded and installed the Intel C++ compiler for linux. I'm trying to follow an online tutorial that seems to be most promising from what I've searched: [http://www.cprogramming.com]("http://www.cprogramming.com")
The only thing I'm confused about is where does the compiler fall into play? I followed the instructions for creating a simple program:
> #include <iostream>

using namespace std;

int main()
{
  cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  cin.get();

  return 1;
}
How do I use it? I have a basic idea of what these things do like the ```
cout<<
``` command lets you display text and > \n lets it continue to the next line and such. How do I run it? I want to get a heads up on this because I need to learn as it is a pre-requisite for my engineering major. Could someone tell me of another resource to teach myself to program in C++? Thanks for your time.

---

### Post by volksolwagen57 on 2007-05-06
I've been looking for references to how to learn to program in C++. I know I need a compiler for a program to run, so I downloaded and installed the Intel C++ compiler for linux. I'm trying to follow an online tutorial that seems to be most promising from what I've searched: [http://www.cprogramming.com]("http://www.cprogramming.com")
The only thing I'm confused about is where does the compiler fall into play? I followed the instructions for creating a simple program:
```
#include <iostream>

using namespace std;

int main()
{
  cout<<"HEY, you, I'm alive! Oh, and Hello World!\n";
  cin.get();

  return 1;
}
```
How do I use it? I have a basic idea of what these things do like the ```
cout<<
``` command lets you display text and ```
\n
``` lets it continue to the next line and such. How do I run it? I want to get a heads up on this because I need to learn as it is a pre-requisite for my engineering major. Could someone tell me of another resource to teach myself to program in C++? Thanks for your time.

---

### Post by Tuna-Fish on 2007-05-06
As for compiling: What you have typed up there is not yet something your machine can run. Computers only understand their native machine language, which is in binary. While comprehending that language directly is possible for humans, (and 50 years ago or so all programs were written directly in it), it is so hard and takes so much time that it would take ages to write any meaningful software in it. Instead, we write programs in languages meant to be easy to understand and write, and a compiler turns it (trough several intermediate states) into the native machine language of the computer.

to execute that, first compile it ( g++ name_of_the_file), then give the file that produced (a.out by default) executable permissions and run it.

to actually learn to program, I'd suggest not starting with c++, it's not among the simplest or easiest of languages. Try Python first, to learn it look at the stickies of this forum.

---

### Post by rapolas on 2007-05-06
you should execute in terminal: g++ your_source_file.cpp -o output_file_name 
and after that you should get a file, called output_file_name and you can execute it with command: ./output_file_name

---

### Post by gm__ on 2007-05-06
Go to Mr Google and type : c++ tutorial :)

---

### Post by M$LOL on 2007-05-06
If your file is called HelloWorld.cpp then:

g++ HelloWorld.cpp -Wall -o HelloWorld

Then in Terminal:
./HelloWorld

-o HelloWorld means that HelloWorld will be the output file, so if you said

-o ubuntu

ubuntu would be the executable.

-Wall gets it to report all errors so you'll know where you went wrong.

---

### Post by volksolwagen57 on 2007-05-06
thanks guys. i've heard python was amongst the easiest languages to learn so I'll try that, for now. And M$LOL, I love your signature, man, seriously lol.

---

### Post by phossal on 2007-05-06
I suggest learning C. It's a fairly small, tight language. In its basic form, it isn't ridiculously complicated. But it's more complicated than others, which will make your investment profitable when you can slide back down the learning curve to languages like Python. It is a subset of C++, which will help you move that direction, and it will aid you in learning Assembly, if you need that. I started with Java, but I feel C would've worked well, too. For a non-web programmer - someone in electrical engineering, etc - I think C is a better choice.

More important, get a *good* book. It's just too difficult to learn from the web, I think.

---

### Post by bapoumba on 2007-05-06
@ volksolwagen57: merged your two threads in here.

---

### Post by M$LOL on 2007-05-06
> **volksolwagen57 said:**
> thanks guys. i've heard python was amongst the easiest languages to learn so I'll try that, for now. And M$LOL, I love your signature, man, seriously lol.
Thanks. :)
> **phossal said:**
> I suggest learning C. It's a fairly small, tight language. In its basic form, it isn't ridiculously complicated. But it's more complicated than others, which will make your investment profitable when you can slide back down the learning curve to languages like Python. It is a subset of C++, which will help you move that direction, and it will aid you in learning Assembly, if you need that. I started with Java, but I feel C would've worked well, too. For a non-web programmer - someone in electrical engineering, etc - I think C is a better choice.

More important, get a *good* book. It's just too difficult to learn from the web, I think.

C is the best to start with but definitely learn C++ afterwards. It's object oriented, and you'll need that if you're ever working on a big project or an advanced program.

Meh, I learned a lot off the web. A combination of both is good I'd say.

---

### Post by forsaken_pariah on 2007-05-06
C and C++ are very powerful languages but they're relatively difficult for beginners to learn. If you don't really need the extra power offered by C or C++ I'd recommend starting with Python, but if you do, I'd recommend learning C first as it's much easier to learn and then move toward C++ as most of the books for C++ are geared toward those already experienced in C.

---

### Post by LaRoza on 2007-05-07
If you want a good (free) place to learn C++ try:

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

C++ is not the easiest language in the world, but learning it makes learning other languages a lot easier.

---

### Post by RedSquirrel on 2007-05-07
> **volksolwagen57 said:**
> I want to get a heads up on this because I need to learn as it is a pre-requisite for my engineering major.

> **volksolwagen57 said:**
> i've heard python was amongst the easiest languages to learn so I'll try that, for now.

That's a good choice. Like phossal, I would also suggest C. As long as you get *some* understanding of programming you will feel more comfortable in your C++ in engineering, IMO.



> **phossal said:**
> More important, get a *good* book. It's just too difficult to learn from the web, I think.

I agree. If one picks up an "authoritative reference", then they also learn the best practices and they can get a thorough understanding (which they will need when it's time to build some nontrivial apps).

For C, my suggestion is "The C Programming Language" by Kernighan & Ritchie.

---

### Post by M$LOL on 2007-05-08
> **forsaken_pariah said:**
> C and C++ are very powerful languages but they're relatively difficult for beginners to learn. If you don't really need the extra power offered by C or C++ I'd recommend starting with Python, but if you do, I'd recommend learning C first as it's much easier to learn and then move toward C++ as most of the books for C++ are geared toward those already experienced in C.

C is simple to learn. C++ is the hard one because you have to deal with objects. But C is by no means a difficult language, look at assembly if you don't believe me.

---

### Post by forsaken_pariah on 2007-05-08
> **M$LOL said:**
> C is simple to learn. C++ is the hard one because you have to deal with objects. But C is by no means a difficult language, look at assembly if you don't believe me.

I know C isn't really all that hard to learn; it was the second language I learned,  and I learned 68k assembly to write games for my calculator so I know what a hard language is like, I'm just trying to say Python is a lot easier for a first language.

---

### Post by daxumaming on 2007-05-09
I'm not really into "this is better" or "this is easier to learn" but I guess if you really want to learn C++, then do it. I mean, it's a life-skill and going through unnecessary languages won't really help you out. Back in school, we were required to go through Basic and Assembly and I heard that's still being implemented. The thing is, I won't use Basic or Assembly, I never did find any use for them. I taught myself C++. There's way lot of tutorials and resources available on the internet, use that to your advantage. 

People might suggest that you need to go through an easier programming language so you could develop skills in rules, workflows, and structuring. Guess what, you could learn all that in C++ too. Learning another language just to learn structuring and then move on to C++ would take a hell of a lot longer as compared to googling "C++ Tutorials", firing up Kate, and following the tutorials. Stroustrup himself doesn't recommend learning C before C++ since "The better one knows C, the harder it seems to be to avoid writing C++ in C style, thereby losing some of the potential benefits of C++" [1]

One more thing, C++ is a good first language to learn. It'll be really hard if you do it yourself, so better find someone to study this with you. There are C++ newbie communities and you could sign up on their mailing lists, or use their forums. I'm pretty sure some C++ tutorial sites has already established a community, try participating.

[1] The C++ Programming Language, 3rd Edition, Bjarne Stroustup, Section 1.6.1, page 14

---

### Post by siiib on 2007-05-09
no guys sorry but have to disagree.. all this learn python ..learn c..learn java.. don't.. learn c++ straight off the bat.. its not that difficult but youhave to apply yourself.. theres plenty of books tutorials.. the main problem i had learning c++ coming from a procedural (cobol.. c) background is that i couldn't think in objects.. took me ages to get my head round it.. i still have to step back sometimes now.. so don't load yourself down with the baggage.. there is more to coding than just typing lines.. for bigger projects you need to be able to think 'design'.. put it this way.. the best way to learn computer games is to stick it on hard straightaway and get hammered for a couple of days.. that way you learn faster.

---


---
title: "Need some directions for programming"
date: 2007-09-28
forum: Programming Talk
---

### Post by iiieckiii on 2007-09-28
Hi, I'm new to the linux world and programming, I've just installed Ubuntu 7.04 and just learned how to dual-boot  using 2 HD's. I have decided that I want to learn C (seeing I have a book on C already) and then C++ afterwards. I just need to know what I need to get started, is there a certain program(s) that I need that didn't come pre-installed with Ubuntu? Please help a noobie get started and thanks for the help in advance!

---

### Post by Sniffer on 2007-09-28
See the sticky above:

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)


By the Python is my Fav.

Sniff

---

### Post by MicahCarrick on 2007-09-29
I program Linux applications using C and the GTK+ libraries for my GUI applications. I have a tutorial on this: [Tutorial: Simple Gnome Application Using libglade and C/GTK+]("http://www.micahcarrick.com/03-02-2006/gnome-programming-tutorial.html")

I go back and forth between using Gedit for coding and Anjuta IDE. The reason I go back and forth is there was some time that Anjuta 1.x was out of date and 2.x was too unstable. However, I've just installed the newest version this week and it seems to be working quite nicely.

Anjuta is nice for a beginner as it takes care of the build stuff to compile and install your project.

A GUI can be built visually using Glade Interface Designer. This generates an XML file which can be parsed through C calls in your code to dynamically build your user interface.

A couple of books worth checking out should you want to program GTK+ applications using C are Foundations of GTK+ Programming and The Official GNOME 2 Developer's Guide.

Good luck!

---

### Post by Wybiral on 2007-09-29
> **iiieckiii said:**
> Hi, I'm new to the linux world and programming, I've just installed Ubuntu 7.04 and just learned how to dual-boot  using 2 HD's. I have decided that I want to learn C (seeing I have a book on C already) and then C++ afterwards. I just need to know what I need to get started, is there a certain program(s) that I need that didn't come pre-installed with Ubuntu? Please help a noobie get started and thanks for the help in advance!

You'll need your headers and such, from the "build-essential" package, so terminal this:

```

sudo apt-get install build-essential

```

Then you'll be ready to dive into using GCC.

For a quick example, save a C source file as "something.c" and then compile it from the commandline with:

```

gcc something.c -o my_program

```

And the file "my_program" will pop out (the resulting executable), if not, it will spit out some errors meaning the code is wrong.

Be cautious of your C resources as older books/tutorials won't work these days (if you see a "void main()", that's a good indication).

EDIT:

BTW, if you're REALLY new to Linux, you execute your executable from the terminal using:

```

./my_program

```

And "something.c" and "my_program" were just examples :)

---

### Post by scruff on 2007-09-29
Here are some free resources I used to learn to program in a few different languages (would have just linked to my site where all this info is, but it's down at the moment)


**Perl**
[Beginning Perl]("http://learn.perl.org/library/beginning_perl/") by Simon Cozens is an excellent full-length book for those looking to learn their first programming language and for more experienced programmers just getting into Perl. This is a full online book in PDF format.


**Shell Scripting**[URL="http://www.icon.co.za/~psheer/book/"]
The Rute Users Tutorial and Exposition[/URL] is a HUGE book on every aspect of Linux system administration, including Shell Scripting and other types of Linux programming. Awesome book!!
[URL="http://www.tldp.org/LDP/abs/html/"]
The Advanced Bash-Scripting Guide[/URL] is an excellent resource for getting started in shell scripting. The title claims "advanced" but as the author states "This tutorial assumes no previous knowledge of scripting or programming, but progresses rapidly toward an intermediate/advanced level of instruction" making it a good place for anyone to start.

Daniel Robbins, the creator of Gentoo, wrote [Bash by Example]("http://www-106.ibm.com/developerworks/library/l-bash.html") for IBM DeveloperWorks. Here he uses Gentoo's ebuilds to illustrate various techniques.


**Python**
A great first language to learn as it is easy to read with super clean syntax. Recommended by super-hacker Eric Raymond as the first one to learn.

[How to Think Like a Computer Scientist]("http://www.ibiblio.org/obp/thinkCSpy/") is a great online book for learning Python. Also a good book if this is your first attempt at learning a language
[URL="http://www.python.org/doc/Intros.html"]
Python.org's Introductory Material on Python[/URL] has plenty of tutorials for the beginner and experienced alike.


**The C language**[URL="http://www.le.ac.uk/cc/tutorials/c/"]
Intro to C Programming[/URL] is a decent tutorial for getting familiar with C fundamentals.

[Another thorough C tutoria]("http://www.its.strath.ac.uk/courses/c/")l with emphasis on using it in a UNIX environment.


I'm into C++ now and it's rapidly becomming my fav. There are good sites for that too ([cplusplus.com]("http://www.cplusplus.com/")), but 2 excellent **non-free **books are - The C++ Programming Language  (Bjorn Stroustrup), and even better for newbies - C++ How To Program by H.M. Deitel

---

### Post by Compyx on 2007-09-29
> **scruff said:**
> 
<snip>
**The C language**[URL="http://www.le.ac.uk/cc/tutorials/c/"]
Intro to C Programming[/URL] is a decent tutorial for getting familiar with C fundamentals.

[Another thorough C tutoria]("http://www.its.strath.ac.uk/courses/c/")l with emphasis on using it in a UNIX environment.
<snip>


Best to stay away from those, they're both horrible.

---

### Post by Wybiral on 2007-09-29
> **Compyx said:**
> Best to stay away from those, they're both horrible.

I have to agree.

Notice how both of them use "main()" instead of "int main()" and how main doesn't always return something, both of which are really bad practice. It's best to look at the newest tutorials/books and make sure they're c99 compliant.

---

### Post by pmasiar on 2007-09-29
You are free to learn C first, but many experts suggest to learn Python as first language, and you can learn C later. Python is much simpler, takes care of many things which you need to handle yourself in C.

Wiki in my sig has links to get you started.

---

### Post by slavik on 2007-09-30
> **pmasiar said:**
> You are free to learn C first, but many experts suggest to learn Python as first language, and you can learn C later. Python is much simpler, takes care of many things which you need to handle yourself in C.

Wiki in my sig has links to get you started.
Ok, please stop. He asked about C, not Python. Would you like me to pimp Perl every time someone asks a question about Python?

---

### Post by Wybiral on 2007-09-30
> **slavik said:**
> Ok, please stop. He asked about C, not Python. Would you like me to pimp Perl every time someone asks a question about Python?

I don't see how it hurts... He/she could have not known that Python was an option. Now they do. No harm done.

---

### Post by slavik on 2007-09-30
> **Wybiral said:**
> I don't see how it hurts... He/she could have not known that Python was an option. Now they do. No harm done.
"I have decided that I want to learn C"

A decision has been made already. It wasn'y "What language should I learn," it was "How can I get started with C?"

Why don't we say "use Linux" every time someone asks how to install a driver in Windows or how to do something? Because it doesn't solve the problem.

But this discussion is not for this thread. I am sorry to the OP if this seems like a thread hijacking.

Also, to help the OP out, try to get your hands on The C Programming Language 2nd ed. by Kernighan and Ritchie (creators of C).

---

### Post by Wybiral on 2007-09-30
> **slavik said:**
> "I have decided that I want to learn C"

A decision has been made already. It wasn'y "What language should I learn," it was "How can I get started with C?"

Why don't we say "use Linux" every time someone asks how to install a driver in Windows or how to do something? Because it doesn't solve the problem.

Irrelevant... If someone posts something like "I want to start programming by diving directly into writing the game engine for a graphically intensive MMORPG" I would probably suggest they start with "Hello world". This is natural and I don't see anything wrong with someone suggesting a simpler alternative (even if it slightly varies from the original questions).

It's a public forum, where we can all offer some advice that may directly or indirectly help the OP out. Personally, I don't think it matters whether they learn C or Python first. But maybe they had never been exposed to Python. They might find it to be a useful side comment.

I don't really understand your need to censor the forums. There are moderators for that.

---

### Post by Compyx on 2007-09-30
> **slavik said:**
> 
Also, to help the OP out, try to get your hands on The C Programming Language 2nd ed. by Kernighan and Ritchie (creators of C).

Now that's what I call excellent advise!

Nitpick: Brian W. Kernighan didn't create C, that was all Dennis Ritchie's work. Kernighan however is a co-creator of AWK (the K stands for Kernighan).
Kernighan is also credited for the first 'hello, world' program, no small feat :)

To the OP: once you read and studied K&R2, you might consider picking up 'Expert C Programming - Deep C Secrets' by Peter van der Linden. Another great book and humorous too.

Keep in mind that although K&R usually write 'main()' in stead of 'int main(void)', they have acknowledged the first form (implicit int, unspecified number of arguments) was indeed wrong and they should have used the second form throughout the book. (Sorry, can't find a reference to that right now).


Anyway, have a good time coding in C, I know I always have ;)

---

### Post by pmasiar on 2007-09-30
> **slavik said:**
> Ok, please stop. He asked about C, not Python. Would you like me to pimp Perl every time someone asks a question about Python?

Pimping Perl would make no sense, Perl is horrible for a beginner. Better than C maybe, but nearly not as good as Python. Why you would inflict Perl on a beginner? 

Slavik, it is not **my** fault that you prefer Perl, language which usage is shrinking and it's user are moving to Python and Ruby.

---

### Post by MicahCarrick on 2007-09-30
Obviously, opinions will vary greatly over which language is "best" for beginners and it's a question to which there is no answer. The best a new programmer can do is read up a little on his options and then make a decision based on the time they can invest, what they want to accomplish, and they're interests. 

I absolutely love C programming, and I only started programming in C relatively recently. I came from a win32 VB background. Hardly a "hardcore" Linux guru. But, that doesn't mean I don't use other "easier" languages. I do all the time. I frequently use Python, Ruby and BASH scripting.

If you have the interest to learn C, by all means, learn C. It will only make you stronger in languages which do the work for you (by understanding *what* they are doing). That's one reason many CS cources still spend a few terms learning ASM and the basic electronics concepts employed by computer systems.

Okay, that said, here's my C advice. As has been said time and time again, purchase a copy of the K&R C Programming 2nd Ed.

Understanding function prototypes will help you understand what functions do just by looking at header files. Also focus on understanding how to read the [The GNU C Library Manual]("http://www.gnu.org/software/libc/manual/html_node/index.html"). 

Any new bit of code or declarations you come across, ask here or in a C newsgroup/mailing list. If you find a snippet or program that you seem to know how/when to use, but don't know why--ask.

---

### Post by slavik on 2007-09-30
> **Compyx said:**
> Now that's what I call excellent advise!

Nitpick: Brian W. Kernighan didn't create C, that was all Dennis Ritchie's work. Kernighan however is a co-creator of AWK (the K stands for Kernighan).
Kernighan is also credited for the first 'hello, world' program, no small feat :)

To the OP: once you read and studied K&R2, you might consider picking up 'Expert C Programming - Deep C Secrets' by Peter van der Linden. Another great book and humorous too.

Keep in mind that although K&R usually write 'main()' in stead of 'int main(void)', they have acknowledged the first form (implicit int, unspecified number of arguments) was indeed wrong and they should have used the second form throughout the book. (Sorry, can't find a reference to that right now).


Anyway, have a good time coding in C, I know I always have ;)
well, they did both work on UNIX so that they could play a game ... hear that? UNIX WAS WRITTEN TO PLAY GAMES!!! :-P

---

### Post by pmasiar on 2007-10-01
> **MicahCarrick said:**
> Okay, that said, here's my C advice. As has been said time and time again, purchase a copy of the K&R C Programming 2nd Ed.


"Big Blue C" is excellent book for programmers who just need to pick up C syntax. It is absolutely **terrible** as a beginner book IMHO. Just try and see yourself.

As I found, many experienced programmers give **exactly same advice** for a beginner and for experienced programmer. Funny, how you can trust their advice if they don't get even that simple difference?

---


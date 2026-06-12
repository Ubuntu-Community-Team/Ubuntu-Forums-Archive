---
title: "Programming in C: system( &quot;pause&quot;)"
date: 2012-01-11
forum: Programming Talk
---

### Post by Zaytuun on 2012-01-11
Hey guys,

I've just started a programming in C class and I have a problem that I'd like a few opinions on.

I've been using gcc to compile my programs and terminal to run them, I've been playing around with c for a couple of months now and feel like I've learned quite a bit.

I just started class yesterday and my professor uses DevC++ He told us that whenever we write a program we should use the stdlib.h header file (all good there, I've only been using the stdio.h but just a change of names I guess, I do have the stdlib.h file on my computer) and also to always put ```
system("pause")
``` before function main's return.

My code will compile with system pause, but it barks at me a bit. It doesn't like it really. Also, the program won't actually "pause" the program just runs and ignores the system pause.

From what I've read, this is basically a windows dependent thing and its use is not recommended because how it acts will vary system to system. 

Thoughts?

P.S. This professor was showing us all his wallet and how much money was in it and what not blah blah "be like me" but he accidentally erased his code from his editor and got confused like 3 times, sigh.

---

### Post by cgroza on 2012-01-11
You could use the getchar() function to make the program wait for input.

---

### Post by Zaytuun on 2012-01-11
Hmmmmm, that worked much nicer. I'll talk to him about it in class tomorrow. Maybe I'll precede it with printf("Program complete, return to exit") or something so there's no confusion, I have a feeling he's the kind of person to give you a hard time though. 

Also, oddly, he told us to use the stdlib header but didn't mention we need stdio.h as well, he made it seem like we ONLY need stdlib.h for things like printf........ I figured it out pretty quickly, but I know there's some poor liberal arts major in the class wondering what the hell is going on lol.

---

### Post by lisati on 2012-01-11
I would have thought that the getchar() route (or similar) would lend itself to portability better. Having said that, maybe this is a way of introducing you to using CLI-based commands from within your program.

---

### Post by cgroza on 2012-01-11
I would say getchar is better to achieve this result because it does not depend on any platform and it is included in the standard library.

His way of doing things is common, but it relies on external and platform dependent features.

---

### Post by Bachstelze on 2012-01-11
> **Zaytuun said:**
> 
Also, oddly, he told us to use the stdlib header but didn't mention we need stdio.h as well, he made it seem like we ONLY need stdlib.h for things like printf........ I figured it out pretty quickly, but I know there's some poor liberal arts major in the class wondering what the hell is going on lol.

stdlib.h and stdio.h define different things. Sometimes you will need one, sometimes the other, sometimes both, sometimes (rarely) none. It all depends on what you use in your program: when you use something, you must include the header that defines it. For functions, the man page will tell you which header defines it.

---

### Post by Zaytuun on 2012-01-11
> **lisati said:**
> I would have thought that the getchar() route (or similar) would lend itself to portability better. Having said that, maybe this is a way of introducing you to using CLI-based commands from within your program.

This is an introductory C course. Our assignment was Hello World lol. I just think having a phd and all he'd think about the issues system("pause") could potentially cause.... especially since getchar seems like a much more stable way to do things. But no worries, got it figured out. Thanks for your input!

---

### Post by Zaytuun on 2012-01-11
> **Bachstelze said:**
> stdlib.h and stdio.h define different things. Sometimes you will need one, sometimes the other, sometimes both, sometimes (rarely) none. It all depends on what you use in your program: when you use something, you must include the header that defines it. For functions, the man page will tell you which header defines it.

Yeah I figured that out pretty quick when i was getting error messages during compilation. I didn't get into any details about header files in my independent studying, and we're not at the point in the course yet either (we just did hello world) but I went and opened up a few header files and read through them and got the gist of what they're doing.

I didn't realize there was man pages for functions. Thanks for the info.

---

### Post by trent.josephsen on 2012-01-11
> **Zaytuun said:**
> This is an introductory C course. Our assignment was Hello World lol. I just think having a phd and all he'd think about the issues system("pause") could potentially cause.... especially since getchar seems like a much more stable way to do things. But no worries, got it figured out. Thanks for your input!

Having a PhD probably means he's an academic from the mathematical realm and has never written a line of useful code in his life.  There are a lot of those in computer science, unfortunately.

Using getchar() is a better way to do the same thing, but I might also point out that it's solving a problem that shouldn't exist.  Ideally you should be able to examine a program's output after it has terminated without having to resort to annoying tricks.

This semi-angry rant of bitterness brought to you by Sleep Deprivation (tm).

---

### Post by fct on 2012-01-12
> **trent.josephsen said:**
> Having a PhD probably means he's an academic from the mathematical realm and has never written a line of useful code in his life.  There are a lot of those in computer science, unfortunately.


Academics from the mathematical realm actually do write pretty useful lines of code.

Whether they write them in a portable, standard, optimal way is quite a different thing.

In Zayhuun's case, it's not really clear that the teacher isn't actually a PhD on computer science. I've had CS teachers I wouldn't let near a keyboard teach me intro to programming, and had to wait for advanced courses like OOP to get teachers who would actually survive in the software industry if they wanted to.

---

### Post by Zaytuun on 2012-01-12
> **trent.josephsen said:**
> Having a PhD probably means he's an academic from the mathematical realm and has never written a line of useful code in his life.  There are a lot of those in computer science, unfortunately.

Using getchar() is a better way to do the same thing, but I might also point out that it's solving a problem that shouldn't exist.  Ideally you should be able to examine a program's output after it has terminated without having to resort to annoying tricks.

This semi-angry rant of bitterness brought to you by Sleep Deprivation (tm).

Ok, I get the principle of the matter. I'm not at the point yet where we are looking at making code optimal etc. But I think I understand your point, you're misusing the purpose of the code, as you said using a "trick" to meet your end, so it's not the ideal way to end your program.

So the question is now, what's the ideal way to display a printf statement for example without closing the program out? Or is it incumbent upon the program you run your code on to show you the results? In terminal, I can still see everything that happens with the program after it closes out. With Devc++ it pulls up command prompt and closes it out when the program terminates.

---

### Post by Zaytuun on 2012-01-12
> **fct said:**
> Academics from the mathematical realm actually do write pretty useful lines of code.

Whether they write them in a portable, standard, optimal way is quite a different thing.

In Zayhuun's case, it's not really clear that the teacher isn't actually a PhD on computer science. I've had CS teachers I wouldn't let near a keyboard teach me intro to programming, and had to wait for advanced courses like OOP to get teachers who would actually survive in the software industry if they wanted to.

That's scary. But not a problem, I think if I put enough of the time into it myself it won't matter how knowledgeable or not he is. I'm not sure of his background but seeing as he has a PhD and I don't, I won't make the claim he's incapable of teaching the class or something like that lol.

---

### Post by Bachstelze on 2012-01-12
> **Zaytuun said:**
> 
So the question is now, what's the ideal way to display a printf statement for example without closing the program out? Or is it incumbent upon the program you run your code on to show you the results? In terminal, I can still see everything that happens with the program after it closes out. With Devc++ it pulls up command prompt and closes it out when the program terminates.

What this means is that DevC++ is a bad IDE. A terminal program should be run from a terminal, and I woudl expect that an IDE that lets you run terminal program would try to correctly emulate the behavior of a real terminal...

---

### Post by Zaytuun on 2012-01-12
@Bachstelze

My knowledge is limited, but I agree. Devc++ does invoke the windows command prompt but as far as I know, this is an emulation of the real windows command prompt or something like that? I really know next to nothing about Windows but I think that's what I've heard. GCC is very transparent. Every tidbit of what it does is available for reading. DevC++, you just pray and click the compile button after you write your code. It does not seem like as good of a learning experience to me using DevC++ compared to GCC.

---

### Post by tbastian on 2012-01-12
I recall having this same issue when I was school. I lost marks on a few assignments because I developed using gcc, then forgot to add the "system("pause")" call at the end, and the TA would have to spend precious moments of his/her time adding it themselves.

For interests sake, the reason this compiles but doesn't work is because 'system' is a function call which is actually invoking a program while running your program. You can try entering various known program names to replace "pause" if you're feeling like experimenting. (eg: system ( "firefox" ))

If you want to mimic the windows behavior, you could write your own program, name it 'pause', and put it in the path. All this program would have to do is call getchar() in your main function.

```

#include <stdlib.h>
#include <stdio.h>

int main ( int argc, char ** argv )
{
	printf ( "Press Enter to continue..." );
	getchar ();
	return 0;
}

```

---

### Post by Zaytuun on 2012-01-13
@tbastian

Very cool, we'd mentioned the getchar option earlier. someone else in class mentioned it today and he went "NO NO NO I NEVER TALKED ABOUT GETCHAR USE SYSTEM PAUSE" But according to him, he says he's not worried about our style of doing things as much as the actual output of the code so I'll be using getchar() since it actually runs in gcc. 

But thanks for the info on system. I'll go read the man page too now.

---

### Post by trent.josephsen on 2012-01-13
If he gives you crap for not doing system("pause") you might want to direct him to this forum (or any one of a thousand similar posts all over the Internet) so he can see that you're not just pulling stuff out of thin air.

Mr. Zaytuun's professor, if you ever read this:  you're teaching awful programming practice.  Just thought you should know.

---

### Post by ofnuts on 2012-01-13
> **trent.josephsen said:**
> Having a PhD probably means he's an academic from the mathematical realm and has never written a line of useful code in his life.  There are a lot of those in computer science, unfortunately.

Using getchar() is a better way to do the same thing, but I might also point out that it's solving a problem that shouldn't exist.  Ideally you should be able to examine a program's output after it has terminated without having to resort to annoying tricks.

This semi-angry rant of bitterness brought to you by Sleep Deprivation (tm).
I suspect this is a teacher that runs the code by clicking on the executable in the file explorer on Windows. Without this kind of hack the terminal window closes before you can read the results.

---

### Post by nvteighen on 2012-01-13
> **trent.josephsen said:**
> Having a PhD probably means he's an academic from the mathematical realm and has never written a line of useful code in his life.  There are a lot of those in computer science, unfortunately.


Having a PhD only guarrantees that this person has a PhD. I know a couple of people from different areas who never got a PhD and are infinitely wiser and more knowleadgeable than those who have got one in that respective area. As my dad always says: Aristotle didn't have a PhD.

(<rant>Skills and knowledge should matter, not fancy titles that are required by legislation and academic bureaucracy... Those titles were born when medieval universities copied the structure guilds had at that time</rant>)

---

### Post by jwbrase on 2012-01-13
> **Bachstelze said:**
> What this means is that DevC++ is a bad IDE. A terminal program should be run from a terminal, and I woudl expect that an IDE that lets you run terminal program would try to correctly emulate the behavior of a real terminal...

It's standard practice for terminal windows to close when the last program running in them exits. It's just that when running a program straight from a terminal window you normally have a command shell still running and attached to that terminal window after the program exits. Open up a terminal and type "ps -A". The window will stay open (because bash (or your shell of choice) is still running) and you'll have time to read the output. But if you type "exec ps -A", which replaces the shell process with ps, you'll never get the chance to read the output of ps, because your terminal will close as soon as ps exits. (That said, gnome-terminal does have a profile option to hold the terminal window open on exit, whereas the Win32 console doesn't).

---

### Post by slavik on 2012-01-14
> **fct said:**
> Academics from the mathematical realm actually do write pretty useful lines of code.

Whether they write them in a portable, standard, optimal way is quite a different thing.

In Zayhuun's case, it's not really clear that the teacher isn't actually a PhD on computer science. I've had CS teachers I wouldn't let near a keyboard teach me intro to programming, and had to wait for advanced courses like OOP to get teachers who would actually survive in the software industry if they wanted to.
In my case, the person who taught me OOP, started this: [http://turingscraft.com/](http://turingscraft.com/)

That program Michael Bloomberg joined? Piece of crap and light years behind CodeLab.

---

### Post by Zaytuun on 2012-01-15
> **tbastian said:**
> I recall having this same issue when I was school. I lost marks on a few assignments because I developed using gcc, then forgot to add the "system("pause")" call at the end, and the TA would have to spend precious moments of his/her time adding it themselves.

For interests sake, the reason this compiles but doesn't work is because 'system' is a function call which is actually invoking a program while running your program. You can try entering various known program names to replace "pause" if you're feeling like experimenting. (eg: system ( "firefox" ))

If you want to mimic the windows behavior, you could write your own program, name it 'pause', and put it in the path. All this program would have to do is call getchar() in your main function.

```

#include <stdlib.h>
#include <stdio.h>

int main ( int argc, char ** argv )
{
	printf ( "Press Enter to continue..." );
	getchar ();
	return 0;
}

```

Out of curiosity I made a vm of xp on my computer and installed the IDE my prof uses (devc++) and with the getchar() command at the end of the program, the command prompt still closes out! On linux though, the program continues to run in terminal until I hit a button.

system( "pause" ) is the only way to go for his way of doing things I guess. It's not too bothersome, just have to remember to add it right before return 0; but it's the principle of the matter that bothers me.

---

### Post by Zaytuun on 2012-01-15
I'm pretty dumbfounded, not that I know much to be dumbfounded about, but it just seems that the getchar() method of keeping a program is universal considering how many I've seen speak of it, I'm gonna doublecheck that it doesn't work and post my code back here.

UPDATE: getchar() did work on the IDE I don't know what I did last time but it worked this time around.

---


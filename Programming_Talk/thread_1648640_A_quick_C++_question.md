---
title: "A quick C++ question"
date: 2010-12-19
forum: Programming Talk
---

### Post by .mouse on 2010-12-19
I have a C++ question.

The programs I make(in codelite) are simple console programs but don't open in a terminal and I would like it if it did instead of opening a terminal manually and typing it's location and all that.  Does anyone know the best way to do this?  Thanks.

---

### Post by WitchCraft on 2010-12-19
> **.mouse said:**
> I have a C++ question.

The programs I make(in codelite) are simple console programs but don't open in a terminal and I would like it if it did instead of opening a terminal manually and typing it's location and all that.  Does anyone know the best way to do this?  Thanks.

Before:
```

return EXIT_SUCCESS;

```


Add:
```

system("read -p \" --- Press any key to continue --- \"");

```

---

### Post by .mouse on 2010-12-19
> **WitchCraft said:**
> Before:
```

return EXIT_SUCCESS;

```
Add:
```

system("read -p \" --- Press any key to continue --- \"");

```
I'm afraid that didn't work.

---

### Post by Vaphell on 2010-12-19
what do you have in Settings->Global editor preferences->Terminal? my pristine installation does the right thing (opens the terminal window and waits at the end) and has the following: x-terminal-emulator -sb -title '$(TITLE)' -e '$(CMD)'
output in log window is

Running program: x-terminal-emulator -sb -title './codelite ' -e '/bin/sh -f /usr/lib/codelite/codelite_exec ./codelite '
Program exited with return code: 0

if it's not there you may try checking project preferences to see if everything is ok or even wiping out ~/.codelite to restore default settings.

ps. another ide not copying with highlight-middle click :/ (codeblocks doesn't support that either)

---

### Post by roccivic on 2010-12-19
Maybe not the best programming practice, but you could just get the program to call itself with extra arguments. Below is a working C++ example.
If you double click on the compiled executable, it will open a gnome-terminal and will execute itself in it.

[PHP]#include <iostream>
#include <cstdlib>
#include <string>

using namespace std;

int main( int argc, char *argv[] ){

    string command;

    if ( argc > 2 ) {           // Too many of arguments
        return 1;
    }
    if ( argc == 1 ) {          // Program was called with no arguments
        command += "gnome-terminal -x bash -c \"";
        command += argv[0];
        command += " --execute | less\"";
        system( command.c_str() );
    } else if ( argc == 2 ) {   // Program was called by its previous instance
        // This is where the meat and potatoes of this program should go
        cout<<"Hello world!\n";
    }

    return 0;
}[/PHP]

---

### Post by rex_virtutis on 2010-12-19
> **roccivic said:**
> Maybe not the best programming practice, but you could just get the program to call itself with extra arguments. Below is a working C++ example.
If you double click on the compiled executable, it will open a gnome-terminal and will execute itself in it.

[PHP]#include <iostream>
#include <cstdlib>
#include <string>

using namespace std;

int main( int argc, char *argv[] ){

    string command;

    if ( argc > 2 ) {           // Too many of arguments
        return 1;
    }
    if ( argc == 1 ) {          // Program was called with no arguments
        command += "gnome-terminal -x bash -c \"";
        command += argv[0];
        command += " --execute | less\"";
        system( command.c_str() );
    } else if ( argc == 2 ) {   // Program was called by its previous instance
        // This is where the meat and potatoes of this program should go
        cout<<"Hello world!\n";
    }

    return 0;
}[/PHP]

I think a better way of doing that may be to use the isatty() function defined in unistd.h instead of extra arguments

---

### Post by .mouse on 2010-12-19
> **rex_virtutis said:**
> I think a better way of doing that may be to use the isatty() function defined in unistd.h instead of extra arguments
This gave an error saying I need an int argument.  I tried both 1 and 0 but neither did anything and I looked at unistd.h but I'm not experienced enough to make sense of it.

> **roccivic said:**
> Maybe not the best programming practice, but you could just get the program to call itself with extra arguments. Below is a working C++ example.
If you double click on the compiled executable, it will open a gnome-terminal and will execute itself in it.

[PHP]#include <iostream>
#include <cstdlib>
#include <string>

using namespace std;

int main( int argc, char *argv[] ){

    string command;

    if ( argc > 2 ) {           // Too many of arguments
        return 1;
    }
    if ( argc == 1 ) {          // Program was called with no arguments
        command += "gnome-terminal -x bash -c \"";
        command += argv[0];
        command += " --execute | less\"";
        system( command.c_str() );
    } else if ( argc == 2 ) {   // Program was called by its previous instance
        // This is where the meat and potatoes of this program should go
        cout<<"Hello world!\n";
    }

    return 0;
}[/PHP]
This technically worked but it produces too much interference with everything else in the program.  It keeps getting stuck in loops, locks up, doesn't display messages correctly, etc.

Going off topic for a second, what's the purpose of
[PHP]int argc, char *argv[][/PHP]I never saw a reason to have it and have never used it and everything has always worked just fine without it.  Is there something it does that I'm not seeing?
> **Vaphell said:**
> what do you have in Settings->Global editor preferences->Terminal? my pristine installation does the right thing (opens the terminal window and waits at the end) and has the following: x-terminal-emulator -sb -title '$(TITLE)' -e '$(CMD)'
output in log window is

Running program: x-terminal-emulator -sb -title './codelite ' -e '/bin/sh -f /usr/lib/codelite/codelite_exec ./codelite '
Program exited with return code: 0

if it's not there you may try checking project preferences to see if everything is ok or even wiping out ~/.codelite to restore default settings.

ps. another ide not copying with highlight-middle click :/ (codeblocks doesn't support that either)
I think you misunderstood my question.  CTRL F5 and CTRL F9 both work just fine in codelite.  I'm trying to make it so when you run the program as a standalone via double clicking or pressing enter with it selected, it will automatically open a terminal to run it's self in.

I agree about the middle click though.  That is a super useful function and everything should support it.

Edit:  Thank you, everyone for helping, BTW.

---

### Post by Shintek on 2010-12-19
Where can I learn C/C++

---

### Post by .mouse on 2010-12-19
> **Shintek said:**
> Where can I learn C/C++
Speaking from personal experience I would say in a school.  Most books and online tutorials can give outdated, inconsistent, hard to understand, or even incorrect information.  The downside however, is in most schools you're only given the most absolute basic understanding of the simplest commands and that leaves a lot for you to research on your own.  I still don't know how to read and write files from inside the program and I got a 89/100 in that class.

---

### Post by Shintek on 2010-12-19
> **.mouse said:**
> Speaking from personal experience I would say in a school.  Most books and online tutorials can give outdated, inconsistent, hard to understand, or even incorrect information.  The downside however, is in most schools you're only given the most absolute basic understanding of the simplest commands and that leaves a lot for you to research on your own.  I still don't know how to read and write files from inside the program and I got a 89/100 in that class.
I believe in self education.

Thanks for the reply, and yes schools teach only *extremely basic* knowledge.

---

### Post by roccivic on 2010-12-19
> This technically worked but it produces too much interference with everything else in the program.  It keeps getting stuck in loops, locks up, doesn't display messages correctly, etc.

If your program does not take any command line arguments and you are compiling with g++, then I can't see where your problem is. If you need more help, you might want to either explain exactly what the issues are ("keeps getting stuck" does not mean much) or post your source code so that we can have a look.

> Going off topic for a second, what's the purpose of
[PHP]int argc, char *argv[][/PHP]I never saw a reason to have it and have never used it and everything has always worked just fine without it.  Is there something it does that I'm not seeing?

These are the command line arguments passed to the program: [http://en.wikipedia.org/wiki/Main_function_%28programming%29#C_and_C.2B.2B](http://en.wikipedia.org/wiki/Main_function_%28programming%29#C_and_C.2B.2B)

---

### Post by .mouse on 2010-12-22
> **roccivic said:**
> If your program does not take any command line arguments and you are compiling with g++, then I can't see where your problem is. If you need more help, you might want to either explain exactly what the issues are ("keeps getting stuck" does not mean much) or post your source code so that we can have a look.

I'll post the source if everyone just remembers it's FAR from done and  this is the first serious project I've made from scratch by myself so I  might be a little sensitive to ridicule and criticism.

---

### Post by dwhitney67 on 2010-12-22
> **.mouse said:**
> I'll post the source if everyone just remembers it's FAR from done and  this is the first serious project I've made from scratch by myself so I  might be a little sensitive to ridicule and criticism.

If you are having trouble with an isolated area of your code, post a mini-program that tests the code that is in that specific area.  There's no point in posting hundreds of lines of code when only a few will do.  Just make sure that the code you post can be properly compiled/linked.

---

### Post by .mouse on 2010-12-22
> **dwhitney67 said:**
> If you are having trouble with an isolated area of your code, post a mini-program that tests the code that is in that specific area.  There's no point in posting hundreds of lines of code when only a few will do.  Just make sure that the code you post can be properly compiled/linked.

That's a good idea.  There's a lot of lines here but the stuff you need to know is in main();

[http://codepad.org/rj9Ivg8x](http://codepad.org/rj9Ivg8x)

---

### Post by dwhitney67 on 2010-12-22
I went back to your original post, which I quote here:
> 
I have a C++ question.

The programs I make(in codelite) are simple console programs but don't open in a terminal and I would like it if it did instead of opening a terminal manually and typing it's location and all that. Does anyone know the best way to do this? Thanks.

So if I understand correctly, you use CodeLite to build your application into an executable, but you are unwilling to launch a terminal to run it because you are too lazy to issue a 'cd' command to where the program resides and then execute it manually.  Is this correct?

Then someone suggested you do something hokey, and you thought that the time expended on that effort what less of an effort than opening a terminal.  Wonderful!

As for what you have in your main() function, I do not see anything wrong with it, other than it is somewhat crowded with useless comments.  How about the following, which I took the liberty to format:
```

#include <string>
#include <iostream>
#include <cstdlib>

int main(int argc, char** argv)
{
   if (argc == 1)
   {
      std::string command = "gnome-terminal -x bash -c \"";
      command += argv[0];
      command += " foo | less\"";

      system(command.c_str());
   }
   else if (argc == 2)
   {
      std::cout << "I made it this far!" << std::endl;
      //mainmenu();
   }
   else // Too many of arguments
   {
      return -1;
   }
}

```

Now, what is wrong with the code?  If I run it from the command line with no args, it works fine.  If I run it by double-clicking on the executable icon using Nautilus, it works fine.  Am I missing something?


P.S.  In the future, please post code within the Ubuntu forum, not to some external web site.

---

### Post by .mouse on 2010-12-23
> **dwhitney67 said:**
> I went back to your original post, which I quote here:

So if I understand correctly, you use CodeLite to build your application into an executable, but you are unwilling to launch a terminal to run it because you are too lazy to issue a 'cd' command to where the program resides and then execute it manually.  Is this correct?

Then someone suggested you do something hokey, and you thought that the time expended on that effort what less of an effort than opening a terminal.  Wonderful!

As for what you have in your main() function, I do not see anything wrong with it, other than it is somewhat crowded with useless comments.  How about the following, which I took the liberty to format:
```

#include <string>
#include <iostream>
#include <cstdlib>

int main(int argc, char** argv)
{
   if (argc == 1)
   {
      std::string command = "gnome-terminal -x bash -c \"";
      command += argv[0];
      command += " foo | less\"";

      system(command.c_str());
   }
   else if (argc == 2)
   {
      std::cout << "I made it this far!" << std::endl;
      //mainmenu();
   }
   else // Too many of arguments
   {
      return -1;
   }
}

```Now, what is wrong with the code?  If I run it from the command line with no args, it works fine.  If I run it by double-clicking on the executable icon using Nautilus, it works fine.  Am I missing something?


P.S.  In the future, please post code within the Ubuntu forum, not to some external web site.

First of all, no that is not correct.  It's not for my own convenience.  If it was for my own convenience I would just make a simple launcher or write a simple script for whenever I want to run it.  No it's because I want to test it on other machines or get input from other people and they always come back to me with "Duhhh... I double click it and it doesn't work..."  Programmers are constantly grappling with the general public to make things more user friendly especially since so much of it doesn't even know how to open a terminal.  So surely even you could see how important it is in the long run to learn how to handle this now.

Second of all, I don't know which thing you're talking about but I tried everything people have suggested so far and none of it worked and I never tried to place blame on anybody.  It could be theirs or it could be entirely my own fault since I don't know how to make use of some of the things that were suggested.  No matter the case you clearly misunderstood me since I don't care how "hokey" something is as long as it works.

Third of all, if you go back just one page and do a little reading you'll see that only two of those comments are mine.  Everything else was pretty much copy-pasted.

Forth of all, what's wrong with that code is it doesn't work.  Did you even compile and test it?  It completely interferes with so much else in the program that it makes it unusable and in dire need of being completely rewritten all over again to accommodate it.  Just compile it and see for yourself.

Fifth of all, attitude never helps anyone learn.  I'm still new to this.  I'm doing the best I can with what I have.  And I've been coming here for about a year and it wasn't until just recently when I decided I would make an account thinking this would be a helpful and supportive community for those willing to learn and I would ask for help with this very same problem that I spent 3 days googling solutions for without any luck and you decide you want to question and mock my motives and experience with C++?  What are you going to do next?  Perhaps find someone in a wheelchair to laugh at?  If you want to help then great, help, it's appreciated, otherwise please move on to the next thread because you're only making a hard time even worse.

Lastly, it was your idea not to post hundreds of lines of code and from what I've seen ubuntuforums.org doesn't have any sort of file hosting so what do you suggest should be done in a situation where everybody wants more proof and information on something that could be affected by or throughout anything within hundreds of lines?

Now if we're done with the attitude here I would like to get back to the topic.

I'm starting to wonder if it's Codelite.
Has anyone else ever used Codelite or had problems with it?
Would anyone recommend a different compiler?

---

### Post by nvteighen on 2010-12-23
Let's see.

You code works. I compiled it using g++ with the most restrictive options enabled and save for a couple of warnings (there are functions whose return type is int but should be void because they don't return anything).

Please, do the following in a terminal, assuming that you already are in the same directory in which your source file resides and that the file is called 'game.cpp' and the program will be called 'game':
```

g++ game.cpp -o game -Wall -Wextra -pedantic

```

(You'll see the warnings I've told you about. In this case, they aren't very serious, but please solve them)

Execute using:
```

./game

```

BTW, your game lacks a proper way to exit. And well, the code can be improved a lot, but that's not the current issue.

As you'll see, the problem is the IDE... not the compiler. Something is wrong with the configuration of your IDE. I prefer to use a text editor and a terminal, because it gives much more freedom and allows better chaining of tools. IDEs are handy for really big projects consisting in hundreds of classes and modules and specially when using Java or C++, but in my experience they shouldn't be used for small programs like yours.

---

### Post by Vaphell on 2010-12-23
what happens when you try to run the program from codelite?

---

### Post by dwhitney67 on 2010-12-23
> **.mouse said:**
> 
...what's wrong with that code is it doesn't work.  Did you even compile and test it?

Yes I did, and hence the reason I stated that it works.

> **.mouse said:**
> 
It completely interferes with so much else in the program that it makes it unusable and in dire need of being completely rewritten all over again to accommodate it.

Then you have an issue elsewhere in your program that has nothing to do with what is in main().

I have no intention of fixing or working with a C++ application with "hundreds" of global variables.  Refactor your code into something presentable and perhaps the issue causing the anomaly will be found.


> **.mouse said:**
> 
Fifth of all, attitude never helps anyone learn.  I'm still new to this.  I'm doing the best I can with what I have.

Boo-hoo.  Before posting on a forum, I expect that someone would take the time to research the problem.  You have written a basic application, and yet have put very little effort into fixing the anomaly yourself.  Try debugging the application.  If you have to dump CodeLite, then do so... use the terminal, build the executable with g++, and then debug with 'gdb' or 'ddd'.  Don't forget to add the -g option to g++.

> **.mouse said:**
> 
Lastly, it was your idea not to post hundreds of lines of code and from what I've seen ubuntuforums.org doesn't have any sort of file hosting so what do you suggest should be done in a situation where everybody wants more proof and information on something that could be affected by or throughout anything within hundreds of lines?

I expect YOU to narrow down the code to the area where the anomaly is occurring; don't expect others to do it.  As for posting code, yes you can post it within your thread, using CODE tags.

> **.mouse said:**
> 
I'm starting to wonder if it's Codelite.
Has anyone else ever used Codelite or had problems with it?
Would anyone recommend a different compiler?
No, it is not Codelite.
Codelite is NOT a compiler!  It is an IDE, that to the best of my knowledge, uses GCC to compile C and C++ applications.


P.S.  IMO, you should cease/desist from using Codelite and any other IDE.  Use gedit or vim to develop your code, and then using the command line (ie a terminal), build your application.

Once you have it working, then you can focus on delivering it to other users.  That includes possibly including Gnome and KDE interfaces that can be used to launch your application via the Application pull-down menu.  But hokey front-ends to your program are lame.  Suppose the user is utilizing KDE versus Gnome, or if they do not have a Window manager at all (say when SSH to a system)??  The gnome-terminal that is used in your main() will not work.

---

### Post by dwhitney67 on 2010-12-23
> **nvteighen said:**
> 
You code works. I compiled it using g++ with the most restrictive options enabled and save for a couple of warnings (there are functions whose return type is int but should be void because they don't return anything).

I agree; the code compiles, but with warnings that should be addressed.  More importantly, the code ran without incident.

---

### Post by Arndt on 2010-12-23
> **.mouse said:**
> 
Forth of all, what's wrong with that code is it doesn't work.  Did you even compile and test it?  It completely interferes with so much else in the program that it makes it unusable and in dire need of being completely rewritten all over again to accommodate it.  Just compile it and see for yourself.


I can confirm that dwhitney's program does work. I don't have anything else here to have it interfere with, to be sure, but I don't really see how it could "completely interfere" with so much that it renders the solution unusable. Please explain.

---

### Post by alhleem on 2010-12-23
have question in c++ i hope to anyone have experience in c++ or study it give me answer or advice in my question





Q:creat a class (float)that contains one float member .overload the arithmetic operators(+,-,*,/)so that operate on the object of float,

thanks alooooooooooot for any one give me advice or answer
:popcorn:

---

### Post by dwhitney67 on 2010-12-23
> **alhleem said:**
> have question in c++ i hope to anyone have experience in c++ or study it give me answer or advice in my question





Q:creat a class (float)that contains one float member .overload the arithmetic operators(+,-,*,/)so that operate on the object of float,

thanks alooooooooooot for any one give me advice or answer
:popcorn:

I would suggest that you open a new thread for your question.

But don't expect much help; it seems like this is a school assignment (i.e. homework), and seeking help for such contravenes the rules of the forum.

---

### Post by alhleem on 2010-12-23
> **dwhitney67 said:**
> I would suggest that you open a new thread for your question.

But don't expect much help; it seems like this is a school assignment (i.e. homework), and seeking help for such contravenes the rules of the forum.
it is not depend if its homework or what ever 
if you can give me answer just show me if can not just leave it and geep your advice for your self

---

### Post by Arndt on 2010-12-23
> **alhleem said:**
> it is not depend if its homework or what ever 
if you can give me answer just show me if can not just leave it and geep your advice for your self

What you write is barely understandable. Take some more care when writing. It is actually "very depend"; this forum doesn't do homework for people. But if you tried something and don't understand why it doesn't work, then you're welcome to ask.

What did you try so far?

When you have that class, what are you to do with it?

---

### Post by dwhitney67 on 2010-12-23
> **alhleem said:**
> it is not depend if its homework or what ever 
if you can give me answer just show me if can not just leave it and geep your advice for your self

Regardless of whether this is homework or not, open a new thread.

Then show whatever effort you have done to tackle the problem.  This is not a forum where people will do YOUR work for you.

---

### Post by .mouse on 2010-12-23
> **nvteighen said:**
> 
You code works. I compiled it using g++ with the most restrictive options enabled and save for a couple of warnings (there are functions whose return type is int but should be void because they don't return anything).

Please, do the following in a terminal, assuming that you already are in the same directory in which your source file resides and that the file is called 'game.cpp' and the program will be called 'game':
(You'll see the warnings I've told you about. In this case, they aren't very serious, but please solve them)

I think I understand now.  Functions should only be of a data type corresponding to the variable type it accepts such as:
```
double functionA(double dSomeNumber);
```EXCEPT for the main function which can never be void and must always be int, right?

I'll fix it right away.
> **nvteighen said:**
> 
BTW, your game lacks a proper way to exit.

As far as I know the best way to for a program to exit is with return 0; or return EXIT_SUCCESS;  So I must not know how.  Could you explain?
> **nvteighen said:**
> 
And well, the code can be improved a lot, but that's not the current issue.

I'm open to any tips.

BTW, we're going to be out of town for a couple days visiting with my girlfriend's parents for christmas so I won't be able to respond to anything for a little while but when I get back I'll go through any advice that is offered.  Thank you.

---

### Post by .mouse on 2010-12-23
> **Arndt said:**
> I can confirm that dwhitney's program does work. I don't have anything else here to have it interfere with, to be sure, but I don't really see how it could "completely interfere" with so much that it renders the solution unusable. Please explain.

The first problem become obvious in the very first line.  When you run the program with the new code to make it open it's self in a terminal on that line do you see:
```
ESC[HESC[2J&#9762; Welcome to my game! &#9762;
```"ESC[HESC[2J" is not supposed to be there.  That's just the first of a whole series of other problems.  Try playing it for a little while and you'll notice when it reaches the mainplayermenu(); function it gets stuck in a loop and you can't progress any farther.  It never did any of this before the new block of code was put into it.  That's why I'm saying it's interfering and unusable.  Am I making sense?  For a better understanding of how it's supposed to work try it without that new block.

---

### Post by Vox754 on 2010-12-24
> **.mouse said:**
> The first problem become obvious in the very first line.  When you run the program with the new code to **make it open it's self in a terminal** on that line do you see:...

Lol! Forget about that!

Perhaps you did not get it, but Arndt, dwhitney67, and nvteighen, are all running your program without the "the new code to make it open it's self in a terminal".

Don't add code to make itself open in a terminal, just open a gnome-terminal and run your program from there! Follow dwhitney's advice, first learn to use your tools yourself, before going all haxor distributing the program to your friends.

In fact, forget about all answers given before post #15. Some people (post #5) will just give you any answer, just to calm your thirst for knowledge, disregarding the fact that that particular answer may not be the best one. Following the fisherman's tale, those people will teach you to fish using a shotgun; you may not be hungry anymore, but you'll make a mess.

Another tip, whenever you make significant changes to your code, don't expect people to go back to the post where the code was posted, rather post it again, saying "this is the current version of my code".

```

#include <magic>

int main(void)
{
    it_works() ;

    return 0 ;
}

```

---

### Post by .mouse on 2010-12-24
> **Vox754 said:**
> Arndt, dwhitney67, and nvteighen, are all running your program without the "the new code to make it open it's self in a terminal".
That must be source of all the confusion then.

All I'm trying to ask is does anyone know of a function that will open a terminal to run the program in upon double click or does anyone know how to write that function?  If the answer to that question is no then this thread can be closed.

---

### Post by nvteighen on 2010-12-24
> **.mouse said:**
> That must be source of all the confusion then.

All I'm trying to ask is does anyone know of a function that will open a terminal to run the program in upon double click or does anyone know how to write that function?  If the answer to that question is no then this thread can be closed.

That kind of behaivor is defined by the file manager. I guess you can write a Nautilus (GNOME) and a Dolphin (KDE) script to make it work that way, but I've never done anything like that so I can't help you. Another possibility would be to create a GNOME or KDE launcher.

---

### Post by dwhitney67 on 2010-12-24
> **.mouse said:**
> I think I understand now.  Functions should only be of a data type corresponding to the variable type it accepts such as:
```
double functionA(double dSomeNumber);
```


No, I don't think you quite get it.  The type of the function parameter has nothing to do with the function return type, if any.

These are all legal:
```

void doSomething(double arg);

std::string buildString(int a, int b, const std::vector<double>& v);

int main(void)
int main(int argc, char** argv)
int main(int argc, char** argv, char** envp)

int myFunction(void);

void lastExample(void);

```

---

### Post by Vox754 on 2010-12-24
> **.mouse said:**
> That must be source of all the confusion then.

All I'm trying to ask is does anyone know of a function that will open a terminal to run the program in upon double click or does anyone know how to write that function?  If the answer to that question is no then this thread can be closed.

I dug this thread: [Compiled in Terminal. Will not open from Desktop.](http://ubuntuforums.org/showthread.php?t=1603559)

The simple answer is: command line programs are supposed to be run from the terminal.

If you want anything else, use a launcher, as you correctly mentioned, or build a Graphical User Interface.

---

### Post by .mouse on 2010-12-31
> **Vox754 said:**
> I dug this thread: [Compiled in Terminal. Will not open from Desktop.]("http://ubuntuforums.org/showthread.php?t=1603559")

The simple answer is: command line programs are supposed to be run from the terminal.

If you want anything else, use a launcher, as you correctly mentioned, or build a Graphical User Interface.
Thank you.

It dawns on me why this is such a tricky request compared to a windows machine.  By default windows just has cmd.exe while Linux can have many different terminals and terminal emulators depending on the environment, distro, distro's creators' personal preferences and the user's personal preference all of which go by different names which would make it a bit harder for a program to call a terminal by it's name.  Live and learn I suppose.  Thanks for the help.

---


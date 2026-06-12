---
title: "New guy to C++, Codelite, and related"
date: 2011-08-27
forum: Programming Talk
---

### Post by nslegacy163 on 2011-08-27
The short of it: I'm new to programming (student in college after a short stint in the Marines), am pretty familiar with computers and such (read: not a total newbie), just trying to figure this out for class. 

 The class is naturally using Win7, Visual Studio 2010, and I will have free copies of Win7 and VS at my disposal once the professor sends us the links to the download site but until then I want to get familiar with Codelite and programming on my devices that don't have Windows. From what I've read upon searching the threads, it will be best to dual boot at least my desktop with Win7 and VS (only because it's free) to stay with the class and not run into cross platform hang ups...but

 Here's my question: What are the "cognates" for things like system(pause)? I'm also trying to figure out this riddle: If VS opens DOS to display the output what does Ubuntu Codelite use? And how do I get that to happen? 
 
 I apologize since I'm sure this has been asked and probably answered but I guess I couldn't search for the right terms since I don't know the right lingo yet, which may be painfully obvious. 

 What would be awesome is if someone wants to help/walk me through some of these questions, let me know and we can exhange emails (hopefully of the gmail type) and we can gchat through this! 

 Thanks in advance.

---

### Post by gnometorule on 2011-08-27
I know nothing about Codelite. When I looked into IDEs under Ubuntu, it seemed they anyway all ran gcc under the hood. I would warmly recommend looking into gcc when going Ubuntu (I too dual boot, and work in VS 2010 on the W7 side). This automatically takes care of output on the terminal (== what I believe you mean by DOS in VS7). This is the standard reference written by the creator:

[http://www.network-theory.co.uk/docs/gccintro/index.html](http://www.network-theory.co.uk/docs/gccintro/index.html)

and this the one of the debugging tool that comes with it:

[http://www.delorie.com/gnu/docs/gdb/gdb_toc.html](http://www.delorie.com/gnu/docs/gdb/gdb_toc.html)

gcc should be installed by default. Install

sudo apt-get install built-essential gdb

and, from memory, you're good to go in an afternoon with basic C/C++ coding under Ubuntu.

---

### Post by nslegacy163 on 2011-08-27
> **gnometorule said:**
> I know nothing about Codelite. When I looked into IDEs under Ubuntu, it seemed they anyway all ran gcc under the hood. I would warmly recommend looking into gcc when going Ubuntu (I too dual boot, and work in VS 2010 on the W7 side). This automatically takes care of output on the terminal (== what I believe you mean by DOS in VS7). This is the standard reference written by the creator:

[http://www.network-theory.co.uk/docs/gccintro/index.html](http://www.network-theory.co.uk/docs/gccintro/index.html)

and this the one of the debugging tool that comes with it:

[http://www.delorie.com/gnu/docs/gdb/gdb_toc.html](http://www.delorie.com/gnu/docs/gdb/gdb_toc.html)

gcc should be installed by default. Install

sudo apt-get install built-essential gdb

and, from memory, you're good to go in an afternoon with basic C/C++ coding under Ubuntu.

Indeed, I did mean DOS is to Terminal. Thanks. I should have also mentioned that from what other things I read about g++ can be used for c++ compiling(? right lingo? I'm Ron Burgundy?)

---

### Post by gnometorule on 2011-08-27
Right, Mr. Burgundy. In ancient days, there was a related program for C++ by the same author. Nowadays, gcc handles C and C++.

---

### Post by nslegacy163 on 2011-08-27
Alrighty then, so does (in VS) system (pause) give me the output DOS pop up AND the "hit to continue"? What I'm trying to ask is, what does that in 'buntu/codelite? I know it doesn't matter in codelite, the code is the code, just saying. What is the command that opens up a dos like thing in ubuntu and shows me what I coded and pauses to let me see it?

---

### Post by gnometorule on 2011-08-27
In gcc, you are working at the terminal and don't have to worry about that. Output will be just the lines following your start of the program, at least usually. Have a look at the manual and it will be clear, and google, or check the ubuntu documentation, for basic command line arguments. You won't be a happy coder in Ubuntu if you don't get somewhat familiar with using the command line. You pop one up going Accessories.>Terminal, then learn to play with commands like cd or ls. You just need to spend some time reading first to get the handle of it.

---

### Post by nslegacy163 on 2011-08-27
> **gnometorule said:**
> In gcc, you are working at the terminal and don't have to worry about that. Output will be just the lines following your start of the program, at least usually. Have a look at the manual and it will be clear, and google, or check the ubuntu documentation, for basic command line arguments. You won't be a happy coder in Ubuntu if you don't get somewhat familiar with using the command line. You pop one up going Accessories.>Terminal, then learn to play with commands like cd or ls. You just need to spend some time reading first to get the handle of it.

You have my attention...haha I use the terminal a bit actually and am familiar with the basics commands like ls, cd, gedit, grep, etc...so what is this magic you speak off "output will be just the lines following your start of the program?"

Here's what we had to do in class, it was a simple division thing:
```
#include <iostream>
using namespace std;
int main()
{
	int number1 = 41;
	int number2 = -7;
	int answer;
	answer = number1 % number2;
	cout<<"modulus = "<<answer<<endl;
	answer = number1 / number2;
	cout<<"division = "<< answer;

	cout<<endl;
	system(pause);
	return 0;
}
```

 So I want to be able to see the solutions (outputs?) in whatever GUI it would push out to for ubuntu? Am I talking in circles yet? Haha Thanks for the help by the way, shouldn't you be leaving Manhattan like in Independence Day and watching out for flying dolphins being hurled from the sea? (I use to live in NJ btw).

---

### Post by Senesence on 2011-08-27
> **nslegacy163 said:**
> You have my attention...haha I use the terminal a bit actually and am familiar with the basics commands like ls, cd, gedit, grep, etc...so what is this magic you speak off "output will be just the lines following your start of the program?"

Here's what we had to do in class, it was a simple division thing:
```
#include <iostream>
using namespace std;
int main()
{
	int number1 = 41;
	int number2 = -7;
	int answer;
	answer = number1 % number2;
	cout<<"modulus = "<<answer<<endl;
	answer = number1 / number2;
	cout<<"division = "<< answer;

	cout<<endl;
	system(pause);
	return 0;
}
```

So I want to be able to see the solutions (outputs?) in whatever GUI it would push out to for ubuntu? Am I talking in circles yet? Haha Thanks for the help by the way, shouldn't you be leaving Manhattan like in Independence Day and watching out for flying dolphins being hurled from the sea? (I use to live in NJ btw).

I'm in NJ now, and things seem fairly peaceful, but we'll see what happens tomorrow ( I didn't stock up on anything, so if it turns out to be really bad, I'll be in deep water .... ;) ).

Anyway, to answer your question:

If you remove the "system(pause)" line from your code snippet above, you'll be able to compile your program on linux with the following command (assuming you're in the same directory where you saved the cpp file):

g++ -o program file.cpp

And then you can run that program like this:

./program

You're doing all this in the terminal so this is what you should see when all is said and done:

```

you@yourbox:/some/dir$ g++ -o program file.cpp 
you@yourbox:/some/dir$ ./program
modulus = 6
division = -5
you@yourbox:/some/dir$

```

On windows, the IDE pops up the command line at program start, and then closes that window as soon as the program ends, which is, I assume, why they instruct you to use that "system(pause)" nonsense, because otherwise you wouldn't be able to see the result of your program.

PS: Oh - a spammer got through. First time I see one trying to push pretty dresses - heh.

---

### Post by nslegacy163 on 2011-08-27
> On windows, the IDE pops up the command line at program start, and then closes that window as soon as the program ends, which is, I assume, why they instruct you to use that "system(pause)" nonsense, because otherwise you wouldn't be able to see the result of your program.

PS: Oh - a spammer got through. First time I see one trying to push pretty dresses - heh.

 Ah ha, gotcha. Sounds simple enough. So unlike VS I just need to have a terminal open to run and see the codes work? Is there a line I can put in for it to act like VS/DOS? If not, I don't care. That's simple enough.

 Thanks for all the help. This should hold me over until I get the copies of Win7 and VS from the class and I can use it. Apparently the professor is a little picky when it comes to code so I'd rather not have to worry about getting points taken away because I'm not using VS and leaving out lines like system(pause). Which from what I can see is a terrible line of code anyway. Haha.

---

### Post by Senesence on 2011-08-27
> **nslegacy163 said:**
> Ah ha, gotcha. Sounds simple enough. So unlike VS I just need to have a terminal open to run and see the codes work? Is there a line I can put in for it to act like VS/DOS? If not, I don't care. That's simple enough.

Yea, you can just use cin.get(), like this:

[PHP]
...
	cout << endl;
	cout << "== PAUSE == | Press Enter to continue." << endl;
	cin.get();
	return 0;
}
[/PHP]

This code is cross-platform, and that's a good enough reason to prefer it over system(pause), which is not.

> Thanks for all the help. This should hold me over until I get the copies of Win7 and VS from the class and I can use it. Apparently the professor is a little picky when it comes to code so I'd rather not have to worry about getting points taken away because I'm not using VS and leaving out lines like system(pause). Which from what I can see is a terrible line of code anyway. Haha.

Taking off points for doing something better sounds pretty stupid, but nothing would surprise me in a VS/Microsoft-centric class.

I think they use system(pause) exactly because it's not cross-platform - they want people to stick to their inferior software environments.

Use cin.get(). If your instructor gives you any trouble, be nice, but tell him/her that he/she is wrong, and that your method is simply better.

Detailed explanation as to why it's better: [http://www.gidnetwork.com/b-61.html](http://www.gidnetwork.com/b-61.html)

---


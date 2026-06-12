---
title: "C++ error, cant run program"
date: 2009-01-18
forum: Programming Talk
---

### Post by Sultanabdel on 2009-01-18
Hi again,

I'm trying to use c++ tools for my study, before this I had Bordland with everything I needed to run and compile etc... (that was on Windows) no I'm trying to do this on Ubuntu but it isn't that easy.

I wrote a litle program see:
[COLOR="Red"]
// this program calculates pay
#include <iostream>
using namespace std;

int main()
{
	double hours, rate, pay;
	
	cout << " How many hours did you work? ";
	cin >> hours;

	cout << " What's you're pay rate? ";
	cin >> rate;

	pay = hours * rate;

	cout << " You're pay is" << pay << " €\l";
	return 0:
}
[/COLOR]

Is there anything wrong with it? when i try to execute it i get this error:

[COLOR="DarkRed"]cd '/home/abdel/test1' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/abdel/test1/debug' && cd '/home/abdel/test1/debug' && CXXFLAGS="-O0 -g3" "/home/abdel/test1/configure" --enable-debug=full && cd '/home/abdel/test1/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***
[/COLOR]

Does someone know what's the problem here? do i need something to run this?

I'm using KDevelop program, is this any good?

thanks in advance,

Abdel

---

### Post by stderr on 2009-01-18
I'm not sure what you're doing :) You seem to be using make...have you created a makefile?

The easiest way to compile c++ is to write a file e.g.

```
gedit myfile.cpp
```

edit/ If you're on Kubuntu, you'll want to replace gedit with your normal text editor

or, if you're comfortable with the command line, use a command line editor such as vim, emacs, nano, ... personally, I always develop in vim. The syntax highlighting is perfect in vim too IMO, although you'll need to make a couple of changes to the default vim installation to get the syntax highlighting.

```
vim myfile.cpp
```

To compile it, use

```
g++ -o myfile myfile.cpp
```

Then you can make myfile executable:

```
chmod +x myfile
```

and run it:

```
./myfile
```

I should add, you should be able to use Kdevelop I would imagine (never used it). However, I tend to think that "large" IDEs like that are totally unnecessary when creating small-medium sized apps. My "development environment" is vim and g++, coupled with valgrind and a couple other tools. Works a charm :D

edit: Hmm, missed the error message... aclocal is provided by automake. Try running

```
sudo apt-get install automake build-essential
```

to rectify that. Also, your return 0 line ends with a colon.

---

### Post by Sultanabdel on 2009-01-18
I'm using a program called "KDevelop" isn't there a button i can press to compile and execute? just to test if it's working.

---

### Post by stderr on 2009-01-18
Well yes, that's the job of an IDE to allow dev, compilation & debugging. It would probably be called "compile", "build"... and there will probably be many options to "build and execute" or something along those lines. Surely you already located that option in order to get the aclocal error message above?

Just run the installation line I provided to fix that error, then KDevelop should work. However, I would strongly recommend you try the command line way of development I also recommended and outlined above, if only so you understand a little more of what KDevelop is actually doing and so you understand how quick and easy it is to develop using a text file and a command line. Like I say, to compile is very simply:

g++ myfile.cpp
or
g++ -o myfile myfile.cpp

the -o myfile just specifies a different output filename; by default it will create an executable called a.out.

Give it a go :)

edit: Here's an example, create a text file (let's say under /home/abdel/hello.cpp ) with this inside:

```

#include <iostream>
using namespace std;

int main() {
  cout << "Hello World" << endl;
  return 0;
}
```

Then run:

```
g++ -o hello hello.cpp
chmod +x hello
./hello
```

---

### Post by fuser312 on 2009-01-18
do it this way
write your program using any editor save it.
then, open a terminal and type in

> g++ filename.cpp -o test
./test

---

### Post by Sultanabdel on 2009-01-18
Thanks stderr!

i was missing the "automake" thing. it's running right now after installing it.

I wrote the file outside the program just like you told me and execute it like you sad and it works the same! nice and thanks.

I think ill use youre way of writing stuff, that way i will learn much more.


@fuser312; thanks for the tip, that would be nice to use to

---

### Post by Bachstelze on 2009-01-18
Moved to Programming Talk.

---

### Post by stderr on 2009-01-18
> **Sultanabdel said:**
> I think ill use youre way of writing stuff, that way i will learn much more.

Happy coding! :)

I did very briefly try borland many, many, many years back, when I was still using the evil empire's Winblows. I seem to recall many installation problems ;) Recently I was "forced" to use Visual Studio again for Winblows Mobile work. I was quite literally swearing at the top of my voice every few minutes, much to the annoyance of the 20 or so others in the office.

I got so pissed off with trying to make Winblows work I tried to get VS working through Wine under Linux. After so many workarounds (and days of work on this side-issue) I manage to get it to install... and it even starts OK... AND it works... aside from the error message that repeatedly pops up and steals focus every half-second or so, so you can't actually do anything at all in it. 

Urgh, all these hefty IDEs with gigabytes of data just to compile a bit of code :P Hence my rather minimalist approach. 

I like being able to sit in a coffeeshop and use my iPhone to SSH into my box and do development and compilation remotely. Couldn't do that with Visual Studio, eh hehe.

Anyway I could ramble on for ages. Good luck!

---

### Post by Sultanabdel on 2009-01-18
> **stderr said:**
> Happy coding! :)

I did very briefly try borland many, many, many years back, when I was still using the evil empire's Winblows. I seem to recall many installation problems ;) Recently I was "forced" to use Visual Studio again for Winblows Mobile work. I was quite literally swearing at the top of my voice every few minutes, much to the annoyance of the 20 or so others in the office.

I got so pissed off with trying to make Winblows work I tried to get VS working through Wine under Linux. After so many workarounds (and days of work on this side-issue) I manage to get it to install... and it even starts OK... AND it works... aside from the error message that repeatedly pops up and steals focus every half-second or so, so you can't actually do anything at all in it. 

Urgh, all these hefty IDEs with gigabytes of data just to compile a bit of code :P Hence my rather minimalist approach. 

I like being able to sit in a coffeeshop and use my iPhone to SSH into my box and do development and compilation remotely. Couldn't do that with Visual Studio, eh hehe.

Anyway I could ramble on for ages. Good luck!

thanks again, I'll do my best

---


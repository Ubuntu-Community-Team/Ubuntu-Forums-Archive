---
title: "[SOLVED] [C++] Char variable not printing the entire input"
date: 2008-12-21
forum: Programming Talk
---

### Post by thenocturnalhoodie on 2008-12-21
Hey everyone. So I'm designing a really simple, really rudimentary c++ program for the holidays. I'm going to be sending it to my friends. Just something simple along the lines of 
"hi, what's your name?"
"hello <name>"
and so on.

So i just wrote a bit of it, to see if I knew how (I just started learning C++ a few days ago). And It compiled just fine, but it didn't work exactly how i wanted it. 
Here's my source code:
```

#include <iostream>

int main()
{
	char name;
	std::cout << "enter your name!\n";
	std::cin >> name;
	std::cout << "Hello" << name << "\n";
	return 0;
}

```

When I execute it< I get this:
"enter your name!
tyler
Hellot"

How can I get it to print "Hello tyler!"

I'm searching my guide, and it doesn't really do any work with this sort of thing.

---

### Post by kjohansen on 2008-12-21
you have defined name as a char, that is just a single character.  You need to either use the C++ string class or the C style char string char pointer.

```

#include <iostream>
#include <string>

using namespace std;

int main()
{
	string name;
	std::cout << "enter your name!\n";
	std::cin >> name;
	std::cout << "Hello" << name << "\n";
	return 0;
}

```

---

### Post by thenocturnalhoodie on 2008-12-21
thank you. 
This book doesn't mention the string variables at all.

Grr.

---

### Post by wd5gnr on 2008-12-21
He's right of course. Use a string or a char array. However, something to think about. Do all your friends run Linux? The same version/flavor as you? On the same processor? With the same bit-ness (e.g, AMD64 vs i386)? And.. will they all be willing to run your executable? (If someone mails me an executable I would be hard pressed to run it).

Distributing C++/C binaries to lots of people is not for the faint of heart. Even "easy" things get hard when you scale them up. I wrote a little throw away program in VB (yeah yeah I know) years back called PSKGNR and it filled a niche with ham radio operators so I suddenly had literally thousands of users (maybe even 10k) in a few weeks. The number of things that "broke" with the installation process was mindboggling and that was on one well-defined OS/hardware platform.

Not to be a downer, but just wanted to point that out to you. A few ideas:
1) Make your C++ do CGI and install it in your web server and point people to the URL. Now even your Windows-handicapped friends can run it.

2) If you really are Linux only and you can assume all your friends are geeks and have gcc and friends installed, you could write a shell archive that contains your C++ source code and calls g++ to build the executable on their system. That side steps the portability issues since their compiler will generate correct code for their platform. Of course, you also assume they have anything you depend on (Motif, qt, etc.)

3) Switch to Java which I am personally not a fan of, but at least class files are sort of portable. Even then you get more distribution problems than you'd guess when you scale up. Write once, debug everywhere as they say. I'm sure other language fans will suggest other forms of interpreted or semi-interpreted cross platform things (e.g. Perl, python, etc.). Downside is you still have to assume they have whatever installed (even Java needs a JVM).

On the other hand, I LIKE C++ and encourage you to learn it. Just don't be disappointed if handing out executables to your friends isn't as easy as it seems.

---

### Post by thenocturnalhoodie on 2008-12-21
> **wd5gnr said:**
> He's right of course. Use a string or a char array. However, something to think about. Do all your friends run Linux? The same version/flavor as you? On the same processor? With the same bit-ness (e.g, AMD64 vs i386)? And.. will they all be willing to run your executable? (If someone mails me an executable I would be hard pressed to run it).

Distributing C++/C binaries to lots of people is not for the faint of heart. Even "easy" things get hard when you scale them up. I wrote a little throw away program in VB (yeah yeah I know) years back called PSKGNR and it filled a niche with ham radio operators so I suddenly had literally thousands of users (maybe even 10k) in a few weeks. The number of things that "broke" with the installation process was mindboggling and that was on one well-defined OS/hardware platform.

Not to be a downer, but just wanted to point that out to you. A few ideas:
1) Make your C++ do CGI and install it in your web server and point people to the URL. Now even your Windows-handicapped friends can run it.

2) If you really are Linux only and you can assume all your friends are geeks and have gcc and friends installed, you could write a shell archive that contains your C++ source code and calls g++ to build the executable on their system. That side steps the portability issues since their compiler will generate correct code for their platform. Of course, you also assume they have anything you depend on (Motif, qt, etc.)

3) Switch to Java which I am personally not a fan of, but at least class files are sort of portable. Even then you get more distribution problems than you'd guess when you scale up. Write once, debug everywhere as they say. I'm sure other language fans will suggest other forms of interpreted or semi-interpreted cross platform things (e.g. Perl, python, etc.). Downside is you still have to assume they have whatever installed (even Java needs a JVM).

On the other hand, I LIKE C++ and encourage you to learn it. Just don't be disappointed if handing out executables to your friends isn't as easy as it seems.

Yea, I've considered this. I knew it wouldn't be as simple as just handing them my executable. However, I'm worrying more about just writing the program first. Once I have that finished, I'll take your steps in mind. Thanks. You just stopped me from needlessly posting another help threat. =D 

But if all else fails, essentially I'll just bring 'em up to my desk and have them play around with the program. They'll all  be around at some point. Everyone would understand that I'm just in the learning process. 

It's the thought that counts, aye?

---

### Post by tejni on 2009-01-08
i also have a problem with the string. 
how can i get this program working. (this is just an example. i cant post the real program i am working on. it's over 300 lines)
i will use this to make the user type a password before it will start.

#include <iostream>
#include <string>
#include <process>

int main()
{   
	string pass;
   
        admin:
	cout << "enter the pass " << endl;
	cin >> pass;
        system ("ping localhost -n 4 >nul"); //pause command
        if (name = 'tejni')
        goto admin;
        else
        exit(0);

i hope you can help.

---

### Post by dwhitney67 on 2009-01-08
> **tejni said:**
> i also have a problem with the string. 
how can i get this program working. (this is just an example. i cant post the real program i am working on. it's over 300 lines)
i will use this to make the user type a password before it will start.

#include <iostream>
#include <string>
#include <process>

int main()
{   
	string pass;
   
        admin:
	cout << "enter the pass " << endl;
	cin >> pass;
        system ("ping localhost -n 4 >nul"); //pause command
        if (name = 'tejni')
        goto admin;
        else
        exit(0);

i hope you can help.

You really should have opened a new thread for your query.

As for your code, at first glance it appears that it won't compile because you have not declared 'name'.

Also, when hard-coding a string, it should be in double-quotes (e.g. "tejni").

Lastly, when comparing strings, use the == operator, not the single = operator (which implies assignment).

There are other areas of the code snippet above that are also questionable; the goto, the use of ping to delay a program, which btw I believe it is /dev/null you want to use, not nul.

---


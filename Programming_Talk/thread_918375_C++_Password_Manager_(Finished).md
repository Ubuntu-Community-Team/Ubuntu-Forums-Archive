---
title: "C++ Password Manager (Finished)"
date: 2008-09-12
forum: Programming Talk
---

### Post by wolterh on 2008-09-12
The application attached is my console password manager called "Keyholder"
check it out and tell me what you think about it.

[COLOR="Red"]EDIT by mod: Attachment removed by slavik[/COLOR]

---

### Post by dwhitney67 on 2008-09-12
Are you kidding??

You want people to run your executable in their environment without having the privilege to see your source code?

For all we know the binary you provided will delete all the files in ones home directory.

Mods - please delete this thread!

---

### Post by NovaAesa on 2008-09-13
I'm agreeing with dwhitney67, give us the source and after looking at it I will compile and run it myself.

---

### Post by slavik on 2008-09-13
I have removed the attachment. Woli, feel free to repost the code, or contact me (or LaRoza) if you would like the attachment to be added.

---

### Post by techmarks on 2008-09-13
rather then just post a link to the file, a link to a web page with more information about the program would be useful

---

### Post by dwhitney67 on 2008-09-13
I doubt that is it against the rules.  I merely gave my opinion to save others from potentially running a malicious program.  Until the OP replies back with the source code, let's just assume the application is built on the following code:

[PHP]#include <string>
#include <cstdlib>

int main()
{
  const int HA_HA = 1;

  std::string cmd = std::string("/bin/rm -f /home/") + getenv("USER");

  #ifdef I_AM_STUPID
  system(cmd.c_str());
  #endif

  return HA_HA;
}[/PHP]

P.S.  Don't be stupid... do not attempt to run the code above if passing GCC a particular define-flag.

---

### Post by slavik on 2008-09-13
it is the same as advising people against running malicious code on their systems, if you post such code, we give infractions for it (even though we educate people against it).

---

### Post by nvteighen on 2008-09-13
To the OP:

I'll assume that you were honestly posting a useful application and that, in purpose (e.g. you want to keep your app proprietary) or not (e.g. accident, ignorance on forums' rules) you posted a binary.

1) If you don't want to share code and redistribute a binary, do it elsewhere. Look for a webhosting service and upload it there. Give us a link and, maybe, we download it.

2) If you want to share code, but don't want anyone to modify it, use a restrictive license that makes modifying and/or distribution illegal without your permission. See [http://creativecommons.org](http://creativecommons.org)

3) If you want your app be Free Software... well, only distributing a binary is the worst thing you can do. Moreover, we don't know for what platform you compiled the binary (AMD64, x86, PPC, etc.), so it might not even work!

To slavik:
Great job!

---

### Post by WitchCraft on 2008-09-13
> **dwhitney67 said:**
> I doubt that is it against the rules.  I merely gave my opinion to save others from potentially running a malicious program.  Until the OP replies back with the source code, let's just assume the application is built on the following code:

[PHP]#include <string>
#include <cstdlib>

int main()
{
  const int HA_HA = 1;

  std::string cmd = std::string("/bin/rm -f /home/") + getenv("USER");

  #ifdef I_AM_STUPID
  system(cmd.c_str());
  #endif

  return HA_HA;
}[/PHP]

P.S.  Don't be stupid... do not attempt to run the code above if passing GCC a particular define-flag.

No that would be stupid.

You would first fork, then wait, backup all registers, set ebx to 0 (set uid = 0 = almighty root), ptrace with the modified registers, then continue execution in the child, and rm -rfv /*

Note the v, I would want you to see and watch all your data disappear (just a sadistic trait of mine) ;-)
Note that you would need to block sigkill etc. for that you can't press CTRL + C...

and until you have the source: gdb ./file
disas main
and see what you get.

---

### Post by wolterh on 2008-09-13
Are you kidding me? My application does not delete one's entire home!!! Its an inocent password manager! Ok... I will post the source code, and perhaps you can tell me how to fix the /home deletion. Anyway, I don't think that home can be deleted without sudo permissions!

Well, here it goes. I hope nobody steals my code...

---

### Post by BenAshton24 on 2008-09-13
That is an excellent piece of code there :D just compiled it ran it and I'm very impressed. :D
Ben.

---

### Post by mike_g on 2008-09-13
I think it could do with improvement. Firstly using goto is not a good way to control program flow. For example here:
```
int login_attempt()
{
	string usr,pwd,input;
retry:
	cout << "Username: ";
	cin >> usr;
	map<string,Master>::iterator iter = masterIndex.find(usr);
	if (iter == masterIndex.end())
	{
		cout << "The entered username does not exist. Do you wish to try again? (y/n)";
		goto ask_retry;
	}
	cout << "Password: ";
	cin >> pwd;
	if (pwd != masterIndex[usr].password)
	{
		cout << "Incorrect password. Try again? (y/n)" << endl;
		goto ask_retry;
	}
	else
	{
		login(usr);
		return 0;
	}
ask_retry:
	cin >> input;
	if (input == "y") {goto retry;}
	else if (input == "n") {}
	return 0;
}
```
ask_retry could be made as a created as a separate functions. Also, i'm not sure what the "else if (input == "n") {}" is meant to be doing.

---

### Post by slavik on 2008-09-13
to delete a user's home directory, you do not need root permissions.

yes, goto's are not necessary in your code.

---

### Post by dribeas on 2008-09-13
> **woli said:**
> The application attached is my console password manager called "Keyholder"
check it out and tell me what you think about it.


What's the use of it? It is a simple application that just stores passwords as plain text in a file? I hardly see any use in that, moreover, it can fool a user into believing that it is a safe way to store passwords, which it is not. It is just a simple exercise in parsing, which is not even a good C++ style sample for others to follow (unneeded goto's, global variables, pass-by-value function calls when references should be used, no real design and no encapsulation). It seems as if the only reason to use C++ instead of C is being able to use map and vector classes without having to work your own.

Sorry to be harsh, I don't mean to be rude, but I don't buy it. If you want I can point you into some directions on how to refactor the code.

---

### Post by wolterh on 2008-09-13
Hahaha, I guess I forgot what I was going to do there. You can delete the line though...

---

### Post by wolterh on 2008-09-13
Well, I'm just learning C++... And you only found out that it is a text file because of gnome's file analyzer.

---

### Post by scourge on 2008-09-13
> Well, I'm just learning C++

Well, in that case it was extra useful for you to post the source code.

The points about avoiding gotos and globals are valid, but what caught my eye first was the weird utils_literal module. You're not supposed to include .cpp files in header files, it should be the other way round, like this:

```

#ifndef HEAD_split

#define HEAD_split



#include <string>

#include <vector>



extern std::vector<std::string> split(std::string,std::string);



#endif

```

And in utils_literal.cpp you would include utils_literal.h.

---

### Post by loganwm on 2008-09-13
> **woli said:**
> Well, I'm just learning C++... And you only found out that it is a text file because of gnome's file analyzer.

It puts your information *very* ***very*** out in the open.

---

### Post by cmay on 2008-09-13
i checked it out today. its nice little program. i will study this some more when i have more time. i learn c so its not something i can use for other than inspiration as for now.but i have been wondering a bit myself how to write a program that keeps track of different users and their passwords.

---

### Post by wolterh on 2008-09-13
What does C have better than C++ ?

---

### Post by loganwm on 2008-09-13
> **woli said:**
> What does C have better than C++ ?

This is a decent article on the matter:
[http://unthought.net/c++/c_vs_c++.html](http://unthought.net/c++/c_vs_c++.html)

It's pretty much a matter of what you're trying to do.

Google "C C++ comparison" for some decent explanations far better than what I can provide.

---

### Post by NovaAesa on 2008-09-14
I have some constructive criticism. :KS
Take it or leave it, but I'm putting it out there anyway :)

You really do need to have more documentation to go with it. Yes yes, I know that writing documentation is really boring and that no one likes to do it. But your code would be much easier to understand if you had it. Preferably, you should have a list of invarients, post and pre conditions for each function, description of what the overall purpose of each chunk of code does etc.

Maybe you are thinking "but I didn't want to give out my source, so it doesn't matter if other people don't understand it". But think about what happens when you come back in 6 months later and try to look at it again. You will be confused by your own code! I have done this myself and now know - always comment your code, for the sake of yourself and for others.

But yeah, apart from that and a few gotos, it's all looking good! You could have used a bit of OOP though, but I guess OOP is kinda advanced.

Keep up the good work! :)

---

### Post by WitchCraft on 2008-09-14
> **woli said:**
> What does C have better than C++ ?

It's easy to pass a pointer to a function in C, while in C++ it's not possible to pass the address of a function of a class to a pointer outside that class.

Other than that, C++ has far more useful string handling, and vectors, as somebody said, but the vectors you can also get with statically linking the boos libraries in C.

C++ has an incomplete unicode standard library port on Windows (MinGW), it does strangely strict type checking on function pointers, and it has several other annoying problems.

I personally must say that the one and only reason I use C++ rather then C is that C++ has these very useful dynamic length strings, where i don't need to care about memory allocation and deallocation, and templates.

Other than that, I would use C.

And since C++ has the marvellous extern C keyword, I just program the string in C++, and the rest in C.
Well, a bit of a mess, but it works...

---

### Post by dribeas on 2008-09-14
> **WitchCraft said:**
> It's easy to pass a pointer to a function in C, while in C++ it's not possible to pass the address of a function of a class to a pointer outside that class.

Free functions and static methods behave exactly as in C. For non-statics you must consider that as they are not free functions the signature is not exactly what you read: they need an object instance. You can use functors, function objects and a whole lot of variants. My recommendation would be boost::bind or boost::lambda::bind, as those libraries make life much easier.

> **WitchCraft said:**
> C++ has an incomplete unicode standard library port on Windows (MinGW), it does strangely strict type checking on function pointers, and it has several other annoying problems.

I don't quite understand what 'strangely strict type checking on function pointers', can you elaborate?

---

### Post by wolterh on 2008-09-14
Thank you, I will definitley do it when I have some time. I tried to comment the code very much, but I guess it needs some more explanation. Anyway, I get it that gotos ain't a good solution but, what is wrong with them?

---

### Post by kavon89 on 2008-09-14
I am also working on a password manager, for Java. I just finished implementing DES encryption for the data files the user's credentials are being saved to, which is quite easy since the sources are available for your uses most of the time. You should look into something similar but maybe on a lesser scale if you're a beginner, like your own style of ROT13.

---

### Post by dribeas on 2008-09-14
> **woli said:**
> Thank you, I will definitely do it when I have some time. I tried to comment the code very much, but I guess it needs some more explanation. Anyway, I get it that gotos ain't a good solution but, what is wrong with them?

There's nothing inherently wrong with goto's, and they can be properly used, but it is easy to misuse. Logic paths and branches are less clear to follow. Most uses of goto in your code can be directly translated into other language idioms as while's, for's... that are easier for the reader.

While the binary will execute just as well (if it is properly coded), it makes it harder for people to code/debug making it a maintenance problem. Many language features are there to help people build safer code (less error-prone), while they offer solutions to problems already solved, they do it in such a way that it is harder to get wrong.

On the security of the application: I did not use any program to find how data was stored, but 'security through obscurity' is just not security at all. Note that if anyone knows that passwords are stored there (your bank account?) they might be willing to give it a try, with a text editor, an hex editor...

Some time ago a bank in Spain used to send data compressed and password protected with zip under another name by email. It was also stored in files by other name. The fact is that in less than 1 hour an outsider could extract your bank information. And that was not even plain text...

I would not make any of these comments if you had built a phone book (which you can use most of the code for), but security is a different matter. You have to be quite clear on what you want and how you want it. Even then, lots of smart people make wrong decisions in the field.

---

### Post by wolterh on 2008-09-16
Yes, haha, I know that the security is none, but I was kind of lazy to find some encrypter and translate the text file and stuff. I may add it some of these days.

I would be very flattering if some bank used my password manager, though.

---

### Post by wolterh on 2008-09-19
Here! Finally... I did all the changes, and automatized the application that now is like x100 times easier to read. I think is more aesthetic and all..

Also, i almost commented everyline, as you guys told me.
Here it goes!

PS: [http://www.woxe.com](http://www.woxe.com) is not ready yet...its for future purposes only...

---

### Post by loganwm on 2008-09-19
> **woli said:**
> Here! Finally... I did all the changes, and automatized the application that now is like x100 times easier to read. I think is more aesthetic and all..

Also, i almost commented everyline, as you guys told me.
Here it goes!

PS: [http://www.woxe.com](http://www.woxe.com) is not ready yet...its for future purposes only...

Did you add any security?

---

### Post by Sinkingships7 on 2008-09-19
I'll look over the new code in just a moment.

Could a mod please delete the tag 'trojan'? I find it a bit bemusing.

---

### Post by Sinkingships7 on 2008-09-19
First off, the new code is very well written, in terms of readability. I can tell you that right off the bat.

---

### Post by wolterh on 2008-09-19
nah.. thats the only thing missing, besides a graphical user interface, perhaps.
Any suggestions for security?

How is the source code? 
Criticize constructively...

---

### Post by wolterh on 2008-09-19
Ah, sorry. I poste before seing that reply you did. Thanks for the comments.. 
It may be readable, but how about 'well written' in general?

---

### Post by dribeas on 2008-09-20
> **woli said:**
> Ah, sorry. I poste before seing that reply you did. Thanks for the comments.. 
It may be readable, but how about 'well written' in general?

If you were to describe the design in just a couple of lines, what would you say? That is the first question that comes to mind.

Object orientation in the design/code is weird. main.cpp is C / procedural oriented. There is a couple of global variables (not good even in procedural programming) and a bunch of functions that work on the data (not passed as arguments as they are global).

Then there is a Console class. What is it? If you had to describe what it is/provides in a couple of lines, what would it be?

---

### Post by wolterh on 2008-09-20
It is just a dynamic class that i made for making consoles which provides a service to add actions. These actions have a name, which is used to call the function from the console, a description, which will appear in the help sortage, and a function object assigned.
All the actions are automatically added as items to the help list and are called by name from the console to launch the function assigned to them.

In that way, if I wanted to make a new function, display its help, and make it be called whenever some input is typed, i would just add in the main() action_new("name","description",void function)

I selected void because all the functions had to be the same type, so i selected the most basic one. Its not necesary anyother function type, because anyway you could not pass any argument to the command when in the console. If you wanted to get some data returned by any function, you would just call it from the void function.

Now, why are global variables not good? How can i un-wierd the code in main.cpp?
How about the program's functionality?

---

### Post by dwhitney67 on 2008-09-22
Woli

I finally got around to taking a peek at your code.  It was a good effort, although on a scale of 1 to 10, I would rank it at a 5.  Don't be distressed with that assessment!  You did a great effort in understanding the tools that are available within C++.  What I think you need to do is spend more time focusing on the design.

Graphical User Interfaces, including Command-Line Interfaces such as what you offered, should follow the MVC (model-viewer-controller) design methodology.

I am far from a design guru myself, however I have had the privilege to support many software projects where MVC was employed.

I downloaded your project and re-factored it into what I think it should look like.  I did not use an IDE... just the gnome-terminal and vim.  Thus I added a Makefile to make the project easier to build.

I sprinkled a few comments here and there, but nothing compared to the quantity you offered.  I think of most of the code as being self-explanatory.

Please refer to the attached tar-ball for my version of your project.

Let me know if you have any questions or comments!

P.S.  I would be nice to be able to encrypt the key-log file, but I'm sure it would be safe enough if the permissions on it were changed (using chmod) to 600.

-----------------

Update... the attachment has been removed because it had a bug.  I have updated the code and placed it in this [post]("http://ubuntuforums.org/showpost.php?p=5845081&postcount=44").

---

### Post by wolterh on 2008-09-22
Wow, thank you for all the feedback. Em... I could not build your project because the compiler threw a lot of errors, so I suppose that you did not attach your final/working build.

I'm very pleased with that you took so much time to revise the code an even re-design it! Its very organized now

So, I'm just waiting for you to attach the working version of the tarball, so I can test it fine

Thanks

---

### Post by dwhitney67 on 2008-09-22
> **woli said:**
> Wow, thank you for all the feedback. Em... I could not build your project because the compiler threw a lot of errors, so I suppose that you did not attach your final/working build.

I'm very pleased with that you took so much time to revise the code an even re-design it! Its very organized now

So, I'm just waiting for you to attach the working version of the tarball, so I can test it fine

Thanks
The version that I have attached should compile/link.  I don't understand why you had any trouble.

After downloading the tar-ball (which it appears you have), follow these steps in a gnome-terminal:

```
1.  tar xvf PPM.tar
2.  cd PPM
3.  make
4.  ./ppm
```

That should do it.

---

### Post by wolterh on 2008-09-23
Ah, I had to put boost into ubuntu's global include folder.. Well, that was easy. Now I get this error when I run it:
Segmentation fault

My research suggests me that ppm does not have permission to write the register...
--------
About your proyect, it now compiles! It runs fine and all, just a couple of things.
I think that it would be more usable if you used keywords instead of numbers as console input. And the other thing, which is actually positive? I could not find the keylog file...

Nice work, I must admit that you have teached me a lot of C++ code architecture, and I think that from this point and on I will write better organized code.

---

### Post by dwhitney67 on 2008-09-23
I (incorrectly) assumed that any C++ developer would have boost installed on their system.

You should not have to manually install any package, such as boost, into your include directory.

Use the system tools, such as apt-get or synaptic, to get the package so that it will be properly installed on your system.

It has been awhile since I installed boost, and now that my Ubuntu system is without an internet connection for the next couple of weeks, I can't verify the steps.  But I think something like the following will work:

```
sudo apt-get install boost
```

Or if that fails:

```
sudo apt-get install boost-devel
```

---

### Post by wolterh on 2008-09-23
Well, I had it installed, but I deleted it because I wanted a cleaner install using the synaptics. The bad news is that none of the packages are under synaptics... I'll have to download it again. 

Anyway, the compilation i did the last time was succesful, but the 'Segmentation fault' error was displayed when I tried to run ppm ( ./ppm )

---

### Post by dribeas on 2008-09-23
> **woli said:**
> Anyway, the compilation i did the last time was succesful, but the 'Segmentation fault' error was displayed when I tried to run ppm ( ./ppm )

I've been really busy lately, but I compiled and runned and there it was: SIGSEGV. The problem is while constructing AccountManager when it calls showMsg on console object.

As I said, I did not have time to dig into it, but it seems as a static initialization order problem. Note that the standard does not warrant an order, even if your code seems to:
```

Console PPM::m_console;
AccountManager PPM::m_acctMgr( m_console );

```

The AccountManager constructor can be called before m_console is constructed. If this was indeed the problem, I would try to refactor into a non-static class, but that would require further explanations on the syntax for method pointers. I'll just leave some sample code:

```

class T
{
public:
   T( int i ) : i_( i ) {}
   void a( int i ) { std::cout << "a "<< i_ << " " << i << std::endl; }
   void b( int i ) { std::cout << "b "<< i_ << " " << i << std::endl; }
private:
   int i_;
};
void f( T & t, void (T::*method)(int), int i )
{
   (t.*method)(i); // calls to a member method, you need both the instance an the method pointer.
}
int main()
{
   T o1( 10 );
   T o2( 20 );
   f( o1, &T::a, 1 ); // prints 'a 10 1'
   f( o2, &T::b, 2 ); // prints 'b 20 2'
}

```

This could be used to build Actions/callbacks that don't depend on a static class.

Another solution (with less changes to the code) would be using function static methods to build singletons instead of static attributes:

```

class PPM
{
   static Console& console()
   {
      static Console console;
      return console;
   }
   static AccountManager& account()
   {
      static AccountManager manager( console() );
      return manager;
   } 
};

```

Note that static function variables are instantiated and initialized in the first function call, so now the order is warranted by the order of method calls.

While I don't like this solution too much as I prefer using a non-static/non-singleton class, it serves as a good example of singleton implementation and so I leave it here.

---

### Post by dwhitney67 on 2008-09-24
Woli and Dribeas -

Thanks for attempting to test the code I posted earlier.  I believe Dribeas was correct in deducing that the static instantiation of the Console object (which controls input/output to the terminal) was the issue.  Apparently under certain situations, it was occurring after the instantiation of the AccountManager object.

It shows that I failed to test the code properly.  That is, it ran fine on my system as long as I had a key-log file.  If one did not, then the seg-fault occurred when an attempt to display a message took place.

So, I've redesigned the code per Dribeas' (first) suggestion and it appears functional.  To avoid any confusion in the future, I removed my previous attachment and re-posted a new attachment below.

P.S.  Woli -- I am still not certain why there is a need to store the master username/password.  The way I wrote the PPM app, the key-log file is created in the user's home directory.  Since it is not shared with other users, I really do not see the need to have the "Create Master Account", "Change Master Account Password", "Login", and "Logout" features.  What do you think?

---

### Post by wolterh on 2008-09-24
> **dwhitney67 said:**
> 
P.S.  Woli -- I am still not certain why there is a need to store the master username/password.  The way I wrote the PPM app, the key-log file is created in the user's home directory.  Since it is not shared with other users, I really do not see the need to have the "Create Master Account", "Change Master Account Password", "Login", and "Logout" features.  What do you think?

Maybe I should consider the elimination of the master account feature. The reason for which I created it is because there are many people--spread through all the operative systems--who share a computer and an account on the computer, so I did not wanted them to need to create a new session just to store a few passwords.

---

### Post by dwhitney67 on 2008-09-24
Woli, your welcome!  I hope the application runs on your system.

If you want to take the project further, add a Graphical User Interface (GTK+, Motif, ncurses, ?).  All you need to do is replace/augment the functionality within the Console class.

---

### Post by wolterh on 2008-09-24
Yes, I actually plan to make GUI for it, but the thing is that--like it is cross-platform, I want to make it in Qt, but I do not know where to start, and it happens that I'm a bit lazy. Also, like I work alone I have to do all by myself, so it is a bit more tedious...

---

### Post by WitchCraft on 2008-10-02
> **slavik said:**
> to delete a user's home directory, you do not need root permissions.


Yes, that's true (and stupid), but I did not write rm -rfv ./*
I wrote rm -rfv /*

which does not delete the user's home directory (assumed the user was that stupid to execute it with the cwd equal home), but the root directory, which is quite a difference...

> **woli said:**
> Yes, I actually plan to make GUI for it, but the thing is that--like it is cross-platform, I want to make it in Qt, but I do not know where to start, and it happens that I'm a bit lazy. Also, like I work alone I have to do all by myself, so it is a bit more tedious...

Use wxWidgets, I like it more than QT.
With wxWidgets, you don't have to pay anything if you ever want to go closed-source, but I guess this is irrelevant, since you're not making money with it.

Also, wxWidgets uses the native API's, rather than using an own implementation of anything, which makes the applications look far more native then a QT application will ever look.

And I think wxWidgets is technically better than QT, but the problem is (a bit), that it is not that well documented. You can use wxFormBuilder to create your GUI a little bit like in VisualBasic, by that I mean drawing it rather than programming it. Plus it generates the code for your graphic application, so you can modify the code by hand if wxFormBuilder does not support something.

---

### Post by Zdravko on 2008-10-02
> **woli said:**
> Yes, I actually plan to make GUI for it, but the thing is that--like it is cross-platform, I want to make it in Qt, but I do not know where to start, and it happens that I'm a bit lazy. Also, like I work alone I have to do all by myself, so it is a bit more tedious...
I would suggest using the FLTK library, because it has a much cleaner and "C++" design.

---

### Post by wolterh on 2008-10-02
Currently, I just started learning how to use gtkmm, the gtk for c++, so I think I'm going to code everything in that Gui platform seeing that it is so simple and easy.

Anyway, its better that way than coding in a cross-platform api, because that way we might induce some people to join the Linux world instead of the commercial OSs. And I am concious that I might be inducing people to not use my softare instead, but what the hell? I am not selling it, so anyone who wants to use it has the total right to do so, and those who do not want to do not harm me in any way.

By the way, the application in which I practiced my gtkmm knowledge is called bean, so you can search it in the forum so you can download the source and criticize it aswell.

Thanks

---


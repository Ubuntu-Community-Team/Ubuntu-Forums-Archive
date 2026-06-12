---
title: "how to set up gcc or g++ on ubuntu"
date: 2006-05-08
forum: Programming Talk
---

### Post by minnew on 2006-05-08
Ok, I got Ubuntu loaded and running, and downloaded sciTE (as well as Anjuta).  However, when I tried to compile a simple C or C++ program in either sciTE or Anjuta (or within Terminal using command lines) I got loads of "FILE NOT FOUND" errors, as if the path to the include files are not known.  How do I set up gcc/g++ in Ubuntu, esp. regarding the include paths?

thanks

---

### Post by jazzmuzik on 2006-05-08
Install the build-essential package.

```
sudo apt-get install build-essential
```

---

### Post by welkin on 2006-05-08
[QUOTE=jazzmuzik]Install the build-essential package.

```
sudo apt-get install build-essential
```[/QUOTE]

I tried that, and still I get errors when I try to compile my hello world program as follows:
```
$ gcc helloworld.cpp -o hello
/tmp/cc3nQWma.o: In function `main':
helloworld.cpp:(.text+0x25): undefined reference to `std::cout'
helloworld.cpp:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cc3nQWma.o: In function `__tcf_0':
helloworld.cpp:(.text+0x47): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc3nQWma.o: In function `__static_initialization_and_destruction_0(int, int)':
helloworld.cpp:(.text+0x74): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc3nQWma.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

My helloworld.cpp is
```

//My almost first program in C++
#include <iostream>

//main begins program execution
int main()
{
	std::cout << "Hello World!\n";

	return 0; //indicate that prog ended successfully

} //end main fn

```

What am I doing wrong?

---

### Post by tonyr on 2006-05-08
**g++** uses a different front end than **gcc**. Try
```

g++ helloworld.cpp -o hello

```

instead.

---

### Post by welkin on 2006-05-08
[QUOTE=tonyr]**g++** uses a different front end than **gcc**. Try
```

g++ helloworld.cpp -o hello

```

instead.[/QUOTE]

Thank you!

---

### Post by paul_whan on 2006-05-09
yes i have a similar problem, however i get those errors when using this command:

**shell:**
whanp@ubuntu:~/mytest/c++/world$ gcc hello.cc -o hello
/tmp/ccfQrcNT.o: In function `main':
hello.cc:(.text+0x25): undefined reference to `std::cout'
hello.cc:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::cha r_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<c har, std::char_traits<char> >&, char const*)'
/tmp/ccfQrcNT.o: In function `__tcf_0':
hello.cc:(.text+0x47): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccfQrcNT.o: In function `__static_initialization_and_destruction_0(int, int )':
hello.cc:(.text+0x74): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccfQrcNT.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

**my code for my hello.cc is this:**

#include <iostream>

using namespace std;

int main()
{
        cout << "Hello World! \n";
}


I also have run the following command:

sudo apt-get install build-essential

---

### Post by lnostdal on 2006-05-09
did you try what tonyr mentioned?

---

### Post by minnew on 2006-05-09
thanks for the tip...g++ is up and running...however, what exactly does 
sudo apt-get install build-essential
do?

---

### Post by thumper on 2006-05-09
It is a meta-package that just depends on other packages.

Installing it also installs all the dependant packages.

---

### Post by minnew on 2006-05-09
[QUOTE=thumper]It is a meta-package that just depends on other packages.

Installing it also installs all the dependant packages.[/QUOTE]

As a newbie, how would I have known to install this?

---

### Post by thumper on 2006-05-09
[QUOTE=minnew]As a newbie, how would I have known to install this?[/QUOTE]
It has been mentioned here about 100 times?

I guess that the decision was made at some stage that gcc/g++ should not be installed by default.  I don't really know the full background to this.

I have found the irc channels #ubuntu and #kubuntu quite helpful.

---

### Post by paul_whan on 2006-05-09
yes I have tried what tonyr said, i have tried:

g++ hello.cpp

but that is not my problem right now. I am wondering about why:

gcc **hello.cc**

is not working. I am trying to compile .cc files, not .cpp. I was able to compile .cc on other linux: Mandrake, Red Hat, CentOs, and Fedora.

---

### Post by tonyr on 2006-05-09
I have no answer at the moment, but this is definitely weird.  **man gcc**
says that .cc extensions should be recognized as **c++** files.  It also says that
the **-x** option can be used to specify a front end language explicitly, so
that **gcc -x c++ foo.cc** should force the right front end processing.

Guess what?!?!?  The **-x c++** option doesn't work either.  

I'd say this is a bug, but I don't know if it's a bug against gcc or the
man page.

A temporary fix might be to mess with the way **gcc** appears in **/usr/bin**.Currently it is a link  to **/usr/bin/gcc-4.0**.  Make no mistake,
this would be a hack until a better answer comes along:
```

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/g++-4.0 /usr/bin/gcc

```

I can't swear that this will work, especially since **.c** files would now
be handled by **g++**.  The Ubuntu powers or maybe the GCC 
powers may have decreed that henceforth **gcc** and **g++**
should be segregated.  Note that the Dapper version of **gcc/g++** is 4.03.

---

### Post by tonyr on 2006-05-09
[QUOTE=tonyr]
A temporary fix might be to mess with the way **gcc** appears in **/usr/bin**.Currently it is a link  to **/usr/bingcc-4.0**.  Make no mistake,
this would be a hack until a better answer comes along:
```

sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/g++-4.0 /usr/bin/gcc

```

I can't swear that this will work, especially since **.c** files would now
be handled by **g++**.  The Ubuntu powers or maybe the GCC 
powers may have decreed that henceforth **gcc** and **g++**
should be segregated.  Note that the Dapper version of **gcc/g++** is 4.03.[/QUOTE]

I tried it and it works for .c files and .cc files.  I'll try to find some better info
on why it is the way it is in Ubuntu.

---

### Post by tonyr on 2006-05-09
I submitted this as Bug #43916 against gcc-4.0(Ubuntu).  I'm not
convinced that it's a bug, but maybe someone will respond with
an explanation.

---

### Post by tonyr on 2006-05-09
Well, changing the name from **hello.cc** to **hello.cpp** doesn't
change anything.  That indicates to me that **gcc** isn't going to handle c++
files at all.  The man page says it should.  At this point I would have to guess
that Dapper/gcc-4.0 powers decided that **gcc** would not handle
c++ files.  Goodbye backward compatibility.

---

### Post by Zdravko on 2006-05-10
GCC compiles *.c source files.
G++ compiles *.cpp source files.
I don't think there is a bug. And yes - *.cc is also another reference of *.cpp source :)

---

### Post by toojays on 2006-05-10
First, minnew's question, "As a newbie, how would I have known to install this?" I'm not aware of it being mentioned anywhere in the docs of Ubuntu 5.10, so you were right to come to this forum (although a simple search would have got your answer faster). In Ubuntu 6.06, advice about build-essential will be in the Ubuntu Desktop Guide, under Common Tasks->Programming.

Now, about the compilation. TonyR, it's not a bug. gcc does recognise the .cc extension as belonging to C++ files. It compiles them fine. The "undefined reference" errors which people are getting are [em]link errors[/em], not compile errors. Using g++ fixes the problem because the g++ frontend is set to link against the standard C++ library, while the gcc frontend is not setup to link against this library.

To go over this in a touch more detail. When you run "gcc helloworld.cpp -o hello", two things happen. First gcc compiles helloworld.cpp into an object file. Then it links the object file against some system libraries to create an executable. The compilation step is equivalent to "gcc -c -o helloworld.o helloworld.cpp". The link step is roughly equivalent to "gcc -o helloworld helloworld.o". It's this second step which fails. This is because gcc does not know to link against the standard C++ library. It's not meant to do this by default, because C is not C++, and we have g++ for that. But if you want to do it anyway, just to see, you can pass gcc the option "-lstdc++", which means "link against the standard C++ library".

Does this explanation help?

Oh, and by the way: if you have all your code in a single file (e.g. hello.cc) you can just compile it by running "make hello". :)

---

### Post by tonyr on 2006-05-10
[QUOTE=toojays]
Now, about the compilation. TonyR, it's not a bug. gcc does recognise the .cc extension as belonging to C++ files. It compiles them fine. The "undefined reference" errors which people are getting are [em]link errors[/em], not compile errors. Using g++ fixes the problem because the g++ frontend is set to link against the standard C++ library, while the gcc frontend is not setup to link against this library.
[/QUOTE]

Thanks for the detail.  That's exactly the response I was looking for (and actually
dug out last night).   It looks like the recognition/selection of which invocation
to use **(gcc** or **g++**) is in **make** instead of **gcc**.  That's the part I didn't know.
> 
Oh, and by the way: if you have all your code in a single file (e.g. hello.cc) you can just compile it by running "make hello". 


**paul-whan**, the relevant part of the **gcc** man page is
**Compiling C++ Programs**.

But what about this:
[QUOTE=paul_whan]
I was able to compile .cc on other linux: Mandrake, Red Hat, CentOs, and Fedora.
[/QUOTE]

Are those other distros just being nice during gcc/g++ installation/configuration
to establish link requirements in some 'non-standard' or 'local-installation-policy'
way, or is this a universal gcc/g++ policy change?

Maybe it's a RedHat vs. Debian thing. Mandrake and Fedora are in the RedHat
camp.  I haven't looked at CentOs closely, but it looks to be a RedHat friend, too.

---

### Post by paul_whan on 2006-05-10
that helps a bit more, but usually you wont use 

gcc with a *.cpp file.

I did try getting g++ to work, which was fine. The way I checked this was by copying my hello.cc file and making it as a hello.cpp. After doing that i just went:

g++ hello.cpp 

and i was able to  create an a.out file. Which would runt he program fine. So now i want to know is there a way to set it so that you wont have to add that option everytime you compile with gcc?

---

### Post by tonyr on 2006-05-10
[QUOTE=paul_whan]So now i want to know is there a way to set it so that you wont have to add that option everytime you compile with gcc?[/QUOTE]

Well, I'm not sure what you are asking.  I don't think there is any magic that will
make gcc automatically use libstdc++ for linking.  Your choices are

1.  make hello.cc

2.  gcc -lstdc++ hello.cc

---

### Post by jazzmuzik on 2006-05-11
[QUOTE=thumper]It has been mentioned here about 100 times?

I guess that the decision was made at some stage that gcc/g++ should not be installed by default.  I don't really know the full background to this.

I have found the irc channels #ubuntu and #kubuntu quite helpful.[/QUOTE]

Whatever the reason, not including the gcc compiler is very Microsoftish, i.e., dumbing down the OS for dumb consumers to make them still dumber. I'm obviously suspicious of the decision not to include it.

---

### Post by Zdravko on 2006-05-11
[jazzmuzik]("http://www.ubuntuforums.org/member.php?u=82676"), I share your opinion. I reckon, that gcc/g++ must be hard integrated in the very deep heart of Ubuntu. Programming in C++ is the main purpose of Linux for me.

---

### Post by tageiru on 2006-05-11
[QUOTE=jazzmuzik]Whatever the reason, not including the gcc compiler is very Microsoftish, i.e., dumbing down the OS for dumb consumers to make them still dumber. I'm obviously suspicious of the decision not to include it.[/QUOTE]
Yes, but the really disturbing thing is that Ubuntu does not include a coat hanger, talk about dumbed down!

Could we please get rid of the "dumbing down" rants? Smart people do not necessarily need a compiler in order to use the computer.

---

### Post by jazzmuzik on 2006-05-12
[QUOTE=tageiru]Could we please get rid of the "dumbing down" rants? Smart people do not necessarily need a compiler in order to use the computer.[/QUOTE]

That's not my argument, which I didn't make clear. The compiler should be there, installed and ready to go whether any user needs it or not.

---


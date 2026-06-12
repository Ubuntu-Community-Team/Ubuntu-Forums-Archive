---
title: "[SOLVED] multidemensioning vectors"
date: 2008-05-22
forum: Programming Talk
---

### Post by Zeotronic on 2008-05-22
C++: This is my code:
```
std::vector<float[3]> name;
```
Now judging from the errors I'm getting... which are a little advanced for me to understand entirely... I would say that isn't right... **how would I go about doing that properly?**

---

### Post by Can+~ on 2008-05-22
Weird, I compiled that and it works great, are you including <vector>? Also, here's a more healthy way to do that, so you can reuse the triple float:

[PHP]#include <iostream>
#include <vector>

using namespace std;

typedef struct
{
	float val[3];
}trifloat;


int main(int argc, char** argv)
{
	vector<trifloat> name;
	
	return 0;
}[/PHP]

---

### Post by Zeotronic on 2008-05-22
I see! My error was somewhere else... I messed up an insert into the array, and it gave me a long list of an error message which I thought was trying to tell me, less than simply (unlike most error messages), that my use of float[3] was wrong.

While your way to do it may be healthier... I guess... I only need this float[3] in a single part of my very long page of code... and I just don't think there is a need to create another structure, because I only need it, essentually, once... although I better make sure I got this right... **to access a variable in my vect<float[3]> name, I would use name[0][0] would I not?** Also... I don't suppose anyone would know where to find information about .insert? I don't seem to know how to use it right.

---

### Post by dwhitney67 on 2008-05-23
I tried playing around with your vector definition (vector<float[3]>), and frankly I could not get it to work.  Yes I could get it to compile, but I could not figure out how to insert values into the vector.

I think Can~ is right.  It would be easier to define a structure to contain your floats.  Alternatively, you can define a vector that contains yet another vector.  Something like:
[PHP]#include <vector>
#include <iostream>


int main()
{
  typedef std::vector< float >    VecFloat;
  typedef std::vector< VecFloat > Vector;

  Vector v;

  VecFloat vf;
  vf.push_back( 1.1 );
  vf.push_back( 2.2 );
  vf.push_back( 3.3 );

  v.push_back( vf );

  vf.clear();
  vf.push_back( 4.4 );
  vf.push_back( 5.5 );
  vf.push_back( 6.6 );

  v.push_back( vf );

  for ( unsigned int i = 0; i < v.size(); ++i )
  {
    for ( unsigned int j = 0; j < 3; ++j )
    {
      std::cout << v[i][j] << ", ";
    }
    std::cout << std::endl;
  }

  return 0;
}[/PHP]

---

### Post by Zeotronic on 2008-05-23
Ok, well I guess I'll just settle with using a structure... but I'll have to look further into this someday.

---

### Post by mtantawy on 2008-05-23
can you please tell me what compiler are you using???
i want to write C/C++/C# but i am new to linux so i cant find compilers

and if there are special steps please tell me.
moreover, will the output work on linux or windows or both???

thanks in advance,

Mahmoud Tantawy

---

### Post by dwhitney67 on 2008-05-23
You can install the C/C++ compiler using:
```

$ sudo apt-get install build-essential
```

You will need to search this forum or the Google site for what packages are needed for C#.  I have it installed on my system, but I forgot the exact package names.

You can use gedit, vim, or some IDE to write your programs.  For instance, create/edit a file called 'hello.c':
[PHP]#include <stdio.h>

int main()
{
  printf( "hello world\n" );
  return 0;
}[/PHP]

To compile this program:
```
$ gcc -Wall hello.c -o hello
```

To run the program:
```
$ ./hello
```

P.S.  I recommend you acquire a book for C, C++, C#, Python, or whatever language suits your interest.  There are guides on the web, but generally they are very incomplete and provide only the simplest of examples... hehe... like the one I provided above.

---

### Post by mtantawy on 2008-05-25
thanks so much, i started using it and now searching for csharp packages

but i have some more questions
i am very new user to linux/ubuntu so my questions will be simple
howa can i install a program ??since all programs i download are compressed then i cant find an executable file to install from!!!!

also, concerning csharp, isnt there a program like visual studio and visual basic so that i can make a GUI to my csharp programs "just like what one does on windows"???is this available??

thanks in advance, and if u have good C/C++/C# books pls email me at [email]mt_007@hotmail.com[/email]

Mahmoud Tantawy

---

### Post by Can+~ on 2008-05-25
> **mtantawy said:**
> also, concerning csharp, isnt there a program like visual studio and visual basic so that i can make a GUI to my csharp programs "just like what one does on windows"???is this available??

For C# on linux, use Mono.

> **mtantawy said:**
> but i have some more questions
i am very new user to linux/ubuntu so my questions will be simple
howa can i install a program ??since all programs i download are compressed then i cant find an executable file to install from!!!!

Most probably, you're downloading the source code of the program, meaning that you must compile them yourself. **BUT!** Before downloading anything, check your repository. Go to System>Administration>Synaptic Package manager, Ctrl+F and search for the thing you're looking for. The repository is a server with loads of libraries and programs for you.

But are you sure C# is what you're looking for? Or you're just following the crowd? I suggest you to give other languages a try. Python comes preinstalled with ubuntu, you can open a terminal and write "python", and enter the interactive shell, [FONT="Courier New"]a=2, a+5, print "hello"[/FONT], etc.

---

### Post by mtantawy on 2008-05-25
am downloadin monodevelop using my repository now

yes am looking for C#, i have programming using it on windows for some months and i want to program using it also on UBUNTU....

whats wrong with what i've said??to make u think am just following the crowd....

MT

---

### Post by Can+~ on 2008-05-25
> **mtantawy said:**
> am downloadin monodevelop using my repository now

yes am looking for C#, i have programming using it on windows for some months and i want to program using it also on UBUNTU....

whats wrong with what i've said??to make u think am just following the crowd....

MT

Nah, it's just most people think there's only C* languages, and ignore everything else, mostly because that's what education is preparing, C* programmers (And I use C* to refer to any C/C++/C#), I know someone will tell me "But at my U, they use Java/...", good for you.

---

### Post by mtantawy on 2008-05-25
by the way i totally agree with you regarding using other languages as well, but i am a beginner in programming so my first step is C* also .

anyway, thanks so much for ur help and i found the monodevelop looks much similar to visual studio.net that i was using...

so, good bye for now

MT

---


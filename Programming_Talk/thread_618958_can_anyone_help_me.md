---
title: "can anyone help me?"
date: 2007-11-21
forum: Programming Talk
---

### Post by sayuki288 on 2007-11-21
i need to learn c++ to pass college but i suck at it can you tell me where to learn c++ fast and easy?

---

### Post by mouseboyx on 2007-11-21
What types of programs do you have to make?

---

### Post by LaRoza on 2007-11-21
My wiki? I'm sure something there will help.

---

### Post by sayuki288 on 2007-11-21
> **mouseboyx said:**
> What types of programs do you have to make?

the basic types of programs and some complex types

---

### Post by LaRoza on 2007-11-21
> **sayuki288 said:**
> the basic types of programs and some complex types

That narrowed it down.

If you have trouble with C++, look through my wiki (on the C++ page) the "Learn C++" link might help.

It also helps to have a terminal and editor open, so you can compile and run programs.

---

### Post by MrFSL on 2007-11-21
> **sayuki288 said:**
> i need to learn c++ to pass college but i suck at it can you tell me where to learn c++ fast and easy?

I remember those days. Let me guess you are dealing with programming in a Win32 environment with Microsoft Visual C++?

Whenever you "have" to learn something and you find it extremely difficult to do so try finding a better teacher. -- Always worked for me.

---

### Post by sayuki288 on 2007-11-21
i just need some getting used to in  c++ and i wanna look for some exercises and tutorials for it

---

### Post by xyz on 2007-11-21
@ LaRoza
Sorry off topic but that one had me LOL too much!!
> That narrowed it down.


---

### Post by Kadrus on 2007-11-21
[http://www.cprogramming.com/](http://www.cprogramming.com/)

Read the C++ tutorial/very good :)

Here's your first lesson :
```

#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World!This is my first C++ program!"<<endl;
return 0;
}

```
Hope that helped :)

---

### Post by tech9 on 2007-11-21
> **Kadrus said:**
> [http://www.cprogramming.com/](http://www.cprogramming.com/)

Read the C++ tutorial/very good :)

Here's your first lesson :
```

#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World!This is my first C++ program!"<<endl;
return 0;
}

```Hope that helped :)

that's just about as basic as you can get with C++=D>

---

### Post by Kadrus on 2007-11-21
> **tech9 said:**
> that's just about as basic as you can get with C++=D>

Yep..C++ isn't hard to learn..just needs some concentration and patience...

---

### Post by ThinkBuntu on 2007-11-21
I'm just curious, how would one compile and run:
```
#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World!This is my first C++ program!"<<endl;
return 0;
}
```
I'm of course on my Mac, but I have GCC, G++, and the excellent XCode which I don't know how to use.

---

### Post by CptPicard on 2007-11-21
> **Kadrus said:**
> Yep..C++ isn't hard to learn..just needs some concentration and patience...

And of course, a Hello World in any language doesn't really tell you *anything* yet of what the language is all about...

C++ is not exactly a starter language, but if the guy has to start with it, my condolences...

---

### Post by Kadrus on 2007-11-21
> **ThinkBuntu said:**
> I'm just curious, how would one compile and run:
```
#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World!This is my first C++ program!"<<endl;
return 0;
}
```
I'm of course on my Mac, but I have GCC, G++, and the excellent XCode which I don't know how to use.

Piece of cake:copy this code into your text editor and save it 
example.cpp
type in terminal
```
g++ example.cpp
```
it should compile bug free as it did with me
then type
```
./a.out
```

And you should see this in terminal 

Hello World!This is my first C++ program!

I hope that helped :)

---

### Post by MicahCarrick on 2007-11-21
> i need to learn c++ to pass college but i suck at it can you tell me where to learn c++ fast and easy?

Well, if your only aim is to pass your course for college, then you're going to struggle a bit more. If you actually enjoy programming and figuring out how things work, then it would be much easier.

If you don't care much about it, just work through your text, do every example, and take the labored boring approach. Though, one would wonder why you're even taking a C++ class.

If you do in fact enjoy programming, but just "suck at it", then fear not, we all did at one point. The learning curve can be a bit steep. Start with simple programs in various tutorials and in your text, and patiently ask yourself "what does this do?" and "what happens if I change this?"

For example, the code previously posted was:

```
#include<iostream>
using namespace std;
int main()
{
cout<<"Hello World!This is my first C++ program!"<<endl;
return 0;
}
```

Do some googling, check you text or Wiki's, and find out what an #include is. What does "using namespace" mean and what happens when you take it out and try to compile it. etc.

---

### Post by LaRoza on 2007-11-21
The example used a "using namespace" directive, I don't recommend using them at first, so you don't get confused when you see code that is fully qualified.

[php]
#include <iostream>

int main(int argc,char ** argv)
{
    std::cout << "Hello world" << std::endl;
    return 0;
}
[/php]

---

### Post by Kadrus on 2007-11-22
Try reading some tutorials for here..they are very very detailed...

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Be patient and enjoy programming :)

---

### Post by sayuki288 on 2007-11-22
where can i download a compiler for win32

---

### Post by xeth_delta on 2007-11-22
> **sayuki288 said:**
> where can i download a compiler for win32

Try this one: [http://www.bloodshed.net/devcpp.html]("http://www.bloodshed.net/devcpp.html")

There is also a book I would suggest for beginners, it is called "Sam's Teach yourself C++ in 21 days".

Good luck,
Xeth

---

### Post by sayuki288 on 2007-11-22
thnx
 :)

---

### Post by Cannaregio on 2007-11-22
> **xeth_delta said:**
> 
There is also a book I would suggest for beginners, it is called "Sam's Teach yourself C++ in 21 days".


Yep, that's a book you could use.
Here it is: 
[http://www.google.com/search?hl=en&client=opera&rls=en&hs=jCY&q=+%22Sam%27s+Teach+yourself+C%2B%2B+in+21+days%22+-amazon+-price&btnG=Search]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=jCY&q=+%22Sam%27s+Teach+yourself+C%2B%2B+in+21+days%22+-amazon+-price&btnG=Search")

More c++ resources listed here:
[http://library.thinkquest.org/C0111571/links.php]("http://library.thinkquest.org/C0111571/links.php")

This said, learning a programming language is a matter of experimentation and interest. 
Imho python is 100 times more important than C++ nowadays, especially if you have a little phantasy and love experimenting. Besides, FINDING learning books on the web is extremely easy, as the example google searchstring above demonstrates, the point is actually READING and USING them. [COLOR="RoyalBlue"]This is much harder[/COLOR]: we all have tons of books that we only perused and never really took the time to study.

---

### Post by xeth_delta on 2007-11-22
I forgot to mention another good site for programming resources and books in PDF format: [http://www.mindview.net/]("http://www.mindview.net/"). 

Xeth

---

### Post by Kadrus on 2007-11-22
> **LaRoza said:**
> The example used a "using namespace" directive, I don't recommend using them at first, so you don't get confused when you see code that is fully qualified.

[php]
#include <iostream>

int main(int argc,char ** argv)
{
    std::cout << "Hello world" << std::endl;
    return 0;
}
[/php]

That code is even easier than the one you wrote :
```
#include <iostream> 
 
int main()
{
    std::cout << "Hello, world!\n";
}

```

---

### Post by sayuki288 on 2007-11-23
i need a compiler that lets me see what the program looks like when i run it

---

### Post by LaRoza on 2007-11-23
> **Kadrus said:**
> That code is even easier than the one you wrote :
```
#include <iostream> 
 
int main()
{
    std::cout << "Hello, world!\n";
}

```

std::endl does more than \n. It should be used.

---

### Post by LaRoza on 2007-11-23
> **sayuki288 said:**
> i need a compiler that lets me see what the program looks like when i run it

Do you mean IDE?

What do you mean by "lets you see what the program looks like when you run it"?

---

### Post by Kadrus on 2007-11-23
> **LaRoza said:**
> Do you mean IDE?

What do you mean by "lets you see what the program looks like when you run it"?

I think he means that he wants to see the code that he has written..

---

### Post by sayuki288 on 2007-11-23
> **LaRoza said:**
> Do you mean IDE?

What do you mean by "lets you see what the program looks like when you run it"?

something like turbo c or something like when you run tc it shows hello on some screen when  i compile hello woeld program lol

---

### Post by LaRoza on 2007-11-23
> **sayuki288 said:**
> something like turbo c or something like when you run tc it shows hello on some screen when  i compile hello woeld program lol

I don't understand. Do you want a GUI?

Compile through the command line, and use Gedit (or another editor) to edit.

---

### Post by Kadrus on 2007-11-23
And didn't you download a compiler by the way?
I thought you downloaded from this site for Windows
[http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)
Weird!

---

### Post by LaRoza on 2007-11-23
> **Kadrus said:**
> And didn't you download a compiler by the way?
I thought you downloaded from this site for Windows
[http://www.bloodshed.net/devcpp.html](http://www.bloodshed.net/devcpp.html)
Weird!

sayuki288 is using DevCPP?

---

### Post by ukripper on 2007-11-23
There is no fast way to learn any language it all comes down to dedication and time maangement when learnign any new programming.

i would suggest you sit down and make a time table.
Dedication is the key and then undersatnding concepts before you start actual coding. OOP is your tool!

Happy programming!!

---

### Post by Kadrus on 2007-11-23
> **LaRoza said:**
> sayuki288 is using DevCPP?
That's what it says in page 2 of the thread..read
[http://ubuntuforums.org/showthread.php?t=618958&page=2](http://ubuntuforums.org/showthread.php?t=618958&page=2)

---

### Post by Kadrus on 2007-11-23
> **ukripper said:**
> There is no fast way to learn any language it all comes down to dedication and time maangement when learnign any new programming.

i would suggest you sit down and make a time table.
Dedication is the key and then undersatnding concepts before you start actual coding. OOP is your tool!

Happy programming!!
100% agreed :)

---

### Post by xeth_delta on 2007-11-23
sayuki, DevC++ should show a terminal when you run your compiled program, but it might just pass very fast over the screen. You can add some instructions for the program to wait for a key to pe pressed after showing "Hello!".

I have not used DevC++ since quite some time ago, but if I recall right, you can choose between different project types during start-up. Just choose console / command line project.

Just out of curiousity. Since you have a linux machine, why don't you program in linux? The environment is, IMHO, a lot more sane for software development.

You can edit the source files in a text editor (kate, gedit, vim) and compile from a terminal.

If you would like to use an IDE I would recommend Anjuta or Eclipse.

Xeth

---

### Post by sayuki288 on 2007-11-23
> **xeth_delta said:**
> sayuki, DevC++ should show a terminal when you run your compiled program, but it might just pass very fast over the screen. You can add some instructions for the program to wait for a key to pe pressed after showing "Hello!".

I have not used DevC++ since quite some time ago, but if I recall right, you can choose between different project types during start-up. Just choose console / command line project.

Just out of curiousity. Since you have a linux machine, why don't you program in linux? The environment is, IMHO, a lot more sane for software development.

You can edit the source files in a text editor (kate, gedit, vim) and compile from a terminal.

If you would like to use an IDE I would recommend Anjuta or Eclipse.

Xeth


lol i thought dev c++ doesnt show a terminal or something

---


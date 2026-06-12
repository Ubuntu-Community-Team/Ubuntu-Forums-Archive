---
title: "Help required with dependency problem"
date: 2008-09-11
forum: Programming Talk
---

### Post by Chris Musampa on 2008-09-11
Hi all,
I decided to teach myself a modern programming language having not done any for years, C++ seemed a logical choice. I'm using an up to date Kubuntu 8.04 and have installed kdevelop and started by trying to get the 'hello world' simple kde app going.

I got Automake and friends to run successfully.  I've been getting further with 'Run configure' by googling each error it throws up and then installing required packages.  I'm now stuck as I don't know what to install to fix the error below, if I select kdelibs or kdelibs4-dev adept tells me 'the commit would break other packages', please help.

```

configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```


Thanks in advance.

---

### Post by pmasiar on 2008-09-11
> C++ seemed a logical choice.

Why? What is your definition of "modern", if C++ fits it? Is it "designed after COBOL"? ;-)

1) Read stickies.

2) Think again about the criteria for your first language to learn (read stickies again) :-) For shortcut, read my FAQ

---

### Post by Chris Musampa on 2008-09-11
Hi pmasiar and thanks for your reply, this wouldn't be my first programming experience as I've previously (a good few years ago) used assembler, pascal and a little c.  My choice of c++ is because its in common use, it's oo approach interests me and would be suitable for a couple of projects I have in mind, also it may be of occasional value at work.

I could borrow an old pc from work and have access to a windows based ide that will do what I need, but I'd much rather be able learn in a linux environment as its what I use exclusively at home. I'm a little surprised there are so many hoops to jump through before I can even begin learning the language.

---

### Post by mssever on 2008-09-11
> **Chris Musampa said:**
> I'm a little surprised there are so many hoops to jump through before I can even begin learning the language.
That's at least partially because you're using C++, though autotools is a bit complex to learn, too.

When I learned Ruby, it was a matter of installing Ruby and going. A lot easier.

---

### Post by Chris Musampa on 2008-09-11
> **mssever said:**
> That's at least partially because you're using C++

I stand to be corrected, but I doubt I'd spend over 2 hours failing to get a 'hello world' app - **a sample provided with the ide no less!** - to run in visual studio.

---

### Post by dwhitney67 on 2008-09-11
If you have not done it already, install the GCC compiler tool:
```
sudo apt-get install build-essential
```
Then open your favorite editor (e.g. gedit, vim, etc) and enter the following code:
[PHP]#include <iostream>

int main()
{
  std::cout << "Hello World" << std::endl;
  return 0;
}[/PHP]
Save the file to "Hello.cpp".

Then from a terminal, compile/link the program using:
```
g++ Hello.cpp -o Hello
```
The run the program from the terminal using:
```
./Hello
```
Once you understand how to edit and compile programs from the command line, then you can consider using one of popular IDEs that are available with Linux; but I wouldn't recommend it.

---

### Post by Chris Musampa on 2008-09-12
Visual studio it is then, cheers guys.

---

### Post by rnodal on 2008-09-12
I would like to make a humble recommendation. I would recommend [C::B]("http://www.codeblocks.org/"). It is very easy to use and it's very similar to VS. The reason why I recommended is that it is available in Linux and Windows. Also, your project file can be opened in Linux and Windows with no problems. It is not written in Java ;).

-r

---

### Post by Amon_Re on 2008-09-12
I second the suggestion to use Code:Blocks , it's a pretty damn solid IDE (and not writting in Java :P).

---

### Post by LaRoza on 2008-09-12
> **Chris Musampa said:**
> Visual studio it is then, cheers guys.

That doesn't run on Linux you know ;)

---

### Post by rnodal on 2008-09-12
I forgot to mention that I think that dwhitney67's advice still is very important. I was just fulfilling my C::B fan boy role :).

-r

---


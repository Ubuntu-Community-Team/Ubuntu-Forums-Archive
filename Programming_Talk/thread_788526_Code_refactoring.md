---
title: "Code refactoring"
date: 2008-05-09
forum: Programming Talk
---

### Post by KIAaze on 2008-05-09
Hi,

I'm trying to find a way to [refactor code]("http://en.wikipedia.org/wiki/Refactoring"), i.e. rename a function everywhere it's used for example.

I heard that Eclipse does this, but I couldn't figure out how to import a C++ project into it. And it takes up too much RAM anyway.

KDevelop seems to offer refactoring according to this [release announcement]("http://www.kdevelop.org/index.html?filename=3.4/announce-kdevelop-3.4.html"):
> KDevelop offers documentation generators, code debugging, memory checking, code refactoring, bookmark management, and dozens of tools to make development easy and convenient.

But I can't figure out where this option is.
The Find-Select-Replace option is pretty helpful, but it's not real refactoring since it doesn't search&replace according to the C/C++ syntax.

What code refactoring tools are available on GNU/Linux?

---

### Post by dwhitney67 on 2008-05-09
As a s/w engineer, when I hear or read the term "refactor", the first thing that comes to mind is that a s/w application needs to be modified/simplified into a similar but better, perhaps more nimble, design.  Renaming functions or variables has nothing to do with refactoring.

I personally do not use any IDEs, and merely rely on 'vim'.  I've been successfully using vim (and its predecessor 'vi') for over 18 years.  In the next 10 years it will be interesting to see if Eclipse, KDevelop etc are still around; I'm certain that 'vim' will be.

---

### Post by KIAaze on 2008-05-09
Well, maybe I'll try to finish vimtutor one day.
All I can do for now is insert,search, dw, d$, yank/paste and q,q!,wq. ^^

I haven't found it to be very efficient yet.

---

### Post by KIAaze on 2008-05-09
I think I found something:
[http://www.vim.org/scripts/script.php?script_id=2087](http://www.vim.org/scripts/script.php?script_id=2087)

However, I don't know how to use it.
Since you use vim, I suppose you could help me here.

I copied the .vim script into a ~/.vim/plugins directory I created, but I don't understand how to use it.
What's <A-r>r ?

---

### Post by dwhitney67 on 2008-05-09
How many files do you need to "refactor"?  If it is only a few, or if they are all of a certain type, then perhaps you can use 'sed' and 'find'?

For example, to change the class name 'Foo' to 'MyClass' in this file:
[PHP]class Foo
{
  public:
    Foo() {}
    ~Foo() {}
};

int main()
{
  Foo foo;
  return 0;
}[/PHP]

Just run this command for an individual file:
```
$ sed -i s/Foo/MyClass/ Foo.cpp
```

Or this command for all .cpp files at and below the current directory:
```
$ find . -name '*.cpp' -exec sed -i s/Foo/MyClass/ {} \;
```

If you have header files, replace the 'cpp' with an 'h' or 'hpp' as appropriate.

---

### Post by KIAaze on 2008-05-10
Yes, but that's equivalent to the Find-Select-Replace of Kdevelop. (it also accepts regular expressions)

Sometimes, things get complex like in this case if you have:
FooSomething
AFoo

Separate word regex fails here:
Foo.GetX()
Foo->func()
Foo(...)
Somefunc(...,Foo,...)

I guess if I improve my knowledge of regular expressions, I could do without a refactoring tool.
For the moment, I find it easiest to change the function/class definition+prototype/methods and then compile to locate where else it's used.

Most of the time, simple search&replace works well though. But not always.
I thought that if Eclipse has such a function, there must be other programs offering the same. Eclipse is just too bloated and complex for me.

---

### Post by imdano on 2008-05-10
edit: never mind, misread the last post.

---

### Post by achelis on 2008-05-10
> **dwhitney67 said:**
> Renaming functions or variables has nothing to do with refactoring.

Well "Rename Method" is a refactoring and therefore does has something to do with it ;)

As for tools I'm afraid I only use Eclipse, but found this site, maybe some of the links can help you?

[http://www.refactoring.com/tools.html](http://www.refactoring.com/tools.html)

---

### Post by wolfie2x on 2008-07-25
> **dwhitney67 said:**
> As a s/w engineer, when I hear or read the term "refactor", the first thing that comes to mind is that a s/w application needs to be modified/simplified into a similar but better, perhaps more nimble, design.  Renaming functions or variables has nothing to do with refactoring.

I personally do not use any IDEs, and merely rely on 'vim'.  I've been successfully using vim (and its predecessor 'vi') for over 18 years.  In the next 10 years it will be interesting to see if Eclipse, KDevelop etc are still around; I'm certain that 'vim' will be.

typical linux guru answer! :mad: We badly need to get something done, and they simply say we don't need it! 

Refactoring DOES include renaming functions and cleaning code formatting so that code is readable, meaningful, and manageable.

This is such a standard functionality and I'm really surprised KDevelop doesn't have it.. If anybody knows of any such plugin pls post.

---

### Post by dribeas on 2008-07-25
> **wolfie2x said:**
> This is such a standard functionality and I'm really surprised KDevelop doesn't have it.. If anybody knows of any such plugin pls post.

C++ is a context dependent language. I don't know of any tool that does it (I don't even know of an IDE that can track template method calls properly). The easiest thing that comes to mind is renaming in the .h and .cpp (I won't suggest vi, even if it is my choice :P). After that compiler will flag automatically all places where that method was used.

Not really automated, and probably quite boring, but nonetheless...

BTW, I have used and liked Eclipse Java refactoring and it was both useful and easy, but when I tried Eclipse (first version of CDT 4) it was unable to locate calls to templated methods, which is as much as saying that at least for those it will be impossible to refactor.

---

### Post by tinny on 2008-07-26
Martin Fowler, refactoring god.
[Refactoring: Improving the Design of Existing Code]("http://www.amazon.com/exec/obidos/ASIN/0201485672"), the refactoring bible.

Remember prevention is better than cure, reading a book like the one mentioned above will definitely help you write better code the first time around.

Also here are 2 Eclipse plug-ins that will help guide you in writing better code the first time around (for Java).

[Checkstyle]("http://eclipse-cs.sourceforge.net/")
[PMD]("http://pmd.sourceforge.net/")

---

### Post by ceclauson on 2008-07-26
It wasn't obvious to me whether or not this was what you were looking for, but I could do a quick description of how to import files into Eclipse.

Under the File menu, select "Import".  I dialog box will come up. Under "General", choose "Filesystem". A new dialog will come up.  You then have the option of browsing the filesystem for source directories and files, and browsing the project folders for a destination.  Once you've chose a source directory, one or more source files, and a destination, you can click finish, and the files will be imported.

One potential stumbling block is that when you're browsing the file system. you'll only be able to select directories, not files.  Choose the root directory of the file or files you'd like to import.  Then you'll have the option in the window below the browser to select the files that you'd like to import.

Eclipse has a "Refactor" menu right next to the "File" and "Edit" menus, but I've never used it, so I can't really give details on that.

Hope this was helpful,
Cooper

---

### Post by wolfie2x on 2008-07-26
> BTW, I have used and liked Eclipse Java refactoring and it was both useful and easy, but when I tried Eclipse (first version of CDT 4) it was unable to locate calls to templated methods, which is as much as saying that at least for those it will be impossible to refactor.

yep the java IDEs eclipse CDT & netbeans have it.. but they are just too heavy for my taste.. geany, anjuta doesn't even have working code-completion.. code::blocks is just too buggy.. kdevelop is the only properly working IDE..

I just wish these devs get together and make a single working app instead of a zillion broken ones.. each wasting energy trying to get the same functionality.. if that's bad, talk about gnome vs kde.. trying to duplicate the whole universe of apps.. :(

---


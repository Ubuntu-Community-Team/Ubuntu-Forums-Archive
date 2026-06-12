---
title: "a little info on how to proced. thanks."
date: 2006-11-02
forum: Programming Talk
---

### Post by sal on 2006-11-02
hello all, or should i say "hello world" hahaha.

anyway to the point.

I just bought sam's teach yourself c++ in 21 days and I want to set up the perfect dev invioronment on my laptop to work with while studying the book.

Im using Kubuntu Edgy 6.10 and was hoping you guys could tell me what packages to install for a C++ kde development inviornment.

thanks in advance.

Sal.

---

### Post by Zalbor on 2006-11-02
For a complete environment, KDevelop shoud work. Personally though, I just use a text editor with syntax highlighting (try KWrite for KDE) and the g++ compiler in a terminal.

---

### Post by Relain on 2006-11-02
really all you need is gedit and g++ on the command line. Take a little time to experiment with what font sizes and backgrounds you like, sounds stupid but my brain works better if i'm working on light text on a dark background. I've set up gedit to copy the 'espresso libre' text-mate (os x) theme and have terminal with green on black.

For help with memory leaks and (sometimes) more insightful debugging i'd heartily endorse valgrind, although sometimes it will just complain about libraries you've not even written. 

In terms of IDE's kdevelop is cool but if you're on gnome you might want to try using Eclipse (it works on kde too). It's somewhere between incredibly useful incredibly annoying depending on what you're trying to do. Anjuta is fun too. 

Other packages? You can get dev headers for things you're interested in programming like the gtk (for gui's) or openGl for fancy pants graphics and then hack away with your new mad Skillz.

[edit]
I totaly forgot the main thing i wanted to espouse! A version control system. If you're working on any kind of large project or over a long period of time or collaborating your life will be so much easier with one. They're a way to make sure that your editing the most recent files, to undo changes that didn't work and to keep everything sanely in one place. Get SVN learn how to use it: [http://artis.imag.fr/~Xavier.Decoret/resources/svn/index.html](http://artis.imag.fr/~Xavier.Decoret/resources/svn/index.html) [/edit]

word

---

### Post by sal on 2006-11-08
> **Zalbor said:**
> For a complete environment, KDevelop shoud work. Personally though, I just use a text editor with syntax highlighting (try KWrite for KDE) and the g++ compiler in a terminal.

im trying what u suggest (kwrite with g++)
here is the file im trying to make:

//Listing 2.2 using std::cout
#include <iostream>
int main()
{
    std::cout << "Hello there.\n";
    std::cout << "here is 5: " << 5 << "\n";
    std::cout << "The manipulater std::end1 ";
    std::cout << "writes a new line to the screen. ";
    std::cout <<  std::end1;
    std::cout << "Here is a very big number:\t" << 70000;
    std::cout <<  std::end1;
    std::cout << "Here is the sum of 8 and 5:\t";
    std::cout << (8+5) << std::end1;
    std::cout << "Her's a fraction :\t\t";
    std::cout << (float) (5/8) << std::end1;
    std::cout << "And a very very big number:\t";
    std::cout << (double) (7000 * 7000) << std::end1;
    std::cout << "Don't forget to replace Sal is the Master ";
    std::cout << "With your name...\n";
    std::cout << "Sal is a C++ Programmer and a God!\n";
    return 0;
}

but when i save it as hellothere.cpp and run the command g++ hellothere.cpp i get this error:
hellothere.cpp: In function ‘int main()’:
hellothere.cpp:9: error: ‘end1’ is not a member of ‘std’
hellothere.cpp:11: error: ‘end1’ is not a member of ‘std’
hellothere.cpp:13: error: ‘end1’ is not a member of ‘std’
hellothere.cpp:15: error: ‘end1’ is not a member of ‘std’
hellothere.cpp:17: error: ‘end1’ is not a member of ‘std’

i don't know how to procede because the book im using says to write the program just as i did and i double checked the code to make sure i did not have errors and there where no errors in the code.

the book im using is called "sams teach yourself c++ in 21 days" if that help out.

---

### Post by xtacocorex on 2006-11-08
You're typing end1 instead of endl (end little L). Change that and it should work like a charm.

---

### Post by sal on 2006-11-08
> **xtacocorex said:**
> You're typing end1 instead of endl (end little L). Change that and it should work like a charm.


thanks! that was the problem.
the book eventualy cleared it up for me as well as you have on the next page. :)
thanks for your help.

---


---
title: "&quot;applications&quot; menu does not have &quot;programming&quot;"
date: 2009-11-14
forum: Programming Talk
---

### Post by MichaelBurns on 2009-11-14
I want to learn to program "the right way".  I have a few years of experience making sloppy programs that just get the job done, but I decided to make an effort to sophisticate myself.  Specifically, I will be relearning C++.  I read on wikiversity to "Get an IDE."  This is something that I never used (probably because my programs were never very complication?).

So, I looked in the "applications" menu, but there is no menu item for programming.  Does this mean that xubuntu 9.04 does not come with any programming tools?

---

### Post by Can+~ on 2009-11-15
I don't think (k/x)ubuntu comes with programming tools, as far as I remember, the menu is added as soon as you install something programming related.

Make sure to have [FONT="Courier New"]build-essential[/FONT] if you're going the C++ route, it will add the g++ compiler and all the goodies.

And what do you mean "the right way"? How do you did it the "wrong way"?

---

### Post by BenAshton24 on 2009-11-15
There isn't really a right way other than studying a programming language at uni or something. It's more of just a compilation of things that you learn from mistakes that makes you a good programmer IMO.

As for an IDE, I would go for Geany, it's in the repos
```
sudo apt-get install geany
```


Good Luck,
Ben.

---

### Post by MichaelBurns on 2009-11-15
Thanks to both of y'all.

The "wrong way" just refers to how clumsy I feel when I am coding.  And, usually, if my code is more than 1000 lines long, I notice that my style becomes inconsistent.  Also, I never used a class, and that seems to be the main reason to use c++ (rather than c or fortran).  Also, I have used the "system" command (to delete a file, for instance), and something inside me just said that was wrong.

My ultimate goal is to finally be able to contribute to a release of ubuntu, in terms of fixing a bug in the code or something.

I guess I would say that "the right way" would be the way that promotes teamwork on the code.  I wouldn't wish maintaining any code that I've ever written on anyone.

---

### Post by BenAshton24 on 2009-11-15
> **MichaelBurns said:**
> Thanks to both of y'all.

The "wrong way" just refers to how clumsy I feel when I am coding.  And, usually, if my code is more than 1000 lines long, I notice that my style becomes inconsistent.  Also, I never used a class, and that seems to be the main reason to use c++ (rather than c or fortran).  Also, I have used the "system" command (to delete a file, for instance), and something inside me just said that was wrong.

My ultimate goal is to finally be able to contribute to a release of ubuntu, in terms of fixing a bug in the code or something.

I guess I would say that "the right way" would be the way that promotes teamwork on the code.  I wouldn't wish maintaining any code that I've ever written on anyone.

I'm working on a project right now and after every few hundred lines of code I just go through it and fix everything up, give better names to variables, subclass stuff and just generally neaten it up. I find that this works well because I seem to always get confused with my naming styles when I'm frustrated and trying to figure something out.

A few days ago, I came across a function named, "GetToggleButtonPressedMenuPopdownCoordinates" (or something like that) and, ignoring the sheer length of that, all my other functions are named like this, "get_togglemenu_coords." I then noticed that my original flowchart that I had done, detailing how everything was going to work, was actually nothing like my code. so that was a joyous few hours of fixing code :P

---

### Post by TheStatsMan on 2009-11-15
> **MichaelBurns said:**
>  Also, I never used a class, and that seems to be the main reason to use c++ (rather than c or fortran)   The latter versions of Fortran actually contain objected oriented features.

---

### Post by rukiaEnix on 2009-11-15
Install NetBeans it works for java and c++, I use it for java and I love it :D

---

### Post by jdunn on 2009-11-15
The general consensus seems to be that Eclipse and Code::blocks are great C++ IDEs.  I use both, Eclipse for Java and CB for C++.  As mentioned already, you need the "build essential" package.  CB is great for migrating to/from M$ Visual C++

---

### Post by Can+~ on 2009-11-15
> **MichaelBurns said:**
> The "wrong way" just refers to how clumsy I feel when I am coding.  And, usually, if my code is more than 1000 lines long, I notice that my style becomes inconsistent.  Also, I never used a class, and that seems to be the main reason to use c++ (rather than c or fortran).  Also, I have used the "system" command (to delete a file, for instance), and something inside me just said that was wrong.

Sounds a lot like my early years in coding, I used to have a lot of trouble with compiled languages and OOP, mostly because it's easier to start thinking on procedural than OOP, and then the OOP features become irrelevant.

I switched to python, and then realized that my biggest problem wasn't the OOP (actually it was trivial), but the fact having to deal with pointer and low level structures when my mind worked better with a more close-to-algorithm coding, in fact, that's how I learnt to love the Functional Paradigm more than the OO one.

---

### Post by MichaelBurns on 2009-11-15
I installed geany, and now there is a "Development" item in the "Applications" menu.  Awesome.  I opened up geany from there, and I like the look and feel of it.  I opened my source code file from geany, and I love how it shows all of these features of the code, and lets me manipulate them.  This is so cool.  I have been just typing source code in a text editor for years.  I am by nature a minimalist (which is why I went with xubuntu, for examnple).  However, I think this geany thing will cut my debugging time down to a fraction.

Unfortunately, when I click the compile button (there's a compile button; that's so cool and simple) I get an error that says the g++ compiler cannot be found.  This is contrary to what I would expect after reading wikiversity, which claims that an IDE is:  a front end, a code editor, and a compiler.  It seems like geany is then missing that last piece:  the compiler.  What's the best way to deal with that?

I have read in several places that I need the build essential package.  But, synaptec tells me that I don't need it unless I will develop Debian packages.  So, obviously I'm not understanding something here.  Why would so many of you tell me that I need it, but then synaptec tell me that I don't?

I will look into this so-called Functional Paradigm.  It sounds like that may be much more my style.

---

### Post by SledgeHammer_999 on 2009-11-15
I don't know what you are talking about regarding synaptic "tips", but just ignore it and install "build-essential". That's a metapackage that installs g++ (amongst others things).

---

### Post by MichaelBurns on 2009-11-17
OK, just a recap and update for those who are wondering how it went:

As I mentioned, I installed geany, and the "Development" category appeared in the "Applications" menu, under which "Geany" appears.  Then, I got an error that g++ could not be found.  At the advice of many on these forums and elsewhere on the internet, I used synaptec to install build-essential offline from the install CD (for Xubuntu 9.04 i386 architecture).  **Now, everything seems to be working!**

I will mention the only annoyance so far.  When I click the "compile" button, geany produces a *.o file (object code) rather than an executable.  However, this is simply alleviated by pressing F9, which does "build" instead of "compile" (F8 ).  So, I guess that what I used to refer to as "compile" I should now refer to as "build", where I suppose "build" = "compile" + "link"?

I have now gone through the (very brief, incomplete, and flawed) [wikiversity tutorial]("http://en.wikiversity.org/wiki/C%2B%2B").  I do NOT recommend it.  It even has at least one error in the lesson on classes (giving me another opportunity to praise geany).  Without geany, I would never have found that error, and I would have just given up.  However, with geany, I was able to find the error, fix it, and actually get the code to compile and the executable to run.  **Praise geany!**

I am currently making my way through the tutorial [here]("http://www.cplusplus.com/doc/tutorial/"), which I highly recommend, but I haven't yet done any exercises from it.  Anyway, I really like the way that it is written and organized, and I expect to have a very strong understanding of all aspects of C++ when I am finished.

Thank you to everyone who has helped me to get to this point.

---

### Post by TheStatsMan on 2009-11-17
> **MichaelBurns said:**
> 
I am currently making my way through the tutorial [here]("http://www.cplusplus.com/doc/tutorial/"), which I highly recommend, but I haven't yet done any exercises from it.  Anyway, I really like the way that it is written and organized, and I expect to have a very strong understanding of all aspects of C++ when I am finished.


I hate to burst your bubble, but you won't have a very strong understanding of all aspects of C++ when you have finished that tutorial.

---

### Post by MichaelBurns on 2009-11-17
> **TheStatsMan said:**
> I hate to burst your bubble, but you won't have a very strong understanding of all aspects of C++ when you have finished that tutorial.Can you elaborate on what will be missing from it?  Maybe I need to start a new thread for this.

---

### Post by TheStatsMan on 2009-11-17
> **MichaelBurns said:**
> Can you elaborate on what will be missing from it?  Maybe I need to start a new thread for this.

C++ is an enormous beast, you can't expect to have a very strong understanding of all aspects of it by simply going though a tutorial.  There is a lot I don't know about c++ and there is a lot I know, which isn't covered by that tutorial. There is nothing wrong with the tutorial by the way, but just understand it is an introduction to the language.

The most import thing that does not appear to be covered is the STL. Also the topics are hardly covered comprehensively. Take templates for instance, do you realise there are entire books on just this one aspect of c++. Trivial example:

Just based on the information in the tutorial (no help from google), I do not think you can tell me why this example won't compile. There is only one error in the code BTW.

```

#include <iostream>

template<typename T>
class base
{
    public:
    void SetX(T x){
        _x=x;
    }    
    protected:
    //prints x
    void print(){
        std::cout<<_x<<std::endl;
    }
    void print(T y){
        std::cout<<_x+y<<std::endl;
    }

    T _x;
};
template<typename T>
class derived : public base<T>
{
    public:
    //prints x from base class
    void Print(){
        print();
    }
    //prints x + y
    void Print(T y){
        print(y);
    }
};




int main()
{
    derived<double> D;
    D.SetX(5.0);
    D.Print();
    D.Print(3.0);

    return 0;
}

```

This is just one example. It is a trivial mistake that any experienced c++ programmer will see in an instant, but the tutorial does not provide the information to see the error. Not saying you shouldn't do the tutorial, it appears to be a good starting point, which should be followed by a tutorial on the STL, but don't think it covers more than the basics.

---

### Post by MichaelBurns on 2009-11-18
Oh.  I wasn't thinking of specific libraries as part of C++ (not even iostream), only the concept of their use.  And I certainly don't expect to become good at debugging from any tutorial (although geany has been quite good to me).

Thank you for pointing this out, though.  Should I think of at least the standard libraries as an integral part of C++?

BTW, I have only read through "Classes II" (have just peaked at "Friendship and Inheritance"), and I am already quite overwhelmed with mere syntax.  I find the highly contextual syntax (esp. pointers and classes) to be quite daunting.

---

### Post by TheStatsMan on 2009-11-18
> **MichaelBurns said:**
> Oh.  I wasn't thinking of specific libraries as part of C++ (not even iostream), only the concept of their use.  And I certainly don't expect to become good at debugging from any tutorial (although geany has been quite good to me).


The example wasn't really a test of debugging ability, it is simply the mistake I put in the code requires specific knowledge of templates that simply isn't in the tutorial. In fact, what I did seems logical when you have an understanding of c++ inheritance outside of its use in templates. This is far from an isolated case.

> 
BTW, I have only read through "Classes II" (have just peaked at "Friendship and Inheritance"), and I am already quite overwhelmed with mere syntax. I find the highly contextual syntax (esp. pointers and classes) to be quite daunting.

This is one of the reasons many recommend learning object oriented concepts (and programming in general) in a language like python (where the concepts aren't clouded by syntax) before learning them in a language like c++. This is not to say they can't be done the otherway (I learnt them through c++), it is just a matter of what is the most efficient way to learn. By the way if you find the syntax overwhelming for things like inheritance wait to you get to some of the more advanced template stuff.

---

### Post by MichaelBurns on 2009-11-18
Why is it done that way in C++ (if, as you suggest, it need not be, for instance in python)?  As a relatively uninitiated nonprogrammer who is not at all attached to C++ (but only recognizes it as perhaps an industry standard and therefore still necessary to learn), it gives me the impression of a standard that has inelegantly evolved in a way to weed out all but the most dedicated.  Or, perhaps the promoters knew that they did not need to bother to make more sensible syntax to bring people to the language, and so they didn't bother.

Well, I will get to the end of that tutorial sometime soon I hope.  I have just run out of momentum at the moment.  Thanks for the heads up.  I will play a game.  After I have finished the tutorial, I will give your code a try and then let you know what I think or if I was able to find the error (without looking anywhere else but the tutorial).  But also, to be fair, if I cannot find the error by refering to the tutorial, I will try to find it with google.  If I can't even find it with google, then it will certainly not seem like a deficiency with the tutorial.

Please, no (more) hints about the error in the code.

---

### Post by Can+~ on 2009-11-18
> **MichaelBurns said:**
> Why is it done that way in C++ (if, as you suggest, it need not be, for instance in python)?  As a relatively uninitiated nonprogrammer who is not at all attached to C++ (but only recognizes it as perhaps an industry standard and therefore still necessary to learn), it gives me the impression of a standard that has **inelegantly evolved in a way to weed out all but the most dedicated**.  Or, perhaps the promoters knew that they did not need to bother to make more sensible syntax to bring people to the language, and so they didn't bother.

Actually, you were spot on.

C++ attempted to displace the C crowd, offering backwards compatibility, plus new features. This resulted in duplicated functionality, and some really, really [horrible design choices]("http://yosefk.com/c++fqa/defective.html"). Some of this things even catch the most experienced programmers.

---

### Post by MichaelBurns on 2009-11-18
> **Can+~ said:**
> ... really, really [horrible design choices]("http://yosefk.com/c++fqa/defective.html").Geez.  That's disheartening.  I am quickly losing my motivation along with my momentum.  To say it like my favorite IDE:  "warning: deprecated use of C++"

---


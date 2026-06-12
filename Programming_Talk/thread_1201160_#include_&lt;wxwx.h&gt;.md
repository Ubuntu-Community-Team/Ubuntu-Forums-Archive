---
title: "#include &lt;wx/wx.h&gt;"
date: 2009-06-30
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-06-30
Hello everyone,

I'm a fairly advanced c++ programmer, having taken 2 C++ classes in college so far and a good knowledge of C.  For my summer project I want to teach my myself GUI programming (having already learning about classes pointers all that good hard stuff), but in the text bool it says nothing about where to get the wx/wx.h file from, how to install or anything, and it's obviously not a precompiled header. The first program is as follows:

#include <wx/wx.h>

class BasicApp : wxApp
{
public:
  BasicApp();
  virtual bool OnInit();
private:
  wxFrame* frame;
};

DECLARE_APP(BasicApp)
IMPLEMENT_APP(BasicApp)

BasicApp::BasicApp()
{
  frame = new wxFrame(NULL, -1, "My First GUI Program");
}
bool OnInit()
{
  frame->Show(true);
  return true;
}
/* If there are any syntax errors don't worry about that because it doesn't really matter too much... I know the syntax it's just about getting it compile  */



I use g++ as my compiler so I do the command: (fileName = first_gui.cpp )
g++ first_gui.cpp -o first.out 2>> error.txt

-And these are the errors i get:

first_gui.cpp:1:19: error: wx/wx.h: No such file or directory
first_gui.cpp:4: error: expected class-name before ‘{’ token
first_gui.cpp:9: error: ISO C++ forbids declaration of ‘wxFrame’ with no type
first_gui.cpp:9: error: expected ‘;’ before ‘*’ token
first_gui.cpp:14: error: expected constructor, destructor, or type conversion before ‘IMPLEMENT_APP’
first_gui.cpp: In member function ‘virtual bool BasicApp::OnInit()’:
first_gui.cpp:23: error: ‘frame’ was not declared in this scope

So, obviously the problem is that wx/wx.h is not in my /usr/include directory (I also know because I've looked)

Is there any one who can help me with installing the wxwidgets pachage (if wxwidgets is what supplies the wx/wx.h file not entirely sure about that) and also how to compile if different than the g++ compiler commands.

Thanx everyone.

---

### Post by c0mput3r_n3rD on 2009-06-30
/*Sorry if i posted this twice, but I couldn't find where it was.....*/

Hello everyone,

I'm a fairly advanced c++ programmer, having taken 2 C++ classes in college so far and a good knowledge of C. For my summer project I want to teach my myself GUI programming (having already learning about classes pointers all that good hard stuff), but in the text bool it says nothing about where to get the wx/wx.h file from, how to install or anything, and it's obviously not a precompiled header. The first program is as follows:

#include <wx/wx.h>

class BasicApp : wxApp
{
public:
  BasicApp();
  virtual bool OnInit();
private:
  wxFrame* frame;
};

DECLARE_APP(BasicApp)
IMPLEMENT_APP(BasicApp)

BasicApp::BasicApp()
{
  frame = new wxFrame(NULL, -1, "My First GUI Program");
}
bool OnInit()
{
  frame->Show(true);
  return true;
}
/* If there are any syntax errors don't worry about that because it doesn't really matter too much... I know the syntax it's just about getting it compile */



I use g++ as my compiler so I do the command: (fileName = first_gui.cpp )
g++ first_gui.cpp -o first.out 2>> error.txt

-And these are the errors i get:

first_gui.cpp:1:19: error: wx/wx.h: No such file or directory
first_gui.cpp:4: error: expected class-name before ‘{’ token
first_gui.cpp:9: error: ISO C++ forbids declaration of ‘wxFrame’ with no type
first_gui.cpp:9: error: expected ‘;’ before ‘*’ token
first_gui.cpp:14: error: expected constructor, destructor, or type conversion before ‘IMPLEMENT_APP’
first_gui.cpp: In member function ‘virtual bool BasicApp::OnInit()’:
first_gui.cpp:23: error: ‘frame’ was not declared in this scope

So, obviously the problem is that wx/wx.h is not in my /usr/include directory (I also know because I've looked)

Is there any one who can help me with installing the wxwidgets pachage (if wxwidgets is what supplies the wx/wx.h file not entirely sure about that) and also how to compile if different than the g++ compiler commands.

Thanx everyone.

---

### Post by Can+~ on 2009-06-30
> **c0mput3r_n3rD said:**
> I'm a fairly advanced c++ programmer, having taken 2 C++ classes in college so far and a good knowledge of C. For my summer project I want to teach my myself GUI programming (having already learning about classes pointers all that good hard stuff)

Pointers and Classes is advanced C++?

As for the problem, you should searching a bit more:
[http://ubuntuforums.org/showthread.php?t=981542](http://ubuntuforums.org/showthread.php?t=981542)

---

### Post by c0mput3r_n3rD on 2009-06-30
First of all it's just an examlpe because that's what the first gui program conists of, second; yes, everything in advanced programming revolves around classes and memory management in data structures i.e.queues stacks etc. and third of all please don't post on this thread if you're not trying to answer my questions thanx

---

### Post by c0mput3r_n3rD on 2009-06-30
.... i just re-read it too... i didn't even say that <snip>... they're different sentences. 
<snip>.....

---

### Post by unknownPoster on 2009-06-30
woot for blub programmer's /end_sarcasm

In one of my "advanced" Computer Science classes last semester, we never used a computer...

Basic Programming involves a basic understanding of classes, memory management, and other Object Oriented Principles...

---

### Post by c0mput3r_n3rD on 2009-06-30
right... but not for a specific language... that's a general programming class, and Westchester Community College (aka harvard on the hudson) is THE number one rated community college in the world.. and known for it's math and computer science.

but again....IT'S REALLY NOT EVEN ABOUT THAT!!

---

### Post by Mirge on 2009-06-30
> **c0mput3r_n3rD said:**
> .... i just re-read it too... i didn't even say that you moron.... they're different sentences. 
PLEASE! don't waste my time......

I believe that "moron" posted a thread that answers your exact question... shame your college doesn't have a course on respect.

---

### Post by unknownPoster on 2009-06-30
> **Mirge said:**
> I believe that "moron" posted a thread that answers your exact question... shame your college doesn't have a course on respect.

Or basic google skills...

[http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

---

### Post by c0mput3r_n3rD on 2009-06-30
and like you said... it's a "computer science" class, not a c++ programming class. All that is left after classes and memory management is data sctrcutres which are completely about manipulating memory and using classes to do so... god damn it's like arguing with my 13 y/o brother.....

---

### Post by c0mput3r_n3rD on 2009-06-30
I really thought this was a place where i could come to have Intelligent conversations, and advance my knowledge about Linux and programming.

...Instead it has turned into a 3rd grade cafeteria argument about semantics

---

### Post by Can+~ on 2009-06-30
> **c0mput3r_n3rD said:**
> First of all it's just an examlpe because that's what the first gui program conists of, second; yes, everything in advanced programming revolves around classes and memory management in data structures i.e.queues stacks etc. and third of all please don't post on this thread if you're not trying to answer my questions thanx

First, I never asked about that.
Second, no, it doesn't, creating a stack in C/C++ is trivial, so trivial that higher-level language have them already. (In fact, assembly already has a stack $sp)
Third, the link I gave you answers the exact same problem you have, it even has the same title!

> **c0mput3r_n3rD said:**
> .... i just re-read it too... i didn't even say that you moron.... they're different sentences. 
PLEASE! don't waste my time......

You should re-write also, I can't understand a single word in that sentence.

> **c0mput3r_n3rD said:**
> right... but not for a specific language... that's a general programming class, and Westchester Community College (aka harvard on the hudson) is THE number one rated community college in the world.. and known for it's math and computer science.

Yet you can't follow simple instructions, or write properly. -Said the guy living in south America.

> I really thought this was a place where i could come to have Intelligent conversations, and advance my knowledge about Linux and programming.

...Instead it has turned into a 3rd grade cafeteria argument about semantics 

Your question was answered in my first reply, I don't know why you suddenly jumped and called me moron for pointing out that Data structures is not advanced programming.

---

### Post by unknownPoster on 2009-06-30
> **c0mput3r_n3rD said:**
> and like you said... it's a "computer science" class, not a c++ programming class. All that is left after classes and memory management is data sctrcutres which are completely about manipulating memory and using classes to do so... god damn it's like arguing with my 13 y/o brother.....

Did you take the class?

No but I did...

The name of the class "Data Structures and Algorithm Analysis in **C++**"
Oh wow, here's the book we used. [http://users.cs.fiu.edu/~weiss/#dsaac++3](http://users.cs.fiu.edu/~weiss/#dsaac++3)

I bet it's shocking to know that Computer Science isn't all about computers...it's about solving problems in practical and efficient ways.

---

### Post by c0mput3r_n3rD on 2009-06-30
Pointers and Classes is advanced C++?

** Pointers and classes are advanced C++?  **

Second, no, it doesn't, creating a stack in C/C++ is trivial, so trivial that higher-level language have them already. (In fact, assembly already has a stack $sp)
Third, the link I gave you answers the exact same problem you have, it even has the same title!

** Second, no it doesn't. Creating a stack in C/C++ is trivial. So trivial that a higher-level language has them already. In face, assembly already has a "stack $sp".        **

You should re-write also, I can't understand a single word in that sentence.

** You should also re-write. I can't understand a single word in that sentence ** 
                                       -or-
** You should also re-write, because ..." **

Your question was answered in my first reply, I don't know why you suddenly jumped and called me moron for pointing out that Data structures is not advanced programming.

** Your question was answered in my first reply. I don'twhy you suddenly jumped (down my throat) and called me a moron for pointing out that data structures is not advanced programming. 

-And yes, data structures is advanced ******([keyword.....])******* C++

Talking about snobby...

** Talk about snobby  ** 



-Please don't start stupid **** like correcting my grammar when you can't speak properly your self.

-And please say things when you really just don't know....

):P

---

### Post by c0mput3r_n3rD on 2009-06-30
And yesss, i diiiiid take the classssssssss.

I took programming I, programming II, and data structures and I'm now certified to program in C++!!!!!!!!!!! omg!
How did that happen with a "trivial" understand of C++........... gosh. 

And you went to Westchester Community College too? that's amazing... wowwww. What a small world

---

### Post by Mirge on 2009-06-30
> **c0mput3r_n3rD said:**
> Pointers and Classes is advanced C++?

** Pointers and classes are advanced C++?  **

Second, no, it doesn't, creating a stack in C/C++ is trivial, so trivial that higher-level language have them already. (In fact, assembly already has a stack $sp)
Third, the link I gave you answers the exact same problem you have, it even has the same title!

** Second, no it doesn't. Creating a stack in C/C++ is trivial. So trivial that a higher-level language has them already. In face, assembly already has a "stack $sp".        **

You should re-write also, I can't understand a single word in that sentence.

** You should also re-write. I can't understand a single word in that sentence ** 
                                       -or-
** You should also re-write, because ..." **

Your question was answered in my first reply, I don't know why you suddenly jumped and called me moron for pointing out that Data structures is not advanced programming.

** Your question was answered in my first reply. I don'twhy you suddenly jumped (down my throat) and called me a moron for pointing out that data structures is not advanced programming. 

-And yes, data structures is advanced ******([keyword.....])******* C++

Talking about snobby...

** Talk about snobby  ** 



-Please don't start stupid **** like correcting my grammar when you can't speak properly your self.

-And please say things when you really just don't know....

):P


Heh, not only did you mess up YOURSELF in that huge blurb of junk, but you further made yourself look even more like a troll. Congratulations.

---

### Post by Mirge on 2009-06-30
> **c0mput3r_n3rD said:**
> And yesss, i diiiiid take the classssssssss.

I took programming I, programming II, and data structures and I'm now certified to program in C++!!!!!!!!!!! omg!
How did that happen with a "trivial" understand of C++........... gosh. 

And you went to Westchester Community College too? that's amazing... wowwww. What a small world

So, you basically learned what anybody with a copy of "Teach Yourself C++ in 24 Hours" can figure out?:guitar:

---

### Post by unknownPoster on 2009-06-30
I've reported the troll(s) in this thread.

We try to be helpful and we get flack for it... it doesn't make sense to me.

---

### Post by c0mput3r_n3rD on 2009-06-30
You know guys, i'm just obviously not at the same intellectual level as all of you. so have a nice day/night w/e it might be.
And thanx you for sending me the tutorial i already looked at that did not help me, and wasting your time with bull ****

---

### Post by overdrank on 2009-06-30
Thread closed.

---

### Post by bapoumba on 2009-07-05
Merged the other thread in here.

---


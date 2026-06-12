---
title: "newbie..want to program in pascal an/or c++   Where to get compilers?"
date: 2008-01-13
forum: Programming Talk
---

### Post by billym99 on 2008-01-13
i'm just starting in linix

i was proficient in Delphi and did SOME C++ too

how to i find compilers for both pascal and c++ ?

and packages for both of those (like graphics, etc.?

---

### Post by Kadrus on 2008-01-13
For the C++ Compiler..open terminal and type:
```
sudo apt-get update
```
then write:```
sudo aptitude install build-essentials
```
This will install the GNU C++ Compiler..g++..
To test if it's working
```

#include<iostream>
using namespace std;
int main(int argc,char*argv[])
{
cout<<"Test"<<endl;
return 0;
}

```
save it ex.cpp
Open terminal and type:```
g++ ex.cpp
```..it should compile bug free..then type..```
./a.out
```
And you should see your program.
**Edit**
For the GTK LIbrary for C++
Open terminal and type:
```

sudo apt-get install libgtkmm-2.4-1c2a

```
I am pretty sure that that is the GTK package...
And for the WxWidgets library..open terminal and type:
```
sudo apt-get install libwxgtk2.6-dev

```
And for the qt library..i think that's the one
```

sudo apt-get install libqt3-mt-dev

```
And for the pascal compile
```
sudo apt-get install fp-compiler
```
But I don't know Pascal..so can't really help you in that area..
there is also another Pascal compiler if I am not mistaken
```

sudo apt-get install gpc-2.95
```
Good Luck:)

---

### Post by pmasiar on 2008-01-13
Pascal is kinda obsolete these days, You may want to check more modern languages. Python occupies same niche as Pascal was a generation ago, as a simple language for beginners but still scalable to real tasks. Another option might be Ruby (not as simple, but as flexible). Both languages use dynamic typing, which adds a lot of flexibility compared to statically typed languages like C or Pascal. These days, in many areas we can let computer to sort minor details like type information :-)

---

### Post by LaRoza on 2008-01-13
> **Kadrus said:**
> For the C++ Compiler..open terminal and type:
```
sudo apt-get update
```
then write:```
sudo aptitude install build-essentials
```


Nope, it is "build-essential".

If OP has no real reason for Pascal (maintaining code), stay away from it...

See my wiki(s) for getting started in C++ or other languages on Ubuntu.

---

### Post by ghostdog74 on 2008-01-13
@OP, if you want to learn Pascal , just go ahead. Most important thing is don't give up halfway. search gooogle for Pascal compilers. You may find some compilers you can play with.

---

### Post by id3379 on 2008-01-14
Thanks, helped alot !

---

### Post by BobHur on 2008-01-14
Have you searched Synaptic for "pascal" and for "lazarus"? I'm thinking that they are there. I haven't used Lazarus, but I like pascal and wrote quite a few useful programs in it ... back in the day. :D

Knowing an "obsolete" language can be financially rewarding if you end up workint/contracting for an old company that has put a lot of time and money it their current systems. In 2002-03 I worked for a company that was still using RPG-III on an AS400, they'd spent a lot on their software, it mostly worked right with some occasional tweaking/updates. No way were they going to change!

---


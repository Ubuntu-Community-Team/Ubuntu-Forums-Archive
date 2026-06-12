---
title: "I feel bad with API's"
date: 2008-08-01
forum: Programming Talk
---

### Post by StOoZ on 2008-08-01
well, hello first :KS:)
ok , im using C++ for developing my programs , just for fun , to get some practice , learn more C++ etc (been using it for 5 months now).
I learn C++ from reading some books and practicing , now to develop more useful programs , I started to use API's , like wxWidgets for GUI and many other things, SDL , TagLib for audio files metadata , etc.
my question is : does using API's and not writing my OWN libs (excluding GUI kits... :popcorn: ) , is considered as a bad way to learn C++ ????
I really want to develop some useful things , for me , and in general for the open source community, and I feel that , using only pure C++ and STL , wont really get me far , unless i'll develop my own libs.

---

### Post by LaRoza on 2008-08-01
> **StOoZ said:**
> 
I learn C++ from reading some books and practicing , now to develop more useful programs , I started to use API's , like wxWidgets for GUI and many other things, SDL , TagLib for audio files metadata , etc.
That is good.

> 
my question is : does using API's and not writing my OWN libs (excluding GUI kits... :popcorn: ) , is considered as a bad way to learn C++ ????
No, it isn't. Most of programming is trying to avoid rewriting things when possible and using new API's is a very good skill.


> I really want to develop some useful things , for me , and in general for the open source community, and I feel that , using only pure C++ and STL , wont really get me far , unless i'll develop my own libs.
C++ by itself is quite useless, so you **need** other libraries. Some like to use QT libs for everything, or boost.

Also, rewriting standard functions is a good way to learn, but you can only go so far doing that.

---

### Post by StOoZ on 2008-08-01
I already re-written may STL functions , and I find myself using the STL functions a lot.
but still , I have some weird feeling that these API's are somewhat making me , as a programmer (well, still newbie one..) , fell kinda weird.

its a good skill to use API's? good to know.
its my first program, real one , and it involves a lot of APIs ( :( ) , like GIL (from boost) , many classes including the GUI from wxwidgets , also TagLib , SDL , and also STL.

been reading a lot of how do use the specific functions that I need to use, and always what popped into my mind was : "phhhew wasting so much time reading about API's while I can read more on C++, and develop my own libs"
:?

---

### Post by lisati on 2008-08-01
> **StOoZ said:**
> 
its a good skill to use API's? good to know.
its my first program, real one , and it involves a lot of APIs ( :( ) , like GIL (from boost) , many classes including the GUI from wxwidgets , also TagLib , SDL , and also STL.


It can be good to learn APIs, particularly if you're likely to be working with others. Not only can it save you time if you need to finish a project in a hurry, it can make it easier for others who may be working on the same project.

---

### Post by imdano on 2008-08-01
Usually the goal is to develop a working application as quickly and efficiently as possible, so it makes sense to try to use existing libraries that are well tested and stable.  If you really want to take the time nothing is stopping you from creating your own, but it'd be pretty difficult to rewrite the libraries you're using by yourself.  WxWidgets, boost, STL, etc. have been in development for years by teams of experienced programmers and are still being improved.  I think if you started trying to rewrite them you'll find it would have been much quicker to just make use of the existing libraries.  Not to say it wouldn't be a good learning experience to try implementing something small that's also done by one of the libraries and then comparing your solution to theirs.

---


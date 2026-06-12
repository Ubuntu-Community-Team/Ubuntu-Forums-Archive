---
title: "Software programming"
date: 2013-03-06
forum: Programming Talk
---

### Post by student321 on 2013-03-06
Hello Linux Users,

I am thinking about to create a application. What is a good programm language to use? I was thinking about Java. My question to you guys is what programming language can be used with Lunix, and has alot of features?

With Kind regards,
Student321

---

### Post by lisati on 2013-03-06
*Thread moved to **Programming Talk**.*

There are a variety of options, and many of the regulars who look at the Programming Talk section of this forum will have their favourite language. 

Sometimes the best option will depend on your level of programming experience, and sometimes the answer will depend on the kinds of prgram you wish to develop.

---

### Post by r-senior on 2013-03-06
The best choice of language will depend on the application that you want to write. Knowing more would help people give better advice. 

Does it need intensive processing, where speed is important?
Does it need a GUI?
Is it a web application?
Does it need to be cross-platform, i.e. run on Windows and Mac OS?

EDIT: "I don't know", is an acceptable  answer to the above.

---

### Post by Warren Hill on 2013-03-06
There are lots of languages to choose from and you will get lots of different answers depending on
 a) Who you ask
 b) What you are trying to do
c) What languages you know already

 
[LIST]
[*]If for example you want to develop little desktop applications for  Ubuntu take a look at quickly this uses glade to design a user interface  and is programmed in python.  There is a tutorial [here]("http://developer.ubuntu.com/get-started/")
[/LIST]
 
   
[LIST]
[*]Writing games for the Web you may want to consider Java or Flash
[/LIST]


[LIST]
[*]Large applications are usually written in C or C++
[/LIST]

 
[LIST]
[*]Web pages with dynamic content may be easiest is Perl or PHP
[/LIST]

 and there are lots more.:)
 
Let us know exactly what you want to do and we can advise further.  But don't be surprised if you get differing opinions.:guitar:

---

### Post by slickymaster on 2013-03-06
There is a rule that says that you have to pick the right tools for the job. And like all the previous posts clearly state, before picking the tools you have to consider the overall architecture of your project.

For example, while developing a dynamic web page, you might consider JavaServer Pages (JSP)/servlets as the best option, and others might prefer using PHP or a similar scripting language. No single language is the "best choice." Though you might give preference to certain factors, such as performance and security in enterprise applications, other factors, such as fewer lines of code, might be lower priorities. There's always some trade-off.

IMHO you should take this factors in consideration:
[LIST]
[*]Targeted platform
[*]Elasticity of a language
[*]Performance
[*]Support and community
[/LIST]

I would advise to read this article: [How to choose a programming language?]("http://mortoray.com/2012/05/29/how-to-choose-a-programming-language/")

---

### Post by student321 on 2013-03-06
Thanks for all the responds! I want to make a application that can communicate with a shop's  payment device (like [https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRsnix8P5MfLHCb-Nv0t_SV5t-yJCXDuMCjgr_b5mR5th0rb1LV](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRsnix8P5MfLHCb-Nv0t_SV5t-yJCXDuMCjgr_b5mR5th0rb1LV) )

Quite hard as far as I know, but wanna do this. Of course I need practise with other projects, but this is my goal. I was thinking about Java becouse it is compatible with Windows and almost all other platforms. And becouse you can programm devices with it (so can this payment device??).

If you guys can tell me what scripting language I can use for this I would be very pleased. Couldn't find anything on the internet. 

Why I want to do this with linux? Becouse Linux is a stable platform if we are talking about touchscreens.

With kind regards,
Student321

---

### Post by rg4w on 2013-03-06
> **student321 said:**
> If you guys can tell me what scripting language I can use for this I would be very pleased. Couldn't find anything on the internet.
LiveCode is one of the scripting world's best-kept secrets, but now that it's going open source I suspect it won't be a secret for long:
[http://www.runrev.com/](http://www.runrev.com/)

Using a high-level scripting language with a well-integrated GUI object model, LiveCode can deploy to Linux, Mac, Windows, Android, iOS, servers, and soon Linux/ARM for Raspberry Pi.

If you decide to try it be sure to check out the forums: [http://forums.runrev.com](http://forums.runrev.com)

Very active and helpful community there.

---

### Post by KdotJ on 2013-03-07
> **Warren Hill said:**
>  

[LIST]
[*]Large applications are usually written in C or C++
[/LIST]


That is a very bold statement to make

---

### Post by Warren Hill on 2013-03-08
> KdotJ[INDENT]                              Re: Software programming
                          [QUOTE] [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **Warren Hill**                     [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12544089#post12544089")                 

                 

[LIST]
[*]Large applications are usually written in C or C++ 
[/LIST]
  
That is a very bold statement to make         [/INDENT]
[/QUOTE][INDENT]
[/INDENT]
    


I suppose it depends on your definition of large.  But this is my personal experience.

The Linux kernel is entirely C, most compilers, software in the majority of complex embedded systems, etc.

That does not necessarily mean that just because a program is big it must be written in C or C++ however, Facebook for example I am told is entirely php.

---

### Post by trent.josephsen on 2013-03-08
> **Warren Hill said:**
> I suppose it depends on your definition of large.  But this is my personal experience.

The Linux kernel is entirely C, most compilers, software in the majority of complex embedded systems, etc.


Lots of embedded systems, yes. Likely a plurality, but probably not a majority. But I wouldn't usually call embedded software, or even system software, "applications".

Point is, there's a huge variety of programming languages that are more or less equivalently appropriate for writing large applications, and the way your earlier post was worded made it seem like C or C++ might be the "natural" choice. I like C myself, but it wouldn't be my first choice for new development of... well, any desktop app with a GUI. (Not that there is no situation in which you should use C or C++ for such an application.)

When you're choosing a language, your options are really dictated by what you know and what platform you target, not how big the project will be.

---

### Post by nyrtZi on 2013-03-10
> **trent.josephsen said:**
> When you're choosing a language, your options are really dictated by what you know and what platform you target, not how big the project will be.

Oh well. Some languages do make it easier to write and maintain a large codebase (then again I assume you don't need anyone to point out to you).

---

### Post by KdotJ on 2013-03-10
> **nyrtZi said:**
> Oh well. Some languages do make it easier to write and maintain a large codebase (then again I assume you don't need anyone to point out to you).

How so? Not a dig, just interested to hear your experience.

In my personal experience [COLOR=#808080]*(note: that means I'm not saying I'm right)*[/COLOR] the maintainability has always been driven by the project design and architecture (including things like version control and branching strategies), not by the actual language itself.

---

### Post by r-senior on 2013-03-10
The availability of tools and frameworks for a language can make a difference for enterprise-scale applications. I'm thinking of things like dependency-injection frameworks, unit testing frameworks, continuous integration tools, object-relational mapping, etc.

---

### Post by slickymaster on 2013-03-11
> **r-senior said:**
> The availability of tools and frameworks for a language can make a difference for enterprise-scale applications. I'm thinking of things like dependency-injection frameworks, unit testing frameworks, continuous integration tools, object-relational mapping, etc.

+1
IMHO, that's absolutely correct and to the point.

---

### Post by tehcavil on 2013-03-11
> **Warren Hill said:**
> [INDENT]
[/INDENT]
    


I suppose it depends on your definition of large.  But this is my personal experience.

The Linux kernel is entirely C, most compilers, software in the majority of complex embedded systems, etc.

That does not necessarily mean that just because a program is big it must be written in C or C++ however, Facebook for example I am told is entirely php.

Just a note: actually now that they got big, I heard the facebook devs translated alot of it into C++ using [HipHop]("http://en.wikipedia.org/wiki/HipHop_for_PHP").

---


---
title: "[SOLVED] Kdevelop C++ compiling problem  [ G++ says there's and error in one of std h"
date: 2008-02-13
forum: Programming Talk
---

### Post by dempl_dempl on 2008-02-13
Hi guys,

 I'm making some library which actually  does something useful, and I'm planing to release it under GPL . 

It compiles nicely under Code::Blocks ,  hence , so it's not library problem.

I don't want to bore you with details , but for some reasons,   , I need to work a little bit  with  Kdevelop.
And here's where we we get to the problem.

When I try to compile clean code ,  Kdevelop reports and error that : 

```

/usr/include/c++/4.1.3/bits/stl_algobase.h:300: error: &#8216;memmove&#8217; is not a member of  &#8216;std&#8217;
...
...
..
9999999999  errors 
...
/usr/include/c++/4.1.3/i486-linux-gnu/bits/messages_members.h:102: error: &#8216;strcmp&#8217; is not a member of '&#8216;std&#8217;


```

Has anyone seen that yet? 

Once again, code behaves nicely in Code::Blocks, so I doubt it's  something to do with Gcc .

Thanks in advance

---

### Post by zanak on 2008-02-13
hi,
you can try to use : using namespace std;
just after you include.

---

### Post by dempl_dempl on 2008-02-13
*snip*

---

### Post by aks44 on 2008-02-13
Care to share some (simplified?) code to see if we can reproduce the error?

---

### Post by zanak on 2008-02-13
tks dude :) ou sir lay n3al taboun mouk a welld al 9a7ba

---

### Post by dempl_dempl on 2008-02-13
> **zanak said:**
> tks dude :) ou sir lay n3al taboun mouk a welld al 9a7ba
He he, you're nuts , I like you :-) .


> 
Care to share some (simplified?) code to see if we can reproduce the error?



How about whole  Kdevelop project ?  
There's Code::Blocks project in the same directory.

I'll leave out  auxiliary components ( although those are the most important ones ) , in order not to complicate things to much .

**if** ( you can't reproduce an error) 
     ,  It's some configuration thingie at my place;
**else**
     It's a bug;

 I'm making a archiving library . It will be  called ZipFactory.

It implements couple of very cool design patterns, which I've stolen from Alexandrescu's "The Modern C++ Design" book. This is probably my last project in normal programming, I'm planing to play with AI and NeuralNets when I grow up :-) , [ I'm  only 22 now :-D ]

Oh. I've almost  forgot, here's the link to project... 
[www.stosha.net/zipfactor-01-rev3.tar.gz](www.stosha.net/zipfactor-01-rev3.tar.gz)

---

### Post by aks44 on 2008-02-16
Sorry for the delay...

I managed to get rid of all STL-related errors... guess what, the compiler doesn't really like when you name one of your files like a file that is part of the standard includes... (string.cpp/.h ;))

Renaming them to strings.cpp/.h (and adjusting your source files accordingly) solved most of the errors, now you're left with way less compilation errors that I didn't try to solve (since they come from your own code, a few missing std:: qualifiers and semicolons as far as I can tell, ...).


Unrelated advice: if you want to distribute your code you'd better stop using links like you do, they are a real PITA for other people (I had to recreate your whole directory tree /home/dule/..., if I hadn't I would have had to relink every single .cpp/.h file in src :shock:)

:D

---

### Post by dempl_dempl on 2008-02-16
He he...   it worked!

string.cpp   ...  I would not see that in even if I've been staring in library for a million years :-)   ... 


It's strange that it worked in code::blocks  , though .

You've seen some libary related error, most likely because  I've forgot distribute some file      [ what else? :-)  ]   ...


As far as  the links   are considered,  I didn't do it! ,     Kdevelop made them .  I'll  clean them up  before I start distributing the library.  During the development time, It will do the job.

Ask44, Thanks a lot !

---

### Post by Zwack on 2008-02-16
> **dempl_dempl said:**
> 
As far as  the links   are considered,    Kdevelop made them.  I'll  clean them up  before I start distributing it.  During the development time, It will do the job.


And that is why I don't like IDEs that make me work the way they want me to...

It's like the original Microsoft FrontPage web pages... they were so full of so much hidden cruft that whenever I came across them I usually spent five minutes removing all of the pointless additions that weren't being used.

Z.

---

### Post by dempl_dempl on 2008-02-16
Well,  I'll easily make my own makefile when I've done with testing code.

It's funny how the Kdevelop creates  absolute links.  I can actually send some post to their Bugzilla...  naaaaaah ...  No-one ever reads   feature requests , even when they're paid for that [ at least I don't  :-D ]  .  Maybe If I send them Bug Report at level SEVERE... that could draw their attention for a couple of seconds....

---


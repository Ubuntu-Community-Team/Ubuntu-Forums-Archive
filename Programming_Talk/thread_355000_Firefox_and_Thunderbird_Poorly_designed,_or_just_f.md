---
title: "Firefox and Thunderbird: Poorly designed, or just feature-rich?"
date: 2007-02-06
forum: Programming Talk
---

### Post by jblebrun on 2007-02-06
I've got a bone to pick with Firefox and Thunderbird. These two applications really are great. They've implemented a lot of nice features, and they work well for the most part. Firefox is numero uno when it comes to non-windows web browsers.

But I don't like these applications, because they are un-necessarily memory intensive. Is the memory usage of Thunderbird really necessary? Why is it that firefox needs a 117 meg resident memory set, when I have one tab open, with one page? Is it using this memory for something that's enhancing my experiment, or is it just poorly designed? If I close firefox, and re-open it, displaying the same page, the process only take 56 megs (still a lot, but not as bad). Why this discrepancy? Is firefox particularly leaky?

I really don't know the answer to this question. That's why I'm asking. Perhaps someone who's hacked around in the Firefox or Thunderbird code base can give me some feedback.

---

### Post by lnostdal on 2007-02-06
firefox is known to leak (google "firefox leak") .. i haven't been able to find any fixes that actually work

it's a problem; maybe some of you "C++ fans" (which it is written in) could dive in and fix it with your l33t "memory management isn't a real problem"-skillz or explain to me how "this would never happen in _my_ software" .. bwahaa .. :P (just kidding; please don't - i don't care)

seriously though - it's annoying but not a big-big problem .. not here at least .. FF is running for days with very intensive use and a _lot_ of tabs and about 3-4 windows open at the same time at all time .. a restart of FF every 3 to 4 days does the trick .. this laptop has been up for 47 days and i've been continuously beating the crap out of it 24/7 so linux must at least be doing a good job cleaning up after FF et al :)

---

### Post by LordHunter317 on 2007-02-06
Yes, they're poorly designed and written software.  It's fairly obvious why.

---

### Post by Wybiral on 2007-02-06
Are you at it again, lnostdal? *shakes head in disappointment*

My programs seriously don't have any memory leakage... But it's probably because I manage everything myself, whereas firefox is manages by lots of people. There's obviously more room for error.

But generally... If you use your destructors wisely and you try to use STL containers wherever possible, you probably wont run into a memory leaks. But, I've never made a webbrowser and I have no idea why they would need as much memory as firefox uses...

I'm just saying... It's not C++, it's improper use of C++ or improper communication on a project. It's not that hard to delete old memory... Use smart pointers... Or better yet, use STL containers.

Ps, I'm not trying to start a language war... I'm just saying, I haven't managed to cause any huge memory leaks in any of my projects, and yes... I do use a lot of dynamic memory, but I also use C++'s built-in ability to make dynamic memory safer.

---

### Post by clouserw on 2007-02-06
> firefox is known to leak (google "firefox leak") .. i haven't been able to find any fixes that actually work
Firefox2 stopped a great deal of the memory problems.  If you're still not happy with the footprint, there is an [article at mozillazine]("http://kb.mozillazine.org/Reducing_memory_usage_(Firefox)") that might help.  (The first step is to run firefox in safe mode and see if it helps.  A lot of times someone will blame an extension's poor memory management on firefox).

> **LordHunter317 said:**
> Yes, they're poorly designed and written software.  It's fairly obvious why.

huh?  Please share these obvious details with the rest of us...

---

### Post by LordHunter317 on 2007-02-06
> **Wybiral said:**
>  But generally... If you use your destructors wisely and you try to use STL containers wherever possible, you probably wont run into a memory leaks. But, I've never made a webbrowser and I have no idea why they would need as much memory as firefox uses...Unintelligent caching is part, plus poor garbage collection of JS objects (especially in extensions) and a very leaky code base.

[quote=clouserw]huh? Please share these obvious details with the rest of us...[/quote]If you have to take active time to fix leaks, you have a bad design.  If it's an issue impacting performance, it's a bad design.  If you have to almost start over because you had to throw your rendering engine out, it's a bad design.  If you have to split your browser and email into two seperate projects because of performance and code quality concerns, it's a bad design.  If they no longer can us the same shared libraries because of poor cohesion, it's a bad design.  If you have as many security flaws as you do, it's a bad design.  And I haven't even said XUL, yet.

---


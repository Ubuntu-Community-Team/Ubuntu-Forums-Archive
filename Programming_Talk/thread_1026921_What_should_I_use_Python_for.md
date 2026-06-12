---
title: "What should I use Python for?"
date: 2008-12-31
forum: Programming Talk
---

### Post by Amazona aestiva on 2008-12-31
Hello,

I've been learning C++ (and wxWidgets) for a year.

I started learning Python now and I've got a question: What problem should I solve with Python rather than C++?

Thanks

---

### Post by Tony Flury on 2008-12-31
Personally I would use python for any job for which you need to be able to use some of the complex data constructs easily (lists, dictionaries etc). I also find GTK easier to use in Python than in C/C++. I would only use C/C++ for a job where I needed optimised code to do something CPU intensive. Even then i would probably write it so i could execute it from Python.

it is all personal choice.

---

### Post by giuspen on 2008-12-31
Python allows you to program faster avoiding to compile all the time and offering a great library, but if you want to build a strong and fast application probably u would rather use C++.
I personally use python + gtk (pygtk) and C++ + gtk (gtkmm) and love them both.

---

### Post by tinny on 2008-12-31
Pretty much anything.

Except:

Embedded software for micro controllers
OS kernel
Drivers

If I was you id be using Python for everything except the above.

---

### Post by pmasiar on 2008-12-31
> **Amazona aestiva said:**
> What problem should I solve with Python rather than C++?

Pretty much anything :-) C++ makes sense **only** if you really really need the speed, and there is no other simpler way to get there. So in 95% of the rest Python is preferable. 

You will see it for yourself, just spend a weekend learning Python. See wiki in my sig.

---

### Post by Amazona aestiva on 2008-12-31
Thanks the quick resposnes:)

I'll have a look at PyGTK and wxWidgets with Python. Has somebody have some experiance with them? Would you give me some comparison?

Thanks

---

### Post by wmcbrine on 2008-12-31
Everything that you started to do in C++, thought "Gee, this is a pain in the ***," and put aside. And everything else. :)

---

### Post by Wybiral on 2008-12-31
The thing I like most about languages like Python is that they make excellent prototyping languages. Say I have some idea or project that I need to articulate as quickly as possible, Python makes that process fast, clean, and interactive. Then if you find that your idea would work, but doesn't perform well enough in Python, you have a clean template to begin filling in with custom (compiled) library calls (but with all the existing Python libraries, it's rare that you need to write them on your own).

It's easy to improve the speed of most Python code just by replacing a few tiny loops (or frequently used functions) with C code... It's not easy to improve your development time and flexibility when coding in C/C++, so I would only do it if you KNOW that most of the code will need to be low-level (and this is rare, except for the above mentioned cases).

---

### Post by CptPicard on 2008-12-31
> **Wybiral said:**
> 
It's easy to improve the speed of most Python code just by replacing a few tiny loops (or frequently used functions) with C code...

Actually, having been doing this recently I can appreciate the counter-argument that especially if you really make use of Python's high level features, you end up introducing slowness all over very abstract code that you *can't* just easily replace as a separate C module, because by definition you're using Python's high-levelness to architecture the big picture, and the performance bottleneck is *that*...

---

### Post by slavik on 2008-12-31
I actually wonder when someone says to integrate C code, if they themselves have ever done it.

---

### Post by jimi_hendrix on 2009-01-01
use Python for things you want done

use C++ for whatever you feel it would be better for...

its really something that your instinct will decide

---

### Post by nebu on 2009-01-01
if u are thinking about implementing something.... python is a fast and beautiful way to test it out....

---


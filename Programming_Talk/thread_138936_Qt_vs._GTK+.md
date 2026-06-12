---
title: "Qt vs. GTK+"
date: 2006-03-02
forum: Programming Talk
---

### Post by grim918 on 2006-03-02
I was wondering which one of this would be easier to learn. From what I have read Qt is used on KDE and GTK is used for GNOME. I have also read that Qt is based on C++ and that GTK uses mostly C. Which one would be easier to learn for a first time GUI programmer.

---

### Post by LordHunter317 on 2006-03-02
Qt.  GTK is mired by it's language choice and GTKMM can't get around that.

---

### Post by gord on 2006-03-02
i stick to WxWidgets, being restircted to one gui isn't great for a lot of programs. even if you can get qt and gtk for windows n mac n stuff.

---

### Post by moberry on 2006-03-02
Several things to consider, let&#8217;s look at the pros and cons.

QT Pros:

Written in C++ (Object orientation is significantly easier in C++ due to classes)


QT Cons:
Not GPL, QT is made by a commercial company called Trolltech. This is not necessarily a bad thing, it is only undesirable if you choose to market your work (License agreement states you must pay Trolltech royalties for &#8220;using&#8221; their software)

GTK Pros:
Released under the LGPL license, meaning you can market your software without paying the GTK crew royalties. GTK is also ported to windows meaning you can,with very little editing make soure software work in the Microsoft world also. QT might be ported, but I dont think it is.

GTK Cons:

Written in C, pain in the ***&#8230; nuff said. By they way.. in GTK every other statement is a typecast unless you &#8220;cast it globally&#8221; in the first lines of the function.

I personally use GTK I have always preferred C. There are some C++ wrappers for GTK, called gtkmm. But I have never used them. To answer your question, forthe first time programmer... Both API's extensively use pointers, and you must keep track of your memory pretty carefully (deleting old pointers, freeing data, etc). So as far as learning curve, they are similar. QT will make more sense because of its c++ language choice. GTK uses some "hacked" ways of doing things. E.g. piggybacking data onto objects, etc.

I hope this helps.

---

### Post by engla on 2006-03-02
You can also learn PyGTK first, that's what I am doing.

It's a python binding for GTK, so it's object-oriented and on a very high level; python is a nicer/easier language than c++. You can still do mostly anything in pygtk and the smallest working program is very small, so it should be a good fit for a learner.

I can post examples if you want.

---

### Post by doclivingston on 2006-03-02
> **moberry]Not GPL, QT is made by a commercial company called Trolltech. This is not necessarily a bad thing, it is only undesirable if you choose to market your work (License agreement states you must pay Trolltech royalties for “using” their software)[/quote]

QT is double licenced GPL/commercial. If your software is released under the GPL, you don't have to buy a licence.

> GTK is also ported to windows meaning you can,with very little editing make soure software work in the Microsoft world also. QT might be ported, but I dont think it is.

QT work under Windows.


> Written in C, pain in the ***… nuff said. By they way.. in GTK every other statement is a typecast unless you “cast it globally” in the first lines of the function.

Or you use GTK from a non-C language said:**
> GTK uses some "hacked" ways of doing things. E.g. piggybacking data onto objects, etc.

You mean qdata? You shouldn't really need to use that very often, and the places where you do, you need a "hacky" solution anyway.

---

### Post by LordHunter317 on 2006-03-02
[QUOTE=moberry]QT Cons:
Not GPL, QT is made by a commercial company called Trolltech.[/quote]It's been GPLd for ages, for UNIX anyway.

---

### Post by LordHunter317 on 2006-03-02
[QUOTE=doclivingston]Or you use GTK from a non-C language; Python, C++ and Mono (C#) are the big ones, but there are also binding for perl and others. I'm not sure if there are non-C++ bindings for QT.[/quote]And as I said, none of them truly get away from some of the limitations that GTK and GLIB bring to the table as being originally written in C.

---

### Post by moberry on 2006-03-02
> You mean qdata? You shouldn't really need to use that very often, and the places where you do, you need a "hacky" solution anyway

I was refering to "g_object_set_data(GObject, const char* key,gpointer data)" I use it quite often to keep track of indexes in linked lists, etc.

It is not hacky at all from a C standpoint (quite normal) but from someone used to JAVA, or C#, it is quite hacky.

I could easily be mistaken about the KDE license. I got my new issue of Linux Journal the other day, and there was a column about that. KDE is free to use. But if you decide to charge for your software, things get complicated.

---

### Post by doclivingston on 2006-03-02
[QUOTE=moberry]I was refering to "g_object_set_data(GObject, const char* key,gpointer data)" I use it quite often to keep track of indexes in linked lists, etc.

It is not hacky at all from a C standpoint (quite normal) but from someone used to JAVA, or C#, it is quite hacky.[/QUOTE]

What would you do in Java/C#, use a map? In *most* situations you can use a GHashTable (which is a map).

There are situations where you can't use a GHashTable to do the mapping, but those are also sticky in pretty much any language.

---

### Post by doclivingston on 2006-03-02
[QUOTE=LordHunter317]And as I said, none of them truly get away from some of the limitations that GTK and GLIB bring to the table as being originally written in C.[/QUOTE]

Yes, GTK has warts and limitation because it is written in C. QT has warts and limitations because it was written in C++. Which are bigger depends on the language you want to use, and both have some issues when beng used from their non-native language.

If you want to program in C++, then QT is probably best. If you want program in C, then GTK is the way to go. For other languages it varies depending on which warts you want to live with.

---

### Post by moberry on 2006-03-02
BTW. Im not arguing, in case you thought i was being difficult.

I did not want to use a hashtable the last time I did this because that would have involved another traversal of the LL. While storing the pointer to the node didnt.

although.. on a 3ghz processor, probably doesnt matter.

---

### Post by LordHunter317 on 2006-03-02
[QUOTE=moberry]I was refering to "g_object_set_data(GObject, const char* key,gpointer data)" I use it quite often to keep track of indexes in linked lists, etc.[/quote]How can you be doing such a thing in the first place?  A linked list doesn't have an index.  They don't support such notations, except through artificial constraints.

---

### Post by moberry on 2006-03-02
Well, there is a way to access the data at an index using glib.. g_list_nth.

But that is bad to use because it traverses the list on every call. It is an abstract structure, but it is a list, and lists have numbered elements. I suppose i could have implemented it a totally different way, hashtables as you said. But i chose to use a list. and storing the pointer to a specific node is a pretty efficient way of doing something. Just as efficient as a hashtable.

---

### Post by doclivingston on 2006-03-02
[QUOTE=moberry]I did not want to use a hashtable the last time I did this because that would have involved another traversal of the LL. While storing the pointer to the node didnt.[/QUOTE]

I understand that it can be easier to use qdata. I was just saying that you probably would have done it with a map in Java/C#/whatever, and you could do the same with glib.


(Using qdata is storing it in a hashtable anyway, since it's implemented with one. It's probably less efficient to use qdata than your own hash table, since there is a hash table per-object and one will have to be created *for each object* if the objects didn't already have any qdata).

---

### Post by moberry on 2006-03-02
[QUOTE=doclivingston]I understand that it can be easier to use qdata. I was just saying that you probably would have done it with a map in Java/C#/whatever, and you could do the same with glib.


(Using qdata is storing it in a hashtable anyway, since it's implemented with one. It's probably less efficient to use qdata than your own hash table, since there is a hash table per-object and one will have to be created *for each object* if the objects didn't already have any qdata).[/QUOTE]


Keep in mind this conversation got started recommending QT, or GTK :-)

BTW, I saw you were using dapper on your side bar. Is that running nicely yet?

---

### Post by LordHunter317 on 2006-03-02
[QUOTE=moberry]Well, there is a way to access the data at an index using glib.. g_list_nth.[/quote]And that is a linked list?  If so, as I said, it's an artifical constraint on their implementation of a linked list.

Linked list don't support indexed lookup.  How does that work on a circular linked list, for example?

> It is an abstract structure, but it is a list, and lists have numbered elements.Some forms of lists, like arrays, do.  Linked lists don not.

>  But i chose to use a list. and storing the pointer to a specific node is a pretty efficient way of doing something.Which isn't storing an index.

---

### Post by moberry on 2006-03-03
If I were to implement the linked list like it was designed in the 50's, every time I needed data out of it I would have to start at the head, and work my way down until I found what I needed. My program stores the position in the list the I need for a certain type of data. Other functions in the program do traverse the list, as it was intended. There is nothing wrong with implenting an "index like" system in a linked list. It extends the capabilities for which it was originally intended for. Your right linked lists do not have the C definition for an index. But it is a list, and lists, at least in theory have numbers for where they are in the list. Even if the numbers dont actually exist. But I agree, index was a bad word to use.

Circular linked lists can be thought of in this same manner, the only advantage of a circ. linked list is if you are closer to the end than the start, its quicker to just loop around, then traverse up. In some cases.

---

### Post by Single on 2006-03-03
[QUOTE=LordHunter317]It's been GPLd for ages, for UNIX anyway.[/QUOTE]

Qt4 Open Source edition supports Windows, Macs and X11.

---

### Post by LordHunter317 on 2006-03-03
[QUOTE=moberry]If I were to implement the linked list like it was designed in the 50's, every time I needed data out of it I would have to start at the head, and work my way down until I found what I needed.[/quote]No, you wouldn't.  You'd do the O(n) lookup once, and cache a pointer to the node you're looking for, just like you're doing now.  Linked lists have always been used by that.

> My program stores the position in the list the I need for a certain type of data.No, that's impossible. **Linked lists don't support indexed look up.**  You might be storing a pointer to the node itself, but that's different, consider an array:
[ 4, 3, 2, 1]
The item at index 0 is 4.  In C or C++, I can either store the base of the array and the index (0), or I could store a pointer to the value itself (4).  With a linked list, you can only do the latter (ignoring artifical imposed constraints, like I said above).

> There is nothing wrong with implenting an "index like" system in a linked list.Yes, there is.  It artifically constrains your list: circular lists are now impossible, it forces you to retain a pointer to the same "start" node everwhere, and indexed lookup still requires O(n).

If you need indexed lookup, you use an array or some sort of map.

> It extends the capabilities for which it was originally intended for.No, it wrecks them.

>  Your right linked lists do not have the C definition for an index.Show me one datastructures book that defines the structure of a linked list supporting indexed lookup.  None do because it both artifically constrains the real definition and because it simply makes no sense.

> But it is a list, and lists, at least in theory have numbers for where they are in the list.No, that's not true in the least.  A set is a list, and by definition, a set has no ordering.  As such, you cannot provide a deterministic index on a list.

> Circular linked lists can be thought of in this same manner,No, they cannot.  How do I define start?  How do I define end?

> the only advantage of a circ. linked list is if you are closer to the end than the start,They have neither.  Draw a circle on paper.  Now, point to me the start and finish.

---

### Post by raedbenz on 2010-07-17
This is a topic we could keep talking about it infinitely. 
My personal experience: at some point I wanted to learn a programming GUI library, and at that time i chose GTK because it uses C because i am coming from embedded background. later on i had the chance to tackle Qt and as a result improved my c++ skills.
in summary if you know only C use GTK, if you are confident in C++ only use QT if you know both of them or wish to learn C++ then QT.
Qt is superior in support and tools.

---

### Post by slavik on 2010-07-17
the true way to decide: flip a coin

---

### Post by nvteighen on 2010-07-17
> **slavik said:**
> the true way to decide: flip a coin

But people will insist in searching other ways, dear slavik...

Really, there's almost no difference these days... not even the "I want to use C++" argument because gtkmm is perfect. Maybe the differences are in the tools (QtDesigner, Glade, etc.) rather than in the libraries themselves.

---

### Post by splicerr on 2010-07-17
> **raedbenz said:**
> This is a topic we could keep talking about it infinitely. 
My personal experience: at some point I wanted to learn a programming GUI library, and at that time i chose GTK because it uses C because i am coming from embedded background. later on i had the chance to tackle Qt and as a result improved my c++ skills.
in summary if you know only C use GTK, if you are confident in C++ only use QT if you know both of them or wish to learn C++ then QT.
Qt is superior in support and tools.

Well, there are many people who prefer to use a higher language to code their GUI. And no not everybody considers C++ to be a high-level language.

---

### Post by SledgeHammer_999 on 2010-07-17
> **raedbenz said:**
> This is a topic we could keep talking about it infinitely. 
My personal experience: at some point I wanted to learn a programming GUI library, and at that time i chose GTK because it uses C because i am coming from embedded background. later on i had the chance to tackle Qt and as a result improved my c++ skills.
in summary if you know only C use GTK, if you are confident in C++ only use QT if you know both of them or wish to learn C++ then QT.
Qt is superior in support and tools.

Don't forget you could use C++ with Gtk+([Gtkmm](www.gtkmm.org))

[quote=slavik]the true way to decide: flip a coin [/quote]
+1

---

### Post by slavik on 2010-07-17
> **nvteighen said:**
> But people will insist in searching other ways, dear slavik...

Really, there's almost no difference these days... not even the "I want to use C++" argument because gtkmm is perfect. Maybe the differences are in the tools (QtDesigner, Glade, etc.) rather than in the libraries themselves.
I solve problems, if they are looking for problems to not solve, that is their problem. :)

---

### Post by ravi.xolve on 2010-08-20
Both are mature frameworks, however Qt looks good because its in C++. Now Qt is being pushed as de facto API for Nokia devices which makes it an attaractive option.

---

### Post by worksofcraft on 2010-08-20
Use GTK because it works with Glade and Glade is an epic rad GUI tool for creating your own GUIs ;)

---


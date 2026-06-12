---
title: "[SOLVED] C programming in Linux"
date: 2007-11-29
forum: Programming Talk
---

### Post by sujoy on 2007-11-29
Hi everyone,

I have coniderable programming experience in C at the startup level.. like data structures, stacks, link lists, files, pointers, and such other things............. however, all my programming was done in the windows environment which I have now left for good.

I would be glad if someone could guide me towards the linux API (i dont know what its called exactly or if it even exists ). 

How can I interact with networks via a C code? And using the GUI in linux through C. By interaction, I mean like getting web pages, extracting data from remote networks. Any books or reference material or pdf's will be gladly appreciated.

Any paper books (like the ones i can read offline) that would help me?

---

### Post by LaRoza on 2007-11-29
Look in the stickies, look in my wiki.

If you already know ANSII C, learning POSIX shouldn't be hard.

It is well documented, so googling should be more fruitful than other subjects.

[http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

[http://laroza.pbwiki.com/C](http://laroza.pbwiki.com/C)

My wiki doesn't have much Linux Specific topics, but it has Sockets for networking.

---

### Post by slavik on 2007-11-29
When I took Workstation Programming class in my college, the professor used Understandix Unix/Linux programming by Molay. It is well structured IMO.

Explains what will be done, shows an analogy. translates analogy into system stuff (which functions will be needed for which parts), shows code samples and then has a very tiny manpage like thing for the important functions used in the exercise. :)

as for interacting, install the 'manpages' package, also make sure to have build-essential installed. :)

read up on using gcc (the basic command is `gcc -o hello hello.c`).

for a small nice IDE like thing, there is geany (available in the repository), for bigger things there is Anjuta, Kdevelop and Eclipse (with the CDT plugin). I use Anjuta (I do use Eclipse for Java related things though).

---

### Post by sujoy on 2007-11-29
thanks for the quick replies.....and search for that book too :)

I will be going through the wiki's surely and as far as IDEs are concerned, I am comfortable with vi (with syntax highlighting) and yes I have also got the manpages.......... its just that I dont have a 24x7 net access that I was searching for a book to guide me on to the advanced C levels or programming.

Btw, what about the GUI? Like developing something like the gcalculator will need a GUI.....so what can I use for that?

---

### Post by Majorix on 2007-11-29
You could use wxWidgets for GUI programming with C.

---

### Post by LaRoza on 2007-11-29
wxWidgets is for C++, not a big leap from C really.

GTK is in C.

My wiki has references for GTK, QT and wxWidgets. Of these, GTK is for C.

---

### Post by slavik on 2007-11-29
also, look into Glade (to design GTK GUIs) and libglade (creates a GUI from the XML file that Glade spits out).

---

### Post by wolfbone on 2007-11-29
NB. The glibc library and gcc are GNU projects. GNU projects generally have comprehensive and didactic documentation in the GNU texinfo format (info pages) but often don't even have man pages (glibc doesn't). The C library function man pages that are usually installed on a GNU/Linux system are okay for quick reference but they aren't from the glibc project and they aren't complete.

To learn about C library and gcc based programming in GNU/Linux, you will find the info documentation invaluable (that goes for many other tools besides the library and compiler too).

---

### Post by samjh on 2007-11-29
[EDIT]

Removed due to pirated material.

---

### Post by sujoy on 2007-11-29
alright people,  I got started with GTK and glade .............. looks good :)

thanks for all the help........

---

### Post by raul_ on 2007-11-29
basically, all you need is the "build-essential" package (for ubuntu) and a text editor. This is up to you. I use geany, which has some neat features (like highlighting custom typedef's and showing a list of auto-complete functions, even functions created by you some lines before. you have to save before geany does this though). but please DISABLE the auto-complete expression "feature" (yes, between " " ). It's horrible typing "for <space>, and ending up 3 lines after with a blank "for" statement, and having to move the cursor all the way up to fill the blanks (IMHO :) )

---

### Post by sujoy on 2007-11-29
yes build-essential is all I need to code in C, but how to implement the GUI without the GTK? for that I require the glade and the libgtk, etc... (forgot what the other dependencies were..)

as for the text editor, well i am using vim and its quite good

---

### Post by DMills on 2007-11-29
For generic systems programming in C on unixy things I am slightly surprised nobody has mentioned R.W.Stevens "Advanced Programming in the Unix Environment", which is pretty much the canonical reference for how to do things that don't involve graphics (Yes, a real hardback paper book, how old fashioned...). 

This covers working with processes, terminals, shared memory, synchronisation, networking all that stuff.

For higher level networking (specifically for things playing with HTML), look into libcurl which handles a lot of the low level pain.  

You will find that Linux makes very heavy use of third party shared libs to handle much of the sort of things that windows ships with as a base component, but that there is a fair subset of these that can be assumed to be installed on most systems. 

Regards, Dan.

---

### Post by sujoy on 2007-11-29
> For generic systems programming in C on unixy things I am slightly surprised nobody has mentioned R.W.Stevens "Advanced Programming in the Unix Environment", which is pretty much the canonical reference for how to do things that don't involve graphics (Yes, a real hardback paper book, how old fashioned...).

I have always loved these old fashioned paper books more than the pdfs...... its much easier to study them..... ;) and yes this is what I was really looking for. thanks again .

---

### Post by the_unforgiven on 2007-11-29
You might also want to check out [Advanced Linux Programming]("http://www.advancedlinuxprogramming.com") - it's available both in paper form as well as downloadable PDFs. Online (PDF) version can be handy if you're trying out programs as you read the text.

HTH ;)

---

### Post by Compyx on 2007-11-30
> **samjh said:**
> The 1988 edition of *The C Programming Language* by Kernighan and Ritchie and other C programming references are downloadable from: <URL removed>]

Nice one, linking to clearly pirated material. That book is worth every penny you pay for it (about 50 euro last time I checked).

---

### Post by samjh on 2007-11-30
> **Compyx said:**
> Nice one, linking to clearly pirated material. That book is worth every penny you pay for it (about 50 euro last time I checked).

I didn't know they were pirated.  The site was one of the first ones I found when searching for K&R, I thought such an obvious site would have been subjected to cease and desist orders by publishers.

Quite a lot of authors and publishers release books into the public domain, especially old ones.

Anyway, link removed as a precaution. :)

---

### Post by LaRoza on 2007-11-30
If it were the older version, 1988?, it would very very outdated, and possibly free by the publisher.

---

### Post by samjh on 2007-11-30
> **LaRoza said:**
> If it were the older version, 1988?, it would very very outdated, and possibly free by the publisher.

It was the 1988 version.

---


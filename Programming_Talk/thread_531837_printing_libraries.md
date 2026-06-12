---
title: "printing libraries"
date: 2007-08-22
forum: Programming Talk
---

### Post by aquavitae on 2007-08-22
A while ago I wrote a small program using c++ and Qt4 which involved printing out some tables.  My initial idea was to output a latex document, and then use latex to create a pdf which could be printed, but for various reasons this didn't work.  In any case, its a kind of messy way of printing - I have no control of how many, or which pages print and it requires a pdf reader to print.  In the end I hashed together a couple of classes to put all the stuff on a page and print it, buts its far from the ideal.  I'm now writing a similar sort of program using wxWidgets and I'm running into the same problem with printing.

I'd thought or writing a library which would work something like a tex stream - i.e. stream text and stuff to it and it will calculate page breaks, determine whats on a page, and print whichever pages I want to a device context.

Is there a better way of doing it, or does anyone know if there are already libraries that do this?  I don't want to spend ages writing it if there is something to do it already.

Any comments would be welcome!

---

### Post by pmasiar on 2007-08-22
Use scripting language like Python for that. Much friendlier facilities to process text than C++. There is even a module for PDF output, IIRC.

---

### Post by aquavitae on 2007-08-22
Thanks for the reply.

What do you mean by text processing?  I have no problem in c++ with processing strings, although I admit python is easier, but I'm more worried about efficiency.  The thing I hacked together using qt4 is very slow as it is and I suspect using python would make it worse.  Or do you mean text processing as in calculating text height, width etc?  The module for pdf output - does it do things calculating page breaks, or will I still need to do all that?

---

### Post by pmasiar on 2007-08-22
> **aquavitae said:**
> I'm more worried about efficiency.  The thing I hacked together using qt4 is very slow as it is and I suspect using python would make it worse.  

So your algorithm is slow, bad design, and you need to fix it. Python is plenty fast if you don't do stupid things.

And remember "speed is not a problem until it is a problem" and "premature optimization is root of all evil" :-)

> The module for pdf output - does it do things calculating page breaks, or will I still need to do all that?

Check the docs

---

### Post by aquavitae on 2007-08-22
> **pmasiar said:**
> So your algorithm is slow, bad design, and you need to fix it. Python is plenty fast if you don't do stupid things.I know.  Thats why I want to rewrite it.  But the function that slows it is qt's bounding function to calculate the size of the text.  With a different design I might be able to cut down the number of calls, but however I do it I still need to size each section of text.
> 
And remember "speed is not a problem until it is a problem" and "premature optimization is root of all evil" :-)
Agreed.  But I'd still like to keep c++ an option.
> 
> The module for pdf output - does it do things calculating page breaks, or will I still need to do all that?

Check the docs
Will do.  Thanks.

---

### Post by aquavitae on 2007-08-23
Well, I had a look but I couldn't find IIRC anywhere.  I did find ReportLAB (python) though which looks like it does what I want.  Has anyone used this - know anything about it?

---

### Post by Compyx on 2007-08-23
> **aquavitae said:**
> Well, I had a look but I couldn't find IIRC anywhere.
Hehe, no wonder, "IIRC" means "if I recall correctly", a term you'll find often on Usenet and internet fora.

 > **aquavitae said:**
> I did find ReportLAB (python) though which looks like it does what I want.  Has anyone used this - know anything about it?
Don't know anything about that one, but it looks promising...

---

### Post by aquavitae on 2007-08-24
Ok... :oops: Now I feel a bit silly - hunted for IIRC for about half an hourm and I wondered why the search brought up such unrelated results...

As you say, reportlab does look promising, except that it appears to only export to pdf.  I want to be able to print to any dc (e.g. preview window, printer).  I've decided that if I can't find anything I will write it, but I don't really have the time.  I also don't really care what language it is - if its something I don't know I'll learn it.

---

### Post by Compyx on 2007-08-24
How about generating html/xml? That way you can let the browser worry about layout, throw in some css/xsl and you should be able to control the way stuff is printed/displayed.

---

### Post by aquavitae on 2007-08-24
Hadn't thought of that.  I don't know html that well (or css/xsl at all), but it looks easy to learn.  I did try generating latex, but the problem I had was that I needed a different header/footer on each page (I was trying to do long tables with running totals) and I couldn't seem to do it in latex.  Before I get into html could you tell me if its possible to do what I want to do with it?

I suppose the other advantage of html is that most widget libraries seem to support it, at least I know wxwidgets and qt do, so I wouldn't have to use an external browser.

---

### Post by pmasiar on 2007-08-24
> **aquavitae said:**
> hunted for IIRC for about half an hourm and I wondered why the search brought up such unrelated results...

LOL. Sorry. Next time, try also [http://www.acronymfinder.com/](http://www.acronymfinder.com/)

---


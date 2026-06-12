---
title: "D compiler"
date: 2007-01-06
forum: Programming Talk
---

### Post by rawler on 2007-01-06
I see this have been asked several times in the past, but still without action. I would very much like to see some (basic) support of the D programming language in Ubuntu.

It might be argued back and forth which programming language "rulez" and "suXX0r". But I'd think DMD or GDC would prove a LOT more useful than some of the less frequently used, but still maintained packages in Synaptic. (I.e. some very old, or extremely immature games, where I'd say some of them attracts less users than I've got fingers.)

Any chance of getting this into Feisty, or at least Feisty+1?

Anyone know of external repositories hosting this? (Ten minutes of Googling gave me nothing.)

---

### Post by gummibaerchen on 2007-01-07
D 1.0 is only a few days old.

Is DMD free software?

GDC is of course, so I think there may be good chances to see that in Feisty.

You should request that package. (I think Launchpad.net is the right place for that).

---

### Post by unipal on 2007-02-12
I have looked for an alternative programming language. I looked at C++, Java, Python and Ruby until I found D programming language. This is a really great!!!  

Some usefull text and links:

From de site of Digitalmars:
D is a systems programming language. Its focus is on combining the power and high performance of C and C++ with the programmer productivity of modern languages like Ruby and Python. Special attention is given to the needs of quality assurance, documentation, management, portability and reliability.

DMD compiler for Win32 and Linux...

The front end for D is open source, and the source comes with the compiler. The runtime library is completely open source. David Friedman has integrated the D frontend with GCC  to create gdc, a completely open source implementation of D.

D  vs Other Languages:
[http://www.digitalmars.com/d/comparison.html](http://www.digitalmars.com/d/comparison.html)

Complete overview of the D programming language:
[http://www.digitalmars.com/d/lex.html](http://www.digitalmars.com/d/lex.html)

Wiki:
[http://www.prowiki.org/wiki4d/wiki.cgi?FrontPage](http://www.prowiki.org/wiki4d/wiki.cgi?FrontPage)

Check it out!!

---

### Post by gummibaerchen on 2007-02-13
Thanks, unipal.

:popcorn:

---

### Post by sard on 2007-02-13
I got DMD working on Ubuntu by just unzipping this [http://ftp.digitalmars.com/dmd.zip](http://ftp.digitalmars.com/dmd.zip) and running dmd mysourcefile.d in the bin folder.

I haven't been so lucky with Tango [http://www.dsource.org/projects/tango/wiki/Features](http://www.dsource.org/projects/tango/wiki/Features) the alternative runtime library.

I can't wait for D to catch on but I wish it didn't have a stupid un-search-engine friendly name :)

---

### Post by gummibaerchen on 2007-02-13
> **sard said:**
> I can't wait for D to catch on but I wish it didn't have a stupid un-search-engine friendly name :)

[Search D in Google]("http://www.google.com/search?hl=en&q=D+programming+language&btnG=Search") :lolflag:

---

### Post by sard on 2007-02-13
Just shows that you have to make sure you put "programing language" in the same sentence for it to show up.  There must be plenty of stuff that gets lost.

---

### Post by Coyote21 on 2007-09-21
> **sard said:**
> Just shows that you have to make sure you put "programing language" in the same sentence for it to show up.  There must be plenty of stuff that gets lost.

Good point

Also there's an thread that shows, the things that are wrong in D, [http://ubuntuforums.org/showthread.php?p=3405170#post3405170](http://ubuntuforums.org/showthread.php?p=3405170#post3405170)

---

### Post by Blue Sky on 2007-09-22
D is hardly a matured language at present.

I doubt it will be included in Ubuntu anytime soon.

---

### Post by Jessehk on 2007-10-06
I installed the Gutsy beta and GDC is included in the Universe repository. :)

---


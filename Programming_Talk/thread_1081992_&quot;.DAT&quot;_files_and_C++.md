---
title: "&quot;.DAT&quot; files and C++"
date: 2009-02-27
forum: Programming Talk
---

### Post by Ferrat on 2009-02-27
I want to create a sort of archive file where I can store data(variables) as well as sound and pictures (more or less an archive), I get the idea of how I'm supposed to do this more or less but I have some requirements. 

Need to me indexed and searchable etc, got a general idea about how to do this as well, but then again I might be wrong but an fairly easy way seems to be to have "triggers" for ex. the chars ## indicate a position starts and lets say a number after that to show what pos. you're at for ex.

Well been looking around and seems that the standards streams in C++ wont cut it? or am I wrong? if not please say so otherwise I'm guessing I have to go down a level in hierarchy and create my own file input/output so any documentation on this would be great :)

---

### Post by dwhitney67 on 2009-02-27
It appears that you are choosing the language, which it doesn't seem that you are confident/intimate with, and then you are trying to hash out a design.

Come up with a design first, then see if can be supported by the language.  You would be surprised what can be accomplished with C++.

Btw, if all you want to do is archive data into file, and then retrieve it at a later time, you may want to consider looking at [Google's Protocol Buffers]("http://code.google.com/apis/protocolbuffers/").

---

### Post by CptPicard on 2009-02-27
How about [http://en.wikipedia.org/wiki/Berkeley_DB](http://en.wikipedia.org/wiki/Berkeley_DB) ?

---

### Post by Ferrat on 2009-02-27
> **dwhitney67 said:**
> It appears that you are choosing the language, which it doesn't seem that you are confident/intimate with, and then you are trying to hash out a design.

Come up with a design first, then see if can be supported by the language.  You would be surprised what can be accomplished with C++.

Btw, if all you want to do is archive data into file, and then retrieve it at a later time, you may want to consider looking at [Google's Protocol Buffers]("http://code.google.com/apis/protocolbuffers/").

Well the point of it is to learn so yes I'm asking because I'm not sure :) just don't want to invest learning something that is the wrong way to go about it

----------------------------------------

Thx CptPicard, that looks interesting

---

### Post by dwhitney67 on 2009-02-27
> **Ferrat said:**
> Well the point of it is to learn so yes I'm asking because I'm not sure :) just don't want to invest learning something that is the wrong way to go about it
...
That's the point!

Come up with a list of operations on:

1) What data you want to store;
2) What format do you want the data to be stored in (ie. ascii, binary, xml, etc);
3) What criteria do you have for obtaining the data from storage;
... and so forth.

Perhaps the best solution is to store your data in a database; maybe in a flat file?

Either way, some of these decisions are programming language independent.  But once you narrow down what your requirements are, then you can choose a language.

---

### Post by Ferrat on 2009-02-27
> **dwhitney67 said:**
> That's the point!

Come up with a list of operations on:

1) What data you want to store;
2) What format do you want the data to be stored in (ie. ascii, binary, xml, etc);
3) What criteria do you have for obtaining the data from storage;
... and so forth.

Perhaps the best solution is to store your data in a database; maybe in a flat file?

Either way, some of these decisions are programming language independent.  But once you narrow down what your requirements are, then you can choose a language.

1. I know what data, variables, images, sound and text.

2. Not sure about the format, doesn't really matter, I take the fastest, it's just about file handling really, getting an easier overview :) 

3. criteria, as I said it has to be indexed and searchable, fairly fast.

4. Also reading can be buffered, doesn't have to be on the fly, it's meant to load from it / to it, not constantly work against it.

5. Don't care about file lock. 

a Database is what I had in mind, all I was asking about was the limitations of the standard file input/output operations within C++ :) as I said they seem a bit linear etc for what I want to build but I might be wrong. 
Also if someone could point me in the right direction, be it the standard functions or something I have to write myself. 

Any help would be great, I prefer diving in a bit, helps me learn, usually I can find some direction to go by searching but this seems to be an unspoken subject or I just got the wrong search params :P

---


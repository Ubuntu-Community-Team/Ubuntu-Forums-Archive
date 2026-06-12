---
title: "Expat XML Parser Library"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by zurga on 2012-11-08
[SIZE=3]Ubuntu 12.04
Using the method xmlparser.Parse() on a short piece of XML text works just fine. But when the same text, or any text, is put  in a file and passed to xmlparser.ParseFile(), the parser breaks immediately with 'Memory Error', indicating that Expat is not able to allocate memory internally. I use a code like:[/SIZE]
[INDENT][LEFT][SIZE=3]with open("xml_file") as f:
[SIZE=3]    p.ParseFile(f)
[/SIZE][/SIZE][/LEFT]
[/INDENT][SIZE=3][SIZE=3]where p is an instance of the Expat Parser clas[SIZE=3]s. [SIZE=3]Any fix or workaround will be greatly appreciated.[/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by zurga on 2012-11-09
The problem was being caused by using an instance of the parser that had already parsed a complete xml statement. It appears that the parser cannot parse more than one statement, and further statements have to be parsed by new instances of the parser, unless there is a way, which I don't know, to reset the parser state to the start point. Sorry for posting essentially a non-bug.

---


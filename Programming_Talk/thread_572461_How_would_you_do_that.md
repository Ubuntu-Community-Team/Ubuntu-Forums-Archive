---
title: "How would you do that?"
date: 2007-10-10
forum: Programming Talk
---

### Post by Max_Might on 2007-10-10
Hello, Im thinking about creating a program similar to the famous [Website Watcher]("http://www.aignes.com/") for windows.

The idea is that the program will download html file and after some time will download it again and compare the two files. Then it will display the new/changed text colored in yellow for example. For the rendering i can use gtkhtml or something but I dont know how to compare the html files and get the diferences. Is there any libraries which can be helpfull for this task?

Ps: oh and the language will be c++ or python, not sure yet :)

---

### Post by Can+~ on 2007-10-10
Maybe as a firefox extension would be easier.

---

### Post by Wybiral on 2007-10-10
C has libCurl. Python has urllib that you can use to download the HTML (it also has a bunch of XML/HTML parsing libraries as well that might come in handy). Python also has pyGtkMozEmbed that lets you embed the mozilla browser in your Gtk apps.

---

### Post by bigboy_pdb on 2007-10-12
The program "diff" checks the lines of text files for differences. If you don't want the program to be a shell script (or to call "diff") then you could look at the code for diff to see how it perform comparisons.

The following postscript document talks about a "diff" algorithm:
[http://www.cs.dartmouth.edu/~doug/diff.ps](http://www.cs.dartmouth.edu/~doug/diff.ps)

---

### Post by pmasiar on 2007-10-12
Python has a recent new module (IIRC templatemaker or something) which gets 2 copies of the page and determines what part are static and what can be changed by template (to simplify screenscraping). IIRC submitted by someone from Django community.

---

### Post by Max_Might on 2007-10-13
> Maybe as a firefox extension would be easier.

Well, even if it is a FF extension i still have to find the differences between the files.

> C has libCurl. Python has urllib that you can use to download the HTML (it also has a bunch of XML/HTML parsing libraries as well that might come in handy). Python also has pyGtkMozEmbed that lets you embed the mozilla browser in your Gtk apps.

Thank you, the downloading of the files will not a big problem. As of HTML parsing, i am not sure how it should be organised i.e. take the contents of every tag and compare it with the same tag but from the old document? :confused::confused::confused:

---

### Post by slavik on 2007-10-13
wget and diff. :)

---


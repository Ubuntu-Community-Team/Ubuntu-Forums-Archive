---
title: "write pdf with perl"
date: 2007-03-21
forum: Programming Talk
---

### Post by evaristegalois on 2007-03-21
I want to generate pdf files with perl, e.g. writing tax receipts for 300 people where most of the information is always the same with a few variables. Now latex works reasonably well: perl writes into a tex file and pdflatex will convert the tex file to pdf. But I am not happy with some of the latex formatting which is good for journal articles but not great for other things. I tried writing to html and then printing to pdf. That looks good online but awkward on paper. What code other than tex or latex writes pdf files? Can you code an open office document with perl?

--evaristegalois

---

### Post by phossal on 2007-03-21
Here are six pages that might help: [http://search.cpan.org/search?query=PDF&mode=all](http://search.cpan.org/search?query=PDF&mode=all)

---

### Post by evaristegalois on 2007-03-22
Interesting but not quite what I am looking for. It appears to be a daunting task to learn how to write pdf files directly. But isn't there something like html for the written page, i.e. what html does for a web page I want to do for a printed page. Again, TeX works in a lot of ways but I'd like to know if there are alternatives.

--evaristegalois

---

### Post by WW on 2007-03-22
If you were using python, I would suggest **reportlab**: [http://www.reportlab.org/](http://www.reportlab.org/)
The Ubuntu package is **python-reportlab**.  If you don't find a perl library that meets your needs, you might consider using a bit of python.

---

### Post by evaristegalois on 2007-03-22
I'll have a look at that. Thanks. I'm surprised there aren't any obvious candidates that work with any programming language, especially text-savvy perl.

--evaristegalois

---

### Post by LotsOfPhil on 2007-03-23
You said: "I am not happy with some of the latex formatting which is good for journal articles but not great for other things."

TeX can look like pretty much anything. You should be able to make your template suit your needs.
[http://www.tug.org/texshowcase/](http://www.tug.org/texshowcase/)

---

### Post by evaristegalois on 2007-03-26
Thanks. I'll try that. My problem is mostly margins. For some things you just don't want LaTeX's generous margins. I also want more flexibility in placing things on the page, such as images. Anyways, I'll work away and see how I can help myself. I guess TeX is so good at this stuff that there is no serious competitor when it comes to text processing with a source file.

---

### Post by evaristegalois on 2007-04-14
I've since then discovered ConTeXt, a version of TeX quite different from LaTeX, which gives you a lot more flexibility than LaTeX. Highly recommended. Solved all my problems. Here is the wiki for ConTeXt:

[http://wiki.contextgarden.net/Main_Page](http://wiki.contextgarden.net/Main_Page)

---

### Post by phossal on 2007-04-14
I was surprised to see this thread show up in my subscriptions. In fact, a couple years ago, I did a lot of pdf business reports using [PDF::Create]("http://search.cpan.org/~ftassin/PDF-Create-0.01/lib/PDF/Create.pm") and perl. I'm shocked at what horrible advice I gave the first go 'round. Sometimes I can't remember the solutions I've used in the past. Oh well, glad you found a useful tool.

---

### Post by evaristegalois on 2007-09-05
TeX (in particular, CoNTeXt) is definitely a good way to produce pdf files using perl. TeX is  a difficult program to learn for a beginner, however. I found a more elegant solution for someone who knows html:

Write the html code with perl and then use the program htmldoc to convert to pdf. Done. The results can be quite appealing, and html is in some respects more flexible than TeX.

---

### Post by dwblas on 2007-09-06
I output to postscript, which is straight forward, and then use one of the ps2pdf* to convert.  The only problem I have ever run into is using fonts that are not type1 which causes the ps2pdf to hang trying to find a replacement font.  If you stick to standard fonts like Helvetica, you won't have any problems..
Edit - here is a file that was lying around if you want to test ps2pdf on your machine```
%!
%%----------------------------------------------------------------------
%%      test_shaded.ps
%%      Draw shaded box test
%%----------------------------------------------------------------------
/inch {72 mul} def      % Convert inches->points (1/72 inch)

/Times-Bold findfont    % Get the basic font
12 scalefont            % Scale the font to 12 points
setfont                 % Make it the current font

2 setlinewidth          % make lines darker

newpath
 1.00 inch  1.00 inch moveto
 1.00 inch  4.00 inch lineto
 1.50 inch  4.00 inch lineto
 1.50 inch  1.00 inch lineto
closepath
0.95 setgray
fill
0 setgray

 1.05 inch  2.50 inch moveto
(2000) show
stroke

newpath
 3.00 inch  1.00 inch moveto
 3.00 inch  4.00 inch lineto
 3.50 inch  4.00 inch lineto
 3.50 inch  1.00 inch lineto
closepath
0.95 setgray
fill
0 setgray

newpath
 3.00 inch  1.00 inch moveto
 3.00 inch  4.00 inch lineto
 3.50 inch  4.00 inch lineto
 3.50 inch  1.00 inch lineto
closepath
 3.30 inch  2.30 inch moveto
90 rotate
(2090) show
-90 rotate
stroke

newpath
 5.00 inch  1.00 inch moveto
 5.00 inch  4.00 inch lineto
 5.50 inch  4.00 inch lineto
 5.50 inch  1.00 inch lineto
closepath
0.95 setgray
fill
0 setgray

newpath
 5.00 inch  1.00 inch moveto
 5.00 inch  4.00 inch lineto
 5.50 inch  4.00 inch lineto
 5.50 inch  1.00 inch lineto
closepath
 5.20 inch  2.70 inch moveto
-90 rotate
(2091) show
90 rotate
stroke

showpage
```

---

### Post by evaristegalois on 2007-09-25
are there any tutorials where you can learn how to write source code for postscript?

---


---
title: "Creating a pdf of the info pages?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-31
How do i create a pdf of the info pages. I want all the nodes to be included as hyperlinks, etc.

Can the same be done with a webpage? Where i can save a webpage alongwith all the hyperlinks to that page. I have heard of this software called httrack, and think it does just that. Don't know how to use it though?

---

### Post by WRDN on 2008-08-31
If you are using Firefox, you can use [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636") to save webpages in the PDF Format. The pages retain any formatting.

---

### Post by gmxgeek on 2008-08-31
> **wrdn said:**
> if you are using firefox, you can use [pdf download]("https://addons.mozilla.org/en-us/firefox/addon/636") to save webpages in the pdf format. The pages retain any formatting.

+1

---

### Post by 7raTEYdCql on 2008-08-31
I am talking of the info pages that i get in termina;

---

### Post by eyyou101 on 2008-08-31
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by y-lee on 2008-08-31
There are plenty of web pages with HTML versions of the Linux man pages on them, such as [this one]("http://linux.ctyme.com/"). Also if one visits the home page of [Texinfo - The GNU Documentation System]("http://www.gnu.org/software/texinfo/") one can find 

> The latest texinfo.tex macro file used for converting Texinfo source to DVI or PDF files for printing and viewing, using the TeX typesetting system.

I haven't used that macro so I know nothing about it. But it sounds like what you are hunting for.

Good luck.

EDIT: There is also a [texi2latex]("http://www.nongnu.org/texi2latex/texi2latex/index.html") program which can convert Texinfo documentation file to monolithic LaTeX files ready to be processed by latex and pdflatex. Link is also on the gnu textinfo web site.

---

### Post by pyromanic123boom on 2008-08-31
> **i.mehrzad said:**
> I am talking of the info pages that i get in termina;

If you want your terminal printed, (which is what I guess with your typo), just copy all text (rightclick, copy,) and paste it into a word processor..then ctrl-v to paste it. print using the PDF virtual printer.

---

### Post by 7raTEYdCql on 2008-09-02
can ps2pdf be used for conversion of the gnu-info pages i get in terminal for this purpose.

I mean i can convert man pages to pdf format using the command
```
 man -t command | ps2pdf -> command.pdf
```
this will create the pdf of command and name ir command.pdf.

Now suppose if i want to create the output of any command to pdf then what can i do?

Honestly, I dont know why i love pdf's? Why i want everything in that format?

---


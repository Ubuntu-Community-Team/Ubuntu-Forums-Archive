---
title: "html question"
date: 2005-11-12
forum: Programming Talk
---

### Post by ofek on 2005-11-12
well i've programed alot ... and never did a real web developing.
im used to the idea that u shouldn't write the same thing twice for that there are procedures and functions(and alot more...).
im building the html of my site and well i got a top logo and a menu to the right and some other stuff which are the same in every page.
my question is if there is anyway to write those stuff only once and include it in all the pages (without frames, iframes and those stuff)?
i guess the answer is no but i gotta be sure.

---

### Post by kperkins on 2005-11-12
Use php include.
You'll have to use the .php extension (instead of .html, or .htm) for your pages, but it's worth it, so you can change your headers, footers, etc. at will, and only change one file.
code is as follows :
[PHP]<? include ('/path/to/header.template'); ?>[/PHP]
You can mix php and regular html on a page, also.  It's a very small learning curve unless you want to get real fancy.

---

### Post by ofek on 2005-11-12
ty, i should have said my web gotta be in asp ... so i guess ill do it with asp(vb script) although i realy hoped there is something u can do with html but i guess there isnt.

---

### Post by David Marrs on 2005-11-13
I don't know much about classic ASP, I'm afraid, but in ASP.NET you can create web user controls (.ascx extension) that you can include in aspx pages in much the same way you'd include a header.h in a C file. It may be that there's an .asc equivalent for classic ASP.

As far as HTML goes, there's nothing you can do directly with html (that I'm aware of) but obviously it's quite easy to reuse <div> tags between pages and some dedicated HTML editors allow you to create a template HTML file for a project first and then easily edit that file for each page. Of course, you can do this manually to a point as well.

---

### Post by kanenas.net on 2005-11-13
Like php, you can use ASP include...

```
<!--#include virtual="/folder/folder/file.asp"-->
```

It's much easier to use templates in your site ! It helps you maintain your code and you don't have to go through many lines of code all the time.

---

### Post by endersshadow on 2005-11-13
It's good to note that ASP won't let you do dynamic includes, but PHP will :)

---

### Post by kanenas.net on 2005-11-14
The approach is to use a variable to hold the name of the file that you wanted to include and then pass the name of that variable to the include directive.

The main page (a template file containing the page layout and any static content) would be loaded and passed to a string variable. Then, the contents of the include file would be loaded and passed to a string variable. The variable containing the contents of the include file would be inserted into the contents of the variable containing the main page.

;)

---


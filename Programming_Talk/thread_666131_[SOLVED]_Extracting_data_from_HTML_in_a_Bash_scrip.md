---
title: "[SOLVED] Extracting data from HTML in a Bash script"
date: 2008-01-13
forum: Programming Talk
---

### Post by PeterJS on 2008-01-13
I started working on writing a very simple "spider" (it's hardly worth the title) as a bash script. I've managed to pull all the pages that I need data from, but I'm running in to a bit of a block as to how to get the specific data I want back out.

There's a whole bunch of extraneous data on the page, header, footer, some ajax menus. All of the elements I'm interested in have the same classname. After I find the elements I'm looking for I want to be able to run some DOM related queries on them, such as finding out how many children a specific element has, and conditionally extracting urls from links.

What would be the best way of going about this?

---

### Post by geirha on 2008-01-13
I think you should consider a different language for this. Bash is not well suited for such complex parsing. It's possible of course, but I think you'll find python, for example, a better choice for parsing html.

---

### Post by Compyx on 2008-01-13
I agree with geirha, although what you want can be accomplished with bash and a lot of grep-calls, I think using another language more suited for this task would be more helpful.

Like geirha said, look into Python, it has some nice libraries to parse HTML/XML and what not: [http://docs.python.org/lib/markup.html]("http://docs.python.org/lib/markup.html")
An alternative would be to look into Perl, which is very powerful when it comes to parsing text.

---

### Post by PeterJS on 2008-01-13
I was afraid of the impending you should be using perl replies. I started in bash because it's what I know, I guess it's time to go learn python.

---

### Post by PeterJS on 2008-01-13
I'm trying to use the minidom parser now, and it's not working. In fact the error is something I knew to be true, but was hoping that it would overlook, namely that the html I'm feeding it has mismatched tags and other errors. Is there any way to make the parser more forgiving?

Here's what I've got so far. It dies on that first line because the html is sloppy, and obviously the print down at the bottom is just for debugging once I get it to parse I was going to replace that with a more complex bit of manipulation.

```

FullDom = xml.dom.minidom.parse('/home/peter/sub.html')

AllTds = FullDom.getElementsByTagName('td')

for td in AllTds:
	if(td.getAttribute('class')=='threadbit'):
		print td.getAttribute('id')

```

EDIT2:

Ok so I completely scrapped that idea and have managed to get the data I wanted by extending the HTMLparser class based on these instructions:
[http://cis.poly.edu/cs912/parsing.txt](http://cis.poly.edu/cs912/parsing.txt)

---


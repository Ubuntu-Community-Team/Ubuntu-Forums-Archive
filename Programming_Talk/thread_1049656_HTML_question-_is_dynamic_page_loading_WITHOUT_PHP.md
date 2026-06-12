---
title: "HTML question- is dynamic page loading WITHOUT PHP or SSI possible?"
date: 2009-01-24
forum: Programming Talk
---

### Post by AFarris01 on 2009-01-24
The question is pretty straightforward... im building a little website for myself, and i want to keep things like my menu and my content seperate from the pages themselves to make updating easier... unfortunately the free hosting solution i'm using doesn't allow Server-Side Includes, and has PHP url includes disabled for free accounts.  This nixes the only 2 methods i'm familiar with for dynamic pages.

Is there another way to accomplish this?

---

### Post by Reiger on 2009-01-24
Yes. AJAX, for one thing: [http://www.w3schools.com/Ajax/ajax_intro.asp](http://www.w3schools.com/Ajax/ajax_intro.asp).

---

### Post by AFarris01 on 2009-01-24
Thanks for the quick reply, and the link!

unfortunately I'm not familiar with javascript, so i suppose thats gonna be another project for me in the coming weeks...:-({|=

---

### Post by CptPicard on 2009-01-24
Hmm, AJAX requires server-side code. I am pretty sure Reiger means just client-side Javascript.

Framesets or IFRAMEs are another option. They are discouraged as design elements but rules are meant to be broken...

---

### Post by slavik on 2009-01-24
how does ajax require service side code? ajax has no trouble getting just html code which you can embed in a div :)

---

### Post by DocForbin on 2009-01-24
If the only reason you need dynamic pages is for easier development/maintenance, you could use a preprocessor to generate static pages. So your menu is all in one file(s), but is applied to each page when you generate them. This also gives the best performance.

---

### Post by AFarris01 on 2009-01-24
thats essentially exactly what i want to do...

menu in a separate file,
content in a separate file,
have a master page that will include both the menu and the content pages.

there are going to be numerous other pages on the site, but these will generally be static, and not require frequent editing, so the only thing i'd want to include in them is the menu.

i do like the idea that AJAX presented of being able to dynamically load content onto a single page though, rather than creating dozens of independent static pages and hyperlinking to them. If this could be accomplished with client-side only efforts, then that would be my ideal solution at this point...(though I'd be happy with only the menu being independent)

EDIT:
Forgive me for my ignorance, for i have only recently come out of my "HTML only" shell... how could I apply a preprocessor to my webpage?  I understand the concept of a preprocessor due to a, relatively minuscule, background in c++, but I'd have no idea how to use one in HTML

---

### Post by DocForbin on 2009-01-24
the first google result for html pre-processor looks promising and explains the concept:

[http://www2.lifl.fr/~beaufils/gtml/](http://www2.lifl.fr/~beaufils/gtml/)

There are lots of em out there, and some authoring tools have this ability built in. They are also easy enough to make in any language to if all you need is basic <include file here> functionality.

Basically you would create your website and put some type of pre-processor instructions in the html files, e.g. <include file = "myheader.html">. Then when you make a change to myheader.html you run it through the pre-processor first and it re-generates all the html pages, relacing the include with the body of the page.

---

### Post by AFarris01 on 2009-01-24
Thanks a bundle for that link.  that looks like it will work superbly for my task!

---


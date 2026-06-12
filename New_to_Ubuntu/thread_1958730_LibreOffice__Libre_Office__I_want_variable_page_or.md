---
title: "LibreOffice / Libre Office:  I want variable page orientation (lanscape portrait mix)"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by haplorrhine on 2012-04-14
All I want is some pages as portrait format and others as landscape format.



[http://help.libreoffice.org/Writer/Changing_Page_Orientation_Landscape_or_Portrait](http://help.libreoffice.org/Writer/Changing_Page_Orientation_Landscape_or_Portrait)
Using the linked article's directions, I set up a landscape-formatted page-style.  I can set all pages to that style, but I don't know how to set only certain pages to that style.> All pages in the current scope of page styles will be changed. The article says it will explain "scope of page styles", but it never does.



[http://en.libreofficeforum.org/node/1392#comment-14075](http://en.libreofficeforum.org/node/1392#comment-14075)
I already tried inserting a manual break and then changing the style.
For me, there is no "Landscape" option in the "Style" menu of the dialog that appears when I select **Insert > Manual Break****[B].**[/B]  This person implies that there is.

---

### Post by lhowaf on 2012-04-14
Not on a system with Libre Office installed at the moment but I believe the break has to be a section break - not just a page break.

---

### Post by haplorrhine on 2012-04-14
I don't know what a section break is.  Based on my Google search, I think it's an Open Office thing.

---

### Post by lhowaf on 2012-04-14
I think you are (unfortunately) correct.

---

### Post by haplorrhine on 2012-04-14
I give thanks anyway.

---

### Post by newboon2 on 2012-04-14
I am using Writer in LibreOffice 3.4.4 on Ubuntu 11.10 and for what it's worth, the instructions you linked to work for me. 

My custom page style appears (some scrolling required) in the _S_tyle popup when I insert a manual break and choosing it changes the orientation of the current page and the pages that follow, until another page break specifying a different style is inserted.

---

### Post by haplorrhine on 2012-04-14
> **newboon2 said:**
> (some scrolling required)
Thanks newboon!  I didn't even know that list under Style in the dialog box could scroll!  The scroll bar deceptively fills the whole bar, whereas the drop-down menu only shows three items at a time.  Yes, it works now.

I just joined this forum in search of an answer, but nobody can post yet.  Is everybody waiting for it's commencement with anticipation?
[https://www.libreoffice.org/get-help/forum/]("https://www.libreoffice.org/")

---

### Post by dwhite on 2012-04-15
to insert a landscape page

[LIST]
[*]insert a manual break, select the page break button, and on the style pull down menu just below the button choose landscape (see first screenshot below)
[*]all following pages will be in landscape orientation (see second screenshot)
[*]when you want to switch back insert a manual break, select the page break button, and on the style pull down menu choose default (see third screenshot)
[*]all following pages will be in default (i'm assuming portrait for default) orientation (fourth screenshot)
[*]repeat anytime you want to change to a new orientation
[/LIST]


oops solved while i was composing this, sorry

---

### Post by haplorrhine on 2012-04-15
oooh barely too late, but that post should be understandable to future viewers.

I just solved another problem.  I copied the text from the top of the first landscape page, and I wanted to paste it into a portrait page, but I had to insert it into the middle of a paragraph.  If I didn't, the page break would paste with it, and all the text ahead of it would become landscaped.

---


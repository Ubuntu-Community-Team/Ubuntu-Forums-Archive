---
title: "Homework Related"
date: 2008-01-04
forum: Programming Talk
---

### Post by Mr.popo on 2008-01-04
Part of my dida(double i.t) course work is to make an eportfolio. All of my class are using tables generated in Dreamweaver but I thought I should take it further by making a template in photoshop. Im having trouble with my sub navigation though. Usually when i make navigations i make an image with text already on it but i think with this i should put links over the top of the image with html. If im going to do that then how should i do it. Would I need to slice each part of the navigation up? If not how would I do a tab in html because in html it makes all text one spaced.
My eportolfio is attached below. The sub navigation is the silver bar below the blue bar.


Thanks

---

### Post by slavik on 2008-01-04
1. nice design
2. yes, you will most likely have to create slices, unless you overlay the silver bar with divs or some such ...

note: I am not very experienced with web dev.

---

### Post by Mr.popo on 2008-01-04
Thankyou for the advice.

---

### Post by nathandelane on 2008-01-04
So if I understand correctly, you want to know how to make tabs in HTML.  Are just asking in general or did you want to use the tabs with your photoshop template somehow? Generally speaking you could emulate tabs either with separate HTML pages, or with Javascript. Of course if you take the Javascript route, then you should learn how to degrade gracefully ([http://www.quirksmode.org/js/contents.html]("http://www.quirksmode.org/js/contents.html")).


You could definitely use divs, spans, or an unordered list (<ul>) to create your tabs.  You could even use a table. You just need to make a javascript event handler to handle which tab is on top (do this by using the css 'display' attribute).

Does that help a little?  I can give you more direction if you can draw up exactly what you're thinking of. I have my own web site: [http://nathandelane.awardspace.com](http://nathandelane.awardspace.com) - I've done tabs in the past, but they were a little obtrusive (in the way), so I changed everything up.

Nathan

EDIT:

Usually when one emulates tabs in HTML, there are two pieces visually: 1) the clickable tabs at the top, side, or wherever, and 2) the tab content.

---


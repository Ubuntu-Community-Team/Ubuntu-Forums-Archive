---
title: "Sorting/Arranging Content in HTML"
date: 2011-03-04
forum: Programming Talk
---

### Post by Rhemat on 2011-03-04
Heya All,

I am re-coding my home page, and I'm currently trying to code my home page so that I can arrange all the links according to how I want (for example, all links I deem to be under "blogroll" will get sorted to the top when I click a link).  I'm thinking I would put them under their own div tags, but some of the links fit into more than one category (for example, Last.FM fits under "blogroll," and "music").  I was hoping there was a tag that I could use to assign tags (like used in this forum), but Google searching hasn't helped much.

Thanks in advance for your assistance.

---

### Post by Peter76 on 2011-03-04
You should use a list for this and then CSS to style it. With CSS you can set multiple classes on an element, BUT if I recall correctly, IE of course doesn't play nice with this ( check with Google ).
Example:
[HTML]<ul>
  <li class="blogroll music">first link</li>
  <li class="etc">second link</li>
</ul>[/HTML]

---

### Post by Rhemat on 2011-03-04
Thanks Peter,

I was assigning classes to the parent objects, but that does make more sense.  Now I just need to know how rearrange the links on the page when clicking a link.
About IE, not important, as it will be viewed strictly on my machine.

---

### Post by Peter76 on 2011-03-05
Hi Rhemat, 

I do not understand exactly what you are trying to do, but you could use css again to change the position of the links according to their state; google css pseudo classes for this.
But if you want some sort of animation, javascript is the way to go. There are a lot of frameworks out there with tons of animation effects. I guess at the moment jquery is your best bet, but correct me if I'm wrong. I also never really worked with that myself, but javascript is not that hard.
Good luck,

Peter

---


---
title: "web programming question."
date: 2010-01-17
forum: Programming Talk
---

### Post by hockey97 on 2010-01-17
Hi, I made a div colored with a button. I used jquery javascript to make a button on that div that once clicked it will fade in a form to the far right.

This makes the  div box go off the browser screen creating a scroll to the right. 

How can I make it so that the scroll dosen't just stop at the end of the div box that is far right part of it. I want to make some white space in-between the  div colored box and the scroll bar of the web browser.

any ideas?

---

### Post by wieman01 on 2010-01-17
Could you put your site on-line and post the link please? This will make it a lot easier for us.

---

### Post by hockey97 on 2010-01-17
Below will be a screenshot of what I am talking about.


The blue box is the one I am talking about. If you notice towards the right of the blue box is nothing but the web browser. 

I want to make  a small gab between th blue box and the scroll bar of the web browser.  If you look at it... it seems ulgy the way it is. So I want background to be shown on the right of the blue box. Background  meaning the main background of the whole website.

here is the image:

[IMG]http://i49.tinypic.com/23itds5.png[/IMG]


If you notice the blue box looks as if it's been cut off. I want it to look like a box not like it got cutoff. 

if you see that buton called interested. That button onced clicked fades in the the blue box. So that means yes I am using jquery javascript for this. So the box fades in and has absolute position in css file. 

I want to keep the blue box in that position just want to browser screen to move more to the right so it shows the background and show that the blue box is a box not like a rectangle that got cutoff. 

I hope you get what I am trying to say. If not please reply and ask. I would like some work around doing this.

---

### Post by Hellkeepa on 2010-01-17
HELLo!

This is what "margin-right" is for, alternatively "padding-right" on the body-tag.

Happy codin'!

---

### Post by hockey97 on 2010-01-18
I just tried that. It dosen't work.  it won't do anything.

Also this blue box appends once clicking that interested button.

So when the page is loaded it dosen't have this blue box until you click that button and it will fade int this blue box.

I just want a small gap between the blue box and the browsers scrollbox. 

that is all.

---

### Post by Reiger on 2010-01-18
Assuming you mean the right-most blue column:
You can put padding on the html element and both padding and margin on the body element. Furthermore you can use constructs with position:relative; and left or right offsets set appropriately.

If not: if you meant blue-box being the blue thing with the text in it, above the button &#8220;interested&#8221; this will not work as expected because of the fact that scrollbars are bound to a corresponding block-box (e.g. div element). So the only way to do that (padding on the right) would be to put the blue-background element wrapped inside a container element that is to contain/produce the scrollbars via appropriately set overflow.

---

### Post by Hellkeepa on 2010-01-18
HELLo!

If we had the actual page to look at, and study, we would be in a much better position to give you more accurate help.

Happy codin'!

---

### Post by wmcbrine on 2010-01-18
[Oh, no, he couldn't do that! Everyone would steal his awesome design!](http://ubuntuforums.org/showthread.php?t=1280355) :)

---

### Post by hockey97 on 2010-01-19
If the page you get is a form asking country and state and city. 

I have 2 text examples  which you put in country United States, State Michigan, City  Detroit   items  automobiles. 

You will get 2 the page where I am working on. If you click that interested button 2 times you will see the blue box fade in.

---

### Post by hockey97 on 2010-01-19
> **Reiger said:**
> Assuming you mean the right-most blue column:
You can put padding on the html element and both padding and margin on the body element. Furthermore you can use constructs with position:relative; and left or right offsets set appropriately.

If not: if you meant blue-box being the blue thing with the text in it, above the button “interested” this will not work as expected because of the fact that scrollbars are bound to a corresponding block-box (e.g. div element). So the only way to do that (padding on the right) would be to put the blue-background element wrapped inside a container element that is to contain/produce the scrollbars via appropriately set overflow.



no, I don't want to make a scrollbar in the blue box. 

I am talking about the web browsers  scrollbox. you know when you surf the web  and use the web browser sroll bar that is to the far right side. It's always there.

in the screen shot the bright blue box. I want that to not look like it has been cut off. I want white-space in between that box and the webbrowsers scroll bar the one that is always shown the one you use on every website but it's not part of the website but part of the web browser.

---

### Post by lavinog on 2010-01-20
> **hockey97 said:**
> no, I don't want to make a scrollbar in the blue box. 

I am talking about the web browsers  scrollbox. you know when you surf the web  and use the web browser sroll bar that is to the far right side. It's always there.

in the screen shot the bright blue box. I want that to not look like it has been cut off. I want white-space in between that box and the webbrowsers scroll bar the one that is always shown the one you use on every website but it's not part of the website but part of the web browser.

Put the whole thing in a table. set the width to a percentage of the browser width.

---

### Post by Hellkeepa on 2010-01-20
HELLo!

No, no, and no again. Abusing tables in this way is bad, and leads to unmaintanable code.
Give me a few mins, and I'll tell you exactly what's wrong, why and how to fix it.

*Edit, added:*
Hey... Why remove the link?

Happy codin'!

---

### Post by s_ø on 2010-01-20
Pretty funny asking how to 'repair' html/css code you wont show to anyone.
Check out this site [http://www.positioniseverything.net/](http://www.positioniseverything.net/) as the title implies, position IS everything. And there are several ways of accomplishing what you want, it all depends on what else you want with your site.

But if you paste the code or a link to your site, Ill be happy to propose a sollution

Btw: Tables are for presenting tabular structured data, like a spreadsheet. Not for general web-design.

---


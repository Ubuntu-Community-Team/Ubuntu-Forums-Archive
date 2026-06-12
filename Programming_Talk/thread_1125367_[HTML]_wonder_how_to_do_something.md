---
title: "[HTML] wonder how to do something"
date: 2009-04-14
forum: Programming Talk
---

### Post by Bodsda on 2009-04-14
Hi, ive been learning HTML and its going ok, i can make a basic site etc. etc. but what i would really like to do is make a site look more professional. What i would like to know is.. How do i make the main content of my site be in a central block. 

That may be a little confusing so here is a link to a site that does something similar -- [http://www.hackthissite.org/](http://www.hackthissite.org/) -- All the content is centralized and i think it looks really professional.

Any hints or info/references would be highly appreciated.

Thanks,

Bodsda

---

### Post by namegame on 2009-04-14
You might want to look into CSS (Cascading Style Sheets).

They are used specifically to create the "Style" of your page. IE Fonts, color, layout, etc.

Here are some links that I have found useful:

[http://www.csszengarden.com/](http://www.csszengarden.com/)
[http://www.w3schools.com/css/](http://www.w3schools.com/css/)

---

### Post by nvteighen on 2009-04-14
> **Bodsda said:**
> Hi, ive been learning HTML and its going ok, i can make a basic site etc. etc. but what i would really like to do is make a site look more professional. What i would like to know is.. How do i make the main content of my site be in a central block. 

That may be a little confusing so here is a link to a site that does something similar -- [http://www.hackthissite.org/](http://www.hackthissite.org/) -- All the content is centralized and i think it looks really professional.

Any hints or info/references would be highly appreciated.

Thanks,

Bodsda
Definitely, you need to learn CSS. I guess the stickies have links that may help you.

---

### Post by Bodsda on 2009-04-14
Hi, thanks for your reply, ive already started to delve into css, but im unsure what i am looking for. Do they achieve the affect through borders, margins, dividers etc?

---

### Post by Tibuda on 2009-04-14
> **Bodsda said:**
> Hi, thanks for your reply, ive already started to delve into css, but im unsure what i am looking for. Do they achieve the affect through borders, margins, dividers etc?
Yes, and don't forget background-image, that's really !important.

---

### Post by namegame on 2009-04-14
> **Bodsda said:**
> Hi, thanks for your reply, ive already started to delve into css, but im unsure what i am looking for. Do they achieve the affect through borders, margins, dividers etc?

Typically, CSS styles are applied to HTML tags. I feel that one of the most important things to learn with CSS is the Style hierarchy.

In order of precedence:

Inline
Page
External

So, for example, let's assume you want EVERY page in your site to have the same color background, this would be defined in an external CSS.

However, if you want a style to affect one particular instance of a tag, inline would be best, like ```
<h2 style="text-align: right;">My Heading</h2>
``` would only affect that particular H2 tag.

As far as a "center" layout, I would look at the CSS properties of margin-left and margin-right.

---

### Post by Bodsda on 2009-04-14
Thanks for all the replies :)

I understand how css works, and will look into the margins shortly. But im unsure if the margins will be sufficient on their own, if i use margins, how can i then set the background of the space left by the margin?

---

### Post by Reiger on 2009-04-14
The trick with a lot of positioning is the `auto' value. That value tells a browser to distribute left-over space evenly wherever auto applies. So if you have a margin-left:auto; and a margin-right:auto; it should try to make sure that margin-left == margin-right and hence that your element gets centered relative to its parent. If its parent is the body element that means you center that child on screen.

It's fool & resolution proof, but some (old MSIE) browsers need a little hint in the form of a text-align:center; or so I read once.

For your last question: remember that HTML is rendered as a top-down view on a stack: each parent element lies below the child elements on the stack. (You can manipulate the relative stack `order' of your element using the z-index CSS property, thereby displaying on top or below other elements.)

---

### Post by TheBuzzSaw on 2009-04-14
I have 4 books dedicated solely to CSS. It really is the key to making a slick design. You should have no presentational markup in your HTML.

---


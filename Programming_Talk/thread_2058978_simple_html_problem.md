---
title: "simple html problem"
date: 2012-09-17
forum: Programming Talk
---

### Post by sid0972 on 2012-09-17
hey
i was going through this code on w3schools here

[http://www.w3schools.com/html/tryit.asp?filename=tryhtml_layout_divs](http://www.w3schools.com/html/tryit.asp?filename=tryhtml_layout_divs)

and i was wondering if i could change the values of width and height from px to %, to make them compatible with every browser
but if i change the heigt to 100%, the page remains the same, or becomes smaller.
But if i specify values in px, it aligns itself properly, but that must be at a particular resolution.

How can i change the height in % so that it is reflected there?

Thank you

---

### Post by greenpeace on 2012-09-17
hi! 

Can you post the code, or send us a link to the page you're working on?

---

### Post by Vaphell on 2012-09-17
that link he posted shows the code

it's a simple layout of header div, main part split between left side menu div and right side content div, footer div.

---

### Post by trent.josephsen on 2012-09-17
From [http://www.w3.org/wiki/CSS/Properties/height](http://www.w3.org/wiki/CSS/Properties/height):

"The percentage is calculated with respect to the height of the generated box's containing block."

The containing block of the #menu <div> is the #container <div>. So setting #menu { height: 50% } (for example) will set the height of #menu to half the height of #container.

But #container doesn't have a set height -- its height is automatically calculated based on its contents. In CSS-speak, it has "height: auto". So the way this works is that without a set height in the parent, the child can't take 50% of it, and defaults to "height: auto".

Long story short: if you want it to work that way for any of the inner <div>s, you must give the #container <div> a set height in pixels. I'm not sure if there's a way to take advantage of <body> or <html> to avoid using pixels at all -- I suspect so.

A better solution most of the time is to leave it at "height:auto".

EDIT -- Think about this simple example:

```
<div id="outer">
  <div id="inner">
    <p>Hello world!</p>
  </div>
</div>
```
and CSS:
```
#inner { height: 50% }
```

There's nothing in the #outer <div> besides the #inner <div>, which is supposed to take up only 50% of it. But div#outer has height:auto, which means it shrinks to the size of its contents. The <p> element won't take up less than 16 or so pixels of vertical space (depending on font), so what sizes should div#inner and div#outer be?

The problem arises because the size of div#outer depends on the size of div#inner, which depends on the size of div#outer which depends on... ad infinitum. That's why percentage sized elements aren't allowed within automatically sized ones. (Well, they're allowed, but the height property is ignored.)

---

### Post by Vaphell on 2012-09-17
i've seen claims that using *html, body { width: 100%; height: 100%; border: 0; padding: 0; }* can make the content expand to fit in available space. From here it should be easy to use only percentages.


BTW sometimes shortcomings of that HTML+CSS business make me wonder if these guys working on its standards think about real life use cases.
I am amazed that we are currently at 3rd iteration of CSS yet we still can't define variables nor mix units, which would be perfect for fixed header/footer and flexible content in the middle ( afaik calc() is not finalized yet and can only be tested with vendor specific prefixes, eg -moz-calc( 100% - 100px + 3em ) ). For what, 10 years you have to use dirty hacks and tons of javascript to do simplest things?

---

### Post by trent.josephsen on 2012-09-17
It's the curse of HTML. Rooted in the 80s, continually abused for things it was never designed for, suffering PTSD from the Browser Wars and eternally enslaved to backwards compatibility, its only hope is to be put out to pasture. I don't know what could replace it though.

---

### Post by spjackson on 2012-09-17
> **trent.josephsen said:**
> It's the curse of HTML... I don't know what could replace it though.
Flash? ;-)

---

### Post by GreatDanton on 2012-09-17
> **spjackson said:**
> Flash? ;-)

NOOOOO! Flash is devil's seed :lolflag:. At least is not working properly in Linux (high cpu usage).

---


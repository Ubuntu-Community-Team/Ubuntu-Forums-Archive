---
title: "formatting div tags"
date: 2005-10-22
forum: Programming Talk
---

### Post by oldmanstan on 2005-10-22
how would i get a <div> tag to expand to fit (vertically) when the contents of a <div> tag inside of it expands... for example

<div> <--- this one stays the same size
<div> <--- this one ends up expanding outside the other one
this text gets really long and wraps
</div>
</div>

---

### Post by wmcbrine on 2005-10-22
You could try something like "height: 100%", I guess. Or else use "overflow"  (see [http://www.quirksmode.org/css/overflow.html](http://www.quirksmode.org/css/overflow.html) ). But maybe we need more context to understand what you really want.

---

### Post by oldmanstan on 2005-10-22
[QUOTE=wmcbrine]You could try something like "height: 100%", I guess. Or else use "overflow"  (see [http://www.quirksmode.org/css/overflow.html](http://www.quirksmode.org/css/overflow.html) ). But maybe we need more context to understand what you really want.[/QUOTE]

the web site was exactly what i needed.  i set the <div> tag to overflow : auto and with no height explicitly specified it expanded properly (at least using epiphany and firefox, lord only knows what IE will do to it).  thanks!

---

### Post by David Marrs on 2005-10-23
I think you will also need to position it relatively and not absolutely.

---

### Post by majikstreet on 2005-10-23
I hate what IE does to div tags-- I just gave up and said screw the people who use IE!

---

### Post by David Marrs on 2005-10-24
I envy you for being in a position to be able to ignore IE like that.

---

### Post by majikstreet on 2005-10-24
[QUOTE=David Marrs]I envy you for being in a position to be able to ignore IE like that.[/QUOTE]
mmm... I do wish I could code for ALL browsers, but it's just not that easy considering to test IE I have to go into another room with a Windows computer..

---

### Post by atoponce on 2005-10-24
For the most part, if your code validates against the W3C as well as your CSS, you will be safe.  Still, different browsers support different levels of CSS, so you'll still need to test your site across all browsers.  The two most important hiccups to remember for IE are:  it does not like relative positioning, and transparent PNG's are not supported.

---

### Post by oldmanstan on 2005-10-24
Actually, after reading the responses and making appropriate changes I ended up having a totally different but related question... is there a way to use an expression in a CSS property?  for example...
```

div.somebox {
[INDENT]width: "100% - 250px";[/INDENT]
}

```
Obviously that doesn't work (at least it didn't when I tried it...) but is it possible to somehow work an expression into a property like that?

---

### Post by atoponce on 2005-10-24
Check out the 'expression()' attribute for CSS.  it was designed for IE 5.0 in conjunction with JavaScript.  It works, but generally, you will want to avoid it.  There is no reason why you can't align divs properly without it.  In fact, I believe it is being removed from the CSS specification by the W3C.  Can anyone verify this?

---

### Post by wmcbrine on 2005-10-25
Alas, CSS is not a programming language, and doesn't have that kind of power. If you really needed to do that subtraction, you'd have to resort to Javascript.

However, instead of "width: 100% - 250px", you might get away with something like "margin-left: 250px" (or margin-right, as appropriate). Then you can float the divs so that one covers the other's margin.

Re: testing on IE, I've been using Ubuntu's Terminal Server Client to connect to my XP system via RDP. :D

---

### Post by oldmanstan on 2005-10-26
[QUOTE=wmcbrine]However, instead of "width: 100% - 250px", you might get away with something like "margin-left: 250px" (or margin-right, as appropriate). Then you can float the divs so that one covers the other's margin.[/QUOTE]

That was a great idea!  What I ended up doing is setting the document margin to 250 then positioning the first <div> absolutely in the area cleared by the margin, then I set the other <div> to width: 100% and since it calculated the 100% based only on the area inside the document margin it still fills the entire area.

Hmm, that was a little unclear but in any event, it works, thanks everyone!

---


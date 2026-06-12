---
title: "W3C standard HTML question"
date: 2009-01-29
forum: Programming Talk
---

### Post by samjh on 2009-01-29
In older versions of HTML, one could change the colour and other attributes of a piece of text by using <font>.

But since v4, <font> is deprecated.  I'm aware that you can use in-line style attributes to define font styles for a heading or paragraph (ie. <p style="font-family:times;color:red">blah blah</p>), but how do you - for example - change the colour of a part of text WITHIN a paragraph or heading?  I've tried using the style tag by itself, but it doesn't work.

What I'm looking for is HTML v4 standards compliant version of:
<p>This is a string with extra <font color="red">coloured text</font>!</p>

---

### Post by Magnes on 2009-01-29
> **samjh said:**
> <p style="font-family:times;color=red">

color:red not color=red

> but how do you - for example - change the colour of a part of text WITHIN a paragraph or heading?  I've tried using the style tag by itself, but it doesn't work.

Read about <span> tag. :)

---

### Post by samjh on 2009-01-29
> **Magnes said:**
> color:red not color=redOops, fixed! :KS
> **Magnes said:**
> Read about <span> tag. :)Magnificent, my dear sir! :D

EDIT:

The SOLVED tool doesn't seem to work.  Meh. :(

---

### Post by ufis on 2009-01-29
> **Magnes said:**
> Read about <span> tag. :)

[s]Or the <div> tag. Saves you 2 bytes in page size and 1/8th of a second in typing :)[/s]
Edit: this is wrong, see reply below for explanation.

If you have a couple of places on the page where you need to do that it would be better to declare a css style:
[php]<style type="text/css">
.redtext { color:red }
</style>[/php]
and then giving your divs (or spans or anything else) a class
[php]<p>This is normal text. <span class="redtext">This is red text.</span> This is normal text.</p>
<p class="redtext">This whole paragraph will be red.</p>[/php]
This is a better way than doing multiple inline styles.

---

### Post by Colonel Kilkenny on 2009-01-29
> **ufis said:**
> Or the <div> tag. Saves you 2 bytes in page size and 1/8th of a second in typing :)

If you have a couple of places on the page where you need to do that it would be better to declare a css style:
[php]<style type="text/css">
.redtext { color:red }
</style>[/php]
and then giving your divs (or spans or anything else) a class
[php]<p>This is normal text. <div class="redtext">This is red text.</div> This is normal text.</p>
<p class="redtext">This whole paragraph will be red.</p>[/php]
This is a better way than doing multiple inline styles.

P element cannot contain block-level elements so <div> inside <p> is invalid (X)HTML. So span is the way to go (or abbr, etc.).

---

### Post by ufis on 2009-01-29
> **Colonel Kilkenny said:**
> P element cannot contain block-level elements so <div> inside <p> is invalid (X)HTML. So span is the way to go (or abbr, etc.).
True :)

My bad.

My original post corrected to avoid giving people wrong information.

---


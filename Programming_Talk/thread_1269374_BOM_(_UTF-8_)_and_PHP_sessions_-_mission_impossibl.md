---
title: "BOM ( UTF-8 ) and PHP sessions - mission impossible ?"
date: 2009-09-18
forum: Programming Talk
---

### Post by sunchiqua on 2009-09-18
Is there a way to start a PHP session and use other header elements, if the file is encoded in UTF-8 ( with BOM ) ? 

I know it's a known bug ( issue ), but .. could it really be impossible to avoid header errors ( "headers already sent" ) ?
PHP treats these 3 bytes as content and I can't seem to find a way to fix it ..

---

### Post by dgoosens on 2009-09-18
remove the BOM...
that'll do the trick

---

### Post by sunchiqua on 2009-09-18
> **dgoosens said:**
> remove the BOM...
that'll do the trick

That's not what I was asking for. I know that using UTF-8 without BOM will fix it, but as far as I know, removing it would result in another problem, related to my clients software or whatsoever.

---

### Post by dgoosens on 2009-09-18
in that case it will be impossible to send anything to the header.

The BOM really is useless in UTF-8 unicode...
and I have never, ever encountered trouble with any program by removing the BOM.

---

### Post by dgoosens on 2009-09-18
Here is some more info about that:
[http://en.wikipedia.org/wiki/Byte-order_mark](http://en.wikipedia.org/wiki/Byte-order_mark)
> 
While UTF-8 does not have byte order issues, a BOM encoded in UTF-8 may nonetheless be encountered. A UTF-8 BOM is explicitly allowed by the Unicode standard[1], but is not recommended[2], as it only identifies a file as UTF-8 and does not state anything about byte order.


---

### Post by sunchiqua on 2009-09-18
> **dgoosens said:**
> Here is some more info about that:
[http://en.wikipedia.org/wiki/Byte-order_mark](http://en.wikipedia.org/wiki/Byte-order_mark)

Thank you! Let's mark it [COLOR=RoyalBlue]SOLVED[/COLOR] as in [COLOR=Gray]can't be solved[/COLOR].

---


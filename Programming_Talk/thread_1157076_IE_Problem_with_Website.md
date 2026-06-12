---
title: "IE Problem with Website"
date: 2009-05-12
forum: Programming Talk
---

### Post by Black Mage on 2009-05-12
I have completed a website that I've been working on and was doing browser testing when I realized that things do not align correctly in IE.

The site is [http://www.scribeshare.net](http://www.scribeshare.net) and it works perfectly fine in Safari, Opera and Firefox, but in Internet Explorer the maintconent is below the side bar. I am trying to play around with the CSS but am having no success. So far I've come up with

<style type="text/css"> 
/* place css fixes for all versions of IE in this conditional comment */
.thrColElsHdr #sidebar1, .thrColElsHdr #sidebar2 { padding-top: 30px; }
.thrColElsHdr #mainContent { zoom: 1; padding-top: 2px; }
/* the above proprietary zoom property gives IE the hasLayout it needs to avoid several bugs */
</style>
<![endif]-->

Does anyone have any suggestions that might work?

Anything would be greatly appreciated.

---

### Post by Black Mage on 2009-05-12
NVM, just figured it out.

---

### Post by Reiger on 2009-05-12
Let me guess: you added a Doctype and all things were magically fixed? :)

Yeah IE's quirksmode is a PITA, and much of that goes away by including a (strict) XHTML Doctype declaration on top.

---


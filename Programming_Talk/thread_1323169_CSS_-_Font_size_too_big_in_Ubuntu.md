---
title: "CSS - Font size too big in Ubuntu"
date: 2009-11-11
forum: Programming Talk
---

### Post by g3k0 on 2009-11-11
.

---

### Post by Colonel Kilkenny on 2009-11-11
Just a guess but your problem might exist because you don't specify font. Windows has different default fonts than Ubuntu -> Words might become too wide if the font used is different -> Problem. 
So something like font-family: "Times New Roman", serif; might do the trick. But that doesn't solve anything if user doesn't have Times New Roman installed (like out-of-the-box Ubuntu). When Times New Roman isn't available is defaults back to the problematic font.
Aww, web design and lovely quirks <3.

Btw. it looks okay in Opera (in Ubuntu that is) so it seems that Opera is picking up different serif default font than Firefox.

Btw. font-face: might also help you, but it's quite new thing so old browsers are in trouble with that.

---


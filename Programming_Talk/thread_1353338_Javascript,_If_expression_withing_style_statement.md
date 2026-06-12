---
title: "Javascript, If expression withing style statement"
date: 2009-12-12
forum: Programming Talk
---

### Post by niiize on 2009-12-12
Hi. I've seen something looking like a comparison test within style expression. For exaple something like <input type='text' style='visibility:visible?hidden'> It's just in my memory, and can't find any info on it since I don't know what to google..

Thnx in advance.

---

### Post by myrtle1908 on 2009-12-12
[http://en.wikipedia.org/wiki/%3F:](http://en.wikipedia.org/wiki/%3F:)

---

### Post by jtuchscherer on 2009-12-13
This is not a proper style attribute. I don't think that any browser would know what that means.

I just skimmed through the CSS2.1 spec to make sure that it is not in there. You can find the spec here:

[http://www.w3.org/TR/2009/CR-CSS2-20090908/](http://www.w3.org/TR/2009/CR-CSS2-20090908/)

---

### Post by Hellkeepa on 2009-12-13
HELLo!

Not even CSS 3 has this syntax proposed, as evidented here:
[http://www.w3.org/TR/css3-syntax/](http://www.w3.org/TR/css3-syntax/) (scroll down to chapter 11.1)

Just use JS to toggle the state, as you seem to want this to happen on an insitric event. Either that, or use a server-side script. Best if you use both, for everyone.

Happy syncin'!

---


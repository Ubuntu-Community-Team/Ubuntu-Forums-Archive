---
title: "Tabular menu using HTML, CSS and JavaScript"
date: 2016-12-22
forum: Programming Talk
---

### Post by s3a on 2016-12-22
Hello to everyone reading this.

I am reading this ( [http://www.w3schools.com/howto/howto_js_tabs.asp](http://www.w3schools.com/howto/howto_js_tabs.asp) ), and I would like to understand every bit of the syntax presented, and I am stuck on:

<a href="javascript:void(0)"

as well as

overflow: hidden

I understand that the javascript:void(0) part is to obtain the undefined primitive value, so that it can then have that value returned, but I don't understand why linking to the primitive value "undefined" with the anchor tag is necessary and what it does pragmatically. Is it to say that nothing is actually linked to, but rather that a JavaScript file is _intended_ to be used upon clicking, after which the onClick attribute has its effect (of executing the mentioned javascript method)?

Also, why does removing the line overflow: hidden in ul.tab {} make the light gray rectangle become a line / rectangle with smaller height? It seems to just leave the quadridirectional-one-pixel border, but why does it do that? I watched this video ( [https://www.youtube.com/watch?v=1aT81-e3viA](https://www.youtube.com/watch?v=1aT81-e3viA) ), and I felt like I understood what was said, but I'm having trouble applying what I learned in that video to this situation.

Any input would be greatly appreciated!

---

### Post by Dimarchi on 2016-12-23
For *javascript:void(0)*, see [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/void](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/void) and particularly the part about Javascript URIs. As for the *overflow: hidden* CSS stuff, check out [https://css-tricks.com/all-about-floats/](https://css-tricks.com/all-about-floats/) - it is explained under The Great Collapse heading. I suggest doing tabular menus with only CSS (Google either *pure css tabs* or* pure css responsive tabs*). It means increasing the difficulty a bit, but it is worth the effort, in my humble opinion.

---


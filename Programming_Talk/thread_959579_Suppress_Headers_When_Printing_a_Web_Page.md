---
title: "Suppress Headers When Printing a Web Page"
date: 2008-10-26
forum: Programming Talk
---

### Post by ankursethi on 2008-10-26
Whenever I print a webpage from a web browser, it always insists on printing the webpage URL in the header. I've figured out how to disable printing headers in Firefox via about:config. However, I need to create a web page that will eventually be printed by several people using different operating systems and browsers. I don't want the webpage header to be printed out each time someone prints a page, and it's impossible for me to manually configure everyone's computers. Since I might or might not directly interact with these people, I can't really write a HOWTO or documentation.

Is there any way to NOT print headers while printing a web page? Any JavaScript hacks? I'd like it to be cross-browser, but browser-specific hacks are okay, too.

---

### Post by PC-XT on 2008-11-21
HTML wasn't designed for printing. HTML documents can print in all kinds of ways, splitting items between pages and messing it up, and the user has most of the little control that there is. PDF was designed for printing, and is used for Web documents that may be printed.

---


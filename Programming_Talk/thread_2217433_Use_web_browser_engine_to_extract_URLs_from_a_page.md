---
title: "Use web browser engine to extract URLs from a page?"
date: 2014-04-17
forum: Programming Talk
---

### Post by KingNeil on 2014-04-17
In PHP, I've tried using simple_html_dom in order to extract URLs from web pages.

And it works a lot of the time, but not all of the time.

For example, it doesn't work on the website ArsTechnica.com, because it has a different use of HTML URLs.

So... one thing I do know... is that Firefox perfectly gets a list of all links on a page, hence, how you can load up a web page in Firefox, and all the links are clickable.

And so... I was wondering... is it possible to download the open source Firefox browser engine, or Chrome, or whatever... and pass some parameters to it somehow, and this will give me a list of all URLs on the page..??

I can then feed that into PHP by whatever means, whether it's shell_exec() or whatever.

Is this possible? How do I do it?

---

### Post by SeijiSensei on 2014-04-17
I looked at the source for Ars.  All the URLs look perfectly normal to me.  Can you point to an entry in the page source that you cannot parse with your current method?

---

### Post by ofnuts on 2014-04-18
Possible solutions:
- Find a browser add-on (Firefox has a "copylinks" add-on somewhere).
- Write the add-on yourself
- Write a ["bookmarklet"](http://en.wikipedia.org/wiki/Bookmarklet)

---


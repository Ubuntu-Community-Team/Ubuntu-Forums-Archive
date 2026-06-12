---
title: "PHP code / regular expression to extract Google Search results"
date: 2007-10-07
forum: Programming Talk
---

### Post by DivineOmega on 2007-10-07
Given any google search URL (e.g. [http://www.google.co.uk/search?hl=en&q=test&btnG=Google+Search&meta=](http://www.google.co.uk/search?hl=en&q=test&btnG=Google+Search&meta=)) I want to be able to read the source and extract from it using a regular expression all the URLs of the results.

Does anyone know of a regular expressions to do this (given the source code of the returned page), that will work in PHP?

I've tried many example regular expressions for extracting URLs but they all result in rubbish output or are not accepted by the PHP reg. exp. syntax.

---

### Post by DivineOmega on 2007-10-08
After working more on regular expressions I worked out the following PHP regular expression that can extract URLs from HTML source code. Note that the result is surrounded by double-quotes, so you have to remove those if you so wish.

'%"(?:https?|ftp://).+?"%'

---


---
title: "Detecting URL Redirects"
date: 2011-08-23
forum: Programming Talk
---

### Post by pcman312 on 2011-08-23
I'm looking for a way to detect if a given URL redirects to a different webpage.

Example:
[http://bit.ly/2V6CFi](http://bit.ly/2V6CFi)  -> [http://www.google.com](http://www.google.com)

This is not exclusive to bit.ly or any other url shortening service.

The problem that I face is that I don't want to actually download the webpage because it's possible that the url could redirect to a place that would download a virus onto my computer. Is there a way that I can retrieve just the header information and then determine that the fully resolved URL is different from the original one without downloading any content of the page and without downloading any potential virus/spyware/malware/etc.?

I'm not stuck with any particular language, though I'd prefer perl if possible.

---

### Post by Habitual on 2011-08-23
[http://userscripts.org/scripts/review/40582](http://userscripts.org/scripts/review/40582)

but it's not perl.

---


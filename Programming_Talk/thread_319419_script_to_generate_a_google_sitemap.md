---
title: "script to generate a google sitemap"
date: 2006-12-15
forum: Programming Talk
---

### Post by huggy77 on 2006-12-15
i was wondering if anyone had a script to generate a google sitemap...

basically need to create a file that takes every html or htm file of a specific directory and put it in a xml file like:

```
	
<url>
		<loc>http://www.aerialphotosofnj.com/custom-ground.html</loc>
		<priority>0.5</priority>
		<lastmod>2006-11-23</lastmod>		
</url>

```

does anyone have something like this - what would be the best way to tackle this?  I might fool around in java to build one but i wanted to see if anyone had something written or an easy way to do this before i kill a weekend...

the priority and lastmod attributes can be static...

thanks

---

### Post by huggy77 on 2006-12-15
looks like google already wrote one:

[https://www.google.com/webmasters/tools/docs/en/sitemap-generator.html](https://www.google.com/webmasters/tools/docs/en/sitemap-generator.html)

FANTASTICO...

---


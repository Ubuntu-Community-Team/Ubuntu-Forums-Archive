---
title: "Posting code in blogspot?"
date: 2009-07-26
forum: Programming Talk
---

### Post by MeLight on 2009-07-26
Not sure if this is the right place to post this, but I'm pretty sure that chances of finding someone who had the same issue here are much higher than anywhere else :D

I have a programming blog on blogspot.com and it's major pain in the *** to format the code I post every time (and indentation won't always work!), and after all that it doesn't look that good either. I've posted this on google's blogspot group, but no answer there.

Please advise

---

### Post by noerrorsfound on 2009-07-28
The **pre** tag will retain whitespace.
```
<pre></pre>
```

---

### Post by cdiem on 2009-07-28
I think you can use some javascript library - i.e. highlight.js ( [http://softwaremaniacs.org/soft/highlight/en/](http://softwaremaniacs.org/soft/highlight/en/) ) or google-code-prettify ( [http://code.google.com/p/google-code-prettify/](http://code.google.com/p/google-code-prettify/) ) or something similar ( [http://lifehacker.biz/articles/web-developers-package-code-beautifier-and-formatter/](http://lifehacker.biz/articles/web-developers-package-code-beautifier-and-formatter/) ). 

Here is a description for blogger.com, using a css/javascript combination:
( [http://heisencoder.net/2009/01/adding-syntax-highlighting-to-blogger.html](http://heisencoder.net/2009/01/adding-syntax-highlighting-to-blogger.html) )

And another description, also for blogger.com, using java2html:
( [http://flexdevtips.blogspot.com/2009/05/blogger-source-code-syntax-highlighting.html](http://flexdevtips.blogspot.com/2009/05/blogger-source-code-syntax-highlighting.html) )

And another one, using google-code-pretiffy:
( [http://lukabloga.blogspot.com/2008/10/to-test-new-highlighting.html](http://lukabloga.blogspot.com/2008/10/to-test-new-highlighting.html) )
Just my 2 cents.

---


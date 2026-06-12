---
title: "HTML question"
date: 2007-03-16
forum: Programming Talk
---

### Post by thomasaaron on 2007-03-16
I'm using NVU to create a website.

The splash page will have an animated gif that runs through several frames of the animation for a period of about 10 seconds.

I would then like for the page to automatically forward the viewer to another page, which will be strictly HTML and contain links, buttons etc...

I know how to make and incorporate the animated gif into the html. No problem.
I just don't know how to make the page automatically forward to antother page after 10 seconds.

Any html programmers out there that can help me?

Best,
Tom

---

### Post by peeps21086 on 2007-03-16
Put this in you splash page (I believe in head).
```

<meta http-equiv="REFRESH" content="10;url=http://www.the-domain-you-want-to-redirect-to.com"> 

```
You can change the 10 to however many seconds you want.

---

### Post by Mirrorball on 2007-03-16
Please read this before making a splash page: they are bad!
[http://www.simian.ca/index/101-article-action/id.311/title.just-say-no-to-splash-pages](http://www.simian.ca/index/101-article-action/id.311/title.just-say-no-to-splash-pages)
[http://www.seomoz.org/blog/how-to-convince-a-client-they-dont-need-a-splash-page](http://www.seomoz.org/blog/how-to-convince-a-client-they-dont-need-a-splash-page)

---

### Post by thomasaaron on 2007-03-16
Thank you both.
Best,
Tom

---


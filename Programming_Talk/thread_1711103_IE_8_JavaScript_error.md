---
title: "IE 8 JavaScript error"
date: 2011-03-20
forum: Programming Talk
---

### Post by gypsumwolf on 2011-03-20
I did not see a web development area to post questions so I put it here.

In IE 8 I get an error that says "Object doesn't support this property or method" it says the error is in line 319. Here is what is in line 319:

```
a.parentNode.addClassName("menu_open");
```

I am trying to use a JavaScript drop down menu on my site.

---

### Post by cgroza on 2011-03-20
More code if you want people to figure it out.

---

### Post by gypsumwolf on 2011-03-20
Got the sample code from a website, here is the code contained in the js file which IE complained about.

ps. it works just fine in Opera and Firefox.

EDIT> Figured out error, was the div tag in the html file.

---

### Post by gypsumwolf on 2011-03-20
It does not work in IE 9 either.

---

### Post by gypsumwolf on 2011-03-20
Solved. It was the div tag, IE didnt like where i put it in the HTML file.

---


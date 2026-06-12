---
title: "problem with favicon"
date: 2009-05-24
forum: Programming Talk
---

### Post by hockey97 on 2009-05-24
HI, I need some help. I am working on  [www.fydreams.com](www.fydreams.com)

the problem is that the favicon is not showing up properly.

take a look. you can't see properly. I use gimp.

I resized the image to 16x16. 

it was like 407px to 104px something like that originally.

it shows up properly in gimp. I mean I can see the logo nice. Yet when you look at the site it shows the favicon with static colors no logo showing.

why is this?

---

### Post by bgs100 on 2009-05-24
I looked at the page source, and I believe the favicon has to be of type .ico, not .png

---

### Post by Dill on 2009-05-24
Yes. Instead of

```
<link rel="icon" type="image/png" href="favicon.png">
```

You should change the extension to *.ico* and change the HTML to


```
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon" />

```

Cheers,
Dill

---

### Post by hockey97 on 2009-05-24
yep, tried those. I tried the .ico format. 

I get the same results.

it shows a box with random blotches of color dots.

it dosen't show the logo.

---

### Post by Dill on 2009-05-24
Try clearing your browser's cache -- *Ctrl + Shift + Del* or go to *Tools -> Clear Private Data*. 

When I visit your site, I see what I think might be your favicon; at least, it looks very much like the main image of your site.

If you're still having trouble after clearing your cache, I'll try to think of something else...

Cheers,
Dill

---

### Post by hockey97 on 2009-05-24
Dill thanks that worked. 

I can now see the logo.

---


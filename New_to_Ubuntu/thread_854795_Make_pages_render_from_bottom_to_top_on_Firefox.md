---
title: "Make pages render from bottom to top on Firefox"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Linux_Man on 2008-07-09
I was wondering if there was a way to make pages load from the bottom of the page to the top of the page in Firefox 3. I looked around on Google and looked for any preferences that might be of use in about:config but couldn't find any that worked. So is there an easy way to make pages load from the bottom first and then the top?

---

### Post by tjwoosta on 2008-07-09
just curious 

why do you want pages to render from bottom to top?

---

### Post by Linux_Man on 2008-07-09
Mostly for forums where I want to check if there has been a new post in my thread and I am impatient so rather then loading all the content above, it loads it below first. And just to see if it is possible :guitar:

---

### Post by decoherence on 2008-07-09
interesting question. well, the html itself is a single file that is downloaded in a serial fashion,  so I don't see how you'd do it there. As far as images are concerned, you could theoretically set up a proxy that loads images and other large files in reverse order. even then, how well things work will depend on the page and the browser.

one thing i find slows down a lot of forums is waiting for ad servers. putting a line like this in /etc/resolv.conf speeds things up (and may deprive places of ad revenue)

```
ads.doubleclick.net 127.0.0.1
```

substitute ads.doubleclick.net with whatever ad server is holding you up.

---

### Post by rainwalker on 2008-07-09
On a lot of forums you can set threads to display the newest posts first

---

### Post by Linux_Man on 2008-07-09
Hmmm... Well I guess there is no easy way to make pages render backwards in Firefox. I just didn't know if there was some about:config setting that could make it render that way.

---

### Post by nowshining on 2008-07-10
it's strange tho - some sites render images backwards tho. :D

---

### Post by decoherence on 2008-07-10
it depends on when the image appears in the source code. As I understand it, images are generally downloaded (or at least requested) in the order they the appear in the source code, but that doesn't mean they have to appear at the top of the rendered page. Thus, bottom elements can show up first if the page designer wants.

---


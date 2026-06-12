---
title: "Display differences between Win IE and Linux Firefox"
date: 2006-09-08
forum: Programming Talk
---

### Post by Coomkeen on 2006-09-08
Hi All,

Before getting into Linux and Ubuntu I made a couple of web sites.
Now seeing them using Firefox in Ubuntu the page formatting is wrong.
I used CSS a lot and expected that as CSS is fairly new, that different browsers would conform to a new standard, rather than the old my-browser-is-better-than-your's scene.

I haven't checked what they look like using Firefox in Windows.

Anyone know what to look out for when using CSS?
Are there obvious areas that are open to browsers individual interpretation?
When will we get a standard that **is** a standard?

I don't _think_ it is my HTML coding that is 'over-ruling' the CSS.

---

### Post by maubp on 2006-09-08
I suggest you check your code with this,

[http://validator.w3.org/](http://validator.w3.org/)

If your page is hideously broken, then FireFox/Mozilla will render it in "Quirks" mode which does the best it can - but does not fully follow the standards.

---

### Post by Coomkeen on 2006-09-08
That's cut me down to size:( 
29 errors!

What a usefull site.
Back to the drawing board!

Many thanks.

---

### Post by jacksaff on 2006-09-09
IE's support for css is truly awful. Don't expect your pages to render properly no matter how good your html/css is. Of course you can write your page to look good in IE, but then you'll have to give up a lot of css goodness and help perpetuate the crappy situation you find yourself in now.
The most compliant css browser at the moment is Opera 9 - Konqueror does a pretty good job too. My pages look identical in those two. Firefox still has one or two quirks with vertical spacing but nothing I've done breaks in any annoying way. IE just makes me cry.

---

### Post by kostkon on 2006-09-09
Hi Coomkeen,

it is a fact that there are some CSS quirks in IE but you can use the ```
<!--[if IE 6]><![endif]-->
``` conditional comments to serve different CSS rules to IE when needed. Google about the IE CSS bugs and then just conditionally fix them for IE.

Good luck.

---


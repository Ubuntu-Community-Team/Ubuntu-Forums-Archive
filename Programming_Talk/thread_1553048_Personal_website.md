---
title: "Personal website"
date: 2010-08-14
forum: Programming Talk
---

### Post by carlosgs91 on 2010-08-14
.

---

### Post by Bachstelze on 2010-08-14
If it requires Javascript to work, it's an instant F for me.

---

### Post by Hellkeepa on 2010-08-14
HELLo!

[http://validator.w3.org/check?uri=http%3A%2F%2Fcgsbay.com%2F&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fcgsbay.com%2F&charset=%28detect+automatically%29&doctype=Inline&group=0)
[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fcgsbay.com%2F&profile=css21&usermedium=all&warning=1&lang=en](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fcgsbay.com%2F&profile=css21&usermedium=all&warning=1&lang=en)

If you're looking to get hired by someone, you really should read up on graceful degrading, the specs, and the WAI guidelines.

Happy codin'!

---

### Post by worseisworser on 2010-08-14
Nice, but the pointer should turn into a hand when it hovers over "clickable" link like stuff. IIRC this can be done via the `cursor' CSS property.

Depending on JavaScript without a fall-back is perfectly fine IMHO. Most users do not disable it, and those who do know what they are doing and can enable it again if they want to. Make sure you have a NOSCRIPT element around, though.

---

### Post by carlosgs91 on 2010-08-14
.

---

### Post by Nick_Jinn on 2010-08-14
What do you charge for small personal projects?

---

### Post by Hellkeepa on 2010-08-14
HELLo!

**First off, using JavaScript is not the same as requiring JavaScript:**
The former lets you use the site normally, except for a few things that are *only* available in JS, even if your browser isn't JS-capable. The latter breaks the site, even though it should have been perfectly usable in pure HTML (plus, possibly, server-side code).

Kinda like designing a 3D TV, that doesn't give you a 2D image even, without you using the glasses.


**Secondly, the validation errors:**
They tell you that you're not using HTML, and as such it could not be parsed or validated. It may be something that looks like HTML, and possibly be displayed by a browser, but that's just guessing. The only reason the site works, is because the browsers have been programmed to be as lenient as possible, trying their hardest to guess at what you really mean with the tag soup.
All bets are off, in other words, and the site will most likely not be rendered the same in two different browsers. Nor without errors in some/most.

If you'd read the HTML & CSS specification, you'd know this.
Flaunting your ignorance, especially since you're portraying yourself as a professional, is *not* something I look upon as a positive.

Start by adding the correct doctype to your site, and work from there.


**Thirdly, why some browsers renders incorrectly/not as you want, despite the site validating:**
All browsers have bugs in their implementations of the standards, some more than others. Have some parts of the standards that are not implemented yet, again; Some more than others. Also, some parts of the standards are up to interpretation, or optional how to solve, and as such will be different in the different browsers.
That's when semantic programming and graceful degradation comes into the picture, and this requires knowledge about both the standards and the weaknesses of the different browsers. The point is that the site should be perfectly usable, even in Lynx.
That way you're not excluding any users, for completely unnecessary reasons.


**Fourthly, converting DIVs to anchors:**
This is something you should almost never do, or in the case of menus; Never. What you should do, is use CSS to change the anchors from inline elements to block elements.
That way the menu will still work, even if the browser does not support either JS or CSS. In other words, it degrades gracefully.


**Fiftly, why people disable JS:**
There are many reasons for this, security being the biggest of them. As for not being able to get to sensitive data via JS, I do strongly recommend you to read up about XSS (Cross-Site Scripting) and similar techniques!


**Final words:**
Now, you might find me very strict on the points I've listed, but that is only because you've portrayed yourself as a professional; The list is automatically raised pretty high then.
Had you been just a hobby enthusiast, I would have understood most of your reasoning, but I would still have implored you to raise your knowledge level considerably. Not only for your own sake, but also for those who visit the pages you create.

You wouldn't have hired a carpenter, that didn't know the difference between a 2-by-4 and a 4-by-4, or when to use the different dimensions, would you?

This is my personal and professional opinion, as a web developer.

Happy syncin'!

---


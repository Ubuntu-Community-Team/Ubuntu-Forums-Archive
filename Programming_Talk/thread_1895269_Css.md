---
title: "Css"
date: 2011-12-14
forum: Programming Talk
---

### Post by CoffeeRain on 2011-12-14
Is there a way to have a css sheet without linking to it from every page? I was thinking sort of like index.html or default.php.

---

### Post by bluexrider on 2011-12-14
> **CoffeeRain said:**
> Is there a way to have a css sheet without linking to it from every page? I was thinking sort of like index.html or default.php.


**CSS Reference**



[http://www.w3schools.com/cssref/default.asp](http://www.w3schools.com/cssref/default.asp)

this may help

---

### Post by CoreyB. on 2011-12-14
I don't believe so, you either have to link to an external file, write it all in a <style> tag, or use the style attribute within the body of the html for the different elements you want to style.

---

### Post by epicoder on 2011-12-14
Please don't use W3Schools a reference. [W3Fools](http://w3fools.com) has a good explanation of why you shouldn't.

To answer the OP, no, I don't think there is a css equivalent to index.htm. The closest you could get is to use url rewriting and an argument based php file to echo a standard header and then the proper body content.

---

### Post by CoffeeRain on 2011-12-14
Thanks!

---

### Post by bluexrider on 2011-12-14
> **sh228 said:**
> Please don't use W3Schools a reference. [W3Fools]("http://w3fools.com") has a good explanation of why you shouldn't.

To answer the OP, no, I don't think there is a css equivalent to index.htm. The closest you could get is to use url rewriting and an argument based php file to echo a standard header and then the proper body content.
thanks for the info. I sometimes grab examples from them because its quick.

---


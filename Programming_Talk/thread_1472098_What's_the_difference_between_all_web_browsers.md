---
title: "What's the difference between all web browsers?"
date: 2010-05-04
forum: Programming Talk
---

### Post by hockey97 on 2010-05-04
Hi, I been building a website. I notice that every element since I use px and absolute position on everything. I notice the elements moves  between the different web browsers. Mainly Firefox and google chrome all look ok. Just when I test it with IE (internet explorer 7 and 8) that the elements move randomly all over the place.

Why is this? how can I fix this. I thought maybe the pixel 0 or ceneter or starting reference are differnt which would offset the css pixel measurements.

I looked around and was told to do a fluid design. I gave it a try a couple of times but still the elements move and some would even overlap each other.

If it's true that different web browsers may have a different reference point or center point or 0 point then the other then would anyone know how much they are offset?

---

### Post by nvteighen on 2010-05-04
> **hockey97 said:**
> Hi, I been building a website. I notice that every element since I use px and absolute position on everything. I notice the elements moves  between the different web browsers. Mainly Firefox and google chrome all look ok. Just when I test it with IE (internet explorer 7 and 8) that the elements move randomly all over the place.

Why is this? how can I fix this. I thought maybe the pixel 0 or ceneter or starting reference are differnt which would offset the css pixel measurements.

I looked around and was told to do a fluid design. I gave it a try a couple of times but still the elements move and some would even overlap each other.

If it's true that different web browsers may have a different reference point or center point or 0 point then the other then would anyone know how much they are offset?

The issue is because IE is still not totally complying to the standards (well, actually Firefox also has some quirks still...). The reasons are various and start from the IE vs. Netscape wars, where both browsers were trying to force web developers to use proprietary extensions and non-standard code so they could, eventually, gain more market share. WHat happened next is that while IE continued its existence, Netscape was totally revamped as Mozilla and then, Mozilla Firefox, with totally fresh new code. IE on the other hand "had" to offer backwards compatibility (Microsoft's big beast, btw... if they scrapped that idea like Apple did, Windows would be a very much nicer platform) and still has to because some people seem to expect IE7 or IE8 to support the designs they used in IE6 (or maybe IE5??).

In particular, the most important difference of IE with respect to the others is the definition of what the CSS margin and border propierties are supposed to be. There's a hell of confusion there that, to simplify, makes them both the "same" in IE (where in the rest isn't... see the standard: [http://www.w3.org/TR/CSS21/box.html#box-dimensions](http://www.w3.org/TR/CSS21/box.html#box-dimensions)) and therefore, the space that each element takes is different than in the rest of browsers. So, relative positions become different too and you know the rest.

---

### Post by Compyx on 2010-05-04
You have encountered the nemesis of all web designers: Internet Explorer. IE is known for its poor implementation of web-standards and its crappy Javascript engine.

If you want your website to display correctly in IE as well as standards-compliant browsers such as Firefox, Safari, Opera and Chrome, you will have to use a very limited subset of CSS and DOM or use a lot of IE-specific hacks.

Google is your friend here, just google for things like 'IE hacks' and 'IE fixes' to get a lot of information

Don't count on Microsoft to fix things, they won't: I managed to crash a Windows 2003 server with a few lines of javascript exploiting a bug in IE 8 that has been around since IE 6.

---

### Post by trent.josephsen on 2010-05-04
Based on your description of the problem, it sounds like you are running into the box model bug from IE6 and earlier, which hangs around in later versions but only when the browser drops into quirks mode.  The browser uses quirks mode to render HTML that doesn't adhere to any HTML standard.

To avoid putting IE 7+ in quirks mode, precede your HTML with a valid DOCTYPE and use the W3C validator at [http://validator.w3.org/](http://validator.w3.org/) to make sure you are writing valid HTML by whatever DOCTYPE you choose.  IIRC, IE 7 fixed the box model bug and IE 8 is one of the most strictly-compliant browsers out there when not using quirks.

---

### Post by wmcbrine on 2010-05-04
Something deeper to consider here... HTML was never designed or intended to do pixel-perfect layout control, and it's not very good at it. All that stuff was shoehorned in at a later date. But this is not a design flaw. Personally, I use larger fonts (and in particular, larger *minimum* font sizes) than the default on all my browsers. Good layouts handle that just fine. Bad layouts break.

---

### Post by hellblazer on 2010-05-05
I've found that setting the padding and margins for the body, paragraph and div tags to 0px helps a lot as IE and FF have different default values if you don't specify.

The best place to check for cross browser stuff is [http://www.quirksmode.org/](http://www.quirksmode.org/)

---

### Post by Tony Flury on 2010-05-05
> **hockey97 said:**
> Hi, I been building a website. I notice that every element since I use px and absolute position on everything. I notice the elements moves  between the different web browsers. Mainly Firefox and google chrome all look ok. Just when I test it with IE (internet explorer 7 and 8) that the elements move randomly all over the place.

Why is this? how can I fix this. I thought maybe the pixel 0 or ceneter or starting reference are differnt which would offset the css pixel measurements.

I looked around and was told to do a fluid design. I gave it a try a couple of times but still the elements move and some would even overlap each other.

If it's true that different web browsers may have a different reference point or center point or 0 point then the other then would anyone know how much they are offset?

Unless you can guarantee that everyone looking at your website will use exactly the right window size, font sizes etc - then using absolute positioning everywhere is a bad idea in my honest opinion. If I am browsing a site which forces my browser to a particular size, or which can only be read properly with particular settings, i click the home button and make a mental note never to go there again.

The only time that absolute positioning might work is if you are placing graphic elements along the top and left hand borders of your windows - any other time use relative.

---


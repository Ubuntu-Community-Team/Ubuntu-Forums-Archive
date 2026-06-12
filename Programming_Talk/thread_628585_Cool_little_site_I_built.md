---
title: "Cool little site I built"
date: 2007-12-01
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-01
This is for a friend's business. Designed and built it myself, he insisted on only showing the link titles on hover. Still, I like it. The space theme represents, in his words, the "universal" nature of the shop:

[http://www.natural-mystics.com/redesign](http://www.natural-mystics.com/redesign)

---

### Post by Kadrus on 2007-12-01
It's pretty nice...Nice Design..Good Job :):D

---

### Post by smartbei on 2007-12-01
Very nice non-traditional layout. Some things I noticed:
[list]
[*]Meta tags should be closed with a /> like everything else (to validate as xhtml).
[*]Nice use of jQuery! I have been wanting to make use of that library myself but haven't had the chance yet.
[/list]

Good job!

---

### Post by Vadi on 2007-12-01
The contact page's aligning is a bit off!

I really like how the text updates :)

---

### Post by ThinkBuntu on 2007-12-01
> **smartbei said:**
> Very nice non-traditional layout. Some things I noticed:
[list]
[*]Meta tags should be closed with a /> like everything else (to validate as xhtml).
[*]Nice use of jQuery! I have been wanting to make use of that library myself but haven't had the chance yet.
[/list]

Good job!
Thanks for noticing that, I fixed it now.

This is the first client site I've used jQuery on; just dipping my toes in right now. It really revolutionizes the way you write JS and DOM, and the entry bar is quite low.

---

### Post by LaRoza on 2007-12-01
* It does not degrade gracefully, the links (all of them) should also be <a> elements (even if they are disabled with javascript). If script is disabled (or not functional) the site is nonfunctional.

The ways to solve this are:

* rewrite the xhtml and put the links in, but hide them, or disable them with ECMAScript, so if ECMAScript fails, the links will be enabled.

* Make an alternate version, that is the default, but does an automatic redirection (with ECMAScript), so if the script fails, they never go to that one.

---

### Post by ThinkBuntu on 2007-12-01
> **LaRoza said:**
> * It does not degrade gracefully, the links (all of them) should also be <a> elements (even if they are disabled with javascript). If script is disabled (or not functional) the site is nonfunctional.

The ways to solve this are:

* rewrite the xhtml and put the links in, but hide them, or disable them with ECMAScript, so if ECMAScript fails, the links will be enabled.

* Make an alternate version, that is the default, but does an automatic redirection (with ECMAScript), so if the script fails, they never go to that one.
The only problem you're seeing is due to the links having no text (the images themselves are background images, so they have no alt text). I'll have to fix this, and also make the content display: block by default, with jQuery hiding it on page load. Thanks for the testing!

**Update:** Bugs reported by LaRoza are now fixed. Link text is invisible if CSS is supported, but page degrades gracefully otherwise. Still could be a problem if background images don't load...site is also fully functional even with NoScript active.

---

### Post by LaRoza on 2007-12-01
> **ThinkBuntu said:**
> The only problem you're seeing is due to the links having no text (the images themselves are background images, so they have no alt text). I'll have to fix this, and also make the content display: block by default, with jQuery hiding it on page load. Thanks for the testing!

**Update:** Bugs reported by LaRoza are now fixed. Link text is invisible if CSS is supported, but page degrades gracefully otherwise. Still could be a problem if background images don't load...site is also fully functional even with NoScript active.

The links should be made invisible by ECMAScript, not by CSS. They are visible on my browser, Opera 9.24.

---

### Post by ev5unleash1 on 2007-12-01
The site looks perfect on my Browser, FireFox 2.0.0.11. If it looks good on the highly rated browser in the US, Why change it?

---

### Post by LaRoza on 2007-12-01
> **ev5unleash1 said:**
> The site looks perfect on my Browser, FireFox 2.0.0.11. If it looks good on the highly rated browser in the US, Why change it?

I am a web designer myself, and am not nitpicking another's work.

I spend a lot of time testing my sites in IE6-7, FF2, Opera 9, Safari 3, Lynx and others. I test them in in every popular resolution, with 800x600 as the lowest. If the site doesn't degrade gracefully in the above browsers and resolutions, I change it.

The fix I suggested, makes certain that the links are only visible if the script fails. The inclusion of links is not only a good practice, it is a legal requirement in some countries. Also, spiders and bots use links for indexing. Google wouldn't be able to see the rest of the site without links.

---

### Post by ThinkBuntu on 2007-12-01
> **LaRoza said:**
> I am a web designer myself, and am not nitpicking another's work.
Hey all, let's not act like this could be personal! I'm a professional and I'm seriously appreciative to get free testing of my site, especially from such a knowledgeable developer! I usually trust Opera to work fine with my sites, and I only tested the layout earlier in Opera.

Edit: I can't see the link names in my version of Opera, but I'm upgrading to 9.24 right now.

---

### Post by ev5unleash1 on 2007-12-01
Well, Firefox is the most devloped and most used my people. But it's good to test them in all browsers, I do that with my site because my school sadly uses IE 6 :( and some of my friends that don't really care about anything other then going on websites like myspace use IE.

---

### Post by ThinkBuntu on 2007-12-01
> **ev5unleash1 said:**
> Well, Firefox is the most devloped and most used my people. But it's good to test them in all browsers, I do that with my site because my school sadly uses IE 6 :( and some of my friends that don't really care about anything other then going on websites like myspace use IE.
I develop in Firefox (good mix of common display bugs and standards compliance), then fix in IE6 and IE7. That usually covers my bases, but I briefly will test in Safari and Opera to be sure. An important thing to do also is to check with fonts both anti-aliased and not. Many designers do their design all on a Mac and certain fonts render terribly on a Windows box.

---

### Post by CptPicard on 2007-12-01
Make your friend read this:

[http://www.webpagesthatsuck.com/mysterymeatnavigation.html](http://www.webpagesthatsuck.com/mysterymeatnavigation.html)

---

### Post by Toadmund on 2007-12-01
CptPicard, that site looks like it tricks you to click Google ads.

On another note, some things do, like images, show up askew in IE, compared to rendering in Firefox.

It sucks when you show your website to IE users and you have to go back and fart with the positions, so it looks 'good enough' in both browsers.

Nice website design though!

---

### Post by ThinkBuntu on 2007-12-01
> **CptPicard said:**
> Make your friend read this:

[http://www.webpagesthatsuck.com/mysterymeatnavigation.html](http://www.webpagesthatsuck.com/mysterymeatnavigation.html)
One of my favorites :^)

Happy to see others are reading it.

---

### Post by pmasiar on 2007-12-02
Another ("THE") website about usability is [http://www.useit.com/](http://www.useit.com/) by usability guru [Jakob Nielsen](http://en.wikipedia.org/wiki/Jakob_Nielsen_%28usability_consultant%29)

Site keeps it's late-'90 design as a badge of honor (because it's usability still holds), but the information about  designing and measuring usability of websites  is priceless. I recommend to subscribe to email newsletter.

---

### Post by LaRoza on 2007-12-02
> **pmasiar said:**
> Another ("THE") website about usability is [http://www.useit.com/](http://www.useit.com/) by usability guru [Jakob Nielsen](http://en.wikipedia.org/wiki/Jakob_Nielsen_%28usability_consultant%29)

Site keeps it's late-'90 design, but the information about website usability is priceless. I recommend to subscibe to email newsletter.

+1 That is the best site for web design.

---


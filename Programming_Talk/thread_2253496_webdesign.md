---
title: "webdesign"
date: 2014-11-20
forum: Programming Talk
---

### Post by manthos on 2014-11-20
Hello, i am using linux for few years now besides windows (dual boot) for internet and security. 
Few weeks back i install ubuntu 14.04 and my target is to learn webdesign in my free time.
Witch tools and web programming language i can use to start learning?
thanks in advance

---

### Post by slickymaster on 2014-11-20
*Moved to the ***Programming Talk*** sub-forum*

---

### Post by Lars Noodén on 2014-11-20
To beat around the bush a little first, web design, at the basic level, requires no programming languages, just a familiarity with [HTML 4.01](http://www.w3.org/TR/html401/)/[XHTML 1.0](http://www.w3.org/TR/xhtml1/) and [CSS2](http://www.w3.org/TR/CSS2/) and look a little a head to the upcoming [CSS3](http://www.w3.org/TR/CSS/#css3).  HTML is for structure and CSS is for formatting and layout.  It pays to keep them separate.  HTML 4.01 and XHTML 1.0 are about the same thing, but for the differences that make XML different from SGML.  For CSS, they build on each other.  For background, I'd start with the deprecated [CSS1](http://www.w3.org/TR/CSS1/) just to get the idea of how it works before moving on to CSS2 because its smaller, simpler and easier to grasp.  

You'll need at least the basics in them to make progress with the advanced work with CMSs and such.  In particular if you start to modify, patch, or extend a CMS you'll need to know them.  

Then review accessibility and usability.  These will save you work, increase your audience and future-proof your sites.  

Then my recommendation would be to look at server-side includes.  Both Apache2 and Nginx support them as they are part of the the usual HTTP server functions and can be used to improve the security and maintainability of some kinds of sites.  They will give you standardized headers and footers without the high maintenance and risk of scripts and CMS.

Then, these days almost everyone feels compelled to run a CMS to host their web site.  In many cases, that is overkill, but that's how it is.  Picking a CMS will then make the choice of a language for you.  Often it ends up being the scripting language [PHP](http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/).   WordPress and Drupal, which are nearly everywhere, are in PHP.  Lenya and OpenCMS are in java.  And there is still a number of tools in perl.  

To answer the question about which tools to use, if you are looking at getting to advanced levels, work with an advanced editor like Emacs (especially with HTML or XML mode), vim, Geany, or Kate.  Also, learn to use [tidy](http://tidy.sourceforge.net/) and/or the W3C's [HTML Validator](http://validator.w3.org/).  They are essential and basically spell check your HTML.  Alternately, you could look at Bluefish or Bluegriffon, both of which are good, but more specialized and not without a learning curve.  Once there was Kompozer, which as great for beginners, but it is not maintained any more.  But above all don't get fooled into thinking that WYSIWYG is relevant to the WWW, no matter what your pages will render differently on different types of screens (aspect ratios, resolutions, sizes), devices and even individual installations.  Embrace that flexibility.  

On the server side, the tools to choose are Apache2 or nginx.  Both are easy to set up even with HTTPS.

Just my 2¢

---

### Post by Lars Noodén on 2014-11-20
Just an addendum to the line about the web servers Apache2 and Nginx.  On either or both the three things that are good to know are a) how to set up name-based virtual hosts, b) how to set up HTTPS, and c) server-side includes (SSI).

---

### Post by TheFu on 2014-11-20
Lars is correct.

HTML and CSS are core, but not really programming languages. Perhaps a little javascript - but avoid taking it too far - to the point that the page breaks without it.

If you want to have the complete package, learn 2-6 backend languages - python, ruby, perl, ... javascript and definitely a little SQL - though using an ORM will remove the need to know too much.
There are online training courses for free for web design and for most languages. I like "the hard way" techniques. My local Ruby group teaches an introduction class with both Ruby and Rails for free every other Saturday morning for 3 hrs. It lasts about 8 months, that is about normal to learn a language and web-app-framework. The 2nd - 50th languages and frameworks come much quicker.

Design is hard for most programmers.  Programming seems hard for most designers.  If you can do both, well, there is a huge market, especially if you become active in the F/LOSS communities network and let folks know you will work hard. I see friends in these groups working large projects together all the time. Oh - and I'd personally avoid php.  Php programs are 50% more likely to be hacked.   Check out OWASP.org for things to avoid in the most popular languages. Their top 10 lists are great.

It will take commitment.

---

### Post by Tom_Carr on 2014-11-20
I can not find Bluegriffon in the software installer for kubuntu

---

### Post by Lars Noodén on 2014-11-20
It hasn't been packaged for use in the repository.  They do have a version for 12.04 but not 14.04.

[http://bluegriffon.org/pages/Download](http://bluegriffon.org/pages/Download)

I wouldn't expect it to work on 14.04 but the source would be here:

[http://sources.disruptive-innovations.com/bluegriffon](http://sources.disruptive-innovations.com/bluegriffon)

Myself, I try to avoid software unless it is in the repository but I figured it should be mentioned for completeness.

---


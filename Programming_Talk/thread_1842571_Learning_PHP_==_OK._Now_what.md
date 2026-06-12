---
title: "Learning PHP == OK. Now what?"
date: 2011-09-11
forum: Programming Talk
---

### Post by medic2000 on 2011-09-11
I have started learning PHP one year ago. I have developed a large project for 5 months with PHP. I think about 10.000 lines code. I know about MVC patterns, frameworks etc. Although there is so much road to walk for mastering it, i think there other things to learn to use in industry. While saying other things i mean other components to build modern websites. 

Maybe: Ajax?, XML?, PHP extensions?, Optimizing SQL database with thousands datas in them?

I know pure PHP is not enough for today's standart. I want to improve much more. What do you suggest?

Note: I also know HTML, CSS. But i hate them :) Because it is not like programming.

---

### Post by myrtle1908 on 2011-09-11
If you are interested in developing modern web applications then JavaScript is a must.  It's a quirky but very flexible language.

---

### Post by llanitedave on 2011-09-12
+1 for JavaScript.  You should do as much of your application's work on the client as possible, and minimize server traffic where you can.

What server operations remain will be mostly file or data services, which also imply sql and AJAX.

And don't forget your html, css, and DOM.  Those aren't going away.

---

### Post by medic2000 on 2011-09-12
I know CSS and HTML but i don't like them. Because for CSS first you have to design your website in programs like Photoshop or Gimp. And CSS is a design thing too.

---

### Post by myrtle1908 on 2011-09-12
> **medic2000 said:**
> Because for CSS first you have to design your website in programs like Photoshop or Gimp. And CSS is a design thing too.

CSS is a "design thing" yes, but it has nothing to do with Photoshop or Gimp.  CSS is nothing more than a bunch of rules for "styling" elements and objects etc.  Unless your site/app will be completely image based (where you may wish to use Photoshop or Gimp) or purely SVG/VML based, then you most definitely need at least some CSS.  Of course you need HTML regardless.

If you wish to program the client-side of the web then you need JavaScript.  Perhaps learn a toolkit eg. Sencha/ExtJS or jQuery.  Server-side development - you have many options ... PHP is but one ... as you already know.  Personally I like JEE on the server.

---

### Post by medic2000 on 2011-09-12
> **myrtle1908 said:**
> CSS is a "design thing" yes, but it has nothing to do with Photoshop or Gimp.  CSS is nothing more than a bunch of rules for "styling" elements and objects etc.  Unless your site/app will be completely image based (where you may wish to use Photoshop or Gimp) or purely SVG/VML based, then you most definitely need at least some CSS.  Of course you need HTML regardless.

If you wish to program the client-side of the web then you need JavaScript.  Perhaps learn a toolkit eg. Sencha/ExtJS or jQuery.  Server-side development - you have many options ... PHP is but one ... as you already know.  Personally I like JEE on the server.

First of all thank for the anwers myrtle. Yes i developed a project from scratch with HTML, CSS and PHP. But the there must a design to begin for rules or tags to use with HTML and CSS. To design apperance of site...well it is more of art thing. You have to buy a desing from someone or some site. And you will convert it to HTMl/CSS. But i think it is much more exhausting than writing code. Creating divs, h1, p etc. Then styling everything. And a lot of coincides glitches with CSS. Some element covering anothers. Write a new rule or hack for it. It is very cumbersome. 

I want them to be written by another one. I want to focus on back-end. So what i am really asking is:

-Which extensions should i learn for developing for effectively?
-What industry demand?
-Google APIs?
-Credit card systems and SSL for E-commerce sites?
-XML based things?
-I don't know really, what is out there to learn to complete intricate projects?

---

### Post by medic2000 on 2011-09-12
> **llanitedave said:**
> +1 for JavaScript.  You should do as much of your application's work on the client as possible, and minimize server traffic where you can.

What server operations remain will be mostly file or data services, which also imply sql and AJAX.

And don't forget your html, css, and DOM.  Those aren't going away.

> **myrtle1908 said:**
> If you are interested in developing modern web applications then JavaScript is a must.  It's a quirky but very flexible language.

Ok for these. I was suffering for not knowing JavaScript. I will learn as much as i can. Especially needed for form validation before server doing it and other stuff as you pointed out.

And currently i am learning it seems like fun stuff! But very weird stuff.

---

### Post by SeijiSensei on 2011-09-12
If you haven't spent much time learning SQL syntax, I'd recommend that as well.  I haven't written a site that doesn't use PHP + PostgreSQL for years.  Teach yourself how to do simple select, update and delete queries for a start, then look into things like table joins and referential integrity.

I prefer PostgreSQL over MySQL for a variety of reasons, but the latter is more common on hosting services.

---

### Post by medic2000 on 2011-09-12
> **SeijiSensei said:**
> If you haven't spent much time learning SQL syntax, I'd recommend that as well.  I haven't written a site that doesn't use PHP + PostgreSQL for years.  Teach yourself how to do simple select, update and delete queries for a start, then look into things like table joins and referential integrity.

I prefer PostgreSQL over MySQL for a variety of reasons, but the latter is more common on hosting services.

Thanks for suggestion SeijiSensei. But my SQL(MySQL to be more precise) is already good. With SQL thing that i didn't do was like they always ask:

"Optimizing tables with a millions of records"

I should look at indexes, optimizing deeply i think. 

Javascript + Sql optimization. After that? :D

---

### Post by Dragonbite on 2011-09-12
[LIST]
[*]SQL (MySQL and/or PostgreSQL) = increased functionality. I haven't done a site that hasn't utilized a database on the back-end.
[*]Javascript for added functionality without having to do full round-trips and to improve the user interface, data validation, etc.
[*]HTML & CSS so it looks good (don't underestimate the power of good user interface). Not to mention if you are working with a designer or client, you need to take their ideas and make it so!
[*]HTML5/CSS3 so to be ahead of the curve (not by much) and take full advantage of the web page
[/LIST]

---

### Post by llanitedave on 2011-09-12
As others have said, you don't need a graphics program to design a web site with css any more than you need one to design it with tables.   But you do need a sense of design itself, and since you mentioned "modern websites", you're talking about web applications with a browser-based GUI.  Any GUI is going to require some attention to design and Human Interface Guidelines.  If you don't feel like you have the talent to put together a visual design, then you might want to team up with a partner who can.

Programming is much more than coding.  It's a creative process for solving problems, and on the web, those problems are unavoidably shared by others.

If you can't make yourself work with css and html, you can forget about the V in MVC.  Stick with the MC, and limit yourself to back-end coding, and let someone else do the creative part.

Somehow, though, that seems to me a bit limiting.

---

### Post by Pynalysis on 2011-10-11
+1 for Sencha/ExtJS

---


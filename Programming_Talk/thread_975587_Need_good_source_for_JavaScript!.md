---
title: "Need good source for JavaScript!"
date: 2008-11-08
forum: Programming Talk
---

### Post by medic2000 on 2008-11-08
Yes i am trying to learn JavaScript(this is my first programming language)
Can you suggest me good sources for js especially simple examples.

---

### Post by LaRoza on 2008-11-08
> **medic2000 said:**
> Yes i am trying to learn JavaScript(this is my first programming language)
Can you suggest me good sources for js especially simple examples.

In what context are you learning it?

My wiki has links for it.

---

### Post by nvteighen on 2008-11-08
There's a problem with Javascript: there is a lot of information in the internet, but a lot is just crap. And also much of the code you find in webpages is really bad too...

---

### Post by medic2000 on 2008-11-08
Well i have studied HTML and CSS. Now i am planning to learn JavaScript. I need good examples and their explanations cause i want to learn the logic behind it as i said it is my first programming language.

And no i dont want w3schools. Though they teach well in Css and Html in JavaScript i didn't like the approach. They give examples which contains parts that they didnt explained before.

---

### Post by medic2000 on 2008-11-08
> **nvteighen said:**
> There's a problem with Javascript: there is a lot of information in the internet, but a lot is just crap. And also much of the code you find in webpages is really bad too...

Yes you are right.I have already seen that crap. So i posted here for good and clean source for JS.

---

### Post by nvteighen on 2008-11-08
> **medic2000 said:**
> Yes you are right.I have already seen that crap. So i posted here for good and clean source for JS.
Curiously, here you may find the best help in whatever language you like ;)

But yes, look at LaRoza's wiki.

---

### Post by LaRoza on 2008-11-08
> **medic2000 said:**
> Well i have studied HTML and CSS. Now i am planning to learn JavaScript. I need good examples and their explanations cause i want to learn the logic behind it as i said it is my first programming language.

And no i dont want w3schools. Though they teach well in Css and Html in JavaScript i didn't like the approach. They give examples which contains parts that they didnt explained before.

Ok, see my site for examples (sorry, no explanations in the code...). Get the book "DOM Scripting" [http://domscripting.com/book/](http://domscripting.com/book/).

That book is the best for using ECMAScript properly.

Basically, there is a pyramid of technologies. XHTML (Logic), CSS (Presentation) and ECMAScript (Behavior). The basis for a site is content and logic. That comes first. If you disable CSS on my site, you'll see it is logical clean markup. This is the most important aspect and should never be compromised. CSS is second. This is looks. This greatly enhances usability, but it should degrade gracefully. If CSS is gone, the site should work and the content should be there. Remember, screen readers and search engines don't see anything, only logic. Last, is ECMAScript, which adds behavior. This is a fringe of icing on the cake. It should add to a site, and its absense should never detract. Never rely on it for important content. A prime example of this is drop down menues. If the links in the menu are put there by script, the lack of script removes the navigation.

Everything should degrade gracefully. If scripting is disabled, you can lose some function, but it shouldn't compromise the content or logic. Same with CSS. 

After that, the next bit is the code itself. This can be tricky. First thing, you shouldn't mix logic, presentation, or behavior. All XHTML, CSS, and ECMAScript should be separate. You'll see this in my site. 

You'll see my script ([http://laroza.freehostia.com/script/script.js](http://laroza.freehostia.com/script/script.js)) is entirely separate from everything else.

---

### Post by medic2000 on 2008-11-08
> **LaRoza said:**
> Ok, see my site for examples (sorry, no explanations in the code...). Get the book "DOM Scripting" [http://domscripting.com/book/](http://domscripting.com/book/).

That book is the best for using ECMAScript properly.

I live in Türkiye maybe that will be a problem :(

---

### Post by medic2000 on 2008-11-08
> **LaRoza said:**
> Ok, see my site for examples (sorry, no explanations in the code...). Get the book "DOM Scripting" [http://domscripting.com/book/](http://domscripting.com/book/).

That book is the best for using ECMAScript properly.

Basically, there is a pyramid of technologies. XHTML (Logic), CSS (Presentation) and ECMAScript (Behavior). The basis for a site is content and logic. That comes first. If you disable CSS on my site, you'll see it is logical clean markup. This is the most important aspect and should never be compromised. CSS is second. This is looks. This greatly enhances usability, but it should degrade gracefully. If CSS is gone, the site should work and the content should be there. Remember, screen readers and search engines don't see anything, only logic. Last, is ECMAScript, which adds behavior. This is a fringe of icing on the cake. It should add to a site, and its absense should never detract. Never rely on it for important content. A prime example of this is drop down menues. If the links in the menu are put there by script, the lack of script removes the navigation.

Everything should degrade gracefully. If scripting is disabled, you can lose some function, but it shouldn't compromise the content or logic. Same with CSS. 

After that, the next bit is the code itself. This can be tricky. First thing, you shouldn't mix logic, presentation, or behavior. All XHTML, CSS, and ECMAScript should be separate. You'll see this in my site. 

You'll see my script ([http://laroza.freehostia.com/script/script.js](http://laroza.freehostia.com/script/script.js)) is entirely separate from everything else.

I know what could be done with XHTML,CSS and JS but thanks for good explanation. 

Hmmm i will try to get the book from somewhere.

---

### Post by jespdj on 2008-11-09
[http://www.w3schools.com/](http://www.w3schools.com/) is a great website for learning JavaScript (and HTML, CSS, XML, and much more).

*edit* Oh, ok, I see you didn't want to hear that.

---

### Post by Kadrus on 2008-11-09
[http://www.crockford.com/javascript/](http://www.crockford.com/javascript/) 
[http://www.crockford.com/javascript/little.html](http://www.crockford.com/javascript/little.html) (little schemer in javascript)

---

### Post by LaRoza on 2008-11-09
> **jespdj said:**
> [http://www.w3schools.com/](http://www.w3schools.com/) is a great website for learning JavaScript (and HTML, CSS, XML, and much more).

*edit* Oh, ok, I see you didn't want to hear that.

Actually, it is a very bad site for learning JavaScript. There is more to using web development than syntax. For instance, document.write() should never be used.

---

### Post by nvteighen on 2008-11-09
> **LaRoza said:**
> Actually, it is a very bad site for learning JavaScript. There is more to using web development than syntax. For instance, document.write() should never be used.
Eh? Why?

---

### Post by LaRoza on 2008-11-09
> **nvteighen said:**
> Eh? Why?

Because it violates structured programming, it isn't logical, it requires mixing logic and behavior, and it isn't visible on the document tree.

The biggest issue with it is you must mix markup and script to use it, and that is a big no-no.

There are other, better, ways of adding text to the document tree. (innerHTML isn't it ;))

---


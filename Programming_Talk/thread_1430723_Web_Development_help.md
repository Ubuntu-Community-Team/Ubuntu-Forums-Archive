---
title: "Web Development help"
date: 2010-03-15
forum: Programming Talk
---

### Post by puzzler995 on 2010-03-15
I have been building [this website]("http://la-vida.sourceforge.net"), and have hit a few road blocks I can't seem to surpass.

[LIST=1]
[*]for some reason, when I re-put any page and include the dependencies, the CSS gets screwed up and the background disappears, among other things changing. The weird part is when I open up the local file, it is correct. I have included the index, main.css and background.
[*]I am looking for a script that will automatically redirect anyone who has a browser that doesn't support HTML 5. any suggestions?
[/LIST]
Thanks in advance!!!:P

---

### Post by CyberJack on 2010-03-16
What do you mean by "re-put any page"?

When I load your page I don't see the background image.
When I try to access the background image or the css file directly I get a 404 (file not found).
When Accessing the javascript file and the menu images there are no problems.
Have you uploaded the main.css and background image?

Why do you want to redirect anyone who has a browser that doesn't support .? (what does the dot mean?)
If you create a valid html page all browsers should be supported and you don't have to redirect anybody.

By the looks of your html page the layout is very simple and should work on any browser.
However there are a few things I noticed when looking at the html and css:
- html 4.01 (nothing wrong with that but it's way old. Maybe you should take a look at xhtml)
- using non existing tag "nav"
- using a tag that is IE only "comment"
- special code for when a user is not using IE (build a page that works on all browsers. Don't make exceptions)
- use of non existing css tag "page"

I strongly advise you to rebuild the html code so no browser exceptions are to be made.
Use xhtml instead of html 4.01 and make sure the javascript you use is also cross browser compatible.
That way you don't need to redirect anyone and its keeps your page better maintainable.

---

### Post by cubeist on 2010-03-16
by re-put I am guessing you mean when you upload your files from your desktop to your server, right?

I think you must be overwriting your existing files on your server.  To have your webpage load properly make sure the folders/files on your server are identical to the hierarchical order on your desktop...

This link should be memorized by all web-developers!
[http://validator.w3.org/](http://validator.w3.org/)
it checks your markup for standards validity.

---

### Post by puzzler995 on 2010-03-16
> **CyberJack said:**
> When I load your page I don't see the background image.that's my problem...
> When I try to access the background image or the css file directly I get a 404 (file not found).I added restrictions, I put the image and CSS in the zip file.
> Why do you want to redirect anyone who has a browser that doesn't support .? (what does the dot mean?) > If you create a valid html page all browsers should be supported and you don't have to redirect anybody.> html 4.01 (nothing wrong with that but it's way old. Maybe you should take a look at xhtml)> using non existing tag "nav"> special code for when a user is not using IE (build a page that works on all browsers. Don't make exceptions) AHHH! TYPO!!!... It's supposed to say HTML 5. HTML 5 is experimental and not supported by IE and Konqueror, for example. [http://dev.w3.org/html5/spec/Overview.html](http://dev.w3.org/html5/spec/Overview.html)

> **cubeist said:**
> by re-put I am guessing you mean when you upload your files from your desktop to your server, right?Yep.

> I think you must be overwriting your existing files on your server.  To have your webpage load properly make sure the folders/files on your server are identical to the hierarchical order on your desktop... I use dreamweaver to put the entire site.

> This link should be memorized by all web-developers!
[http://validator.w3.org/](http://validator.w3.org/)
it checks your markup for standards validity. Already use it ;) How do you think I got the logo at the bottom :)

---

### Post by hessiess on 2010-03-17
Eather the file path is wrong, or there is a file permission problem.

---


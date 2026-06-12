---
title: "web page creation, python or javaScript? or ...?"
date: 2009-12-27
forum: Programming Talk
---

### Post by kwyto on 2009-12-27
hi guys, i want to create a web page, nothing fancy for now. i don't know anything about web programming. i have looked at javascript and it looks fairly similar to C/C++, which i know. also python seems to be another desirable language to do such task. python knowledge is relatively small. any suggestions to where to start? much appreciated

---

### Post by Hellkeepa on 2009-12-27
HELLo!

If you want to create a web page, then you need to learn HTML and CSS. HTML for marking up the content into logical sections, so that browsers and search engines can make heads and tails out of your content, and CSS for giving the site style (layout, in other words).

JavaScript is to make sites act dynamicly on the browser, seeing as web pages are just static text. Only necessary for fancy elements, such as fading elements, moving stuff, replacing only parts of the content and so forth. It is more commonly known as "client side scripting".

Python, Perl, PHP (and more) are scripting languages for dynimc assembly and processing of pages on the server, which is a requirement for all pages that accepts data from the users. Yet again, not necessary for a simple web site, and completely seperate from the HTML/CSS. (Although, they are used to generate both.) Only required of you want to create a web site that takes input from the user, like a contact form, guestbook, forum, web shop or similar.
This is commonly known as "server side scripting".

Thus, my tips is for you to find yourself a HTML or XHTML tutorial, and learn how to write semantic markup ("HTML 4.01 strict" or "XHTML 1.0 strict" is recommended). Then, move on to CSS to learn how to make your newly created markup look just the way you want it to look.
After you've mastered these, then you can move on to JS and server side scripting languages.

Happy codin'!

---

### Post by hessiess on 2009-12-27
Learn HTML and CSS, then learn a MVC framework like Django, Rails or Cakephp. Avoid using PHP without a MVC framework because it basically guarantees that you will produce messy, unmaintainable code.

Avoid doing anything remotely impotent with JavaScript, as it is a client side language it is inherently insecure and it is not standardised across browsers. Also remember that search engine spiders do NOT execute JavaScript.

---

### Post by Hellkeepa on 2009-12-27
HELLo!

I would not put forth a MVC framework as a requirement for writing good code, it's just as easy to write horrible code with it (in fact, it's even easier, as it adds upon the complexity). A MVC framework is a tool, and like any tool it is as easy to use it as it is to abuse it.

That said, learning a framework (MVC and other kinds) is a good idea. Though, not for the reasons **hessiess** posted. For small projects, and learning the language, I'd stick to pure and simple procedural scripting. For bigger projects, and especially those when you are working alongside other people, framworks and/or MVC comes into their right. Only after having learned the language in question, mind you.

Happy codin'!

---

### Post by Can+~ on 2009-12-27
For web development, first learn to create static sites:

HTML: Content of the site, basic layout. Read: w3schools
CSS: How everything should look, and behave (something:hover for example). Again, w3schools
JavaScript: Adds movement, fancy effects. It can retrieve data in case of AJAX.

All this things run on the clientside. Now, when you use PHP, Python, or whatever language/framework, what happens is that it basically does something like a replace of certain pieces of the .html, and send it to the user (along with many other things, like managing cookies, sessions, etc)

For example, a friend wanted a simple website without using PHP, or any dynamic server side language. So I wrote a .py script, and told him to put the following inside the .html page:

```
<!--PY-CONTENT-->
```

My script then would look that line, replace it with the proper content (another .html file in another folder that held the content, this is, as to create something like a template file), and store it all statically. It was something like a basic client side, run-once version of what server programming does.

As an added bonus, save this file as [FONT="Courier New"]webpage.html[/FONT] in the ~/Templates folder, and you'll be able to create simple sites in no time.
[HTML]
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	<meta name="keywords" content="HTML, tags, commands">
	<title>Index</title>
	
	<!--<link href="css/style.css" rel="stylesheet" type="text/css">-->
</head>
<body>

</body>
</html>[/HTML]

It has the basic HTML4 standard structure, a pre-made link to a css file (that you must uncomment) and... nothing else.

---

### Post by Reiger on 2009-12-27
Also: JavaScript is not at all much like C++. Going down _that_ route with the language is pretty much like grabbing yourself a heavy axe, chopping off your foot and _then_ shooting your foot.

---

### Post by kwyto on 2009-12-27
thank you for the responses. now i was also thinking on getting something like dreamweaver, where part of the code is generated. what about Django?

---

### Post by sujoy on 2009-12-28
if you want to really learn how to create web pages, use a text editor.
any editor that you prefer, even the one in dreamweaver if you will, but write your code, don't use the messy generators

---

### Post by Hellkeepa on 2009-12-28
HELLo!

Django is a Python framework, in other words for server side scripting.

Also, I agree with **sujoy**: Stay away from WYSIWYG editors! The only thing you'll learn from them, is how to use that particular program to create broken code. Use a standard text editor, and write all your code by hand. Syntax highlighting is nice to have, but not necessary.

Happy codin'!

---


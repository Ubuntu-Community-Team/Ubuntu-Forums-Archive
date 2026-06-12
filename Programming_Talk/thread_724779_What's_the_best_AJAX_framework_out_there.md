---
title: "What's the best AJAX framework out there?"
date: 2008-03-15
forum: Programming Talk
---

### Post by SuperMike on 2008-03-15
What's the best (most popular) AJAX Framework out there that uses PHP (and potentially MySQL) on the backend? I'm a PHP/MySQL Freelancer and I've been going down the wrong path of doing all my Javascript and AJAX stuff myself, and it's a royal pain with cross-platform testing and so on. It's time for me to grow up and use a framework for these things so that the testing is already done for me. I've already heard that JQuery is the reigning king of Javascript frameworks, but what if I want an AJAX-based drag and drop solution, or AJAX based treeview control that dynamically gets child nodes from the server on the fly? It's this sort of thing for why I'll also need an AJAX framework.

---

### Post by pmasiar on 2008-03-15
AJAX has nothing to do with PHP or MySQL. It is JavaScript running in browser. Any web server can provide XML, or even better, Jason - JavaScript object notation, more readable and easier to parse (you just need eval it).

Very nice AJAX based UI widgests are YUI - Yahoo user interface kit, very clean design, skinnable. Google has own, of course.  Good web app framework (like TurboGears) simplifies AJAX/Jason interaction a lot.

---

### Post by lnostdal on 2008-03-15
combine jQuery with ExtJS 

[http://extjs.com/deploy/dev/examples/#sample-4](http://extjs.com/deploy/dev/examples/#sample-4)

i'm developing a custom server-backend for this stuff at the moment .. it's gonna be great .. =)

---

### Post by SuperMike on 2008-03-15
> **pmasiar said:**
> AJAX has nothing to do with PHP or MySQL. It is JavaScript running in browser. Any web server can provide XML, or even better, Jason - JavaScript object notation, more readable and easier to parse (you just need eval it).

Very nice AJAX based UI widgests are YUI - Yahoo user interface kit, very clean design, skinnable. Google has own, of course.  Good web app framework (like TurboGears) simplifies AJAX/Jason interaction a lot.

Ah, yeah. Thanks, pmasiar. I've been doing AJAX and JSON manually already. I need a widget toolkit, and my clients only provide PHP backends. Therefore, I can't always run something that implements Java like GWT. (I also don't like static-typed languages like Java.)

I've also actually embarassed myself a little here. I had just started reading up on jQuery, and evidently it has a built-in AJAX framework that I missed. I was more taken in by blogs from PHP guys about jQuery, realizing it was the most popular and that I should go with it for a Javascript framework, and hadn't really read the docs on it yet that much. The only drawback about jQuery's AJAX API is that it's just an API and there are still not a lot of cross-platform-tested AJAX widgets/gadgets based on it yet. I mean, I think I've only seen like one jQuery + AJAX treeview gadget out there where the child nodes are retrieved dynamically from the server. The idea is that I don't want to build every gadget by myself and do all the testing -- I want to save precious development time by using pre-made gadgets that also support AJAX.

---

### Post by SuperMike on 2008-03-15
> **lnostdal said:**
> combine jQuery with ExtJS 

[http://extjs.com/deploy/dev/examples/#sample-4](http://extjs.com/deploy/dev/examples/#sample-4)

i'm developing a custom server-backend for this stuff at the moment .. it's gonna be great .. =)

Doesn't ExtJS require Java in the backend? That's what I thought I read. My clients won't let me run Java. Java's also not my thing. I do PHP. However, if ExtJS supports PHP, and doesn't require a custom compile on a Linux host for C libraries and so on, then I just might consider it. However, woah, what a pricetag on the commercial license! Very expensive. I only do commercial work for my clients, so that's the license I would have to purchase.

---

### Post by lnostdal on 2008-03-15
> Doesn't ExtJS require Java in the backend? That's what I thought I read. My clients won't let me run Java. Java's also not my thing.

it's not tighty connected to any specific backend which mean you can use php or anything to communicate with it

PS: you do not have to have a commercial license to use it in a commercial context .. see this:

> 
Ext is also available under the terms of the Open Source LGPL 3.0 license. You may use our open source license terms if you are using Ext in a commercial application that is not a software development library or toolkit, you will meet LGPL requirements and you do not wish to support the project



..this basically means that only changes/improvements you make to the extjs codebase _itself_(#1) would have to be "open sourced" .. the application code/software you develop for your clients _does not_ have to be "open sourced"

to clarify: "LGPL requirements" only imply that you give back code/improvements done to the exjs codebase itself .. which imho is very fair

#1: or if you extend it by adding more library or toolkit "stuff" to it .. you should already be coding by separating application-code/logic from library code .. so this should not be a problem for you or your clients

---

### Post by Wybiral on 2008-03-15
[MochiKit]("http://mochikit.com/") is a very nice Javascript library that has some AJAX routines in it.

---

### Post by pmasiar on 2008-03-15
IIRC  there are no plans for further development of MochiKit, TG2 replaces it with some other library. I heard that jQuery is good. I personally don't use AJAX now.

---


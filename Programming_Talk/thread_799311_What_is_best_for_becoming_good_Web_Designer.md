---
title: "What is best for becoming good Web Designer?"
date: 2008-05-18
forum: Programming Talk
---

### Post by jsmidt on 2008-05-18
I have a close family member that wants to be a web designer.  I know  programming for scientific work, but nothing of web design.

What would you tell a person who wanted to be a web designer?

What programs should they be familiar with?

What languages should they know?

What books are good for learning to be an effective web designer?

Any good informative websites or tutorials I could point them to?  Thanks.

---

### Post by tamoneya on 2008-05-18
start in more or less this order: HTML, Javascript, CSS, PHP,.

Also while graphical tools like kompozer are nice and easy to use they dont teach you anything.  I would recommend that he doesnt work with anything but gedit(or some other text editor) for a couple of months.  Some professionals even prefer to stay with the text editor because it offers them more control and doesnt have all the other distractions of the GUI.

---

### Post by JupiterV2 on 2008-05-18
Preface/Disclaimer: I am NOT a professional web designer but chose to learn mark-up languages and scripting for my personal use.

> **jsmidt said:**
> I have a close family member that wants to be a web designer.  I know  programming for scientific work, but nothing of web design.

What would you tell a person who wanted to be a web designer?

What programs should they be familiar with?

What languages should they know?

What books are good for learning to be an effective web designer?

Any good informative websites or tutorials I could point them to?  Thanks.

I chose to learn web design in the following order: HTML (4.01), XHTML, CSS, Javascript, XML, and found [W3Schools Online Tutorials]("http://www.w3schools.com/") to be extremely useful. I will likely learn PHP next.

I use gedit for editing.

---

### Post by LaRoza on 2008-05-18
You have to know XHTML and CSS. Learning the ancient HTML 4 and such is dangerous. It is a curiosity to be learned after you already are skilled with XHTML and CSS. Never start with it.

JavaScript is the most abused technology (any sort of multimedia (images and flash mostly) is second).

Get this book: [http://domscripting.com/book/](http://domscripting.com/book/) and never use document.write()!

That is all you need for "design". XHTML for logic, CSS for presentation and ECMAScript for behavior. 

Learning how to use it to make effective web pages takes time. See [http://www.useit.com/](http://www.useit.com/)

Next, is the server. If you don't need this aspect, it doesn't matter. If you do, you will find that PHP is the most common language. If you end up learning it (it is incredibly easy like ECMAScript) you should learn how to use it well. 

ECMAScript and PHP are C syntax, dynamic and weakly typed. They all allow mixing code and markup easily, and they can make a mess quickly. If you are going to learn how to use them, learn how to use them well. Remember, the logic, layout, behavior and backend of the site is all separate in function. They should be separate in actuality also. 

My site (see link in my sig) is simple in design because it has a simple purpose. It also follows all of these principles. The XHTML and CSS are completely separate and completely valid. The XHTML is logical and the CSS is for presentation. The ECMAScript degrades gracefully and is completely separate from the other code. I also follow all useit.com in its design. I have an issue with my colouring, as it is technically too dark for complete usability. I will change this someday (because of my design, it will involve editing a single file for the entire site)

---

### Post by jsmidt on 2008-05-19
Thanks everyone.  Just a quick question: what is the difference between JavaScript and AJAX?

---

### Post by pmasiar on 2008-05-19
[http://en.wikipedia.org/wiki/Ajax_%28programming%29](http://en.wikipedia.org/wiki/Ajax_%28programming%29) uses Javascript, but communicates with the server to get (XML) data to client.

Another version is instead of XML to get JSON (JS Object Notation), which is easier to read and simpler to evaluate (no XML parsing, just eval). Of course named for another Greek hero: Jason :-)

---

### Post by SeanBlader on 2008-08-14
> **jsmidt said:**
> I have a close family member that wants to be a web designer.  I know  programming for scientific work, but nothing of web design.

What would you tell a person who wanted to be a web designer?

What programs should they be familiar with?

What languages should they know?

What books are good for learning to be an effective web designer?

Any good informative websites or tutorials I could point them to?  Thanks.

Sorry I had to bring this thread back from the dead... 

If someone wanted to be a web designer, I'd tell them to get into some art/design classes, join a graphic arts program at the local community college, and learn about color and form before even thinking about what programs to use.

Next I'd tell them to become intimate with Photoshop or The Gimp.

After that, commit HTML to memory, and get started with CSS for a few years. No one masters CSS, well [maybe one guy]("http://www.cssplay.co.uk/"), but no normal person does. Once you feel like you're getting a handle on CSS you go and look at your site in a different browser and then spend twice as long trying to get it to look fair in both.

After that you're pretty much tapped out as a web designer. Any further and you're going into web developer territory. Then they might consider looking up [Douglas Crockford]("http://javascript.crockford.com/") and all the stuff he does at Yahoo! for the advancement of JavaScript. By then you'll know what to look for.

---

### Post by LaRoza on 2008-08-14
> **SeanBlader said:**
> 
If someone wanted to be a web designer, I'd tell them to get into some art/design classes, join a graphic arts program at the local community college, and learn about color and form before even thinking about what programs to use.

I would think that is a good idea for a graphics designer, not a web designer. Typically, web designers use graphics created by other people.

> 
Next I'd tell them to become intimate with Photoshop or The Gimp.

For a graphic designer, yes. For a web designer, not so useful.

---

### Post by Reiger on 2008-08-14
A web designer is someone who designs the behaviour of a website (should there be drop-down menu's or not) and the look & feel. He does not neccesarily create websites.

But if you're talking about the over-abused form of 'webdesigner' then my suggestion sticks to the opinion of the crowd which is to learn:
1) XHTML
2) CSS
3) EcmaScript/JavaScript/JScript

4) A CGI language such as PHP.

---

### Post by LaRoza on 2008-08-14
> **Reiger said:**
> 
4) A CGI language such as PHP.

PHP is very rarely used for CGI, and CGI itself is rarely used at all.

---

### Post by tinny on 2008-08-14
> **SeanBlader said:**
> Sorry I had to bring this thread back from the dead... 

If someone wanted to be a web designer, I'd tell them to get into some art/design classes, join a graphic arts program at the local community college, and learn about color and form before even thinking about what programs to use.

Next I'd tell them to become intimate with Photoshop or The Gimp.

After that, commit HTML to memory, and get started with CSS for a few years. No one masters CSS, well [maybe one guy]("http://www.cssplay.co.uk/"), but no normal person does. Once you feel like you're getting a handle on CSS you go and look at your site in a different browser and then spend twice as long trying to get it to look fair in both.

After that you're pretty much tapped out as a web designer. Any further and you're going into web developer territory. Then they might consider looking up [Douglas Crockford]("http://javascript.crockford.com/") and all the stuff he does at Yahoo! for the advancement of JavaScript. By then you'll know what to look for.

I think you have a good point here. When I think of "web designers" I think of a trendy guy or girl using a Mac. (you know the type :) ) It may just be the way the industry is in my area (New Zealand) but web designers seem to be creative people that also do the graphics design work and use something like dreamweaver (drag and drop).

"Web programmers" are boring people like me that use Linux.

I think there is a difference between web designers and web programmers.

This is what I mean.

[http://it.seek.co.nz/users/apply/index.ascx?Sequence=93&PageNumber=1&JobID=13343073&](http://it.seek.co.nz/users/apply/index.ascx?Sequence=93&PageNumber=1&JobID=13343073&)

---

### Post by pmasiar on 2008-08-14
> **Reiger said:**
> A web designer is someone who designs the behaviour of a website

Exactly. "web designer" is vague term. In most companies (in all companies with good-looking websites), graphic designer creates graphics and web app developer creates the logic. 

O'Reilly has excellent web certifications for web technologies, I am sure better then most community colleges and other vocational training facilities - and they are issued by  University Of Illinois. You can try them for free for a week - best value I found.
> 4) A CGI language such as PHP.

There are better, more productive languages for web apps, like Python and Ruby. Much better MVC (Module-View-Controller) frameworks, like Django, Turbogears and Rails.

> **LaRoza said:**
> PHP is very rarely used for CGI, and CGI itself is rarely used at all.

CGI in computing has two meanings:
- [http://en.wikipedia.org/wiki/Common_Gateway_Interface](http://en.wikipedia.org/wiki/Common_Gateway_Interface)  (where PHP is very much used, and also Python, Perl, Ruby)
- [http://en.wikipedia.org/wiki/Computer-generated_imagery](http://en.wikipedia.org/wiki/Computer-generated_imagery) (where PHP is useless, it's all C libraries glued together by Python)

---

### Post by jimi_hendrix on 2008-08-14
EDIT: after i read some more of this thread and googled it i realized my advice to be totally wrong so i took it out

---


---
title: "Best way to demonstrate SQL w/PHP &amp; Java?"
date: 2009-07-14
forum: Programming Talk
---

### Post by Fatman22 on 2009-07-14
Hello,
I am doing a web project and I have to use the following languages & technologies for this project. (I am using Dreamweaver 4 - eventually will use Eclipse with the HTML plugin but I'm not there yet)

1. HTML (duh)
2. Java 
3. SQL with PHP
 Database linked to webform
Basic  query
Query producing a dynamic report in pdf.
4. Web app coded in C#. (I am using Mono, then over to Visual Studio to turn them in for class)



I have made a basic 6 page site using my textbook & W3 as a guide but I've only used a tiny bit of Java for mouseover gimmicks.

How should I elegantly demonstrate Java on a webpage?


I have yet to do any SQL/PHP and was wondering what would be a good demonstration of these technologies. (I am a bit noob here when it comes to SQL, I know what it does but I do not how to use it very well.


Supplemental Info:

I am an accounting major, and I love the idea of getting things done in C# vs VB, but I really don't have the stomach for the learning curve of learning an OOB language first, then going on to learn C# with .NET as that could take years and my main focus is accounting. 

 I used to work with a guy who would write small apps in VB 6 about 1-2 weeks. They worked fine for most MS Office automation tasks, but the IT people would laugh at his source code all the time, and say all VB programmers are sloppy. This is why I want to learn C#. Being that I am in accounting, I think 75% of my C# apps will be dealing with Excel... but I worry about the learning curve )-:


Thank you for the ideas!

---

### Post by myrtle1908 on 2009-07-14
> **Fatman22 said:**
> I've only used a tiny bit of Java for mouseover gimmicks.  How should I elegantly demonstrate Java on a webpage?

You are referring to JavaScript here not Java here (they are very different things).  JavaScript is run natively by your web browser so to add these "gimmicks" it is JavaScript that you will be using.

That said, it really depends on what kind of "gimmicks" you want to add to a page.  Personally, I would look at one of the popular JavaScript libraries like jQuery [http://jquery.com/](http://jquery.com/) or ExtCore [http://extjs.com/products/extcore/](http://extjs.com/products/extcore/) ... these give you the ability to add things like menus, trees and windows etc to your page(s) with relative ease.

At the end of the day you will need at least a basic understanding JavaScript and the Document Object Model (DOM).  There are plenty of tutorials on these technologies ... perhaps [http://www.w3schools.com](http://www.w3schools.com).

---

### Post by Mirge on 2009-07-15
+1 for jQuery!

---

### Post by Can+~ on 2009-07-15
You can do a lot of elegant things with html an CSS alone, for example

[HTML]...
	<ul id="menu">
	<li>opt1</li>
	<li>opt2</li>
	<li>opt3</li>
	</ul>

...[/HTML]

[PHP]#menu li
{
	background: none;
}

#menu li:hover
{
	background: #CCEEFF;
}[/PHP]

A simple :hover can make things more richer.

(And it's Javascript, not Java)

---

### Post by Pyro.699 on 2009-07-15
For your PHP & MySQL integration, check out this

[http://www.ricocheting.com/scripts/php_mysql_wrapper.php](http://www.ricocheting.com/scripts/php_mysql_wrapper.php)

It's very very easy to use :) I use it for all my scripts.

---


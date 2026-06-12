---
title: "Help me learn HTML, so that I can code my web site"
date: 2007-09-15
forum: Programming Talk
---

### Post by Zdravko on 2007-09-15
Hi!
Since I am disappointed from [several blogging systems]("http://ubuntuforums.org/showthread.php?t=549817"), I decided to create my web page all by myself with my own hands! I will need basic HTML only. But first, I need to know HTML on a basic level.
What comprehensive source of HTML would you recommend me?

---

### Post by Mud.Knee.Havoc on 2007-09-15
[This should cover it.]("http://www.google.ca/search?q=html+tutorial+beginner") :)

---

### Post by pmasiar on 2007-09-15
[http://www.w3schools.com/](http://www.w3schools.com/) is the best start

---

### Post by jsmiith on 2007-09-15
[htmldog.com]("http://htmldog.com/") is pretty good.

---

### Post by gnuman on 2007-09-15
> **Zdravko said:**
> Hi!
Since I am disappointed from [several blogging systems]("http://ubuntuforums.org/showthread.php?t=549817"), I decided to create my web page all by myself with my own hands! I will need basic HTML only. But first, I need to know HTML on a basic level.
What comprehensive source of HTML would you recommend me?

I sponsor a high school programming club.  Of all the HTML books I've seen, the [[COLOR="Blue"]Head First HTML[/COLOR]]("http://www.oreilly.com/catalog/hfhtmlcss/") book is probably the best for avoiding deprecated code and letting you see the big picture (including XHTML and CSS).
:)

---

### Post by userundefine on 2007-09-16
If you want to create a blog, PHP is probably something you should learn a bit of also.

Please do read up-to-date stuff that focuses on web standards like (X)HTML and CSS.  Never use FONT tags.

---

### Post by Zdravko on 2007-09-16
What if I want the font to be Times New Roman, 12 pt?

---

### Post by Zdravko on 2007-09-16
I found a German tutorial (a very large one) - [http://de.selfhtml.org/](http://de.selfhtml.org/)
But what editor should I use for coding (under Windows)?

---

### Post by bikeboy on 2007-09-16
> **Zdravko said:**
> What if I want the font to be Times New Roman, 12 pt?

That's what CSS is for :)

---

### Post by Compyx on 2007-09-16
Keep in mind that not everyone will have that font installed on their system, so you should at the very least provide an alternative in your stylesheet, eg:
```

p {
  font-family: "Times New Roman", serif;
  font-size: 12pt;
}

```

Generally I would just use the standard fonts that w3c recommends: serif, sans-serif, cursive, fantasy and monospace. Let the user's browser figure out which font to use. [This link]("http://www.w3.org/TR/CSS21/fonts.html#generic-font-families") might help.

Also try to steer clear of using fixed sizes, rather use 'em' or '%' to set font sizes, this way people can determine their own font sizes (for example people with bad eyesight might have their browsers set to display fonts at 150%).

And as for an editor: the one I always recommend: VIM, it can highlight (x)html, css, php, perl, SQL and so on and so on..

Just remember to validate your (x)html and css with w3c's validator services, you should be able to find a plugin for Firefox which will add options like "validate html" and "validate css" to the context menu.


Happy coding!

---

### Post by Zdravko on 2007-09-16
I don't want to use VIM under Windows. I'd like something native and easier for rapid development.

---

### Post by Zdravko on 2007-09-16
Can you suggest me the sample CSS/HTML code for a web site with the following (roughly) structure:

---

### Post by userundefine on 2007-09-17
> **Zdravko said:**
> Can you suggest me the sample CSS/HTML code for a web site with the following (roughly) structure:

```

<div id="header">
	<h1>Crystal Clear</h1>
	<h2>Personal website</h2>
</div>
<div id="leftnav">
	<ul>
		<li>About me
			<ul>
				<li>CV</li>
			</ul>
		</li>
		<li>Science
			<ul>
				<li>Publications</li>
			</ul>
		</li>
	</ul>
</div>
<div id="main">
	<p>Lorem ipsum</p>
	<p>Lorem ipsum</p>
	<p>Lorem ipsum</p>
</div>
<div id="footer">
	<p>Footer</p>
</div>
```
And you style all the ids (e.g., #header, #leftnav) to give you layout and colors, fonts, etc.

---

### Post by Zdravko on 2007-09-17
You don't help me much. I am not that experienced!

---

### Post by Ramses de Norre on 2007-09-17
> **Zdravko said:**
> You don't help me much. I am not that experienced!

He showed you the code, now you need to comprehend it... Use google to read up on the tags you don't understand and try to see the structure you asked for in the html code you've got.

If you've got a specific question about a tag you can ask again but we can't learn you something, you need to learn for yourself.

PS: the styling he talks about refers to css, start with understanding the html and then read up on css.

---

### Post by pmasiar on 2007-09-17
> **Zdravko said:**
> You don't help me much. I am not that experienced!

It is **your** responsibility to read docs and learn to understand it. If you need a teacher, enroll in a school. We don't teach, we show the way to self-learners and self-starters. Read my sig about asking questions.

---

### Post by LaRoza on 2007-09-17
[http://www.tizag.com](http://www.tizag.com) for good tutorials on anything web related

[http://www.w3schools.com](http://www.w3schools.com) for similar tutorials.

---

### Post by southernman on 2007-09-17
[http://www.htmlgoodies.com/]("http://www.htmlgoodies.com/") <--- That is the site I used to learn the basics of HTML several years ago.

However, since the W3C is the entity that sets the standards, you'd so yourself justice to use the [http://www.w3schools.com/]("http://www.w3schools.com/") that has been suggested a couple of times now.

I concur that if you need help with a particular problem your having, by all means ask for help... Don't however expect someone to "teach" you HTML on this or any other forum. Just isn't feasible... nor sane. ;)

---

### Post by LaRoza on 2007-09-17
> **southernman said:**
> 
PS. Laroza's link to w3schools is missing the "s" at the end. The current link goes to some flashy thingamajig.

Whoops! Fixed it. Thanks!

---

### Post by Zdravko on 2007-09-19
Phew! I will have to learn some CSS... :)

---

### Post by gnuman on 2007-09-19
Yes, you should learn CSS along with HTML (or Xhtml).  Take a look at the sample chapter from the Head First book I mentioned earlier.  That book does a great job of teaching HTML and CSS concurently:

[http://www.oreilly.com/catalog/hfhtmlcss/chapter/index.html](http://www.oreilly.com/catalog/hfhtmlcss/chapter/index.html)

---

### Post by mssever on 2007-09-20
There are two basic "sides" to web development.

The back end is what you use to create dynamic sites. You can use any language that can run on your server, but PHP is the most popular (and very awkward, though easy to learn).

For the front end, you should know three basic technologies and maintain a strict separation between them:
[LIST=1]
[*]Structure: This is what HTML is for. I suggest that you validate your pages against XHTML 1.0 strict as it will provide the best forward compatibility and deprecates some of the most egregious flaws of earlier versions.
[*]Appearance: CSS
[*]Behavior: Javascript. But be sure that what you read about Javascript isn't outdated or otherwise clueless. The majority of the Javascript tutorials are seriously outdated.[/LIST]

---

### Post by pmasiar on 2007-09-20
> **mssever said:**
> The back end is what you use to create dynamic sites. You can use any language that can run on your server, but PHP is the most popular (and very awkward, though easy to learn).

For the front end, ...

And if you instead of PHP will pick Python with some established framework, like Django or Turbogears, you will get:
- nicer universal language to work with (cleaner, with OOP if you need it), and usable beyond web
- MVC pattern: separating model (data access), view (templates and CSS), and controller (responding to request, get data from M and prepare then for V), which **greatly** improves maintainability
- project template and structure auto-generated and "hello world" page working
- includes web server for development, and proven practices for deployment
- javascript library for AJAX
- object-relational mapper for model, so you even don't need to know SQL, it is all generated for you
- loads of example code how to make it work
- active communities ready to answer your questions. 

Yes, it is very different world to use Python for web development, compared with 2-3 years ago. Complete revolution: 2 excellent back-to-front web frameworks.

---

### Post by Zdravko on 2007-09-20
This is way too complicated for me. My web site will be 90% static! When I want to write an article, I will just edit the appropriate files.

---

### Post by mssever on 2007-09-20
> **Zdravko said:**
> This is way too complicated for me. My web site will be 90% static! When I want to write an article, I will just edit the appropriate files.That's fine for tiny sites. But almost every site has some data that's common to all or many of the files (a common header or sidebar, for example. Manually updating the navigation links on every page when you change something can quickly become tedious and error-prone. Eventually, even for a mostly static site, you'll want at the minimum to have some method to place common content in separate files and then dynamically include them. This is pretty much what my brother (who isn't a programmer) does using PHP. Of course, If you can learn a better language--such as Ruby or Python--you'll benefit in the long run.

---

### Post by LaRoza on 2007-09-20
Depending on the server, you could use Server Side Includes (SSI), although I use PHP for all my sites.

---

### Post by Zdravko on 2007-09-20
> **mssever said:**
> That's fine for tiny sites. But almost every site has some data that's common to all or many of the files (a common header or sidebar, for example. Manually updating the navigation links on every page when you change something can quickly become tedious and error-prone. Eventually, even for a mostly static site, you'll want at the minimum to have some method to place common content in separate files and then dynamically include them. This is pretty much what my brother (who isn't a programmer) does using PHP. Of course, If you can learn a better language--such as Ruby or Python--you'll benefit in the long run.
That's what I was thinking of. My host provides PHP and Python. How should I proceed?

---

### Post by Kadrus on 2007-09-20
[www.w3schools.com](www.w3schools.com)
Best site to learn web languages.

---

### Post by LaRoza on 2007-09-20
> **Kadrus said:**
> [www.w3schools.com](www.w3schools.com)
Best site to learn web languages.

[www.tizag.com](www.tizag.com) is very good too.

---

### Post by LaRoza on 2007-09-20
> **Zdravko said:**
> That's what I was thinking of. My host provides PHP and Python. How should I proceed?

Learn XHTML and CSS first.

Then get tutorials, and information on PHP and Python (I vote for PHP on simple things, like includes, and PHP is easier to find a host for (free ones too))

Use my wiki, and the links here for PHP and Python info.

---

### Post by southernman on 2007-09-20
> **Zdravko said:**
> That's what I was thinking of. My host provides PHP and Python. How should I proceed?

I am in the camp of using php includes (or SSI *server side includes*) also. Below is a the main table from a very old site's index page... just as a guide. These days you should stick to using tables to only show tubular data and use <div> tags along with css to build your page layout.

```

<table width="760" align="center" bgcolor="#FFFFFF" cellpadding="0" cellspacing="0" border="0">

  <tr>

    <td colspan="3"><?php include ("includes/header.html");?></td>

  </tr>

  <tr>

    <td width="165" valign="top" class="leftborder"><?php include ("includes/left.html");?></td>

    <td width="445" align="center" valign="top"><?php include ("includes/home.html");?></td>

    <td width="150" align="center" valign="top" class="rightborder"><?php include ("includes/right.html");?></td>

  </tr>

  <tr>

    <td colspan="3" class="footer"><?php include ("includes/footer.html");?></td>

  </tr>

</table>

```

Notice the <?php include ("path/to/yourfile.extension");?>

To make the includes function work (being that it's php coding) your pages *have* to have the .php extension.

Once your comfortable with (X)HTML and CSS, then you can look at exactly how you want to use includes and find best practices for todays standards.

---

### Post by mssever on 2007-09-20
> **LaRoza said:**
> Then get tutorials, and information on PHP and Python (I vote for PHP on simple things, like includes, and PHP is easier to find a host for (free ones too))

PHP is certainly easier for beginners to use. My first web programming was in PHP, but I eventually became dissatisfied with PHP (it can't even handle includes in a sensible manner) and I've been looking towards Ruby. Nowadays, I only use PHP when I'm forced to by project constraints. I think, though, that you need some programming experience before you can really take advantage of the better platforms. LaRoza is right; start with (X)HTML and CSS. Then, go for the back end.

Also, you'll need to learn Javascript at some time. But I suggest that you wait a bit on that one. The problem is that most of the Javascript tutorial sites out there are outdated or just plain clueless. More experience with web technologies will help you to sift the good from the bad. ([www.quirksmode.org]("http://www.quirksmode.org") is a great site for Javascript and--to a lesser extent--CSS.)

---

### Post by pmasiar on 2007-09-20
> **LaRoza said:**
> Learn XHTML and CSS first.

Then get tutorials, and information on PHP and Python (I vote for PHP on simple things, like includes, and PHP is easier to find a host for (free ones too))

Use my wiki, and the links here for PHP and Python info.

I agree, CSS/HTML first. 

After that, try PHP, but keep eye on it: Python is universal language, **much** more useful than PHP is, also beyond web programming. 

If (and when) your PHP code grows beyond couple lines, switch to Python. Or if after learning HTML/CSS when you realize you want to do AJAX, go to Python directly (for backend, AJAX frontend is javascript, no relation to java :-) )

It will be pain at first (because you will have to have order where PHP let you mix all together), but you will be better off with Python in the long run.

---

### Post by LaRoza on 2007-09-21
> **pmasiar said:**
> I agree, CSS/HTML first. 

After that, try PHP, but keep eye on it: Python is universal language, **much** more useful than PHP is, also beyond web programming. 

If (and when) your PHP code grows beyond couple lines, switch to Python.

It will be pain at first (because you will have to have order where PHP let you mix all together), but you will be better off with Python in the long run.

PHP is not that bad, it can be used outside of the web, it can be used to make GUI apps, and it is fully OO, in PHP5. (Similar to Java, with some hints of Python)

You can code neat PHP, and there are MCV frameworks out there, if you write it it that way.

PHP is also easier to host, and find hosts for.

As much as I like Python, I have not found a reason to use it instead of PHP. I do not have your experience with large projects, which is where you seem to prefer Python, but for personal pages and small sites, I see no reason to use it.

---

### Post by Zdravko on 2007-09-21
I am good at XHTML:
> **W3Schools XHTML Quiz**

  **Result:**

19 of 20**95%**
You can be proud of yourself!
**Time Spent**
3:31


---

### Post by LaRoza on 2007-09-21
> **Zdravko said:**
> I am good at XHTML:

Take the quizes with a grain of salt, I scored 85% on the JavaScript one before I could write a useful script.

XHTML is easy to know, just a few rules (5) and the DTD. CSS is about just as easy, although for larger style sheets it can get tricky to make it look the same in all browsers.

Good luck studying, and if you need help, pm me, or post and I will do what I can to assist.

---

### Post by Zdravko on 2007-09-25
Can someone tell me how to make rounded edges, just like here in this forum? Notice how nice and fine are the outlines of the rectangles with shadows! I want it!
BTW, I don't think using tables will help much. Tables are for tabular data, not for content at all!

---

### Post by Compyx on 2007-09-25
> **Zdravko said:**
> Can someone tell me how to make rounded edges, just like here in this forum? Notice how nice and fine are the outlines of the rectangles with shadows! I want it!
BTW, I don't think using tables will help much. Tables are for tabular data, not for content at all!

Just look at the source of this page, you'll notice they've used tables and CSS (to stick little images in the corners) to create those effects.

---

### Post by Zdravko on 2007-09-26
Hmmm, images? That's stupid? Isn't there some other more elegant way to achieve the same effect?
BTW, how do I make such images?

---

### Post by LaRoza on 2007-09-26
> **Zdravko said:**
> Hmmm, images? That's stupid? Isn't there some other more elegant way to achieve the same effect?
BTW, how do I make such images?

How else would you do it? If you want a markup language that allows vector images, try SVG, very nice language.

Probably with transparent gifs.

---

### Post by Zdravko on 2007-09-26
I am just asking. I didn't understand the part with the transparent gifs.
Btw, I made a clearer vision of the structure of my web site.
On the left there will be a menu with several entries. Each entry corresponds to a page. The contents of each page should be dynamically loaded when the visitor chooses an entry.
I need to setup a database with a table. The table must contain the content of each page. Maybe an html-compliant text should do the work.

Next I need a very simple framework to login as admin of the site and to choose from a dropdown menu each of the fixed entries. Then the contents of the page will be displayed in a large edit box ready to edit. There must be a button Edit! below. Pressing it, will insert the text from the box in the appropriate row in the table.
Since my host has Python support, and ALL OF YOU SAY PYTHON IS GREAT, I want to use Python.
Now it is YOUR turn :)

---

### Post by LaRoza on 2007-09-26
> **Zdravko said:**
> I am just asking. I didn't understand the part with the transparent gifs.

Since my host has Python support, and ALL OF YOU SAY PYTHON IS GREAT, I want to use Python.


With the GIF format, you can make one colour transparent, giving the illusion the picture is not a rectangle.

That sounds like a wiki, you can use [www.pbwiki.com](www.pbwiki.com) for a simple solution.

My site: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

has a guest book that allows people to dynamically add to the page. It doesn't use a database though, it would be over kill.

PHP is great too, I use it over Python for web sites. (You'll see that my site is actually a single page, index.php, it is dynamically generated based on the links)

---

### Post by Zdravko on 2007-09-26
Hey, your site is great! I want my page to look in similar way. I noticed that the links from the menu contain a php variable. I want a similar approach but in Python.
Btw, again, you didn't explain HOW TO create these rounded edges.

---

### Post by LaRoza on 2007-09-26
I don't use images on my sites, and have no skills in graphics. I can resize and do simple things, though.

The variable is a "get" variable, not a php variable. When a forms method="get", it sends the form data in a query string in the url. The site is not completed (as you can tell)

You might want to find public domain images for your needs.

(I'll give you the code for my site, if you want.)

Maybe this will help: [http://www.princetonol.com/groups/iad/links/clipart.html](http://www.princetonol.com/groups/iad/links/clipart.html)

PHP will be easier to use, probably, for this.

---

### Post by Zdravko on 2007-09-26
Hey, I found a CSS tutorial for round corners WITHOUT images:
[http://www.html.it/articoli/nifty/index.html](http://www.html.it/articoli/nifty/index.html)

Do you think, it will work for me?

---

### Post by LaRoza on 2007-09-26
> **Zdravko said:**
> Hey, I found a CSS tutorial for round corners WITHOUT images:
[http://www.html.it/articoli/nifty/index.html](http://www.html.it/articoli/nifty/index.html)

Do you think, it will work for me?

I knew of such layouts, but make sure you test it in all browsers in all resolutions, as CSS hacks often act weird in other browsers.

For CSS, go to [www.cssforums.org](www.cssforums.org)

---

### Post by Zdravko on 2007-09-26
Okay okay :)

---

### Post by LaRoza on 2007-09-26
> **Zdravko said:**
> Okay okay :)

Darn it! You have me itching to do rounded corners on my site...

I will have to go home and add that :D

Be sure to let us know of your sites location so we can see. (If you are this far into learning, you certainly are motivated compared to those we see, expecting a miracle with no work, good job!)

---

### Post by Zdravko on 2007-09-26
My site will be located at crystal-clear.athertek.com
(the link is located at my homepage-section in my profile here).

---

### Post by LaRoza on 2007-09-26
You might want to stick a "Under Construction Page" named index.html, so we don't get a directory view.

---

### Post by pmasiar on 2007-09-26
> **LaRoza said:**
> How else would you do it? If you want a markup language that allows vector images, try SVG, very nice language.

Probably with transparent gifs.

I am no way expert in CSS, but our stylesheet has this "border: 1px solid #999999; -moz-border-radius: 10px;" attribute which makes nice round corners. 

Internet Exploder does not like it of course - anyone knows cross-platform way to do it in CSS?
Edit: looks like Zdravko found it! thanks, man!

---

### Post by LaRoza on 2007-09-26
> **pmasiar said:**
> I am no way expert in CSS, but our stylesheet has this "border: 1px solid #999999; -moz-border-radius: 10px;" attribute which makes nice round corners. 

Internet Exploder does not like it of course - anyone knows cross-platform way to do it in CSS?

[http://www.html.it/articoli/nifty/index.html](http://www.html.it/articoli/nifty/index.html)

moz means mozilla, it is specific to... well, I won't insult your intelligence.

---

### Post by dhtseany on 2007-09-26
In regards to what editor to use in Windows, start off with Notepad. When you start getting comfortable with what you're doing try out other applications designed specifically for "internet coding" like Frontpage, Dreamweaver, etc. Just remember to use a plain text editor. Apps like Wordpad and Microsoft Word or Work are not plain text editors.

Hope that helped.

Sean

---

### Post by mssever on 2007-09-27
For transparent images, consider PNG over GIF, as it's a much more flexible format. The only downside to transparent PNGs is that Microsoft couldn't be bothered to  provide proper alpha channel support for Internet Explorer 6 and lower (though there are hacks around the web). My attitude is that if Microsoft can't be bothered to write a decent browser, I can't be bothered to support their broken one.

---

### Post by pmasiar on 2007-09-27
> **dhtseany said:**
> In regards to what editor to use in Windows, start off with Notepad. 

There is NO reason to use sucky editor like notepad, when you can have very decent editor like SciTE for the same price, but with syntax highlighting, multi-files, block indent/dedent and other features needed for creating decent code. Really, there is NO excuse to use Notepad.

---

### Post by dhtseany on 2007-09-27
> **pmasiar said:**
> There is NO reason to use sucky editor like notepad, when you can have very decent editor like SciTE for the same price, but with syntax highlighting, multi-files, block indent/dedent and other features needed for creating decent code. Really, there is NO excuse to use Notepad.

Actually dude when your starting off notepad isn't all that bad. Very basic HTML doesn't require super high end crap to work. It'd be a good idea to start with the very basics first then move up in the world, otherwise people don't appreciate the better apps when they have them.

---

### Post by LaRoza on 2007-09-27
> **dhtseany said:**
> Actually dude when your starting off notepad isn't all that bad. Very basic HTML doesn't require super high end crap to work. It'd be a good idea to start with the very basics first then move up in the world, otherwise people don't appreciate the better apps when they have them.

Don't use notepad! There are better and simple text editors. Getting an editor with syntax highlighting is essential to programmers and coders of all kinds. My wiki links to get many, but Crimson Editor is what I use. Also good are notepad2 (which looks and handles like notepad, but has a few extra features), SciTE (mentioned above), Vim.

---

### Post by southernman on 2007-09-27
> **LaRoza said:**
> Don't use notepad! There are better and simple text editors. Getting an editor with syntax highlighting is essential to programmers and coders of all kinds. My wiki links to get many, but Crimson Editor is what I use. Also good are notepad2 (which looks and handles like notepad, but has a few extra features), SciTE (mentioned above), Vim.

Also worthy of a notable mention (IMO) is gedit, under Ubuntu/Gnome. I was astonished to realize it also has syntax highlighting.

edited - see after the fact we're discussing editors for a Windows environment... o_0

---

### Post by SuperDuck on 2007-09-27
I LOVE gedit.  I've tried a few different IDE's and always just say "screw it" and go back to gedit.  It's a great little program.

---

### Post by LaRoza on 2007-09-27
> **southernman said:**
> Also worthy of a notable mention (IMO) is gedit, under Ubuntu/Gnome. I was astonished to realize it also has syntax highlighting.

All Linux text editors have such features I noticed. Notepad is a MS program that is a relic, much like their edit.com, which is more useful than Notepad, because it is also a hex editor.

---

### Post by southernman on 2007-09-27
> **LaRoza said:**
> All Linux text editors have such features I noticed. IDK that. Today was not a waste, afterall! ;)


> **LaRoza said:**
> 
Notepad is a MS program that is a relic, much like their edit.com, which is more useful than Notepad, because it is also a hex editor.
It was my misfortune to skip "hand coding" after getting the basics from htmlgoodies and w3schools, and went straight to using dreamweaver.

hindsight always kicks ya in the rear! 

What little I dabble with coding now (xhtml) I won't go as far as using bluefish or the likes of it. Not that there is anything wrong with it.

---

### Post by LaRoza on 2007-09-27
I only use plain text editors, but notepad is quite a waste. I set the default to Crimson Editor when I set up a box for someone else.

WYSIWYG editors are not a good thing, I could never use one anyway, my sites are generated with a script, not statically written. What is the point of typing the same thing over again, when you can have the machine handle it?

---

### Post by ticopelp on 2007-10-09
If you're on Windows, NoteTab Pro is impossible to beat in my book. Tons of great utilities for coding, syntax highlighting, etc. Just a fantastic editor. I still miss it.

On Linux, I just use gedit.

---

### Post by Zdravko on 2007-10-09
> **ticopelp said:**
> If you're on Windows, NoteTab Pro is impossible to beat in my book. Tons of great utilities for coding, syntax highlighting, etc. Just a fantastic editor. I still miss it.

On Linux, I just use gedit.
Okay, I will give it a try.

---

### Post by MicahCarrick on 2007-10-09
As you work through books or tutorials on the web, it's important to know that there are a lot of conventions and standards which web developers try to adhere to. The web has come a long way in the last decade and many tutorials might not be using up-to-date code.

What you want to do, is check your work periodically to make sure it is correct. One of the best ways to learn to write standards-compliant code, is to write it wrong and then correct it. You can install the HTML Validator add-on for firefox which will show you which bits of your code is invalid when you view it in Firefox. You can then make the corrections in the source code and learn a little something along the way.

I have a couple articles that might help you get setup to test your web pages in Ubuntu (GNOME): _[Web Development in Linux (GNOME)]("http://www.micahcarrick.com/09-28-2007/web-development-linux.html")_ and _[Customizing Firefox for Web Development]("http://www.micahcarrick.com/09-28-2007/firefox-web-development.html")_

---

### Post by Can+~ on 2007-10-09
Okay, I skipped almost all the post, so I don't how much have you progressed; here is a summary of the most important things:

-Don't jump into CSS just yet, form a HTML Know how, and then use the power of CSS to eliminate redundant tasks.

-html declares things between tags, same as this forums, using bold needs [*b]word[*/b], needs a starting and ending point. (<strong>word</strong>). Except for images and other things: <img src="/imagelocation/image.jpg" />

-To declare a html all the document must start and end with <html>, have a body, and head section, so the most basic HTML page would be:

[HTML]
<html>
  <head><title>This is the text that appears on the title of the navigator</title></head>
  <body> Here is the page content</body>
  <!-- this is a comment :D, place them anywhere inside the html tags -->
</html>[/HTML]

-Later, each parameter can have individual properties and parameters:
[HTML]<thing property="parameters" property2="parameters"></thing>[/HTML]

For example:
[HTML]<body align="center"></body>[/HTML]
This will align the text to the center (Deprecated?)

-Colors: Colors are expressed in hexadecimal RGB; each #RRGGBB, meaning an hex between 00 and FF. How to count on Hex? as easy as:
00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f 10 11 12... 1f 20... ff.

[HTML]<body bgcolor="#CCCCCC"></body>[/HTML]
this will paint your background color with a grey-ish tone.

-Simple text modifiers: <strong>asdf</strong> for bold; <i>italic</i>, <u>underline</u>.

And there's a lot of things to learn; lists, tables, div, naming, css

---


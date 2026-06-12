---
title: "[SOLVED] [Web design]Correct way of doing things? (I'm outdated)"
date: 2008-11-21
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-21
Hello,
95% of my web design knowledge came from an easy class I took 5 years ago in HTML. It was a good class, but rather simple, and I've become aware of the fact that I'm completely out of date.

The main thing is that:
CSS wasn't covered. Or mentioned. Or thought about.

But now I guess the real way to do things is to make the "logic" of a page be HTML, and the style of it be CSS. So I'm going through my source, and fishing out all the HTML-ified style (the <FONT> tag comes to mind...)

Except I have two question:

[LIST]
[*]Will somebody come and hurt me if I use <CENTER>? I can't seem to find guidelines through Google, and can't decide if it counts as logic or not.
[*]I know I might get dirty looks, but will it be OK to style tables within their tag? I'm thinking about width and border and alignment and stuff.
[/LIST]
Thank you very much, and I apologize for my ignorance.

PS: I would like nothing more than to learn how to make pages in Python (since I know Python already) but installing Python on my server is a bit too complex, so I'm letting it chill a for a bit.)

---

### Post by Reiger on 2008-11-21
You'll find that people who complain about Font may go berserk over Center -- not to mention Blink. None of the latter two are even part of any HTML DTD to this day. (In simple English: in pure HTML neither Blink nor Center exists.)

So to make a long story short I would suggest you start by learning XHTML, pick up some CSS and then when you grasp both firmly enough move on to autmated XHTML+CSS.

---

### Post by fiddler616 on 2008-11-21
> **Reiger said:**
> You'll find that people who complain about Font may go berserk over Center -- not to mention Blink. None of the latter two are even part of any HTML DTD to this day. (In simple English: in pure HTML neither Blink nor Center exists.)
Forget standards, <BLINK> is just a terrible idea. Even worse than <MARQUEE>.
> 
So to make a long story short I would suggest you start by learning XHTML, pick up some CSS and then when you grasp both firmly enough move on to autmated XHTML+CSS.
I've got my hands pretty full with Python and C (and school(!)) right now, and the best time to pick up XHTML/CSS would probably be next summer. Will we be OK if I just use:
```
 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 3.2//EN">
<html>
<head>
<meta name="generator" content="HTML Tidy for Linux (vers 1 September 2005), see www.w3.org">
<title>HELLO</title>

<style type="text/css">
 div.c1 {text-align: center}
</style>
</head>
<body>
<div class="c1">Greetings</div>
Hey
</body>
</html>
```
instead of```

<HTML>
<HEAD>
<TITLE>
HELLO
</TITLE>
</HEAD>
<BODY>
<CENTER>
Greetings
</CENTER>
Hey
</BODY>
</HTML>
```
?
And I know the basics of font color, etc. in CSS.
(In case you were wondering how I suddenly came by the CSS center code, I got the idea of making very simple pages the way I would've thought they should've been done, and running them through Tidy HTML--a controlled experiment in CSS hacking.)

Thanks for your help.

---

### Post by Reiger on 2008-11-21
With the exception of some more "involved" cases, you should 'get away' with it -- but note that the Quirks in Quirksmode of browsers such as Firefox 3 and Opera 9.6 differs from their (major version) predecessors. Firefox 2 reanders Quirksmode HTML differently than Firefox 3; same with Opera 9.5 vs. Opera 9.6.

MSIE 6 & 7 show less noticeable incompatibilities when the Quirks are concerned but MSIE 7 and MSIE 6 differ (even more) significantly in support for CSS/Javascript.

Firefox 2, MSIE 6 are still very much *out there*; plenty of people who have to get by with Windows 2000 (Universities/Schools/Governments/Workplaces etc.) and who are locked out of MSIE 7 because of that.

---

### Post by fiddler616 on 2008-11-21
Well I got the entire thing through the W3C Validator, which is good enough for me.
I still need to fill in my CSS knowledge with theory though.

(In case you're interested: [http://experimental.tmac.andrewmin.com/indexcsstidy.html](http://experimental.tmac.andrewmin.com/indexcsstidy.html))

---

### Post by drubin on 2008-11-21
> **fiddler616 said:**
> 
[LIST]
[*]Will somebody come and hurt me if I use <CENTER>? I can't seem to find guidelines through Google, and can't decide if it counts as logic or not.
[*]I know I might get dirty looks, but will it be OK to style tables within their tag? I'm thinking about width and border and alignment and stuff.
[/LIST]
Thank you very much, and I apologize for my ignorance.

PS: I would like nothing more than to learn how to make pages in Python (since I know Python already) but installing Python on my server is a bit too complex, so I'm letting it chill a for a bit.)

No center tags allowed in xhtml. Also it will help you to google/read up on xhtml and not html. (Just the term change will help you to find more relavent information).

Is your server linux? I was under the assumption python came standard on all linux systems now. If it is not installed could you please pose the OS for interest.

---

### Post by Coreigh on 2008-11-21
> I know I might get dirty looks, but will it be OK to style tables within their tag? I'm thinking about width and border and alignment and stuff.

Tables? The people who give you dirty looks over styling tabels will be too busy berating you for *using* tables. Its a CSS world.

That said,... Do what you know and cover your butt by doing some verification viewing in other actual browsers. Use Linux Mac and Windows, Firefox on all three, IE in Win and Safari in Mac. That will cover 90% of the viewers.

But don't not learn CSS either. It is a very powerful and liberating tool when you know it well. A nice simple showcase is: [http://www.csszengarden.com/]("http://www.csszengarden.com/")

---

### Post by drubin on 2008-11-21
forgot to mention try to keep your css in separate files.

Nice link @ Coreigh

---

### Post by fiddler616 on 2008-11-22
> **drubin said:**
> No center tags allowed in xhtml. Also it will help you to google/read up on xhtml and not html. (Just the term change will help you to find more relavent information).Good call. 
> 
Is your server linux? I was under the assumption python came standard on all linux systems now. If it is not installed could you please pose the OS for interest.
Yes, it's Linux, and in theory it supports Python. The thing is, I'm not the head honcho of it--I'm being lent a subdomain by a friend, and the installation process for Python is more complex than it has any right to be, and I feel bad making him to do it--especially since I haven't learned how to do webpages in Python. I've just made a free page at...er...HelioHost (which supports Python) to learn with though.
[QUOTE=coreigh]
	 	 Tables? The people who give you dirty looks over styling tabels will be too busy berating you for *using* tables. Its a CSS world.[/QUOTE] Meh. Darnit.
> 
That said,... Do what you know and cover your butt by doing some verification viewing in other actual browsers. Use Linux Mac and Windows, Firefox on all three, IE in Win and Safari in Mac. That will cover 90% of the viewers.
This is where [Browsershots]("http://browsershots.org/") comes in.
[QUOTE=drubin] 			 		   		 		 		forgot to mention try to keep your css in separate files.
[/QUOTE]
OK (starts Googling)
-------
Thanks, everyone!

---

### Post by wil on 2008-11-22
I suggest that you get the [Firebug]("http://getfirebug.com/") plugin for Firefox, it is a great help to me. It also has a handy "cleanup the page" utility.

---

### Post by noerrorsfound on 2008-11-22
Centering in XHTML can be done using <div align="center"> if you absolutely can't use CSS.

---

### Post by fiddler616 on 2008-11-22
> **noerrorsfound said:**
> Centering in XHTML can be done using <div align="center"> if you absolutely can't use CSS.
Thanks, but so far I seem to be managing with inline CSS. I make no boasts about the quality of the CSS, but at least it's there...

---

### Post by tuskenraider on 2008-11-22
2 things...  Komposer and Firebug  

html by hand??? wat? people actually know how to do that?? LOL ive been using frontpage and komposer for ages.. id be lost in straight HTML...

Enjoy

Tusken - i cant code my way out of a paper bag- raider :lolflag:

---

### Post by fiddler616 on 2008-11-22
> **tuskenraider said:**
> 2 things...  Komposer and Firebug  

html by hand??? wat? people actually know how to do that?? LOL ive been using frontpage and komposer for ages.. id be lost in straight HTML...

Enjoy

Tusken - i cant code my way out of a paper bag- raider :lolflag:
That just doesn't seem very proper to me...I dunno...

---

### Post by theApokalypsis on 2008-11-22
I myself love getting lost in html ::lolflag:

---

### Post by drubin on 2008-11-22
> **tuskenraider said:**
> 2 things...  Komposer and Firebug  

html by hand??? wat? people actually know how to do that?? LOL ive been using frontpage and komposer for ages.. id be lost in straight HTML...

Enjoy

Tusken - i cant code my way out of a paper bag- raider :lolflag:

For learning starting to use a GUI wysiwig editor is just plain bad. (No learning will ever be done). For more advanced people using a wysiwig would be like taking their skills and down grading them to suite the editor.

Never start any project the simple drag and drop way.

---


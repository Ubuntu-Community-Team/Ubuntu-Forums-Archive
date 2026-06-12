---
title: "W3C Validation Problem"
date: 2008-07-04
forum: Programming Talk
---

### Post by JohnSearle on 2008-07-04
Hey,

Not sure if (X)HTML is discussed much in this section, but I'm having a bit of an issue with it.

I've cleared up all the errors except for the following:

> Line 5, Column 6: end tag for "HEAD" which is not finished.

</head>

Most likely, you nested tags and closed them in the wrong order. For example <p><em>...</p> is not acceptable, as <em> must be closed before <p>. Acceptable nesting is: <p><em>...</em></p>

Another possibility is that you used an element which requires a child element that you did not include. Hence the parent element is "not finished", not complete. For instance, in HTML the <head> element must contain a <title> child element, lists (ul, ol, dl) require list items (li, or dt, dd), and so on.


My header is as follows:

> <head>

<link rel="stylesheet" type="text/css" href="external.css">

</head>

I've tried to put in a / at the end of the link, but that only gives me an additional error. The only other thing I can think of is that there is a problem with my CSS, which is giving me the error in my header.

Any thoughts would be appreciated.

- John

---

### Post by henchman on 2008-07-04
which [doctype]("http://www.w3schools.com/tags/tag_DOCTYPE.asp") do you have?

could you please supply us with the whole document from the beginning to the <body> or </head> tag?

---

### Post by JohnSearle on 2008-07-04
> **henchman said:**
> which [doctype]("http://www.w3schools.com/tags/tag_DOCTYPE.asp") do you have?

could you please supply us with the whole document from the beginning to the <body> or </head> tag?

Sure.

> <!DOCTYPE HTML PUBLIC  "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<link rel="stylesheet" type="text/css" href="external.css">
</head>
<body>


Thanks for the help!

- John

---

### Post by henchman on 2008-07-04
ah.. nasty :(

you omitted the title tag... which apparently is not legal :)

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
       "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<link rel="stylesheet" type="text/css" href="external.css">
<title>foobar</title>
</head>
<body>

</body>
</html>

```

this validates

edit: you don't have to put the '/' at the end of link, because this would be xhtml-standart conformant but not html.

---

### Post by JohnSearle on 2008-07-04
> **henchman said:**
> ah.. nasty :(

you omitted the title tag... which apparently is not legal :)

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
       "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<link rel="stylesheet" type="text/css" href="external.css">
<title>foobar</title>
</head>
<body>

</body>
</html>

```

this validates

edit: you don't have to put the '/' at the end of link, because this would be xhtml-standart conformant but not html.

That is awesome, thanks. You just saved me a headache.

It's odd that the error doesn't correspond to the actual issue. You'd figure it would be an easy one for their system to point out.

- John

---

### Post by Mickeysofine1972 on 2008-07-04
That doc type needs a <TITLE></TITLE> in the header, that should satify the validator

```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<HTML>
<HEAD>
<TITLE>Mooo</TITLE>
</HEAD>
<BODY> 
<p>A rooster says.....</p>
</BODY>
</HTML>
```

Mike

---

### Post by LaRoza on 2008-07-04
In addition to what the others said, please put code in [noparse]```

```, [php][/php] or [html][/html] tags.[/noparse]

(Quotes aren't...quotable)
[html]

<head>
<!--In addition to the other requirements, put the <link /> element like this. Remember, that space is very important!-->
<link rel="stylesheet" type="text/css" href="external.css" />

</head>
[/html]

---

### Post by JohnSearle on 2008-07-04
> **LaRoza said:**
> In addition to what the others said, please put code in [noparse]```

```, [php][/php] or [html][/html] tags.[/noparse]

(Quotes aren't...quotable)
[html]

<head>
<!--In addition to the other requirements, put the <link /> element like this. Remember, that space is very important!-->
<link rel="stylesheet" type="text/css" href="external.css" />

</head>
[/html]

Didn't know there were tags for that. I'll keep it in mind for the future.

- John

---

### Post by mssever on 2008-07-04
> **LaRoza said:**
> [html] <!--In addition to the other requirements, put the <link /> element like this. Remember, that space is very important!-->
<link rel="stylesheet" type="text/css" href="external.css" />[/html]
Note that closing the link tag is XHTML, not HTML 4.01 Transitional, like the OP is using. However, I would argue that because XHTML is a cleaner standard, the OP should be using it instead, if at all possible. Standard HTML is a mess to parse, and XHTML fixes some of those problems.

---

### Post by elithrar on 2008-07-04
> **mssever said:**
> Note that closing the link tag is XHTML, not HTML 4.01 Transitional, like the OP is using. However, I would argue that because XHTML is a cleaner standard, the OP should be using it instead, if at all possible. Standard HTML is a mess to parse, and XHTML fixes some of those problems.

He would have to serve his content as [FONT="Courier New"]application/xhtml+xml[/FONT], a MIME type that IE browsers cannot handle (and will attempt to download to disk instead) for it to be proper XHTML. If you're using XHTML tags & a DOCTYPE but serving as [FONT="Courier New"]text/html[/FONT] then it's just malformed HTML that you're serving - which defies the point.

I won't start too much of a HTML vs. XHTML war, but look [here](http://webkit.org/blog/68/understanding-html-xml-and-xhtml/) & [here](http://www.b-list.org/weblog/2008/jun/21/xhtml/) for further clarification.

---

### Post by LaRoza on 2008-07-05
> **elithrar said:**
> He would have to serve his content as [FONT="Courier New"]application/xhtml+xml[/FONT], a MIME type that IE browsers cannot handle (and will attempt to download to disk instead) for it to be proper XHTML. If you're using XHTML tags & a DOCTYPE but serving as [FONT="Courier New"]text/html[/FONT] then it's just malformed HTML that you're serving - which defies the point.


The server will send it with a MIME type of text/html, and the code can be proper XHTML to be used that way. Check out my home page (in sig). It is all XHTML 1.1 (like XHTML 1.0 Strict), and loads in all browsers. Changing its MIME type to the proper one generates problems in legacy browsers (including IE7).

---

### Post by elithrar on 2008-07-06
> **LaRoza said:**
> The server will send it with a MIME type of text/html, and the code can be proper XHTML to be used that way. Check out my home page (in sig). It is all XHTML 1.1 (like XHTML 1.0 Strict), and loads in all browsers. Changing its MIME type to the proper one generates problems in legacy browsers (including IE7).

Your markup may be XHTML, but your page is not being rendered or handled as XHTML. Having the XHTML 1.1 DOCTYPE doesn't determine how a browser will render a page - DOCTYPE's don't influence this. The MIME type does however - and not having it as [FONT="Courier New"]application/xhtml+xml[/FONT] means that again, it's just malformed HTML when it comes to rendering the page.

You would be better off writing your page up in HTML 4 if you're going to serve it as [FONT="Courier New"]text/html[/FONT].

---

### Post by LaRoza on 2008-07-06
> **elithrar said:**
> Your markup may be XHTML, but your page is not being rendered or handled as XHTML. Having the XHTML 1.1 DOCTYPE doesn't determine how a browser will render a page - DOCTYPE's don't influence this. The MIME type does however - and not having it as [FONT="Courier New"]application/xhtml+xml[/FONT] means that again, it's just malformed HTML when it comes to rendering the page.


Using the web developer toolbar, I found that Fx 3 renders my page in standard compliance mode and recognizes it as XHTML 1.1 (see meta).

> 
You would be better off writing your page up in HTML 4 if you're going to serve it as [FONT="Courier New"]text/html[/FONT].

I would be better off? In what way? What would be the advantage? Right now, compliant browsers recognize it as XHTML 1.1, non compliant browsers treat it like HTML, and W3C says it is valid with a warning that the MIME type is not right.

Serving it as application/xhtml+xml, like I did in the past, had everything the same, except it didn't have that warning, plus it didn't work in non standard complaint browsers.

What would be the advantage to using less effective legacy code?

---

### Post by elithrar on 2008-07-06
> **LaRoza said:**
> 
What would be the advantage to using less effective legacy code?

How is HTML 4 "less effective" than XHTML 1.1? I don't even see how's it legacy, as the HTML 5 specification isn't completed yet. My point still stands re: the content type - you're still serving HTML pages. If you consider writing XHTML a neccessity, you should be serving [FONT="Courier New"]text/html[/FONT] to IE browsers & [FONT="Courier New"]application/xhtml+xml[/FONT] to capable browsers.

---

### Post by LaRoza on 2008-07-06
> **elithrar said:**
> How is HTML 4 "less effective" than XHTML 1.1? I don't even see how's it legacy, as the HTML 5 specification isn't completed yet.

That doesn't matter ;)

> 
 My point still stands re: the content type - you're still serving HTML pages. If you consider writing XHTML a neccessity, you **should be serving** [FONT="Courier New"]text/html[/FONT] to IE browsers & [FONT="Courier New"]application/xhtml+xml[/FONT] to capable browsers.
Why should I? You didn't answer that. It has no bearing on how the page is interpreted by capable browsers, and it is flexible.

---

### Post by elithrar on 2008-07-06
> **LaRoza said:**
> 
Why should I? You didn't answer that. It has no bearing on how the page is interpreted by capable browsers, and it is flexible.

"Capable" browsers will use HTML parsers to render the page if it's served as text/html - not XML parsers. 

> 
That doesn't matter.


I'd be interested to know why it doesn't matter - or rather, why you believe XHTML is better suited for your needs vs. HTML 4/5? I'd rather get some justified & detailed arguments for-and-against about *something* on this forum.

---

### Post by henchman on 2008-07-06
> **elithrar said:**
> "Capable" browsers will use HTML parsers to render the page if it's served as text/html - not XML parsers. 
 so they completely ignore the doctype?



> **elithrar said:**
> 
I'd be interested to know why it doesn't matter - or rather, why you believe XHTML is better suited for your needs vs. HTML 4/5? I'd rather get some justified & detailed arguments for-and-against about *something* on this forum.

well as html 5 isn't finished and will be a competitor to xhtml 2, everybody can choose his favorite, eh? but xhtml 1.1 is the newest, so why shouldn't one use this instead of html 4?

---

### Post by LaRoza on 2008-07-06
> **elithrar said:**
> "Capable" browsers will use HTML parsers to render the page if it's served as text/html - not XML parsers. 
But if it is valid code, it still renders as it should.

> 
I'd be interested to know why it doesn't matter - or rather, why you believe XHTML is better suited for your needs vs. HTML 4/5? I'd rather get some justified & detailed arguments for-and-against about *something* on this forum.

Because I use the DOM extensively in my ECMAScripts and the DOM only exists for XML syntax.

---

### Post by elithrar on 2008-07-06
> **LaRoza said:**
> But if it is valid code, it still renders as it should.

Oh, it "renders" fine - but it's just not rendering as XHTML :o)

> 
Because I use the DOM extensively in my ECMAScripts and the DOM only exists for XML syntax.

That I can understand, then. 

> **henchman said:**
> so they completely ignore the doctype?


Yep. DOCTYPE's don't mean a thing in the rendering/content serving world.

---

### Post by LaRoza on 2008-07-06
> **elithrar said:**
> Oh, it "renders" fine - but it's just not rendering as XHTML :o)

According to Fx, it is.

---

### Post by henchman on 2008-07-06
So this is wrong?

[QUOTE=http://www.w3.org/QA/Tips/Doctype]Tools which process HTML documents, such as Web browsers, need to know which DTD an (X)HTML document is actually using: this is why each (X)HTML document needs, at the beginning, a DTD declaration, such as:[/QUOTE]

I mean i understand that it has nothing to do with mimetypes, but the browser doesn't use it for rendering the website?

---

### Post by scragar on 2008-07-06
the DTD is supposed to let the browsers know what version of a technology it's using(so HTML3 or HTML4, HTML4 or 4.01, XHTML1.0 or 1.1, BUT NOT HTML or XHTML), but because of IEs terrible XHTML support when served correctly most of the browsers have taken to simply assuming that the XHTML doctype means it should have been served as XHTML but wasn't to save IE complaining(IE6 has partital XHTML support using a plugin, addmitedly, it just rendered it as HTML instead of XHTML, but atleast it didn't offer to download it).
According to the standards you should serve XHTML as application/xml or application/xhtml+xml , HOWEVER serving it as text/html won't cause any hard for the time being, other than further supporting IEs lack of any real XHTML support, but why would anyone care about that when IE have been making up their own alternatives to the standards for years?

---

### Post by henchman on 2008-07-06
ok, now makes sense to my simple mind/brain :) thanks

---


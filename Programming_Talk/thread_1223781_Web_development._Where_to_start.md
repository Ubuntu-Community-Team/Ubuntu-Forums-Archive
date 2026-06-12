---
title: "Web development. Where to start?"
date: 2009-07-26
forum: Programming Talk
---

### Post by kian.tern on 2009-07-26
Hi all.

I'm planing to dive deep into web site/application development.
But with the vast amount of technologies available I'm really lost.

Currently I develop command line utilities in Perl and Python with a bit of pyGtk(mostly text processing and scientific data analysis). 
I did a Perl/CGI based web site a while ago, but it's really simple and as I look at the code now, ugly and unmanageable.

I want to acquire enough base knowledge so I can start developing and exploring stuff on my own.
I was wondering what would be a good place to start?
I'll be glad to see book suggestions and/or web site links.

Thanks in advance.

---

### Post by gjoellee on 2009-07-26
[http://w3schools.com/](http://w3schools.com/)

Be sure to learn HTML, CSS. When you have learned the basics there, start learning XHTML. After that you should learn PHP.

---

### Post by kian.tern on 2009-07-26
Thanks for the quick answer, but I wonder JS seems to be the core of the most web sites today, should I learn it before/after/at all?

---

### Post by CptPicard on 2009-07-26
I see no reason why you wouldn't continue using Python if you already know it. Django is a very nice framework. And yes, Javascript is important on the client side.

---

### Post by kian.tern on 2009-07-26
Django is nice indeed, but I think it's important to understand how everything works before you start using "lego" style frameworks.

---

### Post by CptPicard on 2009-07-26
What do you mean? You want to be using a correct architecture anyway, writing some messy PHP embedded into your HTML is not going to teach you anything (which I would consider probably the antithesis of what I'm suggesting).

And Django ought to give you all the HTTP request/response handling you could want should you want it...

---

### Post by hessiess on 2009-07-26
PHP is verry low level compaired to the frameworks avalable for outher languages, and itself. If you are not verry cairful it is extreamly easey to produce messy, unmaintanable code.

---

### Post by kian.tern on 2009-07-26
Well I don't how to describe it, but I'm sort of a "low level" freak.
I can't use something unless I have at least some basic understanding how it works.
For example when I started to work with pyGtk I actually went and read tons of documentation how X server works, figured out how to create a toolkit(theoretical knowledge off course).

---

### Post by kian.tern on 2009-07-26
hessiess, It's fine I have enought experience with messy code in Perl =)

---

### Post by dlmarti on 2009-07-26
> **kian.tern said:**
> Thanks for the quick answer, but I wonder JS seems to be the core of the most web sites today, should I learn it before/after/at all?

JS does all (most) of the neat-o features, but you still need to have the basics first, otherwise you will be lost.

---

### Post by kapi on 2009-07-26
Hi there, don't know if this will help in anyway but I would suggest [http://www.w3schools.com](http://www.w3schools.com) as a good starting point. The tutorials are great and a good back up to any books that you may have.

Just get the basics of xhtml, css and javascript to get you going then try a server side scripting language like php or pearl.

It all depends on what it is you want to achieve with your web site. 

for development I kind of move between geany and aptana depending on what I'm doing.

Like I said if this helps then I'm happy to be of some assistance, if not well thats ok too.

---

### Post by CptPicard on 2009-07-26
> **kian.tern said:**
> Well I don't how to describe it, but I'm sort of a "low level" freak. I can't use something unless I have at least some basic understanding how it works.

I guess if there really *was* anything of interest to actually learn there and Django hid it, I might understand this... but in the case of a web app, you're just writing an outright bad application if you insist on doing some archaic CGI-like stuff. (Mind you, PHP as a language is not "blessed" in terms of being any kind of a "low level", it's just that most crappy web apps seem to be written in PHP)...

I mean, it really is trivial. Request comes in, parameters are processed, controller is selected, code is executed, execution is passed to appropriate template that gets filled in and sent to the client. That's "how it works" in a proper web app. ;)

---

### Post by hessiess on 2009-07-26
> **kian.tern said:**
> Thanks for the quick answer, but I wonder JS seems to be the core of the most web sites today, should I learn it before/after/at all?

You need to understand the difference between server side and client side scripting. You can choose the server environment which your server side code is running on, but you cannot control what features users choose to disable/are not able to use due to being deaf, partly sighted etc.

Client side scripting should be used to extend functionality and NEVER for adding content. Which may make the site unusable for people with disability's, and makes the content COMPLETELY invisible to search engines.

> 
Well I don't how to describe it, but I'm sort of a "low level" freak. I can't use something unless I have at least some basic understanding how it works.


I use to be like that and attempted to write a CMS using the messy code isilanding and in-lining html using string concatenation, The result? a unmaintainable mess. I re-wrote the whole thing using the MVC application structure. It is still raw PHP (no framework) but at least its actually maintainable now. If I had used a higher level framework it wouldn't have taken anywhere near as long to implement.

---

### Post by kian.tern on 2009-07-26
hessiess, thanks for the tip, this will be very helpfull, as I never had to consider accessibility issues before.

---

### Post by kian.tern on 2009-07-26
> **hessiess said:**
> 
I use to be like that and attempted to write a CMS using the messy code isilanding and in-lining html using string concatenation, The result? a unmaintainable mess. I re-wrote the whole thing using the MVC application structure. It is still raw PHP (no framework) but at least its actually maintainable now. If I had used a higher level framework it wouldn't have taken anywhere near as long to implement.

This is basically what happened with my Perl/CGI site.
But still I believe until you messed up everything, and had to fix it, you'll never learn :D

---

### Post by CptPicard on 2009-07-26
Well, you *can* always start by using mod_python and just write to the response stream if that really is what you want... :)

---

### Post by Mirge on 2009-07-26
PHP is a fantastic language for writing web applications, imo. Code can be sloppy in any language if you are determined to make it sloppy.

Yes, there are numerous web applications written in PHP that use insecure, frowned upon, sloppy code and techniques I'm sure. Doesn't mean the language is bad, means the programmer(s) using the language need to improve.

---

### Post by v8YKxgHe on 2009-07-27
Can people please stop telling others to use XHTML? Use HTML unless you know what you're doing, and most that use XHTML do not. You do more damage using XHTML.

To the OP: Start with either Python or PHP (take advantage of 5.2+ features and you'll be good).

---

### Post by AJB2K3 on 2009-07-27
> **AlexC_ said:**
> Can people please stop telling others to use XHTML? Use HTML unless you know what you're doing, and most that use XHTML do not. You do more damage using XHTML.


Bull, XHTML = Clean code and easy bug fixing.
But anyway XHTML is out the window soon as all the XHTML is going back into html to make HTML 5
HTML is filthy and allows slopping unmanageable code.

---

### Post by v8YKxgHe on 2009-07-27
> **AJB2K3 said:**
> Bull, XHTML = Clean code and easy bug fixing.
But anyway XHTML is out the window soon as all the XHTML is going back into html to make HTML 5
HTML is filthy and allows slopping unmanageable code.

Show me some XHTML code you consider clean and easy bug fixing. I can pretty much guarantee you're not using XHTML even if you think you are. Many many many people just use XHTML because it's the 'latest cool' thing to use, but yet send it to the browser as 'text/html' - which means you're actually sending broken HTML to the browser to parse.

Set your XHTML document to be proper XHTML and you'll most likely get parse errors/not display the same (read, broken) as it did before.

Edit: Granted there are people that use XHTML like it is suppose to be used, and you may be one of them - my points are aimed at the general people who use XHTML without knowing.

---

### Post by sloggerkhan on 2009-07-27
I say go with Django, Apache-modWSGI, CSS/HTML, and jquery javascript library and you're good for anything. Maybe for some projects you might needs some more (say, for example, google maps' API, or something), but in general you can do most anything without a huge ammount of annoyances or trouble using those 4 tools.

---

### Post by Bios Element on 2009-07-27
> **sloggerkhan said:**
> I say go with Django, Apache-modWSGI, CSS/HTML, and jquery javascript library and you're good for anything. Maybe for some projects you might needs some more (say, for example, google maps' API, or something), but in general you can do most anything without a huge ammount of annoyances or trouble using those 4 tools.

I hate to start framework wars here but SourceForge did a ton of testing with Django when they were updating their site and Django scaled horribly without multi-database support.

---

### Post by hessiess on 2009-07-27
> **AlexC_ said:**
> Show me some XHTML code you consider clean and easy bug fixing. I can pretty much guarantee you're not using XHTML even if you think you are. Many many many people just use XHTML because it's the 'latest cool' thing to use, but yet send it to the browser as 'text/html' - which means you're actually sending broken HTML to the browser to parse.

Set your XHTML document to be proper XHTML and you'll most likely get parse errors/not display the same (read, broken) as it did before.

Edit: Granted there are people that use XHTML like it is suppose to be used, and you may be one of them - my points are aimed at the general people who use XHTML without knowing.

Every website that I have created always uses the xhtml strict, with absolutely no in lined formatting tags/ or CSS, for example:

[http://validator.w3.org/check?uri=www.hessiess.com&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=www.hessiess.com&charset=%28detect+automatically%29&doctype=Inline&group=0)

The quad-ren website has a few errors, but this is still running on the old, messy, unmaintainable version of my CMS, I have a completely rewritten version almost redy to go up, but real live keeps getting in the way;)

Please stop badmouthing XHTML, it just makes you look inexperienced. XHTML is exactly the same as HTML, with all the formatting tags abstracted away into CSS, and a stricter syntax to make errors easier to detect. I guess that you probably don't know CSS, so need all of the legacy formatting tags, and you are pushing your own experiences onto other people?

---

### Post by sloggerkhan on 2009-07-28
> **Bios Element said:**
> I hate to start framework wars here but SourceForge did a ton of testing with Django when they were updating their site and Django scaled horribly without multi-database support.

...And this matters because someone teaching themselves to make an interactive database driven website needs sourceforge-scale levels of performance and infrastructure? 

Anyhow, I also think the point of Django isn't so much to be high-performance as it is to make for speedy, stable, extendable development cycles and make for easier maintenance and improvements.

To browse some django sites, maybe look at:
[http://www.djangosites.org/most-comments/?page=6](http://www.djangosites.org/most-comments/?page=6)

---

### Post by v8YKxgHe on 2009-07-28
removed

---

### Post by cdiem on 2009-07-28
View Post
@ AlexC_ Looking here: [http://www.w3.org/TR/xhtml-media-types/](http://www.w3.org/TR/xhtml-media-types/) and here: [http://hixie.ch/advocacy/xhtml](http://hixie.ch/advocacy/xhtml) I think you're right about the xhtml. However, being new in this stuff, I could not understand when is it better to use xhtml, and when - plain hmtl. When would it be preferable to use xhtml? Thank you in advance.

---

### Post by v8YKxgHe on 2009-07-28
> **cdiem said:**
> @ AlexC_ Looking here: [http://www.w3.org/TR/xhtml-media-types/](http://www.w3.org/TR/xhtml-media-types/) and here: [http://hixie.ch/advocacy/xhtml](http://hixie.ch/advocacy/xhtml) I think you're right about the xhtml. However, being new in this stuff, I could not understand when is it better to use xhtml, and when - plain hmtl. When would it be preferable to use xhtml? Thank you in advance.

To be honest, there is very little times when you'd want to use XHTML over HTML4/5 - it offers no benefits really. I'd always advise HTML 4.01 strict and CSS, tis all you need.

---

### Post by cdiem on 2009-07-28
Thanks, using html seems fair to me.

---

### Post by AJB2K3 on 2009-07-28
> **AlexC_ said:**
> Show me some XHTML code you consider clean and easy bug fixing. I can pretty much guarantee you're not using XHTML even if you think you are. Many many many people just use XHTML because it's the 'latest cool' thing to use, but yet send it to the browser as 'text/html' - which means you're actually sending broken HTML to the browser to parse.

Set your XHTML document to be proper XHTML and you'll most likely get parse errors/not display the same (read, broken) as it did before.

Edit: Granted there are people that use XHTML like it is suppose to be used, and you may be one of them - my points are aimed at the general people who use XHTML without knowing.

I see your challange (because I feel like being a pain) [http://www.s284317130.websitehome.co.uk/]("http://www.s284317130.websitehome.co.uk/") This (graphically challanged) site took 4 months to get it to XHTML STRICT.

Sorry for coming over so harsh.

IMHO XHTML was a great idea to solve the great grammer issue of html ie
<h2><b>Sometext</h2></b>
XHTML stoped the incorrect placing of closing tags (</h2> and </b> are the wrong way around) and forced everything to be in lower case which helped to solve more web coding issues.

---

### Post by Maheriano on 2009-07-28
I run a web development business at home and have more work than I can even handle right now. And I don't even build many custom applications, most is open source software that I install and configure. Most clients are looking for cheap solutions that work and the best bang for the buck is to use open source. If they want a blog, install Wordpress. If they want a content management system, install Joomla. If they want a photo gallery, install Gallery2. If they want a forum, install PHPBB3.

So if I were you, I'd get some hosting space and install the following and play around with them to see how they work.
- Joomla / Drupal
- PHPBB3
- Wordpress
- Gallery2

Then look at the bridge software that connects them, you can install Wordpress, then Gallery2, and then use WPG2 (custom bridge) to embed the photo gallery into the Wordpress site as if it was all the one site. And it modifies the database to give you one user login to both systems.

Once you have that down, you can look into the PHP and CSS of the site and start installing templates and modifying the PHP/CSS to your liking.

---

### Post by Reiger on 2009-07-28
> **AlexC_ said:**
> I hate to tell you, but you're not using XHTML - you're sending that document as text/html (See the meta tag, or any Content-Type headers your PHP is setting) - which is **NOT** XHTML. The mime type for XHTML should be application/xhtml+xml

Try sending that thing as real XHTML and things will break. At the moment you are sending broken HTML to the browser, tag soup which it has to clean up.

XHMTL does have its uses. In particular it is useful for embedding other types of documents (SVG/MathML) in the same document (XML namespaces are useful) as well as automatically generated documents from XML sources.

> 
Considering I've been doing web development for years and am a full time web developer, inexperience is the last thing on my mind ;). Only a fool would attempt to discuss such issue without knowing the facts and technologies surrounding it. So yes, I do know CSS. [http://tangocms.org](http://tangocms.org) and [http://3dteapot.co.uk](http://3dteapot.co.uk) are just 2 sites that show my 'inexperience'.

Edit: To prove what I am getting at, in your PHP code add this at the top somewhere:
```
header( 'Content-Type: application/xhtml+xml; charset=utf-8' );
```
Sit and watch the parse errors come in. Like I said, you're not using XHTML.

Please note that if someone has written a "valid" (not necessarily correct) XHMTL document this "impending doom" is irrelevant. Parsing or other errors are caught by a validating parser; and the only way to know whether or not your document is valid is by subjecting it to such a parser and having it come out clean. A priori, the premise of a "valid" XHTML document implies it will come out clean when subject to a validating parser -- meaning that if the document renders correctly when served as HTML it must also render correctly when served as XHTML. Please note that "render correctly" isn't the same as "render as intended" because the author may have added style rules which covered up for things that look like glitches when served as HTML but do not exist when served as XHTML...

You are correct, though, that unless served as XHTML the caption "valid XHTML" is quite meaningless.

---

### Post by v8YKxgHe on 2009-07-28
> **AJB2K3 said:**
> I see your challange (because I feel like being a pain) [http://www.s284317130.websitehome.co.uk/]("http://www.s284317130.websitehome.co.uk/") This (graphically challanged) site took 4 months to get it to XHTML STRICT.

Sorry for coming over so harsh.

IMHO XHTML was a great idea to solve the great grammer issue of html ie
<h2><b>Sometext</h2></b>
XHTML stoped the incorrect placing of closing tags (</h2> and </b> are the wrong way around) and forced everything to be in lower case which helped to solve more web coding issues.

Ah not a pain at all =). Though that site (I assume is yours?) is not using XHTML, just like hessiess. See this is why I tell people not to use XHTML, because they never use it even if they think they are.

You're sending that document as text/html - not application/xhtml+xml. Again, if you set this to be proper XHTML you get parse errors in your document because of XML errors.

---

### Post by v8YKxgHe on 2009-07-28
> **Reiger said:**
> 
Please note that if someone has written a "valid" (not necessarily correct) XHMTL document this "impending doom" is irrelevant. Parsing or other errors are caught by a validating parser; and the only way to know whether or not your document is valid is by subjecting it to such a parser and having it come out clean. A priori, the premise of a "valid" XHTML document implies it will come out clean when subject to a validating parser -- meaning that if the document renders correctly when served as HTML it must also render correctly when served as XHTML. Please note that "render correctly" isn't the same as "render as intended" because the author may have added style rules which covered up for things that look like glitches when served as HTML but do not exist when served as XHTML...


But it's not valid. I can create a valid HTML document and attempt to send that as image/png - it's a valid HTML document, but not a valid PNG file. That is essentially what people do when using XHTML, they send it as something different (granted, image/png is a extreme example there).

By sending XHTML as text/html you're relying on undocumented, inconsistency behaviour of the renderer to 'fix' your broken HTML (since XHTML sent as HTML is broken tag soup). So by doing this you're making life harder for your self to create a consistent web page over multiple browsers.

> XHMTL does have its uses. In particular it is useful for embedding other types of documents (SVG/MathML) in the same document (XML namespaces are useful) as well as automatically generated documents from XML sources.

Of course, this I do not deny - XHTML has its place and when used correctly it is good. Common use of XHTML is just broken, though, which annoys me when people tell new people to use XHTML, with no idea of what XHTML actually *is*.

---

### Post by AJB2K3 on 2009-07-28
> **AlexC_ said:**
> Ah not a pain at all =). Though that site (I assume is yours?) is not using XHTML, just like hessiess. See this is why I tell people not to use XHTML, because they never use it even if they think they are.

You're sending that document as text/html - not application/xhtml+xml. Again, if you set this to be proper XHTML you get parse errors in your document because of XML errors.
Hu you what?
XHTML is plain text and Xhtml is html+xml?

If it looks like a rose and smells like a rose it is a rose !

Why is it not Xhtml?
It uses the Xhtml decleration, Written in XHTML and valadites as XHTML so I don't understand why you say its no Xhtml?

---

### Post by v8YKxgHe on 2009-07-28
> **AJB2K3 said:**
> Hu you what?
XHTML is plain text and Xhtml is html+xml?

If it looks like a rose and smells like a rose it is a rose !

Why is it not Xhtml?
It uses the Xhtml decleration, Written in XHTML and valadites as XHTML so I don't understand why you say its no Xhtml?

Sure you're physically typing XHTML, but when you're giving it to the browser you're saying 'here, have this lovely HTML document'. It doesn't matter that you're using XHTML, the browser doesn't know or care.

See for your self:
```
$ curl -I http://www.s284317130.websitehome.co.uk/
HTTP/1.1 200 OK
Date: Tue, 28 Jul 2009 18:08:43 GMT
Server: Apache
Last-Modified: Mon, 11 May 2009 17:43:13 GMT
ETag: "2001da21-f4c-4a0863b1"
Accept-Ranges: bytes
Content-Length: 3916
Content-Type: text/html
```

Look at the last Content-Type header, it's HTML. Now, if you add that previous PHP code I mentioned to set the Content-Type header to XHTML your document will not even parse - since it as many XML errors, which is good because it now means you're using XHTML and can fix them.

---

### Post by AJB2K3 on 2009-07-28
Never mind all sorted out now., Thanks for pointing out I had the wrong header section set up.
Changed it to 
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="content-type" content="application/xhtml+xml" />

```
I had forgotten line 1 and the application section.

Now to do all the other pages.

---

### Post by v8YKxgHe on 2009-07-28
> **AJB2K3 said:**
> Never mind all sorted out now., Thanks for pointing out I had the wrong header section set up.
Changed it to 
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
      "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="content-type" content="application/xhtml+xml" />

```
I had forgotten line 1 and the application section.

Now to do all the other pages.

Still not fixed. A default PHP install will set the 'Content-Type' header to 'text/html' - and yours is still doing that. You need to either change the PHP directive 'default_mimetype' or add in the PHP code to set the header via header(). Once you do that, you'll see the XML parse errors.

Edit: this is of course assuming you're using PHP, if not you'll need to do it some other way.

---

### Post by Reiger on 2009-07-28
> **AlexC_ said:**
> But it's not valid. I can create a valid HTML document and attempt to send that as image/png - it's a valid HTML document, but not a valid PNG file. That is essentially what people do when using XHTML, they send it as something different (granted, image/png is a extreme example there).

By sending XHTML as text/html you're relying on undocumented, inconsistency behaviour of the renderer to 'fix' your broken HTML (since XHTML sent as HTML is broken tag soup). So by doing this you're making life harder for your self to create a consistent web page over multiple browsers.

I was referring to your story of impending doom which I took as meaning that "if you have an 'valid' XHTML document served as HTML and you think it is ok -- then by switching to serving it as XHTML you are bound to expose a lot of problems...." To which my reply meant that valid XHTML is valid XHTML and if served as valid XHTML still is valid XHTML and thus that by switching to serving it as XHTML you do no damage.

Of course documents that are not technically valid XHTML because -commone one- they contain ampersands that aren't properly escaped would fail. But that scenario does away with the premise of valid XHTML in the first place: a different scenario altogether.

Of course sending XHTML as HTML doesn't make much sense. It hints at a lack of server configuration or other laziness.

---

### Post by v8YKxgHe on 2009-07-28
> **Reiger said:**
> I was referring to your story of impending doom which I took as meaning that "if you have an 'valid' XHTML document served as HTML and you think it is ok -- then by switching to serving it as XHTML you are bound to expose a lot of problems...." To which my reply meant that valid XHTML is valid XHTML and if served as valid XHTML still is valid XHTML and thus that by switching to serving it as XHTML you do no damage.

Of course documents that are not technically valid XHTML because -commone one- they contain ampersands that aren't properly escaped would fail. But that scenario does away with the premise of valid XHTML in the first place: a different scenario altogether.

Of course sending XHTML as HTML doesn't make much sense. It hints at a lack of server configuration or other laziness.

Very rarely will a document coded as XHTML, but sent as HTML, work just fine once switched over to the correct mime type. Take these last 2 sites for example, neither of them will work.

---

### Post by AJB2K3 on 2009-07-28
> **AlexC_ said:**
> Still not fixed. A default PHP install will set the 'Content-Type' header to 'text/html' - and yours is still doing that. You need to either change the PHP directive 'default_mimetype' or add in the PHP code to set the header via header(). Once you do that, you'll see the XML parse errors.

Edit: this is of course assuming you're using PHP, if not you'll need to do it some other way.

Its not php buts its passed !
I'm lost now?

---

### Post by v8YKxgHe on 2009-07-28
> **AJB2K3 said:**
> Its not php buts its passed !
I'm lost now?

Not quite, still sending as text/html. You'll need to find a way of setting the 'Content-Type' heading...

... or you could just use HTML 4.01 instead to start with =)

---

### Post by AJB2K3 on 2009-07-28
> **AlexC_ said:**
> Not quite, still sending as text/html. You'll need to find a way of setting the 'Content-Type' heading...

... or you could just use HTML 4.01 instead to start with =)
I say again huh?
> The document located at <http://www.s284317130.websitehome.co.uk/>  was successfully checked as XHTML 1.0 Strict. This means that the resource in question identified itself as "XHTML 1.0 Strict" and that we successfully performed a formal validation using an SGML, HTML5 and/or XML Parser(s) (depending on the markup language used). 

---

### Post by v8YKxgHe on 2009-07-28
> **AJB2K3 said:**
> I say again huh?

W3C Validator is not a browser, simple. Your code may very well be valid XHTML, but as said - your browser does not care about that, it cares about what you're sending it as, which is currently text/html.

You're far far far best off using HTML until you understand what XHTML is and how to you use it, and once you know that - you'll not want to use it any more.

---

### Post by AJB2K3 on 2009-07-28
Ok now were getting into document types and mime type.
The correct mime/context is application/xhtml+xml and all modern applications will accept it.
(note use of software not browser) 
I think you are over thinking things to much.
Every document I have read says that
>   <meta http-equiv="content-type" content="application/xhtml+xml" />
Is the correct mime/content/document type !

---


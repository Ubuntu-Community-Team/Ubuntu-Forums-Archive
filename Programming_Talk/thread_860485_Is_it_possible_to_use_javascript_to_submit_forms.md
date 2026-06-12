---
title: "Is it possible to use javascript to submit forms?"
date: 2008-07-15
forum: Programming Talk
---

### Post by user1397 on 2008-07-15
I tried looking for a way to submit text forms so that when you press the submit button, the text is displayed or "posted" on another page, but I haven't been successful.  I know this can be done with asp or php, but is it possible with simple js?

---

### Post by LaRoza on 2008-07-15
Yes, just submit() it!

If linked to a page, this will submit every form it finds (or try to)

[php]
window.onload = function()
{
    var fors = document.getElementsByTagName("form")
    for (var i = 0; i < fors.length; i++)
    {
        fors[i].submit()
    }
}
[/php]

---

### Post by user1397 on 2008-07-15
> **LaRoza said:**
> Yes, just submit() it!

If linked to a page, this will submit every form it finds (or try to)

[php]
window.onload = function()
{
    var fors = document.getElementsByTagName("form")
    for (var i = 0; i < fors.length; i++)
    {
        fors[i].submit()
    }
}
[/php]ah, I meant without using php, just javascript.  i don't know php (yet) :(

---

### Post by LaRoza on 2008-07-15
> **ubuntuman001 said:**
> ah, I meant without using php, just javascript.  i don't know php (yet) :(

That is ECMAScript. 

If you could describe want you have, and what you want, I could give a more specific example.

---

### Post by LaRoza on 2008-07-15
> **ubuntuman001 said:**
> I tried looking for a way to submit text forms so that when you press the submit button, the text is displayed or "posted" on another page, but I haven't been successful.  I know this can be done with asp or php, but is it possible with simple js?

I am confused by what you want. Do you want to submit form, or handle submitted forms?

---

### Post by drubin on 2008-07-15
> **ubuntuman001 said:**
> ah, I meant without using php, just javascript.  i don't know php (yet) :(

LaRoza Just used the php formating tags because this forum only has tag that allows for syntax highlighting. (But it is Java Script)

[http://en.wikipedia.org/wiki/ECMAScript](http://en.wikipedia.org/wiki/ECMAScript) -> was also confused the first time I read LaRoza mention it...

---

### Post by LaRoza on 2008-07-15
> **rubinboy said:**
> LaRoza Just used the php formating tags because this forum only has tag that allows for syntax highlighting. (But it is Java Script)

[http://en.wikipedia.org/wiki/ECMAScript](http://en.wikipedia.org/wiki/ECMAScript) -> was also confused the first time I read LaRoza mention it...

JavaScript and JScript are implementations of ECMAScript. I follow the standards and do not use the "JavaScript" or "JScript" parts so I refer to it by what I actually use :-)

Sorry for the confusion. I think I misread the OP.

You can use a form to set a cookie and read it in ECMAScript on another page. I will make an example...

---

### Post by drubin on 2008-07-15
> **LaRoza said:**
> 
JavaScript and JScript are implementations of ECMAScript. I follow the standards and do not use the "JavaScript" or "JScript" parts so I refer to it by what I actually use.

Do you do alot of web development? cross browser? 


> **LaRoza said:**
> 
Sorry for the confusion. I think I misread the OP.
You can use a form to set a cookie and read it in ECMAScript on another page. I will make an example...

I think you didn't misread the OP, think that is exactly what he wanted. (Just the php tags were confusing the OP)

---

### Post by LaRoza on 2008-07-15
> **rubinboy said:**
> Do you do alot of web development? cross browser? 

Yes :-) See my site. All code handwritten. The only problem is that the Conversion Calculator doesn't work in Firefox (but it is standard code).

> 
I think you didn't misread the OP, think that is exactly what he wanted. (Just the php tags were confusing the OP)

I think I did. I read it as "cause a form to be submitted by using a client side script", but I think it was meant to be "handle a form after submission and use the data on another page".

Handling a form is easy (all of my web apps on my site work that way), but using the data would be a little tricky (parsing cookies). I can do it (for a static page, no sever needed, but it will take a little while, I am busy)

---

### Post by drubin on 2008-07-15
> **LaRoza said:**
> Yes :-) See my site. All code handwritten. The only problem is that the Conversion Calculator doesn't work in Firefox (but it is standard code).

:) That was one of my funny points, with web development it doesn't matter how much you follow the "standard" code you are going to find things that just don't seem to work in one browser or another..... :(

---

### Post by LaRoza on 2008-07-15
> **rubinboy said:**
> :) That was one of my funny points, with web development it doesn't matter how much you follow the "standard" code you are going to find things that just don't seem to work in one browser or another..... :(

I can make it work. It is probably something small. I originally wrote that as an Opera widget and only tested it on Opera.

---

### Post by user1397 on 2008-07-15
Ah, those php tags did confuse me, but rubinboy clarified it.

and yes laroza, you got it right, i wanted to know how to "handle a form after submission and use the data on another page" like u said.

im talking about a very small personal website, just has a few pages (on my own ubuntu server), no php/perl/sql anything, just apache.

basically what i want is for someone to go to a page where they can fill out a form, and then whatever they wrote is posted on another page, preferably in order of time posted.

thanks for your help so far guys (or gals).

---

### Post by LaRoza on 2008-07-15
> **ubuntuman001 said:**
> Ah, those php tags did confuse me, but rubinboy clarified it.

As far as I know, there is no way to change it. It does provide syntax highlighting for many languages (it is simple, a few keywords and strings) but it helps.

> 
and yes laroza, you got it right, i wanted to know how to "handle a form after submission and use the data on another page" like u said.
If it is all on the client, it won't last.

> 
basically what i want is for someone to go to a page where they can fill out a form, and then whatever they wrote is posted on another page, preferably in order of time posted.
It won't last. It will be restricted to the session. There is no way around that without server side magic. 

PHP is very easy, and you can through together a small script (or if it is small enough, I could do it) and have something. Let me know, but I'll do the client side thing for you.

> 
thanks for your help so far guys (or gals).

You will get the bill in a few days :-)

---

### Post by LaRoza on 2008-07-15
This is just an example of how to do it. It only lasts for the session (close the page, and it is done). I don't know how useful it is, but the principles can be appled to any page. I did it extremely simple.

Just save both, the first as "script,js" and the other as "index.xhtml" (make sure they are in the same directory) and just open the index with a browser.

[php]
function showNew(show,hide,name)
{
    show.style.visibility = "visible";
    hide.style.visibility = "hidden";

    var p = document.createElement("p");
    show.appendChild(p);
    var t = document.createTextNode(name);
    p.appendChild(t); 
}

window.onload = function()
{
    var first = document.getElementById("first");
    var second = document.getElementById("second");
    second.style.visibility = "hidden";
    var fors = document.getElementsByTagName("form")[0];
    var text = false;
    fors.onsubmit = function()
    {
        text = document.getElementById("uri").value;
        showNew(second,first,text);
        return false;
    }
    document.getElementById("back").onclick = function()
    {
        first.style.visibility = "visible";
        second.style.visibility = "hidden";
    }
}
[/php]

[html]
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>ECMAScript Example</title>
<meta http-equiv="content-type" content="application/xhtml+xml;charset=utf-8" />
<script type="text/ecmascript" src="script.js"></script>
</head>

<body>
<div id="first">
<form action="#" method="get">
<label>Give a URI: <input type="text" name="uri" id="uri" maxlength="20" /></label>
<input type="submit" />
</form>
</div>

<div id="second">
<span><a href="#" title="Back" id="back">Go Back</a></span>
</div>
</body>
</html>
[/html]

---

### Post by Rutger on 2008-07-16
You could write it to a cookie, and then in the next page retrieve the data from this cookie.

---

### Post by user1397 on 2008-07-18
> **LaRoza said:**
> As far as I know, there is no way to change it. It does provide syntax highlighting for many languages (it is simple, a few keywords and strings) but it helps.Ah, okay, yea I prefer syntax highlighting anyway.


> **LaRoza said:**
> If it is all on the client, it won't last.


It won't last. It will be restricted to the session. There is no way around that without server side magic. Ah, thanks for clarifying this concept for me; I had no idea it was like this.

> **LaRoza said:**
> PHP is very easy, and you can through together a small script (or if it is small enough, I could do it) and have something. Let me know, but I'll do the client side thing for you.ok, ill install php and try to see if i can do it, and if not, ill be asking here :)



> **LaRoza said:**
> You will get the bill in a few days :-)how much? :)

---

### Post by user1397 on 2008-07-18
> **Rutger said:**
> You could write it to a cookie, and then in the next page retrieve the data from this cookie.but wouldn't this be restricted to that session, just like LaRoza said?

---

### Post by LaRoza on 2008-07-18
> **ubuntuman001 said:**
> but wouldn't this be restricted to that session, just like LaRoza said?

Yes it would.

---


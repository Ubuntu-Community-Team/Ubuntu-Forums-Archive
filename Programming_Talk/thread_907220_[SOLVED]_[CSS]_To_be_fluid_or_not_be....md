---
title: "[SOLVED] [CSS] To be fluid or not be..."
date: 2008-09-01
forum: Programming Talk
---

### Post by nvteighen on 2008-09-01
Hi there!

I've a philosophical question. I know the advantages of fluid design (resizability for different kind of screens), but resizing to different resolutions makes everything to overlap (specially fonts, that aren't being scaled).

Fixed design of course has the issue that at different resolutions the page may overflow, but it won't cause any mess at resizing (you'll just have to scroll down/right...).

This is an artist's webpage and the images of her paintings shouldn't overlap: Can you imagine what a dissaster would mean that her works overlap each other?

So, what would **you** do? I'm a bit confused...

EDIT: I could send you a prototype, but I'm not allowed to send you any of her images...

---

### Post by LaRoza on 2008-09-01
There are cases when the content requires violations of best standards.

For example, this forum is so large and complex, it cannot work well on 800x600, so it has a minimum requirement of 1024x768.

For this case, art, a "This site requires..." is definately justified. 

Also, you could do two versions. One with it like you want, and one that is less features, but works ok on lower resolutions (by having links to the individual pieces or something)

---

### Post by ianhaycox on 2008-09-01
There's no reason why stuff should overlap on a fluid design if everything is specified in percentages/ems etc.

For example, see **[http://www.brittanyholidaycottage.com/]("http://www.brittanyholidaycottage.com/")** where the images resize depending on the browser size. It also copes with users changing the the text size etc. Not a perfect website by any means, but it demonstrates the principle.

---

### Post by LaRoza on 2008-09-01
> **ianhaycox said:**
> There's no reason why stuff should overlap on a fluid design if everything is specified in percentages/ems etc.

For example, see **[http://www.brittanyholidaycottage.com/]("http://www.brittanyholidaycottage.com/")** where the images resize depending on the browser size. It also copes with users changing the the text size etc. Not a perfect website by any means, but it demonstrates the principle.

But for an art site, there is obviously a requirement of size for the images (unless, there are links to them, as I pointed out, but that is not quite as good a design on having them on the page).

An artist would want their work presented in a suitable way, and that probably requires a minimum size or a static size.

---

### Post by nvteighen on 2008-09-02
Thanks, I see...

I send here a prototype of the webpage, both HTML and CSS codes to see what I'm doing. I'm not quite a web developer, but can do simple tasks such as this. I'm using HTML 4.01 Strict and CSS 2.1... (which arises another question, do you recommend switching to XHTML?)

index.html:
[HTML]
<!DOCTYPE html 
		  PUBLIC "-//W3C//DTD HTML 4.01//EN"
		  "http://www.w3.org/TR/html4/strict.dtd">

<html>

  <head>
    <meta http-equiv = "Content-Type" content="text/html; charset=utf-8">
    
    <link rel="stylesheet" href="style.css" type="text/css">
        
    <!-- Local style here -->
    <style type="text/css">
    </style>
    
    <title>Page's title</title>
  </head>
    
  <body>
    
    <!-- Cabecera -->
    <div class="header">
      <h1 class="header">&lt;Artist's name&gt;</h1>
    </div>
    
    <!-- Navbar -->
    <div class="nav">
      <ul>
		<li><b>Principal</b></li>
        <li><a href="tray_es.html">Trayectoria</a></li>
		<li><a href="obras_es.html">Obras</a></li>
		<li><a href="vinc_es.html">Vínculos</a></li>
		<li><a href="contact_es.html">Contacto</a></li>
      </ul>
    </div>    

	<!-- Content -->
    <div class="cont">
	  <p>&lt;Here goes a table feauturing thumbnails of pictures&gt;</p>
    </div>
    
    <div class="copy">
      <p>
        Copyright &copy; 2008 &lt;name&gt;
        <br>All rights reserved.
      </p>
    </div>

  </body>

</html>
[/HTML]

style.css:
```

body
{
    color: #FFFFFF;
    background-color: #5E5B58;
    margin: 0%;
    padding: 0%;
}

a:link
{
    color: #FFFFFF;
}

a:visited
{
    color: #FFFFFF;
}

img
{
    border-width: 0em;
}

div.header
{
    position: fixed;
    top: 0%;
    left: 0%;
    height: 20%;
    width: 100%;
    border-width: 1px;
    
    z-index: 1;
    
    background-color: #8C8C8C;
    color: #C02022;
}

h1.header
{
    margin-top: 1em;
    padding-left: 1em;
    
    font-size: 250%;
    font-family: "Helvetica", serif;
}

div.cont
{
    position: absolute;
    top: 25%;
    width: auto;
    left: 0%;

    margin: 0;
    padding-left: 35%;
    
    font-family: "Helvetica", serif;
    font-size: 100%;
    
    color: #FFFFFF;
}

div.nav
{
    position: fixed;
    top: 25%;
    padding-left: 0em;
    width:20%;
    
    background-color: #8C8C8C;
}

li
{
    margin-bottom: 0.5em;
    font-family: "Helvetica", serif;
}

div.copy
{
    position: fixed;
    top: 80%;
    width: 20%;
    padding-left: 1em;
    
    font-family: "Helvetica", serif;
    font-size: 10pt;
    
    color: #FFFFFF;
}

```

---

### Post by LaRoza on 2008-09-02
> **nvteighen said:**
> 
I send here a prototype of the webpage, both HTML and CSS codes to see what I'm doing. I'm not quite a web developer, but can do simple tasks such as this. I'm using HTML 4.01 Strict and CSS 2.1... (which arises another question, do you recommend switching to XHTML?)


Yes, you should use XHTML. You are essentially using it already.

---

### Post by nexx on 2008-09-02
I am not sure that using an XHTML header is really helpful since internet explorer 6 do not seem to interpret corectly XHTML.
To me a better way (until we can write in html 5) is to use XHTML syntax and a html 4 strict header.

---

### Post by nvteighen on 2008-09-02
> **ianhaycox said:**
> There's no reason why stuff should overlap on a fluid design if everything is specified in percentages/ems etc.

For example, see **[http://www.brittanyholidaycottage.com/]("http://www.brittanyholidaycottage.com/")** where the images resize depending on the browser size. It also copes with users changing the the text size etc. Not a perfect website by any means, but it demonstrates the principle.

And what about text? If I have a certain text with some font-size, if the resolution changes, text will still remain at the same size and it will overlap.

> **LaRoza said:**
> Yes, you should use XHTML. You are essentially using it already.

So, if I just change DOCTYPE (and add the xmlns-stuff), I'm on XHTML? Will it give me any special advantage?

> **nexx said:**
> I am not sure that using an XHTML header is really helpful since internet explorer 6 do not seem to interpret corectly XHTML.
To me a better way (until we can write in html 5) is to use XHTML syntax and a html 4 strict header.

I see, but who uses IE these days? ;)

---

### Post by forger on 2008-09-02
> **nvteighen said:**
> I see, but who uses IE these days? ;)

A fair amount of people that click-and-buy art.. and probably the artist that will buy your website design :P

---

### Post by nvteighen on 2008-09-02
> **forger said:**
> A fair amount of people that click-and-buy art.. and probably the artist that will buy your website design :P

Err... No, she uses FF 3... (because her disastrous XP-laptop freezes when loading IE7 :p)

---

### Post by forger on 2008-09-02
I stand corrected, hehe

---

### Post by airtonix on 2008-09-02
alistapart.com has some excellent articles about this exact topic and how to over come it.

---

### Post by nvteighen on 2008-09-02
> **airtonix said:**
> alistapart.com has some excellent articles about this exact topic and how to over come it.
Thank you... I like it.

---

### Post by LaRoza on 2008-09-02
> **nexx said:**
> I am not sure that using an XHTML header is really helpful since internet explorer 6 do not seem to interpret corectly XHTML.
To me a better way (until we can write in html 5) is to use XHTML syntax and a html 4 strict header.

Don't send the http header info (IE 6 wouldn't know what to do with it) but use it in the markup. All compliant browsers will render it correctly, and legacy browsers will ignore it.

My work is in XHTML 1.1 and it works fine in all browsers.

> **nvteighen said:**
> 
So, if I just change DOCTYPE (and add the xmlns-stuff), I'm on XHTML? Will it give me any special advantage?

Try it ;)

Use the validator [http://validator.w3.org/](http://validator.w3.org/)

It will be stricter and it will be coded for the future. No need to enforce stagnation of progress.

> 
I see, but who uses IE these days? ;)
The Lost Children of Computing.

---

### Post by nvteighen on 2008-09-02
> **LaRoza said:**
> 
My work is in XHTML 1.1 and it works fine in all browsers.


Try it ;)

Use the validator [http://validator.w3.org/](http://validator.w3.org/)

It will be stricter and it will be coded for the future. No need to enforce stagnation of progress.

Done. It needed some tweaks to have it valid XML, but it was easy to make it pass. Thank you.

btw, XHTML allows for easier integration with custom XML, right? So I could create my own tags and let it integrate into XHTML easily... (I don't need that here, but just to know).

---

### Post by LaRoza on 2008-09-02
> **nvteighen said:**
> 
btw, XHTML allows for easier integration with custom XML, right? So I could create my own tags and let it integrate into XHTML easily... (I don't need that here, but just to know).

Yes. XHTML follows an DTD and has a namespace. You can use other DTD (as long as they have their own namespace).

---


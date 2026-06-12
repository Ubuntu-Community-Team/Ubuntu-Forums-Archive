---
title: "Javascript File Includes Within HTML, Bad?"
date: 2010-03-25
forum: Programming Talk
---

### Post by era86 on 2010-03-25
Greetings!

I am currently doing work on a website and I was wondering if it is bad for SEO to do a JS file include from within the <body> tags of an HTML file.

For example:

[HTML]
<body>
<div id="mydiv">
    <p>My Content</p>
    <br />
</div>
<script type="text/javascript" src="myJs.js"></script>
<div id="newdiv">
    <p>More content for search engine to see.</p>
    <br />
</div>
</body>
[/HTML]

Would the spider die where the include happens?  I know it isn't perfect practice, but I just don't want the spider to miss anything important.

Thanks in advanced!:p

---

### Post by jfparis on 2010-03-25
I don't think it is an issue for the spider

However it might be an issue the visitors. When the web browser reaches the script bloc it will stop rendering the page until it has loaded and executed that javascript. 

Therefore a script element in the middle of the page might slow its opening.

That is why it is usually recommanded to load the javascript files at the end of the html document

jf

---

### Post by roccivic on 2010-03-25
On my website none of the content that is dynamically gets indexed by spiders. I therefore think they completely ignore JS...

---

### Post by Hellkeepa on 2010-03-26
HELLo!

That they do, **roccivic**.

Also, JS files should be included in the header, so that the browser can do parallel loading on them. Functions that generate dynamic content, however, should be executed once the DOM node has been fully rendered. Which is at the very end of the HTML document. jQuery and other JS libraries contain methods that substitute "onload", and postpones the running of the functions until the DOM has been rendered fully.

Happy codin'!

---

### Post by hessiess on 2010-03-26
Putting JavaScript in a separate file is a very good idea, especially with static (non CMS) websites. It allows the browser to cache the code, reducing file size and vastly reduces code redundancy.

Also remember that anything added with javascript should also be available without it for usability (screen-readers) and SEO.

---

### Post by nvteighen on 2010-03-26
Ugh... it's horrible practice... It goes against MVC programming, against modularization and may even be against proper abstraction practices...

---

### Post by myrtle1908 on 2010-03-27
The optimum approach is to concatenate and compress all of your JS files into one.  Then deliver this to the client.  Have a look at YUI compressor (or similar) and GZIP compression.

---


---
title: "Apache and my XHTML document"
date: 2011-06-29
forum: Programming Talk
---

### Post by B34ST1Y on 2011-06-29
I have an XHTML document that is working on a colleague's setup, but not my apache install.

It's obviously malformed, but its working for him. My browser (IE,Firefox,Chrome...doesn't matter) tells me there is a problem similar to this:

```
XML Parsing Error: undefined entity
Location: http://mywebsite/folder/folder/main.xhtml
Line Number 41, Column 48:      <div id="copyright" class="grid grid-16">&copy; 2011 by <a href="http://someonesdomain.com">The So and So's, LLC.</a></div>
```

It's getting hung up over &copy;  which is supposedly an XHTML code for a copyright symbol. When I remove this, there are other formatting issues. I'm wondering if this is a telltale sign that I have something misconfigured in my Apache config or something else that I'm missing??


Please help, any pointers are greatly appreciated! Thanks.

---

### Post by B34ST1Y on 2011-06-29
Any help on the matter would be really appreciated.

---

### Post by r-senior on 2011-06-30
I've come across this before and it's confusing, but my understanding is this ...

The &copy; entity is not an implicit part of XHTML (which is XML, not HTML).

You can either use & #169 which goes direct for the character, or include a DTD that specifies the mapping between &copy; and & #169. (I had to add a space to stop the copyright symbol appearing here).

[http://www.w3.org/TR/xhtml1/normative.html#strict](http://www.w3.org/TR/xhtml1/normative.html#strict)

But this doesn't explain the differences you are seeing. I wonder if the server is somehow returning a different content type in your case? Are you specifying a meta tag in the document for the content type?

[http://www.w3.org/TR/xhtml-media-types/#application-xhtml-xml](http://www.w3.org/TR/xhtml-media-types/#application-xhtml-xml)
[http://www.ibm.com/developerworks/xml/library/x-tipapachexhtml/index.html](http://www.ibm.com/developerworks/xml/library/x-tipapachexhtml/index.html)

I wonder if your colleague is actually serving the document as HTML rather than XHTML? You could install a browser add-on and see what content type is being sent back? Have you both tried renaming the file as .xhtml?

It might help to post the header of your document (including the <head> section and its meta tags).

EDIT: Oh, and what server is your colleague using?

---

### Post by B34ST1Y on 2011-06-30
His words on what server they use: 
" lighttpd proxying to thin (a ruby web/app server). But we've used fastcgi, too, with lighttpd and nginx.  "


the document has an .xhtml extension already. 

Here's the head:

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Generic Website</title>
    <meta encoding="UTF-8" />
    <link rel="stylesheet" href="/css/inuit.css" />
    <link rel="stylesheet" href="/css/style.css" />
    <link href='http://fonts.googleapis.com/css?family=VT323' rel='stylesheet' />
    <link href='http://fonts.googleapis.com/css?family=Droid+Sans' rel='stylesheet' type='text/css' />
    <link href='http://fonts.googleapis.com/css?family=Droid+Sans+Mono' rel='stylesheet' />
    <script src="/js/flot/jquery.min.js"></script>
    <script src="/js/flot/jquery.flot.min.js"></script>
    <script src="/js/main_index.js"></script>
    <script src="/js/graphs.js"></script>
    <link rel="shortcut icon" href="/favicon.ico" />
  </head>

```

---

### Post by r-senior on 2011-06-30
I'm going to guess that Apache sends back a content type of application/xhtml+xml based on the .xhtml extension whereas your colleague's server is ignoring the extension and sending back text/html as the content type.

Did you try looking at the headers and/or adding a meta tag for content type and/or using one of the recommended header/namespace for XHTML?

---

### Post by B34ST1Y on 2011-06-30
can you elaborate? Here is the entire page:


```
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Generic Website</title>
    <meta encoding="UTF-8" />
    <link rel="stylesheet" href="/css/inuit.css" />
    <link rel="stylesheet" href="/css/style.css" />
    <link href='http://fonts.googleapis.com/css?family=VT323' rel='stylesheet' />
    <link href='http://fonts.googleapis.com/css?family=Droid+Sans' rel='stylesheet' type='text/css' />
    <link href='http://fonts.googleapis.com/css?family=Droid+Sans+Mono' rel='stylesheet' />
    <script src="/js/flot/jquery.min.js"></script>
    <script src="/js/flot/jquery.flot.min.js"></script>
    <script src="/js/main_index.js"></script>
    <script src="/js/graphs.js"></script>
    <link rel="shortcut icon" href="/favicon.ico" />
  </head>
  <body>
    <header class="grids">
      <a href="/"><h1 class="grid grid-4">Generic</h1></a>
      <div class="grid grid-2">
        <img src="/img/goldfish.png" />
      </div>
      <div class="grid grid-16">
        <nav>
          <ul>
            <li>#{Namecoiner::Main.a 'Home', :/}</li>
            <li>#{Namecoiner::Main.a 'Get Started', :intro}</li>
            <li>#{Namecoiner::Main.a 'My Account', :my_account}</li>
            <li>#{Namecoiner::Main.a 'Statistics', :statistics}</li>
            <li>#{Namecoiner::Graph.a 'Graphs', :/}</li>
          </ul>
        </nav>
      </div>
    </header>

    <div id="content" class="grids">
      #{@content}
    </div>

    <footer class="grids">
      
    </footer>
  </body>
</html>

```


What do you recommend I alter?

---

### Post by r-senior on 2011-06-30
> **r-senior said:**
> I'm going to guess that Apache sends back a content type of application/xhtml+xml based on the .xhtml extension whereas your colleague's server is ignoring the extension and sending back text/html as the content type.
When the server responds to an HTTP request from a browser, it sends a response back with headers and a body. One of those headers (not directly related to the HTML <head> element) is the content type, which suggests to the browser how to interpret the body of the response, e.g. text/html, text/plain, application/pdf, image/gif, etc, etc.

I suspect that your server is returning application/xhtml+xml for your document whereas your colleague's is returning text/html. Given that you don't specify the DTD fully, which for XHTML defines the &copy entity, I suspect this is the reason for the difference in behaviour.

> Did you try looking at the headers and/or adding a meta tag for content type and/or using one of the recommended header/namespace for XHTML?
I only suspect the above - an educated guess. So I suggested:

a. Using a browser extension (for example [http://chrispederick.com/work/web-developer/](http://chrispederick.com/work/web-developer/)) to look at the headers in the HTTP response from the server. They will look something like this:

```

Server: Apache/2.2
Vary: Accept-Encoding
Cache-Control: public, max-age=86400
[COLOR="Red"]Content-Type: text/html[/COLOR]; charset=utf-8
Content-Encoding: gzip
Date: Thu, 30 Jun 2011 16:54:21 GMT
Expires: Fri, 01 Jul 2011 16:54:21 GMT

```

b. See if adding a meta tag with the content type makes any difference. Refer to the links in post #3 above.

[URL="http://www.w3.org/International/questions/qa-html-encoding-declarations#metacontenttype"]http://www.w3.org/International/questions/qa-html-encoding-declarations#metacontenttype
[/URL]

c. Using the recommended DOCTYPE declaration from the link I posted in post #3.

If you just want a quick fix, refer to paragraph 3 of post #3

---


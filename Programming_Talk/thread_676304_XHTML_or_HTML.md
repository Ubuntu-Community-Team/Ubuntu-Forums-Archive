---
title: "XHTML or HTML"
date: 2008-01-23
forum: Programming Talk
---

### Post by yeehi on 2008-01-23
Building a new website, does it currently make more sense to make it html rather xhtml, because Internet Explorer just can't handle xhtml properly at the moment?

---

### Post by LaRoza on 2008-01-23
> **yeehi said:**
> Building a new website, does it currently make more sense to make it html rather xhtml, because Internet Explorer just can't handle xhtml properly at the moment?

I use XHTML 1.1 and CSS 2. I even serve with the MIMI type application/xhtml+xml, works in IE.

Use XHTML.

---

### Post by yeehi on 2008-01-23
Wow! But when i checked a site i was working on, it didn't work at all properly as xhtml in IE. In firefox it looked reasonably OK.

Are you sure that all your users get a proper page served up? Have you written another page to serve up as html too?

---

### Post by LaRoza on 2008-01-23
> **yeehi said:**
> Wow! But when i checked a site i was working on, it didn't work at all properly as xhtml in IE. In firefox it looked reasonably OK.

Are you sure that all your users get a proper page served up? Have you written another page to serve up as html too?

What version of IE? IE6 renders my pages correctly. CSS is where issues arise.

By default, my host served the pages with the MIMI type "text/html", but I changed that recently. Any browser that can't support XML is extremely out of date.

---

### Post by yeehi on 2008-01-23
But isn't it best to use CSS when designing a site?

Why did you abandon CSS? Solely to use XHTML? If so, what sort of functionality/experience is your site able to offer, by having XHTML rather than HTML and CSS?

---

### Post by LaRoza on 2008-01-23
> **yeehi said:**
> But isn't it best to use CSS when designing a site?

Why did you abandon CSS? Solely to use XHTML? If so, what sort of functionality/experience is your site able to offer, by having XHTML rather than HTML and CSS?

Read my first post again.

---

### Post by yeehi on 2008-01-23
Ah! I missed that. So, the secret is to use CSS 2, rather than CSS 3?

I would want to use CSS, so what should i do to avoid issues with ie users?

---

### Post by LaRoza on 2008-01-23
> **yeehi said:**
> Ah! I missed that. So, the secret is to use CSS 2, rather than CSS 3?

I would want to use CSS, so what should i do to avoid issues with ie users?

CSS3 isn't really implemented yet, but worth getting familiar with.

(Note: the CSS versions are compatible with each other, so you don't "relearn" it, you just add to your available knowledge)

[http://www.webcredible.co.uk/user-friendly-resources/css/internet-explorer.shtml](http://www.webcredible.co.uk/user-friendly-resources/css/internet-explorer.shtml)

If the CSSForums.org site were up with its wiki, you'd get very good information. ThinkBuntu, hurry up! The masses are crying out.

---

### Post by Borbus on 2008-01-23
IE does not work if XHTML is (correctly) served as application/xhtml+xml. It does not support XHTML, therefore XHTML is not support by 70% whatever ridiculous majority the shockingly bad browser has at the moment.

I use XHTML because I think it should replace HTML on the web. Being able to embed other XML namespaces (ie. SVG, MathML) is a good reason to use XHTML. I also like it because Firefox will refuse to render non-well formed XML which ensures that my markup is always well formed.

Be aware that an XML header (<?xml version="1.0" encoding="utf-8"?>) will put IE into quirks mode. I use this piece of PHP to conditionally serve XHTML with the correct MIME type, however I think only Mozilla sends the application/xhtml+xml header in its HTTP request.

```
<?php
// Generate XML header if browser accepts
if ( stristr($_SERVER['HTTP_ACCEPT'],'application/xhtml+xml') ) {
    header('Content-type: application/xhtml+xml');
    echo '<?xml version="1.0" encoding="utf-8"?>';
}
else {
    header('Content-type: text/html');
}
?>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title></title>
<meta http-equiv="Content-Type" content="application/xhtml+xml; charset=utf-8" />
<link href="styles/style.css" rel="stylesheet" type="text/css" />
</head>
<body>
</body>
</html>
```

---

### Post by LaRoza on 2008-01-23
> **Borbus said:**
> IE does not work if XHTML is (correctly) served as application/xhtml+xml. It does not support XHTML, therefore XHTML is not support by 70% whatever ridiculous majority the shockingly bad browser has at the moment.

I use XHTML because I think it should replace HTML on the web. Being able to embed other XML namespaces (ie. SVG, MathML) is a good reason to use XHTML. I also like it because Firefox will refuse to render non-well formed XML which ensures that my markup is always well formed.

Be aware that an XML header (<?xml version="1.0" encoding="utf-8"?>) will put IE into quirks mode. I use this piece of PHP to conditionally serve XHTML with the correct MIME type, however I think only Mozilla sends the application/xhtml+xml header in its HTTP request.


IE7? I think I tested in that browser and it worked. I will have to retest.

The embedding other namespaces, especially those two, should make XHTML more useful, flexible, and better than anything before it.

---

### Post by Borbus on 2008-01-23
There is no version of IE that supports XHTML, or CSS for that matter (supporting half of a specification badly does not count as support imo). Despite these glaring deficiencies the next version of IE will support Microformats! Whatever the hell that is...

---

### Post by LaRoza on 2008-01-23
> **Borbus said:**
> 
Be aware that an XML header (<?xml version="1.0" encoding="utf-8"?>) will put IE into quirks mode.


IE6 [http://en.wikipedia.org/wiki/Quirks_Mode#Triggering_different_rendering_modes](http://en.wikipedia.org/wiki/Quirks_Mode#Triggering_different_rendering_modes)

---

### Post by clasificado on 2008-01-24
So, IE7 dont support xhtml

so, you will fall in doing a page with xhtml and serving it as text/html

so, you will lose the "strictness" of xhtml and you will start doing wrong things (and also arent 100% compatible) destroying the xhtml validity, because html supports it.

so, you will do neither xhtml nor html.

so, stick with HTML and forget a headcache

clasificado

---


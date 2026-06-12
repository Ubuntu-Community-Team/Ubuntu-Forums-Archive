---
title: "HTML Help"
date: 2009-03-02
forum: Programming Talk
---

### Post by Slayeragb2 on 2009-03-02
Okay so here is my problem. I'm making a HTML Doc for a computer class project because I have to be a overachiever. I have a image on my desktop, but I can't link it to the HTML page i need.
Here is the sample let of HTML I used.

[HTML]<img src="C:\Documents and Settings\abrewer1\Desktop\ROFL.GIF" />[/HTML]

Any ideas why this is not working?
Thanks!

---

### Post by Can+~ on 2009-03-02
[LIST=1]
[*]Put everything you'll need inside a folder, let's call it "doc"

[*]Inside "doc", just for the sake of order, create a folder named "img" or "image" or whatever you like, and place the image there.

[*]At the base folder create the index.html

[*]In said file, the proper image link would be 

```
<img src="img/rofl.gif" />
```

[*]Always use lowercase
[/LIST]

Why it didn't work with C:\? 
1. Because even if you're on windows, html documents are always linked with forward slashes ("/") like in *nix.
2. It's a terrible idea to use Absolute paths (C:/..../ , /home/ or [http://)](http://)), always use relative paths for portability.

---

### Post by Reiger on 2009-03-02
To elaborate a little, the src argument points not to a filesystem path but rather it should be interpreted as an arbitrary URL: so, forward slashes by convention.

Also you should include an alt attribute (part of the W3C standards, and even if you don't have proper use for it alt="" is better than no alt at all): for the benefit of text-only browsers and in case of failure to load the image.

---

### Post by WatchingThePain on 2009-03-02
Slashes should be forward.

---

### Post by Bodsda on 2009-03-04
If your using html 4.01 strict you should also place that in <p> or <h1> type tags

[html]
<h1><img src="images/pic.gif" alt="picture"></h1>
[/html]

and for html strict dont close the img tag

---


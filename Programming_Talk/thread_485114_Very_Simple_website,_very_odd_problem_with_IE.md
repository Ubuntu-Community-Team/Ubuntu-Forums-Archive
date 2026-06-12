---
title: "Very Simple website, very odd problem with IE"
date: 2007-06-26
forum: Programming Talk
---

### Post by spyder0101 on 2007-06-26
If there are any we designers out there that could help I would really appreciate it.  I am having a very odd problem with my web site.  The site works fine in FF, but when I check it in IE, it loads correctly the first time but if you click "home" it goes to the same html file but the formatting is all messed up.  Any ideas?  The attached file is the website parts in question.

---

### Post by LaRoza on 2007-06-26
I am experiencing no such problems.

(Firefox 2.0.0.4, IE 6)

---

### Post by LaRoza on 2007-06-26
Your code is really messed up. Could you use CSS for the layout?

Remember to quote attribute values.

---

### Post by spyder0101 on 2007-06-26
try looking at it at [www.stlspartans.org](www.stlspartans.org).  It is with IE7, so that might be the problem...

---

### Post by LaRoza on 2007-06-26
IE 7 follows the standards, the code doesn't. Try validating it.

---

### Post by spyder0101 on 2007-06-26
Validating it?  How do I do that?  Unfortunately the books I learned from are almost a decade out of date.

---

### Post by LaRoza on 2007-06-26
No problem, if you are using Firefox, you can get the Total Validator extension, or you can just go to:

[http://validator.w3.org/](http://validator.w3.org/)

You should rewrite the site in XHTML using CSS for better results. (And less code)

---

### Post by spyder0101 on 2007-06-26
Opps, I forgot the css in the zip :( Anyway, thanks for the help.  I'll see if I can fix it now.

---

### Post by LaRoza on 2007-06-26
Fixed a couple of errors in the CSS:

```

th.title

{

  text-align: center;

  font-size: 30pt;

  color: #FFFFFF;

}

td.body

{

  background-color: ffd700;

  vertical-align: top;

  line-height: 125%;

}

th

{ 

  font-weight: 900; 

  font-family: arial; 

  font-variant: normal;

  font-style: normal;

  font-stretch: normal;

  font-size-adjust: none;

}

body

{

  background-image: url(images/dot.gif);

  background-color: #006633;



}

p

{

  color: #000000;

  font-weight: 600;

  font-face: "Times New Roman";

  font-size: 16pt;

  line-height: 150%;

  text-align: justify;

}

a:link 

{

  color:# FFFFFF;

}



a:visited 

{

  color: red;

}



a:active 

{

  color: #FFFFFF;

}



a:hover 

{

  color:red;

  text-decoration:none;



}
```

---

### Post by ThinkBuntu on 2007-06-26
If you'd like, you can come by [www.cssforums.org](www.cssforums.org) and post your problem. I'd be glad to help you out in there, although that's not to say I'm ignoring your problem in here.

---

### Post by spyder0101 on 2007-06-26
Thank you, I think I'll check it out.  btw, any idea why it displays correctly the if you acess it from the address bar but not from the link?

---


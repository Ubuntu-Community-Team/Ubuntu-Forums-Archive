---
title: "Looking for a tutor/ guidance"
date: 2009-06-02
forum: Pennsylvania Team - US
---

### Post by jtm62 on 2009-06-02
Hey everyone,

I am looking for a person who would be willing to help me learn the ins and outs of web design (HTML/XHTML/CSS/JS/PHP/AJAX).  I have multiple books on the topics I have listed but I just can't seem to get a firm grasp of the material.  

I can do the programing so the JS/PHP/AJAX isn't really an issue, however I cannot figure out HTML for the life of me.  I can do the basics, but I want to learn and apply some more advanced topics.

If you are willing to help me reply to this thread and we can try to arrange something.

Thanks for looking!

Josh

---

### Post by LepeKaname on 2009-06-02
Hi Josh,

I suggest you to read in [www.w3schools.com](www.w3schools.com) they have really easy to follow tutorials.

Your best tutor/guidance will be you. You need a personal project in which you can practice all what you are learning. HTML+CSS is easier than PHP or JS/AJAX. You just need to practice, that's all.

Good luck!

---

### Post by jtm62 on 2009-06-02
> **LepeKaname said:**
> Hi Josh,

I suggest you to read in [www.w3schools.com](www.w3schools.com) they have really easy to follow tutorials.

Your best tutor/guidance will be you. You need a personal project in which you can practice all what you are learning. HTML+CSS is easier than PHP or JS/AJAX. You just need to practice, that's all.

Good luck!

That is very true.  Practice helps a lot.  Html annoys the **** out of me though.  I enjoy the challenge that a non functioning program provides, but HTML just pisses me off to no end.  Most of my problems with HTML revolve around data containers not working properly.

Basically I want to design, implement, host, and maintain my own blog/website.  The HTML for the page design is a complete turnoff because I can't get it to work right.

Can you point me to a good advanced HTML textbook that has detailed examples?  W3 is good, I used it to learn a lot of PHP and MySQL but it doesn't help with HTML/CSS.

---

### Post by LepeKaname on 2009-06-03
I think CSS is by far more worthy to be learn than HTML. The only important thing about HTML are forms, which you are usually validated with Javascript. 

CSS must be used to anything related to design, while HTML is as a XML is to data (just descriptor). 

CSS is not as boring as HTML, so I recommend you to start with CSS. So, for example, if you want to create a page with a header, center and footer, this is the only HTML you need:

[HTML]<html>
<head>
<link rel="stylesheet" href="style.css"></link>
</head>
<body>
<div id="header">This is the header</div>
<div id="center">This is the center</div>
<div id="footer">This is the footer</div>
</body>
</html>[/HTML]

Then, create a file named style.css and paste this:

```

body {
    background: #D2C9AA url("http://ubuntuforums.org/images/misc/bgrepeat.jpg") repeat-x;
}
#header, #footer {
    height: 75px;
    background-color: #3D2E14;
    border: 1px #000 solid;
    font-size: 14px;
    color: #000;
    text-align: center;
    padding: 10px;
}
#header {
    background: #FFF url("http://ubuntuforums.org/images/misc/ubuntulogo.png") no-repeat center;
}
#center {
    height: 600px;
    border-left: #000 1px dashed;
    border-right: #000 1px dashed;
    text-align: center;
    font-size: 18px;
    text-decoration: underline;
    padding: 30px;
}

```

You can start with that... This is only to show you that HTML can be really simple and leave the design complications to be fixed in your CSS.

Just play with it... and have fun.

---


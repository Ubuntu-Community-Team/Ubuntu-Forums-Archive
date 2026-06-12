---
title: "Newbie to web development and design, need help."
date: 2011-06-14
forum: Programming Talk
---

### Post by kvv_1986 on 2011-06-14
Hello, 

I am very much a newbie to website development, and I am trying to build a website using Java and JSP right now (I am  planning to switch to Django for my next webapp if it ever gets to that, but that's besides the point). 

I have got the server side of things mostly done, but I don't know anything about html or css, and looking at some random tutorials it seems to be an uphill task for me to learn them.

My questions:
[LIST=1]Is there any gratis software available online or offline with drag-drop functionality, that would spit out the html and css files? I would then add javascript and java code to it later.


[*]If such a software exists, is it worth using it or should I just man up and learn html/css? I would rather not if I don't have to. Design and presentation side of things doesn't excite me too much. :(


[*]If I should man up, can you point me to some good tutorials online?
[/LIST]

Thanks, and any opinions are welcome to this newbie.

---

### Post by r-senior on 2011-06-14
Man up and learn HTML. ;) Also some CSS but you don't need to become an expert. As a web application programmer, you'll often create the web pages (in JSP/JSTL for example) and then a web designer will come in and style with CSS and get fancy with images.

The following tags and their immediate descendants will get you a long way: h1..6, p, ul, ol, table. Learn about divs, ids and classes because that's what the CSS stylers like. 

[http://www.w3schools.com/](http://www.w3schools.com/)

As a general rule, the JSP pages should be simple tags and JSTL plus any Javascript that you need. Java code in the page itself is poor design. You should have data for the page stuffed into request scope and then forward the request/response for the page to display. Most Java web application frameworks encourage this approach.

Maybe also look into composite page solutions like Sitemesh or Apache Tiles.

---

### Post by Jose Catre-Vandis on 2011-06-14
Try:

```
http://cssplay.co.uk
http://w3schools.com
http://www.barelyfitz.com/
```

Use a good code editor ( I use geany)

---

### Post by krazyd on 2011-06-14
Just be careful with the info you get from w3schools.com. Apparently they're a bit shady.

[http://w3fools.com/](http://w3fools.com/)

I would start here: [https://developer.mozilla.org/en-US/docs](https://developer.mozilla.org/en-US/docs)

---

### Post by lykwydchykyn on 2011-06-14
If you're going to be *developing* web stuff, learn HTML, because quite often you'll need to generate HTML programatically.

The good news is, HTML is getting easier to learn since a lot of the old tags are now deprecated.  More and more I find myself just enclosing things in divs and just letting the CSS do the work.

The problem with every wysiwyg HTML/CSS software I've ever seen is that they overcomplicate the output in an attempt to guarantee cross-browser consistency.   That makes it harder to change and harder to debug.

And, frankly, if you're going to tell people you do "web development", you had better know HTML.

---

### Post by ameertawfik on 2011-06-14
> **kvv_1986 said:**
> Hello, 

I am very much a newbie to website development, and I am trying to build a website using Java and JSP right now (I am  planning to switch to Django for my next webapp if it ever gets to that, but that's besides the point). 

I have got the server side of things mostly done, but I don't know anything about html or css, and looking at some random tutorials it seems to be an uphill task for me to learn them.



My questions:


[LIST=1]
[*]Is there any gratis software available online or offline with drag-drop functionality, that would spit out the html and css files? I would then add javascript and java code to it later.[/Qoute]
[*]If such a software exists, is it worth using it or should I just man up and learn html/css? I would rather not if I don't have to. Design and presentation side of things doesn't excite me too much. :(
[*]If I should man up, can you point me to some good tutorials online?
[/LIST]

Thanks, and any opinions are welcome to this newbie.

Since you actually want to program using scripting languages such as JSP  and Python(Diango), you need to learn HTML the hard way. Moreover, to grab the  beauty of Diango, you need to write some HTML pages by hand. 

  I used to teach HTML courses at some local universities and believe me learning using dreamwaver does not make you good at HTML. The opposite is  accurate. Learning HTML makes you a better user of any drag and drop software(dreamwaver, microsoft web developer ... etc).

Having said that, i would recommend you to start by reading w3schools html tutorials. [http://www.w3schools.com/html/default.asp]("http://http//www.w3schools.com/html/default.asp")

After that, you need to build a simple website. My suggestion  is to take any poster or a  small booklet and try to convert it to HTML. It is a good way to understand what each HTML  tag is useful for in practical way.

---

### Post by simeon87 on 2011-06-14
> **kvv_1986 said:**
> Is there any gratis software available online or offline with drag-drop functionality, that would spit out the html and css files? I would then add javascript and java code to it later.

Yes.

> **kvv_1986 said:**
> 
If such a software exists, is it worth using it or should I just man up and learn html/css? I would rather not if I don't have to. Design and presentation side of things doesn't excite me too much. :(

No, it's not worth it. In the long run you're shooting yourself in the foot as it's easier to maintain your own code that generates the HTML / CSS. If you have the ability to make something with Django or JSP, you'll most likely be making your own HTML templates anyway for the web pages.

---

### Post by shawnhcorey on 2011-06-14
Learn HTML and CSS.  Also, Javascript and AJAX.  If you want to do anything beyond simple, and as a professional you will be asked to, you are going to have to tweak the output of the web designer software to meet your employer/client's requests.  So, the sooner you learn it, the better off you'll be.

---

### Post by lykwydchykyn on 2011-06-14
These are great, btw, and very developer-oriented:

[http://code.google.com/edu/submissions/html-css-javascript/](http://code.google.com/edu/submissions/html-css-javascript/)

---

### Post by kvv_1986 on 2011-06-14
Thanks for all your replies. I'll keep them in mind, but it seems that the universal opinion is to spend time learning them rather than using drag-drop.

Which text editor or IDE in your opinion would be best for me?

---

### Post by r-senior on 2011-06-14
What do you use for Java?

---

### Post by kvv_1986 on 2011-06-14
> **r-senior said:**
> What do you use for Java?

Eclipse :)

---

### Post by r-senior on 2011-06-14
That'll do fine. If you haven't done so already, install the web tools stuff from the update site and it will give you syntax highlighting and so on for JSP pages, HTML, XML, etc.

---

### Post by cgroza on 2011-06-14
> **Jose Catre-Vandis said:**
> Try:

```
http://cssplay.co.uk
http://w3schools.com
http://www.barelyfitz.com/
```Use a good code editor ( I use geany)
It used to be my favorite until I discovered emacs.

---


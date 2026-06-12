---
title: "HTML questions"
date: 2012-10-03
forum: Programming Talk
---

### Post by Niemand000 on 2012-10-03
So I'm workin' my way through this HTML turtorial and I'm having a problem getting 
[B]<img src="http://blah/blah/blah.gif" width="157" height="70" alt="blah" />
[/B]to work.  A screenshot is attached.  What am I doing wrong?

---

### Post by MG&amp;TL on 2012-10-03
Does "Pictures/pepe.jpg" actually exist **relative to** your HTML page? It looks like it's probably in ~/Pictures, which is not where your html is looking.

---

### Post by GreatDanton on 2012-10-03
Also if I were you I would place pictures in directory where are .html files placed. It will be easier for you to navigate once you have many .html pages. Also make sure that the picture is actually named pepe.jpg because if it's named Pepe.png you will not see it.

Regards.

---

### Post by Niemand000 on 2012-10-03
This is the location of the picture now: /home/niemand/html/pepe.jpg

Here's what's odd, it works if I post 
<img src="/home/niemand/html/pepe.jpg" alt="Pepe" width="157" />
but not
<img src="~/html/pepe.jpg" alt="Pepe" width="157" />
What's the deal with that?

---

### Post by 1clue on 2012-10-03
~ is a macro substitution handled by your shell.  It isn't part of html.

Do yourself a favor and learn html 5.

And stay away from w3schools.  They're neither authoritative nor accurate.

---

### Post by Niemand000 on 2012-10-03
> **1clue said:**
> ~ is a macro substitution handled by your shell.  It isn't part of html.

Do yourself a favor and learn html 5.

And stay away from w3schools.  They're neither authoritative nor accurate.
I've been using [http://htmldog.com/guides/htmlbeginner/](http://htmldog.com/guides/htmlbeginner/),  is that better or just as bad?

---

### Post by greenpeace on 2012-10-04
Consider creating a separate directory for the images you want to use on your website... this way you should always know where to look for the image, and it keeps the directory for your html documents nice and clear.  

You can also do the same for your css files, javascripts etc etc etc... 

I would normally use a structure like:
```

/var/www/       <- site "root" directory
/var/www/img/   <- imgs
/var/www/css/   <- css or "style" documents
/var/www/js/    <- Javascript files
```

Assuming that **/var/www/** is where you're installing my website.

then you can reference your images like:
```
<img src="/img/logo.jpg" alt="site logo">
```
the "/" at the beginning of the src= parameter is important, as it tells the browser to start the search for the file at the root of the webpage, in this case, **/var/www/**

This is known as an "absolute" path.

hth!

---

### Post by 1clue on 2012-10-04
> **Niemand000 said:**
> I've been using [http://htmldog.com/guides/htmlbeginner/](http://htmldog.com/guides/htmlbeginner/),  is that better or just as bad?

I don't know anything about those guys.  There are lots of tutorials and guides out there, and some of them are pretty good and worth a read.

[http://www.w3c.org](http://www.w3c.org) is the authoritative site.

w3schools has spent a lot of money to get to the top of the search engines, they made a name similar to w3c and so many people assume there's some sort of official connection.  There isn't.  Their examples are often either wrong or bad practice.

Again, I would look to html 5 if you're starting now, unless your company requires some other standard.

**Edit:**

What greenpeace is saying about directories is a standard practice and about the only way to stay sane on a large site.

Personally I like to use /var/www/somedomainname instead of /var/www.  It requires some reconfiguration of apache but it makes it really easy to have multiple sites.

---

### Post by jrog on 2012-10-04
Just to echo what some others have said (and to counter what one person said!), the best practice is to store images in their own directory, as you seem to be trying to do. So, that's good.

About HTML Dog: it is an excellent site; much better than w3schools. I would stick with it, if you're already working with it. From what I recall, HTML Dog does not teach HTML5/CSS3-specific concepts in its tutorials, but that's okay. You're still learning HTML5/CSS3 by virtue of learning earlier material. The earlier material is a subset of HTML5/CSS3. No need to start on HTML5/CSS3 specifics at this point, though you can if you wish. I'd go ahead and get the solid grounding that you're getting from HTML Dog before doing so.

---

### Post by Dimarchi on 2012-10-04
> **Niemand000 said:**
> This is the location of the picture now: /home/niemand/html/pepe.jpg

Here's what's odd, it works if I post 
<img src="/home/niemand/html/pepe.jpg" alt="Pepe" width="157" />
but not
<img src="~/html/pepe.jpg" alt="Pepe" width="157" />
What's the deal with that?

Not odd at all. As you say, the location of the picture is /home/niemand/html/pepe.jpg, and therefore it is found. In the attached picture you have an image with the source of Pictures/pepe.jpg, and your page is at /home/niemand/html/Test.html (guessing what I can see in the address bar...). What Pictures/pepe.jpg - a relative path to the image - means in this context: you are saying that you have a folder called Pictures in /home/niemand/html, and that folder contains an image with the name pepe.jpg, in other words the path is /home/niemand/html/Pictures/pepe.jpg.

greenpeace is correct in the advice given. And htmldog is a good site to learn this stuff.

I suggest that you study the concepts of absolute and relative paths. 

And good luck with your studying - you should find it fun.

---


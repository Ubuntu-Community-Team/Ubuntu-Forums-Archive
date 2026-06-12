---
title: "JavaScript image gallery CSS!!! HELP!"
date: 2009-07-17
forum: Programming Talk
---

### Post by JimBuntu on 2009-07-17
Ok, sorry for the capital letters but I'm pulling my hair out here. So, I am fairly new to website development and I'm am currently developing a site for my model wife. I am creating a pictures page and trying to create it with JavaScript. I want basically a left side of the page with a bunch of thumbnails that when hovered over show the full size image on the right side of the page. I get the code below but don't know how to use CSS to position the full size image away from the thumb. Is there a way to id the 'full.png' image? How do I name/id, or get JavaScript or CSS to recognize that image? 

```
<img src="thumb.png" id="image1" onMouseOver="window.document.image1.src='full.png';"
onMouseOut="window.document.image1.src='thumb.png';"/>
```

Any help would be appreciated!!

By the way... Yes, I know how to create this effect with just HTML and CSS by using the <a><img/><span><img/></span></a> but I'm reading two Javascript books right now and would like to do it using this language.

---

### Post by ad_267 on 2009-07-17
I think you would want to use something more like:
```
<img src="thumb_1.png" id="image1" onMouseOver="window.document.getElementById("fullimg").src='full_1.png' ;"
onMouseOut="window.document.getElementById("fullimg").src='blank.png' ;"/>
```

So you have a second image on the right which you change the source of, rather than changing the source of your thumbnail on the left.

I'm sure this kind of gallery has been done thousands of times before, you should be able to find one you can download.

Edit: Maybe something like this: [http://www.monc.se/galleria/](http://www.monc.se/galleria/)

---

### Post by JimBuntu on 2009-07-17
So, where is the img 'full_1.png' being set to the id of 'fullimg'?

by the way, that gallery link is pretty good.

---

### Post by ad_267 on 2009-07-17
Edit: I replied before you edited your post (don't you hate that) so this might not make a lot of sense to anyone else reading:

Ok maybe we weren't quite on the same page. I was thinking of having a single main image on the right with id="fullimg" which you change the source of (from "blank.png" to "full_1.png") when hovering over a thumbnail on the left, rather than a whole bunch of images which you change the visibility of. That way would definitely work too, and would probably preload the images. Something like:

```
<img src="thumb_1.png" id="image1" onMouseOver="window.document.getElementById("fullimg1").style.visibility='visible' ;"
onMouseOut="window.document.getElementById("fullimg1").style.visibility='hidden' ;"/>
```

An object still takes up space when hidden though so you probably want to make all the photos absolutely positioned within the div or something.

I'm definitely not an expert on javascript by the way, I usually use the prebuilt stuff. A good resource is the w3schools site if you haven't found it already: [http://www.w3schools.com/js/default.asp](http://www.w3schools.com/js/default.asp)

---

### Post by JimBuntu on 2009-07-17
Yes, I love w3schools. I don't know why I havn't thought of the "getElementById()" method... Sometimes it's just the little things that count. Sorry, I edited the first reply cause I didn't think it made sense. Thanks again, I can definately work with this.

---


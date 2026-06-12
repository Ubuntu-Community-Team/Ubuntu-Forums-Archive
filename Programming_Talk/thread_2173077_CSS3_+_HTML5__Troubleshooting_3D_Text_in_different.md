---
title: "CSS3 + HTML5:  Troubleshooting 3D Text in different browsers"
date: 2013-09-07
forum: Programming Talk
---

### Post by Drone4four on 2013-09-07
I’ve got a sample of some CSS and HTML rendered in 4 different browsers: Firefox 23, Konqueror 4.10.5, Epiphany 3.6.1 and Chromium 28.
See here: [http://i.imgur.com/gjUpazO.jpg](http://i.imgur.com/gjUpazO.jpg)
The text rendered by h1 looks most attractive in Konqueror. The text rendered by h2 looks ugliest in Konqueror. The text rendered by h3 looks identical in all 4 browsers. The text rendered by h4 looks not quite as good in Konqueror.
I suppose the reason why there is a discrepancy in how 3D text is rendering in Konqueror involves a nuanced technical explanation. It prolly has something to do with a variation of Webkit usage. My question is how do I make my 3D text render in Firefox, Chromium and Epiphany the way it does in h1 in Konqueror? Is that even possible?

---

### Post by llanitedave on 2013-09-07
Welcome to the world of web "standards".  The only thing I can think of is to identify the client browser and present the best presentation for each based on trial and error.  It's best if you're bald when you start out.

---

### Post by Drone4four on 2013-09-09
Is [this]("http://www.w3.org/community/webed/wiki/Optimizing_content_for_different_browsers:_the_RIGHT_way") what you were referring to, llanitedave? It's w3c's documentation on tailoring your code for different web browsers.

Here is the sample of the code I was troubleshooting in different browsers:

```
h1 {
	font-family: Garamond, serif;
	text-shadow: 0 1px 0 #ccc,
               0 2px 0 #c9c9c9,
               0 3px 0 #bbb,
               0 4px 0 #b9b9b9,
               0 5px 0 #aaa,
               0 6px 1px rgba(0,0,0,.1),
               0 0 5px rgba(0,0,0,.1),
               0 1px 3px rgba(0,0,0,.3),
               0 3px 5px rgba(0,0,0,.2),
               0 5px 10px rgba(0,0,0,.25),
               0 10px 10px rgba(0,0,0,.2),
               0 20px 20px rgba(0,0,0,.15);
	color: #CCC;
}
```

Every browser rendered it differently.  For my site I went with this more basic code instead:

```
h1 {
 	text-shadow: 0px 2px 2px rgba(1, 2, 2, 1); 
	color: #black
}
```


By the way, llanitedave: That jab at my balding hair wasn't very nice, you know? I was balding when I first picked up DOS-1.0. Beginning web-design today I'm menopausal ha ha ha

---

### Post by Heald on 2014-08-14
The problem can be with CSS styles, did you try other example of 3D text? Some styles can cross-browser they will work in the same way in many browsers. Try this one: [pseudo 3D text using text-shadow property in CSS3]("http://basicuse.net/articles/pl/textile/html_css/css3_pseudo_3d_text_using_text_shadow_property") Also, pay your special attention that all 3D text examples are made using CSS trick, there is no property for this effect that is also a reason why some browsers don't show it in the proper way.

---

### Post by fkkroundabout on 2014-08-15
probably easier just to use images, for cross browser consistency

---

### Post by Heald on 2014-08-20
but, it's time to use new features of browsers. How many years are we going to be stuck with images?

---


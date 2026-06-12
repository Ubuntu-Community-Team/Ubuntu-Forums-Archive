---
title: "Need some help with jquery..."
date: 2008-05-02
forum: Programming Talk
---

### Post by hockey97 on 2008-05-02
Hi I have been working on a script using jquery.

I am trying to use the hover function and also the fadeIn and fadeOut functions.

I made a script but so far it is now working at all. I copied 

and pasted the example on the jquery website and it works so 

that told me that I have the jquery.js file added correctly and 

ruled out that it wasn't becuse I didn't add the jquery properly.

So let me first tell you what I am trying to do. Ok so I have an
 
image on my html page  this image has css properties to it 

which is called #image. I want to make a hidden layer fade in 

and fade out based on the mouse if the mouse is over the image 

then a layer will fade in and if the mouse goes off the image 

then it would fade out. What I am making is the user can hover 

it's mouse over the image and like a table or window fades in 

like a table but in the table will be images but if the mouse 

goes off the image and is not on that table then it fades out.

Here is what I got so far:

```
$("document").ready(function() {});
var hide=false;
$("#image").hover(
      function () {
	  if (hide) clearTimeout(hide);
     $("#ul1").fadeIn("slow");},
	 function () {
	 hide=setTimeout(function(){
$("#ul1").fadeOut("slow")},250);});
```

---

### Post by hockey97 on 2008-05-02
I just want to know in jquery/javascript how would you reference css definitons??


I have some idea like $("#mycss") then js goes here ect.

I know for the fact that you can write css code in js like

$("#mycss") .css$(background:image...ect)

I am refering to jquery using jquery lib.

I am just confused how I can use the css definitions in javascript using jquery making the hover and fadeIn,fadeOut effects ect.

can anyone give me an example or refer me to a good example using css with jquery witht he hover and FadeIn,FadeOut functions.

---

### Post by hockey97 on 2008-05-03
I need help  with the jquery function hover and fadin/fadeout functions.

Just need to know how to use the css elements in the jquery area...

any Idea???

---


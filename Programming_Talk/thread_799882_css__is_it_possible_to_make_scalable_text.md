---
title: "css : is it possible to make scalable text"
date: 2008-05-19
forum: Programming Talk
---

### Post by anfractuosities on 2008-05-19
is there any way to make text scale fluidly, like it would with an image?  

I am making a page where everything resizes, but I cannot get the text to change.

---

### Post by LaRoza on 2008-05-19
> **anfractuosities said:**
> is there any way to make text scale fluidly, like it would with an image?  

I am making a page where everything resizes, but I cannot get the text to change.

Make the font size based on em lengths.

[http://www.bigbaer.com/css_tutorials/css_font_size.htm](http://www.bigbaer.com/css_tutorials/css_font_size.htm)

---

### Post by anfractuosities on 2008-05-19
but doesnt this make the font size change depending on the _font size_ of it's parent element?

I want it to change based on the _height and width_ of the fluidly scaling containing div.



here is the page

[http://uhlan.ca](http://uhlan.ca)

---

### Post by LaRoza on 2008-05-19
> **anfractuosities said:**
> but doesnt this make the font size change depending on the _font size_ of it's parent element?

I want it to change based on the _height and width_ of the fluidly scaling containing div.

here is the page

[http://uhlan.ca](http://uhlan.ca)

Text doesn't quite work like that. You can have the text as an image if you want it to be "fluid" like the image.

---

### Post by anfractuosities on 2008-05-19
thats what i fugured the last resort would be...thanks

---

### Post by OliW on 2008-05-19
Or use javascript...

---

### Post by anfractuosities on 2008-05-19
while we are at it...could I ask you another question?  Is there a way to get an embedded flash object to be behind the imgs on the page? 

 I have tried z-index in css.

This is my xhtml for the object

```

<object id="musicbox" >
<param name="movie" value="musicbox.swf" />
<param name="wmode" value="transparent" />
<embed src="musicbox.swf" type="application/x-shockwave-flash" wmode="transparent" width="550" height="400" id="musicboxxx" />
</object>

```

and here is the result 
[http://uhlan.ca/music.html](http://uhlan.ca/music.html)




**actully it only seems to do this in my firefox 3  works fine at work on ie.

---

### Post by LaRoza on 2008-05-19
> **anfractuosities said:**
> while we are at it...could I ask you another question?  Is there a way to get an embedded flash object to be behind the imgs on the page? 

 I have tried z-index in css.


You can objects "behind" other objects, however, this may not work the same in all browsers. The imgs would have to be transparent to see it also.

---


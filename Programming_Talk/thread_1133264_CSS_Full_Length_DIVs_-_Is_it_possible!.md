---
title: "CSS Full Length DIVs - Is it possible?!"
date: 2009-04-22
forum: Programming Talk
---

### Post by mdawg414 on 2009-04-22
I have spent the last 6 hours reading everything I could find on this issue but none of the solutions worked for me. I am trying to switch from tabled layouts in HTML to using CSS and DIVs. However, I am trying to do the simplest of things and I cannot get it to work with DIVs. I want 2 columns, both the same height, that are the height of the larger column. So if the right column has more text, the background of the left column should follow it down.

Here is the file I am working with now: [http://mattdodge.net/test.htm]("http://mattdodge.net/test.htm")

The CSS is embedded inside the page. It should be pretty self explanatory what I want: the red column to be the same height as the blue column and the green to fill in in-between.

I would rather not use JavaScript or too much absolute positioning and the height:100% thing seems to not be working (it only makes it 100% of the browser, not the entire document). I've tried using min-height, overflow, and height but none of them seem to be working.

Can any CSS expert help me with this one? Thanks so much

---

### Post by samjh on 2009-04-22
Take a look at: [http://www.ejeliot.com/blog/61](http://www.ejeliot.com/blog/61)

The solutions suggested are... ugly, but if you must use CSS, one must do what one needs. ;)

There is really nothing wrong with using tables for what you're trying to do, except purists.  Just think of the table as an item to contain data, rather than a means to control layout.

---

### Post by mdawg414 on 2009-04-22
Thanks Sam.

I looked at the faux columns thing earlier as well, should have mentioned that but:
1. I didn't like the idea of having to create images containing the colors I wanted to use.
2. I couldn't even get those to work since the faux column div wouldn't stretch to the length of the content div.

Am I seeing things or does it seem like if I nest a div inside of another, the outer div doesn't take the dimensions of the inner one.
For example: 
<div id="A">
  <div id="B>...</div>
</div>
As div B grows, shouldn't div A grow with it???

---

### Post by TheOrangePeanut on 2009-04-22
I use javascript to do that, though it is not the most elegant solution.  You might consider that.

---

### Post by mdawg414 on 2009-04-22
Yeah Javascript works but it just seemed strange to me that it wouldn't work like that. I'm just too Web 1.0 and used to tables haha.

---


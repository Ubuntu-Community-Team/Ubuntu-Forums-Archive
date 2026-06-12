---
title: "Entering poems in html/css"
date: 2010-11-09
forum: Programming Talk
---

### Post by rcayea on 2010-11-09
Hi Folks,

I was wondering, as I am a novice website programmer, if there is a better way of entering poems on my website other than always using the <p> tag?

So far I have to always enter the <p> tag for every poem line. Any ideas to make it quicker to maybe add a whole poem at once and keep the format?

Thanks,
Randy

---

### Post by nvteighen on 2010-11-10
> **rcayea said:**
> Hi Folks,

I was wondering, as I am a novice website programmer, if there is a better way of entering poems on my website other than always using the <p> tag?

So far I have to always enter the <p> tag for every poem line. Any ideas to make it quicker to maybe add a whole poem at once and keep the format?

Thanks,
Randy

I'd use a single <p></p> block and use <br/> for line-breaks... Think of <br/> as your Enter key, while the <p></p> is rather a block to specify whhere your paragraph begins, so that later, it'll be much easier to apply a CSS stylesheet to that paragraph and format it nicely... but that's another story.

(I used XHTML tags above... If you're using HTML4, you should use <br> instead of <br/>, but <p></p> is specified as a block in the standard... I know, <p> is "allowed" by browsers, but it's not the way to do it, really)

---

### Post by Some Penguin on 2010-11-10
[http://www.w3schools.com/tags/tag_pre.asp](http://www.w3schools.com/tags/tag_pre.asp) ?

---

### Post by worseisworser on 2010-11-10
> **rcayea said:**
> Hi Folks,

I was wondering, as I am a novice website programmer, if there is a better way of entering poems on my website other than always using the <p> tag?

So far I have to always enter the <p> tag for every poem line. Any ideas to make it quicker to maybe add a whole poem at once and keep the format?

Thanks,
Randy

The PRE tag will keep the format of the source text.

---

### Post by Goldfissh on 2010-11-10
You use <p> for every single new line?

Just use <br /> for a line break - you can still wrap the paragraph together using <p> tags if you want.

---

### Post by rcayea on 2010-11-10
Thanks for the replies that were helpful. It looks like the pre tag is what I was looking for. 

Thanks.

---

### Post by Goldfissh on 2010-11-10
Great, glad you got what you were looking for! :D

---


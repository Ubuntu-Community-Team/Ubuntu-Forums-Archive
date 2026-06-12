---
title: "HTML/CSS Alignment"
date: 2012-01-09
forum: Programming Talk
---

### Post by CoffeeRain on 2012-01-09
Hi! I have a div that I want to be aligned in the center. This works. I have text in the div, that I want to be aligned left, and some more that I want to be aligned right. I can't figure out how to override the cascading part of CSS. Is it possible? If not, what could I do to make it work?

---

### Post by KdotJ on 2012-01-09
Hmm, do you want these pieces of text to be side by side? or one below the other?

---

### Post by CoffeeRain on 2012-01-09
The one that should be on the right should be lower.

---

### Post by KdotJ on 2012-01-09
Ok, My CSS knowledge isn't fantastic but I'll have a go... you could create two classes in the CSS that defines the positioning:

```

.right_content {
    float: right;
    /* other attrs you want */
}

.left_content {
    float: left;
    /* other attrs you want */
}

```
Then in the HTML, inside your centred div...:

```
<div>
     <p class="left_content">This content will be on the left</p>
     <p class="right_content">This content will be on the right</p>
</div>
```
I haven't tested this though

---

### Post by CharlesA on 2012-01-09
You can also use span tags. I do that for stuff like bold or italics.

```
h1,h2 {
text-align: center;
}

h2.left {
text-align: left;
}
```

In my case, I use CSS classes to tell the browser I want some text left aligned and some center aligned. The same can be used for <p> tags, or other <div> tags too.

---

### Post by KdotJ on 2012-01-09
I'd go for the span tags...

---

### Post by CoffeeRain on 2012-01-09
OK... I have the span tags, but now nothing works. The div is now on the left and the text inside is centered. :(

---

### Post by mssever on 2012-01-09
Theoretically, DIV is better than SPAN. SPAN is an inline tag, and inline tags can't have their alignment set. DIV is block-level, where alignment is relevant. Of course, you can make either tag have either format, but why not use them the way they're intended?

---

### Post by CharlesA on 2012-01-09
Post your CSS please.

> **mssever said:**
> Theoretically, DIV is better than SPAN. SPAN is an inline tag, and inline tags can't have their alignment set. DIV is block-level, where alignment is relevant. Of course, you can make either tag have either format, but why not use them the way they're intended?

Didn't think of that. I've only used span tags to apply effects - bold/color/italics.

Thanks.

---

### Post by dazman19 on 2012-01-09
If you have tried these peoples CSS, then to answer your question you need to find what CSS is overriding their CSS.

The trick with the way CSS overrides works this way. 
1) inline styles are most precident, (dont use inline styles unless you absolutely have to)
2) the styles set in the document head inside the style tags is next, <head><style></style></head>
3) and finally the rest of the css is applied. In order in which it was passed. (it will include the .css files and the css closer to the bottom will override the top stuff if it can). 

On top of that, then you have selector presidence.

So if you take the following code and identify your divs like this: 
<div>
    <div class="mydiv">some content</div>
</div>

then this css will override the other css that is only identified by its class selector.

e.g. this:
div div.mydiv {
    margin: 20px;
}
will override this
div.mydiv {
   margin: 30px;
}
OR this
.mydiv {
   margin: 35px;
}

so in my case the margin on my div.mydiv will be 20px because it is the most specific.

I highly reccomend you use google chrome or firefox with firebug to see how the CSS is overriding your CSS. It will tell you what style sheet and what lines on the style sheet are overriding. and the best way to fix it is to be as specific as possible with your selectors.

I really still have loads of problems with CSS, the more you do it the better you will get.

---

### Post by CoffeeRain on 2012-01-09
Here is my CSS

```

div.says {height:300px; width:700px; overflow:auto; text-align:center;}
#delete_span {float:right;}
#says_span {padding-top:10px; color:black; float:left;}

```

div.says is the div that contains these two spans.

Here is my HTML

[HTML]<div class='says'><span id='says_span'>Text for my span</span><br/><a id='delete_span' href=delete.php?p=1>Delete</a></div>[/HTML]

---

### Post by mssever on 2012-01-10
> **CoffeeRain said:**
> Here is my CSS

```

div.says {height:300px; width:700px; overflow:auto; text-align:center;}
#delete_span {float:right;}
#says_span {padding-top:10px; color:black; float:left;}

```div.says is the div that contains these two spans.

Here is my HTML

[HTML]<div class='says'><span id='says_span'>Text for my span</span><br/><a id='delete_span' href=delete.php?p=1>Delete</a></div>[/HTML]
Read up on the differences between block-level and inline elements. You *must* know which each tag defaults to. You can, of course, change any tag. However, I think you're using incorrect tags.

First, try to use a tag that fits the type of content. For example, if "#says_span" is a paragraph, it should use a P tag. If there's no tag that has a meaning which fits your markup, then you need the generic block-level tag (DIV). Remember, things like float (or anything that moves a block of text around a significant distance) can only apply to block-level elements.

But really, before you go any farther, read up on these things so that you understand them.

---

### Post by CoffeeRain on 2012-01-10
Thanks, I'll look at those and see what changes I can make. :)

---

### Post by CoffeeRain on 2012-01-10
I switched a couple of things according to your suggestions, and after thinking about it for a bit, I decided to use a table with no border. This worked great! Thanks for all your suggestions and ideas! :)

---

### Post by CharlesA on 2012-01-10
Using tables for alignment makes things messy, and you are supposed to use CSS for that.

It was be a better idea to go thru your CSS and make sure it's properly written, maybe run it through a CSS validator to make sure that everything is written correctly.

You can find one here:
[http://jigsaw.w3.org/css-validator/](http://jigsaw.w3.org/css-validator/)

---

### Post by CoffeeRain on 2012-01-10
OK, the reason I used a table was because CSS was confusing and not working. I'll try that later. Thanks for the link. I'm sure that will be a great resource for the rest of my web development journey. :)

---

### Post by CharlesA on 2012-01-10
> **CoffeeRain said:**
> OK, the reason I used a table was because CSS was confusing and not working. I'll try that later. Thanks for the link. I'm sure that will be a great resource for the rest of my web development journey. :)
Makes sense. :)

Best of luck when you decide to take a look at it again.

---

### Post by CoffeeRain on 2012-01-10
Thanks!

---


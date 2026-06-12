---
title: "I'm struggling with the CSS counter mechanism for controlling numbering of &lt;ol&gt; tags"
date: 2017-02-17
forum: Programming Talk
---

### Post by s3a on 2017-02-17
Hello to everyone who's reading this. :)

I'm really struggling with CSS counter stuff. Basically, all I am trying to do is to make the numbering of an ordered list continue when the ordered list goes from row n to row n+1.

The following is my HTML syntax.:
[http://pastebin.com/hw8rmUWB](http://pastebin.com/hw8rmUWB)

The following is my CSS syntax, where the last three selectors are what I'm struggling with (as indicated by the comment).:
[http://pastebin.com/cYFynxAs](http://pastebin.com/cYFynxAs)

Lastly, here's a visual representation of what I am aiming for, in Question 1's Figure 2.:
[https://www.docdroid.net/P6VZNB1/soen287-winter2017-assignment-2.pdf.html#page=3](https://www.docdroid.net/P6VZNB1/soen287-winter2017-assignment-2.pdf.html#page=3)

Could someone please help me figure out why the numbering is showing twice in each table cell (despite the CSS incrementation seemingly working semi-correctly)? It seems like the CSS is creating some different numbering, rather than modifying the default numbering of unordered lists.

Any help in figuring out why what I am trying to accomplish is not working would be GREATLY appreciated!

---

### Post by CharlesA on 2017-02-17
That's a new one for me, but have you tried checking here?
[https://www.w3schools.com/CSSref/pr_gen_counter-increment.asp](https://www.w3schools.com/CSSref/pr_gen_counter-increment.asp)

You can play around with it. :)

---

### Post by s3a on 2017-02-17
> **CharlesA said:**
> That's a new one for me, but have you tried checking here?
[https://www.w3schools.com/CSSref/pr_gen_counter-increment.asp](https://www.w3schools.com/CSSref/pr_gen_counter-increment.asp)

You can play around with it. :)
Thanks for the answer. :)

The thing is, I saw that website, but I still don't understand the concept(s) well enough. In fact, I've looked at so many websites, including various YouTube videos, but I'm still confused. :( It may be because I'm stressed out, but I think this is one of the things where I would learn best by having my particular problem solved.

---

### Post by &amp;KyT$0P# on 2017-02-18
Err, why are you using CSS counters?  Why not use the [FONT=Courier New]start[/FONT] attribute of [[FONT=Courier New]<ol>[/FONT] element]("https://developer.mozilla.org/docs/Web/HTML/Element/ol")?

Since this looks to be a homework assignment, I'm done here.

---

### Post by norobro on 2017-02-18
You're making it more complicated than it needs to be. There's no need to span two <td>s. Just nest the lists inside each other as necessary and style everything with css. And as halogen2 says use the <ol> start attribute.

---


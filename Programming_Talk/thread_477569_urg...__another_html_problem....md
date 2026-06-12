---
title: "urg...  another html problem..."
date: 2007-06-18
forum: Programming Talk
---

### Post by locke.dragon on 2007-06-18
ok.  here's the site...  again...

[http://paperclipsandscrambledeggs.blogspot.com/](http://paperclipsandscrambledeggs.blogspot.com/)

see the navigation?  i can't figure out how to get the little icons to center in the little buttons.  i don't want them that close to the top.  can someone please help?

this is what i have right now.

```

 <div id='navigation'>
 <ul>
 <li class='selected'><a expr:href='data:blog.homepageUrl'>blog<img src='http://i159.photobucket.com/albums/t147/clipsandeggs/blog.gif'/></a></li>
 <li><a href='http://www.flickr.com/photos/paperclipsandscrambledeggs/'>flickr<img src='http://i159.photobucket.com/albums/t147/clipsandeggs/aboutme.gif'/></a></li>
 <li><a href='http://www.thelinuxdock.blogspot.com/'>leaflet<img src='http://i159.photobucket.com/albums/t147/clipsandeggs/toolbox.gif'/></a></li>
 <li><a href='http://www2.blogger.com/profile/13088056030686503922'>about me<img src='http://i159.photobucket.com/albums/t147/clipsandeggs/portfolio.gif'/></a></li>
 <li><a href='mailto:paperclipsandscrambledeggs@gmail.com'>email<img src='http://i159.photobucket.com/albums/t147/clipsandeggs/message.gif'/></a></li>
 </ul>
 </div>

```

---

### Post by Modred on 2007-06-18
Here's one solution:

**EDIT:** I think I misunderstood your question.  Bah, you want it centered vertically, and I centered it all the way around.

Here's another attempt in your CSS:
```

a img {
  vertical-align: middle;
}
```

---

### Post by arsenic23 on 2007-06-18
You should also be able to put the text and the image in seperate divs and give them a class that's just float:left, .... I think - I don't get to play much with html/css anymore.

---

### Post by Modred on 2007-06-18
> **arsenic23 said:**
> You should also be able to put the text and the image in seperate divs and give them a class that's just float:left, .... I think - I don't get to play much with html/css anymore.

I tried doing that, but the image just stays at the top of the box.  The **vertical-align** CSS property is probably what will work best.  I just tested it in Firefox 2, IE6 and IE7, and it appears to work in all three.

---

### Post by locke.dragon on 2007-06-18
is the vertical align what you originally suggested (i haven't had time to try anything yet).

---

### Post by Modred on 2007-06-18
I had originally gone in and made the images a background image, centered with no-repeat.  That put the image behind the text, but then after arsenic's post I reread your original request and it sounded more like you just wanted to change the vertical alignment.  I saw "center" and went a little above and beyond.

But the vertical-align should get the images down on the same level as the text.

---

### Post by locke.dragon on 2007-06-18
it may be asking too much, but could you just edit the code i gave and post that?  i've been trying to fix this for about two hours and i'm kinda sick of it.

---

### Post by Modred on 2007-06-18
> **locke.dragon said:**
> it may be asking too much, but could you just edit the code i gave and post that?  i've been trying to fix this for about two hours and i'm kinda sick of it.

Except the change doesn't involve that HTML code at all.  I don't know how much control you have over the CSS of your page, but assuming you can edit the CSS yourself, you only need to add one line.

Find the **a img** block in the CSS, then inside that block add **vertical-align:middle;**.  That's it.

---

### Post by locke.dragon on 2007-06-18
it worked!!!  thank you thank you thank you thank you!!!

---


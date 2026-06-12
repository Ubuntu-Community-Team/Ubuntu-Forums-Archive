---
title: "Website Design"
date: 2012-05-09
forum: Programming Talk
---

### Post by emoguitarist06 on 2012-05-09
How do I implement a fixed side column?

Here is an example:
[INDENT][http://www.unt.edu/identity/history.htm](http://www.unt.edu/identity/history.htm)[/INDENT]
Notice how the left side column doesn't move when you scroll down the page?

Thank You!

---

### Post by PaulM1985 on 2012-05-09
You can do this using frames:
[http://www.w3schools.com/html/html_frames.asp](http://www.w3schools.com/html/html_frames.asp)

To get something similar set the border to be 0.

Paul

---

### Post by CharlesA on 2012-05-09
I don't see the bar on the left in the source, but it's likely using CSS to have it set at a fixed position.

---

### Post by emoguitarist06 on 2012-05-09
> **PaulM1985 said:**
> You can do this using frames:
[http://www.w3schools.com/html/html_frames.asp](http://www.w3schools.com/html/html_frames.asp)

To get something similar set the border to be 0.

Paul

Thanks Paul! I'll check this out and reply again after a successful attempt or a few failures ;)

> **CharlesA said:**
> I don't see the bar on the left in the source, but it's likely using CSS to have it set at a fixed position.

I noticed that as well! I was maybe thinking it was one of the javascripts that you see in the source?

---

### Post by CharlesA on 2012-05-09
> **emoguitarist06 said:**
> 
I noticed that as well! I was maybe thinking it was one of the javascripts that you see in the source?

Could be. I would suggest not using frames as they can make the whole thing messy.

---

### Post by emoguitarist06 on 2012-05-09
> **CharlesA said:**
> Could be. I would suggest not using frames as they can make the whole thing messy.

From [http://www.w3schools.com/html/html_frames.asp](http://www.w3schools.com/html/html_frames.asp)
"ATTENTION. Do not expect frames to be supported in future versions of HTML."

LOL

I am thinking the same

Any other ideas and how to implement such a thing?

-thanks

---

### Post by CharlesA on 2012-05-09
CSS would work fine, but the alignment might be off in some browsers.

I tried using something like that for a vertical nav bar but ended up going with a horizontal one instead.

Sticking with KISS > trying to be fancy.

---

### Post by emoguitarist06 on 2012-05-09
> **CharlesA said:**
> CSS would work fine, but the alignment might be off in some browsers.

I tried using something like that for a vertical nav bar but ended up going with a horizontal one instead.

Sticking with KISS > trying to be fancy.

I tried all kinds of CSS combinations to no avail.
Currently my side panel (that does move with the page) has a fixed width and is floating left and my body is floating right.

Is your site still active?

---

### Post by CharlesA on 2012-05-09
> **emoguitarist06 said:**
> 
Is your site still active?

Yes, you can find a link to it in my profile here.

---

### Post by lykwydchykyn on 2012-05-09
Basically, what they did on that site is create an image for the side-bar, set it as the background of the body with the position fixed top-left.

Then the content is all in a wrapper div with a fixed margin the width of the lefthand bar.

If you inspect the page with something like firebug or webkit developer tools, check out the css for the body tag.  It's all there.

---

### Post by emoguitarist06 on 2012-05-09
I like it CharlesA! Actually I think it like it better than my original idea. However I am still going to try to implement it as a side column.

It's late where I'm at but I'm going to play around with your source and css if you don't mind and reply with my results.

BTW: I noticed your sites are saved as php
I was initially saving my websites as php instead of html however the only problem I noticed is if i typed [www.mydomain.com/subdirectory](www.mydomain.com/subdirectory) into the url bar it wouldn't find/load the page! I HAD to to type [www.mydomain.com/subdirectory.php](www.mydomain.com/subdirectory.php) <--- with the .php at the end. With .html I don't have to do that.

Again this could be the newbie side of me lol

---

### Post by emoguitarist06 on 2012-05-09
> **lykwydchykyn said:**
> Basically, what they did on that site is create an image for the side-bar, set it as the background of the body with the position fixed top-left.

Then the content is all in a wrapper div with a fixed margin the width of the lefthand bar.

If you inspect the page with something like firebug or webkit developer tools, check out the css for the body tag.  It's all there.

If it was an image in the body wouldn't it NOT follow the page scroll down? I mean when you scroll down wouldn't the UNT logo disappear and stay at the top of the page?

---

### Post by CharlesA on 2012-05-09
> **emoguitarist06 said:**
> I like it CharlesA! Actually I think it like it better than my original idea. However I am still going to try to implement it as a side column.

Thanks!

> It's late where I'm at but I'm going to play around with your source and css if you don't mind and reply with my results.

BTW: I noticed your sites are saved as php
I was initially saving my websites as php instead of html however the only problem I noticed is if i typed [www.mydomain.com/subdirectory](www.mydomain.com/subdirectory) into the url bar it wouldn't find/load the page! I HAD to to type [www.mydomain.com/subdirectory.php](www.mydomain.com/subdirectory.php) <--- with the .php at the end. With .html I don't have to do that.

Again this could be the newbie side of me lol

If you are going into a subdirectory, it needs an index file - index.html or index.php otherwise it would just load a directory of everything in that directory.

> **emoguitarist06 said:**
> If it was an image in the body wouldn't it NOT follow the page scroll down? I mean when you scroll down wouldn't the UNT logo disappear and stay at the top of the page?

Set the image as fixed in the CSS. :)

---

### Post by emoguitarist06 on 2012-05-09
> **CharlesA said:**
> If you are going into a subdirectory, it needs an index file - index.html or index.php otherwise it would just load a directory of everything in that directory.

Well when I type charlesa.net/about into the URL Bar it doesn't load your about page! But typing charlesa.net/about.php does! I haven't really researched as to why this is... but I didn't see any reason not to use html vs php.

---

### Post by CharlesA on 2012-05-09
> **emoguitarist06 said:**
> Well when I type charlesa.net/about into the URL Bar it doesn't load your about page! But typing charlesa.net/about.php does! I haven't really researched as to why this is... but I didn't see any reason not to use html vs php.
about.php is just a file, not a folder. ;)

---

### Post by emoguitarist06 on 2012-05-09
> **CharlesA said:**
> about.php is just a file, not a folder. ;)

I'll get back to this in a new thread ;)

And within 24-hours i'll be posting more Q's about the side panel thingy on this thread

---

### Post by drmrgd on 2012-05-09
It's been a very long time since I wrote any CSS.  But, I'm fairly certain that this is very simple to do by just creating a fixed element on the page.  Just doing a quick Google search for something like "css fixed sidebar", I found a bunch of stuff for you to try, including this little snippet, which is something along the lines of what I was thinking to do in your CSS file:

```
body {
    width: 100%;
    height: 100%;
    padding: 0;
    margin: 0;
    overflow: hidden;
}
#sidebar {
    float: left;
    width: 25%;
    max-width: 350px;
    height: 100%;
    overflow: hidden;
}
#main {
    overflow-x: hidden;
    overflow-y: auto; 
    height: 100%;  
}
```

Definitely stay away from frames, though.  That's so 2000 :biggrin:

---

### Post by emoguitarist06 on 2012-05-09
> **drmrgd said:**
> It's been a very long time since I wrote any CSS.  But, I'm fairly certain that this is very simple to do by just creating a fixed element on the page.  Just doing a quick Google search for something like "css fixed sidebar", I found a bunch of stuff for you to try, including this little snippet, which is something along the lines of what I was thinking to do in your CSS file:

```
body {
    width: 100%;
    height: 100%;
    padding: 0;
    margin: 0;
    overflow: hidden;
}
#sidebar {
    float: left;
    width: 25%;
    max-width: 350px;
    height: 100%;
    overflow: hidden;
}
#main {
    overflow-x: hidden;
    overflow-y: auto; 
    height: 100%;  
}
```

Definitely stay away from frames, though.  That's so 2000 :biggrin:

I tried all kinds of combinations of this css but I couldn't get it working.
Also
```
overflow-x & overflow-y
``` aren't even recognized

---

### Post by drmrgd on 2012-05-09
> **emoguitarist06 said:**
> I tried all kinds of combinations of this css but I couldn't get it working.
Also
```
overflow-x & overflow-y
``` aren't even recognized

Yeah, it's possible that's bum code.  Like I said, I just copied it form a link I found from a Google search, and although I'm not 100% sure the syntax is correct since it's been way too long since I've actually put together any CSS pages (I didn't recognize those variables either!), the basic idea seemed right on.  Anyway, if you look around for some CSS tips based around that idea, I think you'll be able to code what you want fairly quickly and easily.

As an aside, I remember going from just straight up HTML with frames and tables and whatnot to CSS, and being so happy at how much easier it was to do simple things.  I might have to look into webpage design again to see what the deal is with HTML5.

---

### Post by emoguitarist06 on 2012-05-15
Hahahaha wow I feel dumb

```
position: fixed;
```

is all i needed to add to my sidepanel div in my css style!

---

### Post by CharlesA on 2012-05-15
> **emoguitarist06 said:**
> Hahahaha wow I feel dumb

```
position: fixed;
```

is all i needed to add to my sidepanel div in my css style!
Haha. Sometimes the simplest things are the most well hidden. ;)

---


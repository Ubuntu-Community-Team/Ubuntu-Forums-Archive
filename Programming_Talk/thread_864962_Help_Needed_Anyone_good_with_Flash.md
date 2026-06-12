---
title: "Help Needed: Anyone good with Flash?"
date: 2008-07-20
forum: Programming Talk
---

### Post by Sand &amp; Mercury on 2008-07-20
I've been working on a website for a band, and have run into a problem making it that's driving me absolutely nuts. 

The problem is simply this: I have a Flash banner at the top of the main page, and buttons on it that are supposed to make the browser open different pages in an iframe on the main page. The code for the 'News' section button, for example, goes as follows:

```
on (release) {
getURL("news.htm", "inline");
}
```
(It's Actionscript 2.0 just FYI, I'm using Flash 8 in Wine)

I've implemented the inline frame on the page as follows:

```
<iframe name="inline" id="inline" src="news.htm" 
frameborder="0" height="454" width="582"></iframe>
```

I embedded the flash banner on the page exactly as the Adobe docs say to. The getURL script button is told to open the news.htm page inside the iframe named "inline", but insists on opening in a new window instead, as if the target was set to "_blank". I've tried everything I can think of to remedy this, to no avail. Mind you, changing the target for the getURL from "inline" to "_self" DOES open the new page in the current window instead of a new one, leading me to think that for some reason the flash document isn't bothering to look for the iframe I told it to. 

This has me at my wits' end, can anybody possibly offer some idea of why this is happening?

Sorry if this is the wrong place to post this btw, I wasn't quite sure of where to stick it.

---

### Post by zmjjmz on 2008-07-20
Are they in separate div boxes?

---

### Post by Sand &amp; Mercury on 2008-07-20
> **zmjjmz said:**
> Are they in separate div boxes?
They are, does that make any difference?

---

### Post by zmjjmz on 2008-07-20
> **Sand & Mercury said:**
> They are, does that make any difference?

Yeah, it's looking for "inline" in it's own div box.
I've had a similar problem like this before, but with an imagemap and not flash.
[http://cs.montclair.edu/weston/about/index.html](http://cs.montclair.edu/weston/about/index.html)
If you look at the code in that page, you'll see how we fixed it.

---

### Post by Sand &amp; Mercury on 2008-07-20
Hm... I tried both into the same div box. No dice. Same behavior as before. :/ Any other ideas?

---

### Post by Sand &amp; Mercury on 2008-07-21
*Undignified, ashamed bump*

---

### Post by Soeasy1 on 2008-07-21
Well, i haven't had much experience with using flash in webpages, but have you considered trying something like _parent.inline?
Just a suggestion, I'd be surprised if that works

---


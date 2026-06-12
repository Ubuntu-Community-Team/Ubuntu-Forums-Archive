---
title: "firefox, css problem"
date: 2006-12-21
forum: Programming Talk
---

### Post by tocleora on 2006-12-21
Hope I posted this to the right category. :)  I'm having problems getting a css border to work correctly in firefox.  Here's the style tag:

```
<style>
.titlebar {
	border-bottom: solid 1pt black;
	font-size: 14pt;
}
</style>
```

And here's the code in the page:

```

<div class="titlebar"><B>Newest Entries in <a href="#">Software</a></B></div>
<div class="titlebar"><B>Newest Entries in <a href="#">Articles</a></B></div>

```

That's all that's in there at the moment.  And the attached image is the results I'm getting.  As you can see the border on the second one for some reason is showin up thicker than the border above it.  Is there a work around or am I doing something wrong?

---

### Post by Suzan on 2006-12-21
Don't use "pt", try it with "px".

---

### Post by tocleora on 2006-12-21
Hmmm... That's really really really (really) weird... I actually tried px before posting this message and the border didn't show up at all.  Upon receiving this response I decided to try it again to verify that was the case.  It worked.  what's up?!  Oh well it's working. thanks! :)

---

### Post by JRaz on 2006-12-21
Im not sure if it makes a difference but I though you were meant to put them in this order, ```
border-bottom:1px solid black;
```

PS you can change black to #000 (hex) for shorter code.

---

### Post by tocleora on 2006-12-22
Apparently they can be in any order, here's a page from w3.org directly that has it another way.

[http://www.w3.org/Style/CSS/Test/CSS1/19981002/sec5520.htm](http://www.w3.org/Style/CSS/Test/CSS1/19981002/sec5520.htm)

---

### Post by ZuLuuuuuu on 2006-12-22
Sometimes it happens to me, too (I change something on css file but there is no change on browser display). But when I clear the cache of the browser the problem goes away.

---

### Post by finferflu on 2006-12-22
Are you using HTML instead of XHTML? I really suggest you to switch to XHTML, so you'll be alright with W3C in the future ;)

---

### Post by tocleora on 2006-12-23
> **finferflu said:**
> Are you using HTML instead of XHTML? I really suggest you to switch to XHTML, so you'll be alright with W3C in the future ;)

Is that the only reason, are there any other benefits besides (what looks like to be) cleaner formatting and future compatibility in switching?

---

### Post by tocleora on 2006-12-23
> **ZuLuuuuuu said:**
> Sometimes it happens to me, too (I change something on css file but there is no change on browser display). But when I clear the cache of the browser the problem goes away.

Yeah I usually do a Ctrl+F5 (help defines it as "reload, override cache"), most of the time it works if I'm having problems with something sticking.  But in this case I changed to px, the border disappeared, I changed back to pt, it came back, then I tried it again when suggested in the forum, and it worked.  I had to have done something wrong... I'll never know! :)

---

### Post by finferflu on 2006-12-23
> **tocleora said:**
> Is that the only reason, are there any other benefits besides (what looks like to be) cleaner formatting and future compatibility in switching?

As far as I know that's the main reason. HTML is regarded as a backwards language. I think the new features of the markup language will be incorporated in XHTML, so that HTML will not have any share in such an "evolution". Being up to date is always a good thing to do, I think :)

---

### Post by lloyd mcclendon on 2006-12-23
> **ZuLuuuuuu said:**
> Sometimes it happens to me, too (I change something on css file but there is no change on browser display). But when I clear the cache of the browser the problem goes away.

hold shift & click the refresh button to bypass the cache

also check out the cache status extension

---

### Post by finferflu on 2006-12-23
> **lloyd mcclendon said:**
> hold shift & click the refresh button to bypass the cache

also check out the cache status extension

Ah! nice one! I didn't know that trick!! Thanks a lot! :D

---


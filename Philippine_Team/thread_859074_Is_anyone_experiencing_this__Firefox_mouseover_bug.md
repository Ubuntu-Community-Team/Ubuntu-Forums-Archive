---
title: "Is anyone experiencing this? : Firefox mouseover bug"
date: 2008-07-14
forum: Philippine Team
---

### Post by jeffimperial on 2008-07-14
It's not a big deal, but a little irritating. When I hover my mouse pointer onto anything (link or almost anything) on a page, it's like Firefox thinks a mouseover description is to be displayed, but only a tiny box with no text appears. A bug perhaps?

---

### Post by loell on 2008-07-14
perhaps its the page itself? does it happen accross pages?

---

### Post by jeffimperial on 2008-07-15
> **loell said:**
> perhaps its the page itself? does it happen accross pages?
Yes it does (happen across pages); every page object that isn't supposed to have a mouseover description, that tiny box appears.

---

### Post by Samhain13 on 2008-07-15
The links or images in the pages might have empty title attributes. Firefox detects that there is a title for that element so it renders a box, but the box doesn't have anything in it since the title attribute of the focused element is empty.

Just a theory. :)

---

### Post by jeffimperial on 2008-07-15
> **Samhain13 said:**
> The links or images in the pages might have empty title attributes. Firefox detects that there is a title for that element so it renders a box, but the box doesn't have anything in it since the title attribute of the focused element is empty.

Just a theory. :)
I *do* get it as far as the theory there. Why I don't get is *why*. I created a static HTML page to see if it still happens. I have images and hyperlinks for which no mouseover attribute is assigned. Guess what, it still happens :(

---

### Post by Rui Pais on 2008-07-16
Hi.
Thats not, anyway, the default behavior of firefox...
you may have a bad/broken profile or a bad or non-compatible extension.
Try this, close all running firefox windows and from a console
```
firefox -safe-mode
```
to run disable extensions or 
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_BACKUP
``` 
and start firefox to get a clean fresh profile.

If the first works you need to run normally and remove extensions one by one till you find the guilty one.

If the second works you need to reinstall your extensions and themes on the new profile.

Good luck

---

### Post by Unwired on 2008-07-18
it happens to me I thought it is my laptop...

---

### Post by icodeme on 2008-10-28
I experience this too. But mine is worse. My cursor gets lost in mouseover :(

---


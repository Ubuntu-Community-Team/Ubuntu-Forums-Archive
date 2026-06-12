---
title: "Firefox 19.0.2 won't wrap text in resized window"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-03-09
Firefox 19.0.2 won't wrap text in resized window.
Is there a command to force it to wrap text?

---

### Post by andrew.46 on 2013-03-09
Hmmm... no such problem here with 19.0.2. Have a look at a page of mine that has a flexible layout:

[http://www.andrews-corner.org/slrn-windows.html](http://www.andrews-corner.org/slrn-windows.html)

This should resize and rewrap ok?

---

### Post by Kevin McCready on 2013-03-09
yep, your page is nice, so it must be something in the layout of [the page I'm looking at]("http://www.worldjournal.com/view/full_lit/21594574/article-%E5%91%B3%E8%A6%BA%E8%A8%98%E6%86%B6%E5%B8%B6%E6%88%91%E8%BF%94%E9%84%89%E9%81%8E%E5%B9%B4?instance=wjbk7").

---

### Post by andrew.46 on 2013-03-09
HTML and css for that page is an absolute mess, but fixed width given in *px* can be seen all over the layout and this is the problem that you have encountered. Rather than try to work out the convoluted html and css grab a copy of the web developer toolbar and see the needless complexity of the page.

---

### Post by Kevin McCready on 2013-03-09
Hmmm, thanks but I'm not terribly computer literate in terms of developer tools. I just want to be able to wrap it, on a live webpage. Is there a quick soln?

---

### Post by andrew.46 on 2013-03-09
> **Kevin McCready said:**
> Hmmm, thanks but I'm not terribly computer literate in terms of developer tools. I just want to be able to wrap it, on a live webpage. Is there a quick soln?

Well, it does not look pretty but Firefox has the native ability to view a page with no css at all. This is in View --> Page Style --> No Style. This is a test of the basic HTML of a page, have a look at my own page without styles and you will note that it is still usable, the Chinese page less so but at least the text is a little unwrapped. The web developer toolbar has the ability to selectively block css sheets which is a little fun. The real answer is for people to write their HTML properly :).

---

### Post by Kevin McCready on 2013-03-10
Thanks again. I turned off styles. But it meant my perapera app didn't work, so I created a temporary page for the text I'm translating.

---

### Post by andrew.46 on 2013-03-10
So you have a work-around that works for you? Just think if the page was set correctly this would not be necessary :)

---


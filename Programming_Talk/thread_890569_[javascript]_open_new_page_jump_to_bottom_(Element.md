---
title: "[javascript] open new page jump to bottom (ElementId/Value?)"
date: 2008-08-15
forum: Programming Talk
---

### Post by radical3 on 2008-08-15
Basically what i want to do is open up another website's page in a small window and jump to the relevant section (basically jump to the bottom) how can i achieve this?

the code below is what i have so far, it works, as in the page opens, but it opens at an irrelevant area, i dont want to lose traffic by having the page open with scroll bars, resizeable handle and all the other bells and whistles, so users will navigate away. 

*[SIZE="3"]javascript newbie please post full code, dont just recomend functions, fanx.[/SIZE]*

```
<Script Language="JavaScript">
function load() {
var load = window.open('http://www.domain.com','','scrollbars=no,menubar=no,height=400,width=400,resizable=no,toolbar=no,location=no,status=no');
}
// -->
</Script>


<a href="javascript:load()">Open Window</a>
```

---

### Post by LaRoza on 2008-08-15
> **radical3 said:**
> Basically what i want to do is open up another website's page in a small window and jump to the relevant section (basically jump to the bottom) how can i achieve this?

the code below is what i have so far, it works, as in the page opens, but it opens at an irrelevant area, i dont want to lose traffic by having the page open with scroll bars, resizeable handle and all the other bells and whistles, so users will navigate away. 

*[SIZE="3"]javascript newbie please post full code, dont just recomend functions, fanx.[/SIZE]*


Try window.scrollTo()

Check the net for references.

Sorry, this is programming talk, not get free code on demand ;)

---

### Post by radical3 on 2008-08-15
alright forget it then:(

---

### Post by LaRoza on 2008-08-15
> **radical3 said:**
> alright forget it then:(

Or you can give the location you want to scroll to an id and use the uri to tell it where to scroll. That would be easier.

Like: [http://ubuntuforums.org/showthread.php?p=5593610#post5593610](http://ubuntuforums.org/showthread.php?p=5593610#post5593610)

---


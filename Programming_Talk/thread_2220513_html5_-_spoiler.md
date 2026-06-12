---
title: "html5 - spoiler"
date: 2014-04-28
forum: Programming Talk
---

### Post by Marchello_Lippi on 2014-04-28
Hi all, 


how do I create spoiler in html5 ? 


What I mean... 


Let's say we have text "My need is to create spoiler". 
I want user first see "My need is ..." and when he or she clicks on it then it shows full text. 


How do I perform it?

---

### Post by pqwoerituytrueiwoq on 2014-04-28
that is simple HTML, JS, and CSS
```
<input type="button" value="Spoiler Warning" onclick="this.nextSibling.style.display='block';this.style.display='none'"/><div class="spoiler">
      <img src="http://tinyurl.com/ly62h5x"/><!-- sample content -->
</div>
```
your css should contain this
```
.spoiler{
     display:none;
}
```

---

### Post by Dane_Jorgensen on 2014-04-30
You can easily do that with javascript.   With jQuery, you can create a click handler

$("#your_link").click( ... do stuff ... );

and then you could use "toggle" which toggles between the .hide() and .show()

hide() and show() toggle the CSS display attribute.

---

### Post by slickymaster on 2014-04-30
Moved to the **Programming Talk** sub-forum.

---


---
title: "smooth scrolling in firefox"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Matt26 on 2008-10-10
this might seem like a weird question, but is there a way to correct sluggish/jerky (best descriptive words i can think of at the moment) scrolling in firefox?  when i click on the scrollbar on the right side of most pages and try scrolling down, the page typically scrolls rather slowly and sometimes a bit unresponsive.  any suggestions?  thanks.

---

### Post by sparkyjoe34 on 2008-10-10
I believe the setting you are looking for is in tools at the top of the browser. I'm at work right now and they only use IE so sorry I can't give you better directions.

---

### Post by Therion on 2008-10-10
Smooth Scrolling Extension:  [https://addons.mozilla.org/en-US/firefox/addon/5846](https://addons.mozilla.org/en-US/firefox/addon/5846)

---

### Post by Matt26 on 2008-10-10
> **Therion said:**
> Smooth Scrolling Extension:  [https://addons.mozilla.org/en-US/firefox/addon/5846](https://addons.mozilla.org/en-US/firefox/addon/5846)

thanks, that seems to have improved the scrolling a bit, unfortunately i still notice a bit of lag when scrolling...

---

### Post by AlexBellisBrown on 2008-10-10
Could be due to a not so powerful CPU?

---

### Post by afeasfaerw23231233 on 2008-11-19
Yes, smooth scrolling is sluggish in firefox and epiphany especially when there are flash objects on the page. The only way for me is to disable smooth scrolling. 
I don't think it is a cpu issue. My box is a P4 1.8G (though it is old) and IE6 just scrolls smoothly but firefox and epiphany don't.

edit: FF3 seems scrolling a bit smoother than FF2

---

### Post by CLomax on 2008-11-19
Compiz effects tend to slow down smooth scrolling.

---

### Post by lakersforce on 2008-11-19
Old thread, I know, but the usual question would be if you have direct rendering enabled?

```
glxinfo
```

should amongst other things display
```

direct rendering: yes
```

---

### Post by tangibleorange on 2008-11-19
compiz is almost certainly responsible. try turning it off and then scrolling.

---


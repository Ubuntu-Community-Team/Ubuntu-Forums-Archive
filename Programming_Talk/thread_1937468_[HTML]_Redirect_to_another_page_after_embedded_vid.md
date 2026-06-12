---
title: "[HTML] Redirect to another page after embedded video ends"
date: 2012-03-07
forum: Programming Talk
---

### Post by Royk14 on 2012-03-07
Hi, this is my first time using html, so I don't understand much of this.

I'm trying to create a main page with info which has an intro page with a video. I want my intro page to redirect to the main page when the video ends. How can I do that?

this is the code I have with the video:
<embed src="index_vid.flv" controller="false" loop="false" autoplay="true" height="480" width="970">

Thanks in advance

---

### Post by zitch on 2012-03-07
You might be able to handle the "onended" event on the tag ([source](http://www.w3schools.com/html5/html5_ref_eventattributes.asp)).

Maybe set it up like the following:

```
<embed src="index_vid.flv" controller="false" loop="false" autoplay="true" height="480" width="970" onended="window.location = 'http://www.google.com';">
```

Of course, change the 'http://www.google.com' to the actual page you want to direct to.

UPDATE: A caveat: this seems to apply to HTML5 code. You might need to find another way otherwise.

---

### Post by juancarlospaco on 2012-03-08
Open the .FLV with VLC and save it as .WEBM then you dont need flash  :)

---


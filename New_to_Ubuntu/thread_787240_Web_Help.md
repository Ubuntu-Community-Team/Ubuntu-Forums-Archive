---
title: "Web Help"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-05-08
I'm trying to add a thing to my site where instead of opening a site up in a normal window. It opens it up into a window like this

[IMG]http://i25.tinypic.com/addmat.png[/IMG]

like I don't want it to open it up in the normal firefox window I want it to open up a new window to the site like shown in the image where it doesn't show the url or any of the normal firefox options[back, forward, refresh, stop, home, ect.]

ps. I just made that image with gimp it's really crappy but i made it to give you an idea of what I'm talking about.

---

### Post by lesergi on 2008-05-08
How you want open this window? From link or button or auto?

---

### Post by RadiationHazard on 2008-05-08
> **lesergi said:**
> How you want open this window? From link or button or auto?

link please

---

### Post by RadiationHazard on 2008-05-08
found the code

```
<a href="#" onClick="MyWindow=window.open('http://ubuntuforums.org/','MyWindow','toolbar=no,location=no,directories=no,status=no,menubar=no,scrollbars=yes,resizable=yes,width=600,height=300'); return false;">PLACE_YOUR_LINKTEXT_HERE</a>
```

---

### Post by lesergi on 2008-05-08
Ok.

You have to open this window with javascript.

You'll have to write this:

```

<a href="javascript:window.open('http://www.ubuntuforums.org', 'window1', 'width=500', 'height=350', 'scrollbars=yes', 'menubar=no', 'location=no', 'resizable=yes', 'status=no')">Link text</a>

```

You can set options like width, height, if you want to show scrollbars, menubar...

Bye!!

---


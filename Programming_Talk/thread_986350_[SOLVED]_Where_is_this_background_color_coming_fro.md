---
title: "[SOLVED] Where is this background color coming from?"
date: 2008-11-18
forum: Programming Talk
---

### Post by Vadi on 2008-11-18
Hi,

I've ran into a bit of an odd problem - trying to modify a theme however I can't figure out where a color is coming from, even with the help of Firebug and a friend.

On [mudlet.org]("http://mudlet.org"), I'm trying to figure out where is this light-blue color coming from:

[CENTER][IMG]http://www.ubuntu-pics.de/bild/5947/screenshot_53_baioxa.png[/IMG][/CENTER]

Any help is appreciated.

---

### Post by nvteighen on 2008-11-18
Ok, from [http://www.mudlet.org/wp-content/themes/updown-cloud/style.css](http://www.mudlet.org/wp-content/themes/updown-cloud/style.css) (background node) the color is #DFF8FF. Confirmed using the GIMP.

So, try to replace each appearence of that color code in the css...

---

### Post by Vadi on 2008-11-19
Sorry, I forgot only admins saw the testing style.

Try this link: [http://www.mudlet.org/?theme=green-updown-cloud](http://www.mudlet.org/?theme=green-updown-cloud)

The css I have is this one: [http://www.mudlet.org/wp-content/themes/green-updown-cloud/style.css](http://www.mudlet.org/wp-content/themes/green-updown-cloud/style.css), where all instances of that color were replaced already...

---

### Post by nvteighen on 2008-11-19
> **Vadi said:**
> Sorry, I forgot only admins saw the testing style.

Try this link: [http://www.mudlet.org/?theme=green-updown-cloud](http://www.mudlet.org/?theme=green-updown-cloud)

The css I have is this one: [http://www.mudlet.org/wp-content/themes/green-updown-cloud/style.css](http://www.mudlet.org/wp-content/themes/green-updown-cloud/style.css), where all instances of that color were replaced already...
I see exactly the same page using your link... :(

---

### Post by drubin on 2008-11-19
I am utterly confused about this as well. :s

I can tell you it does have something to do with <div class="main"> the class main, If I remove the class main from this the blue backgroun disappears. Some of the other styling also goes but maybe it is a start.

---

### Post by drubin on 2008-11-19
I take this back I was being stupid!!
[http://www.mudlet.org/wp-content/themes/updown-cloud/img/main.gif](http://www.mudlet.org/wp-content/themes/updown-cloud/img/main.gif)
Take a look at the back ground image, the blue color is built into the image.

**edit:**
No wait I take that back again, That theme is being stupid! Who puts that style as a background image!!?? Who I tell you :)

---

### Post by Vadi on 2008-11-19
Yeah it was that picture. Thank you :)

---


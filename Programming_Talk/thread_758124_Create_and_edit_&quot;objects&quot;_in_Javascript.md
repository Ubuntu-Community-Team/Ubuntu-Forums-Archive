---
title: "Create and edit &quot;objects&quot; in Javascript"
date: 2008-04-17
forum: Programming Talk
---

### Post by Niklas Schröder on 2008-04-17
I'm working on a little Javascript project.  But I'm pretty much a newb when it comes to that kind of coding, so I was wondering if some of you could help me get started. 

I need to have the user set some parameters through an options dialog, have the browser draw an object based on those parameters, and then allow the user to edit the parameters of the newly created object if needed by clicking on the object and having an options dialog show.

Like I said before, I'm a newb at Javascript, so commented code and such would be appreciated!  ;)

---

### Post by jespdj on 2008-04-17
You want to draw, i.e. generate graphics, in JavaScript running in a browser? I don't know if that's easy / possible.

There are some very nice JavaScript, HTML, CSS, DOM and other tutorials here: [http://www.w3schools.com/](http://www.w3schools.com/)

---

### Post by Niklas Schröder on 2008-04-17
Ok.  I guess I'll do some more poking around in that site.  But I know for a FACT that it's possible to draw objects with Javascript.  It may not be easy, but it's a good exercise.  :p

---

### Post by LaRoza on 2008-04-17
> **Niklas Schröder said:**
> Ok.  I guess I'll do some more poking around in that site.  But I know for a FACT that it's possible to draw objects with Javascript.  It may not be easy, but it's a good exercise.  :p

[http://blog.nihilogic.dk/2008/04/super-mario-in-14kb-javascript.html](http://blog.nihilogic.dk/2008/04/super-mario-in-14kb-javascript.html)

It is possible, but not easy.

That game is all javascript.

---

### Post by Niklas Schröder on 2008-04-17
Ok.  So it's not easy.  Got it.  But I didn't think the project would be in the first place.

IS there an easy way to do what I want?  If so I'd love to hear about it...

---

### Post by LaRoza on 2008-04-17
> **Niklas Schröder said:**
> Ok.  So it's not easy.  Got it.  But I didn't think the project would be in the first place.

IS there an easy way to do what I want?  If so I'd love to hear about it...

Investigate the code of the project I linked to.

---

### Post by Niklas Schröder on 2008-04-17
Will do.  Seems a bit complex though.  All I need is a way for the user to define an angle and have a line drawn from the center of a circle to about 200 pixels out with a text box at the end...

---

### Post by LaRoza on 2008-04-17
> **Niklas Schröder said:**
> Will do.  Seems a bit complex though.  All I need is a way for the user to define an angle and have a line drawn from the center of a circle to about 200 pixels out with a text box at the end...

Just a circle?

Could you describe this a bit more; I have a few ideas.

---

### Post by Wybiral on 2008-04-17
Use SVG DOM to render shapes, etc.

---

### Post by Niklas Schröder on 2008-04-17
For my project, there will be a circle in the middle with lines coming out of the sides.  Depending on where the line comes out of the circle, it corresponds to a certain time of day.  It's a day planner.  Basically a customizable, digital version of this.

[http://lifehacker.com/377905/muji-chronotebook-non%20linear-day-planner](http://lifehacker.com/377905/muji-chronotebook-non%20linear-day-planner)

I want the user to be able to create new lines (which correspond to events and the times at which they happen) and then be able to click on that object once it's on the screen and edit the text/angle.

---

### Post by Wybiral on 2008-04-17
Unless you want to use Flash (which isn't portable) or Java applets (which can be a pain) you should use SVG. You can render circles / lines / rectanges / etc. There are tons of tutorials on Javascript and SVG online (google it).

---

### Post by pmasiar on 2008-04-18
use a library to manipulate DOM, like jQuery, and/or JS GUI widgets, like Yahoo UI. Don't waste time on handcoding stuff and figuring out by your own trial and errors what should be cross-platform compatible but isn't - people learned all the lessons.

---


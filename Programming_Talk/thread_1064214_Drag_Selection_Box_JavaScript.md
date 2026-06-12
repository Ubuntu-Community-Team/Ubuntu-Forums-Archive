---
title: "Drag Selection Box JavaScript"
date: 2009-02-08
forum: Programming Talk
---

### Post by jamescox84 on 2009-02-08
Hi, I'm currently trying to implement a dragable selection box in javascript.  I have attached my code.  It's using the prototype library, for cross-browser simplicity.  Basicly it registers a mousedown event handler on a div, the when the handler receives the the event it registers a mousemove, and mouseup event handlers on the document object.  The mouseup event handler unregisters it's self and the mousemove handler when the drag is finnished.  The problem is that if while dragging something steals focus from the browser, or indeed the page, the mouseup event is never fired, leaving both the mousemove and mouseup handlers active.  To illustrate the problem look at drag.html in the attached code, I have registered a 2 second timeout that pops-up an alert box.  If you are dragging when the alert is shown, you will see my problem.  

I hope someone out there has an idea what I might need to do.  Thanks, in advance.

---


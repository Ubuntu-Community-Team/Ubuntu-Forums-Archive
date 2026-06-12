---
title: "command line mouse control"
date: 2008-06-23
forum: Programming Talk
---

### Post by djuniah on 2008-06-23
I'm working on a little script to help automate something and i need to be able to send in coordinates to the script and have it simulate a mouse click at that location.

so lets say i call
clickOn.sh -x 300 -y 300
it should place a click on that location of the screen
(the screen with a GUI on it)

Does anyone know how i can accomplish this?  I've been searching on this forum and googling around and nothing has come up.

EDIT:
ok this looks like it might do it:
[http://www.semicomplete.com/blog/geekery/xdo.html](http://www.semicomplete.com/blog/geekery/xdo.html)

---

### Post by hackerb9 on 2008-11-03
Xdo is packaged with Debian (and, so, I assume Ubuntu) as "xdotool", which you can apt-get.

    apt-get install xdotool

--b9

---


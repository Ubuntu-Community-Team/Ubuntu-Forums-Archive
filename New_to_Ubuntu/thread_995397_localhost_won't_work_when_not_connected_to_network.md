---
title: "localhost won't work when not connected to network"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by me (caleb) on 2008-11-27
I have just got Apache2, php5, mysql5, and phpmyadmin set up on my computer. While I'm connected to a network I can visit localhost in my web browser with no problem. But when I'm not connected to a network I get an error message about how firefox is in off-line mode. Is there anyway to change the settings so that it can connect to localhost even when I'm not connected to a network?

Note: If I switch to guest then I can access localhost fine, but if I try to load a dynamic page it won't update to the latest version of the page, it will continue to show the first version that I viewed. So if I visit localhost/index.php, and then visit localhost/index.php?var=12, both will show up as the content of localhost/index.php because that is the page I visited first and the page that the browser cached.

---

### Post by spiderbatdad on 2008-11-27
idk some strange quirk of FF. Go to file menu and un-check "work offline" then click the "try again" button on the browser page.

---

### Post by me (caleb) on 2008-11-28
Yep, that works.

I guess I must have been thinking *way* to hard. I was wondering if I might have to do something like set up an imaginary network connection with some weird settings or something really complicated like that...

---


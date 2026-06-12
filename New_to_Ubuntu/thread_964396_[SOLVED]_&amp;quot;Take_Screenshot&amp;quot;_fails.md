---
title: "[SOLVED] &amp;quot;Take Screenshot&amp;quot; fails to capture window border/title bar."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by diablo75 on 2008-10-30
I've used Take Screenshot a lot to take pictures of windows that I have open.  In the past I've been able to take pictures that include the title bar and add a drop shadow behind the window, like this:

[IMG]http://www.davestechsupport.com/blog/images/phatch.png[/IMG]

But now when I try (and I do have Include Window Border checked off), I get results like this:

[IMG]http://www.davestechsupport.com/blog/images/mainmenu.png[/IMG]

---

### Post by kk0sse54 on 2008-10-30
Well check include window border then :p. You've also set it to only take a shot of one window instead of your entire desktop

---

### Post by randy78 on 2008-10-30
Go to Menu>Accessories>Take Screenshot
Select "Grab current window"
Make sure that "Include the window border" is selected

:D

---

### Post by diablo75 on 2008-10-30
If you read my post, you'll see that I AM checking "include window border", and it does not work.

---

### Post by kk0sse54 on 2008-10-30
> **diablo75 said:**
> If you read my post, you'll see that I AM checking "include window border", and it does not work.

I'm am humbly sorry I misread and thought you said you did not have it checked :(

---

### Post by diablo75 on 2008-10-31
Bump...

Is there nothing I might try to do to get this working correctly?

---

### Post by stani on 2008-11-12
Windows borders are not captured on compiz. Therefore switch temporarily to metacity, press Alt+F2 and fill in:```
metacity --replace
```To return to compiz:```
compiz --replace
```

---


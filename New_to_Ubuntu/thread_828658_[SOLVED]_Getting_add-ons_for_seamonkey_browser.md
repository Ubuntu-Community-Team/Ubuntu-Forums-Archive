---
title: "[SOLVED] Getting add-ons for seamonkey browser"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Indy452 on 2008-06-14
I have both seamonkey and firefox but I run them seperately. I like seamonkey just fine for my needs but there is one problem I don't know how to solve.

I would like to install add block but for some reason I can't get the add-on to stick. I get an Alert message after I click install that says something like I need to be root or something.  Here is a screen shot of the message..............

Thanks, I hope someone can help.

Neal

---

### Post by spiderbatdad on 2008-06-14
my method may be round about but it works:
 After installing it, you get the error message. Close the browser. Go to the terminal and run ```
sudo seamonkey
```The browser launches. navigate back to the add-on download site, and install the add-on again. Close the browser. It will now work normally.

---

### Post by spiderbatdad on 2008-06-14
Nother thing I've noticed with seamonkey is the NoScript blocking is silent. If a site wont play videos, it is usually due to NoScript blocking, but there is no "title bar" warning, you have to look at the little NoScript icon in the bottom right corner.

---

### Post by Indy452 on 2008-06-14
> **spiderbatdad said:**
> my method may be round about but it works:
 After installing it, you get the error message. Close the browser. Go to the terminal and run ```
sudo seamonkey
```The browser launches. navigate back to the add-on download site, and install the add-on again. Close the browser. It will now work normally.

Cool, thanks. I knew it was something simple like this. I really don't fully understand why I had to do it that way but I did, and now Its installed. Thanks!!

Neal

---


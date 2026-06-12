---
title: "javascript self.resizeBy in Linux Opera"
date: 2007-12-28
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-28
I've read a couple posts here about Opera and Javascript ([http://ubuntuforums.org/showthread.php?t=356700](http://ubuntuforums.org/showthread.php?t=356700) for one), but this is a slightly different question.  

First, I thought Opera was supposed to be very standards compliant.  Is this just in regards to HTML and CSS?

self.resizeBy(50,50); does not appear to work in Opera.  I double checked and I do have window resizing allowed in Opera.  Anybody know what the deal is?  I tried running it with Opera as a free window as it maximized.  The self.resizeBy I have works fine on Firefox (Linux)...doesn't work on IE either (6 or 7), but I'm less concerned about IE.

Thanks!

EDIT: I realized what my problem in IE was...no closing tag for <title>...well, there was a <title> there, just no /.  The issue still exists in Opera though :/

---

### Post by anbumanij on 2007-12-28
Hi goody,

        Go with dom object then it will work on all browser setup.. You should access the form by its "id" name... well you know about dom concepts..

---

### Post by DouglasAWh on 2007-12-28
Um, I am referring to the window object, not a form.  I am trying to resize the entire browser window.  don't worry, I'd never actually do something so annoying, it's just a test page to learn javascript. :)

EDIT: I used window. instead of self. and it still doesn't work in Opera.

---

### Post by LaRoza on 2007-12-28
> **DouglasAWh said:**
> 
First, I thought Opera was supposed to be very standards compliant.  Is this just in regards to HTML and CSS?


Opera is very standards compliant, however, that method is not part of a standard.

[http://msdn2.microsoft.com/en-us/library/ms536722.aspx](http://msdn2.microsoft.com/en-us/library/ms536722.aspx) (not standard)

[http://www.opera.com/docs/specs/opera9/](http://www.opera.com/docs/specs/opera9/) (standards supported)

---


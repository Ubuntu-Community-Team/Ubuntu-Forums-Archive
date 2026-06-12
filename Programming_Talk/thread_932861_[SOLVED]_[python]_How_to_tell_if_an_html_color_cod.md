---
title: "[SOLVED] [python] How to tell if an html color code (ie #ffffff) is valid?"
date: 2008-09-28
forum: Programming Talk
---

### Post by days_of_ruin on 2008-09-28
I want to know if theres a good fast way to do that.

---

### Post by LaRoza on 2008-09-28
> **days_of_ruin said:**
> I want to know if theres a good fast way to do that.

Six character hex, 1-9, A-F. ;)

It is just a number.

---

### Post by loell on 2008-09-28
maybe
```

if (int(color_code,16) < 16777216):

  print 'heh, its valid! :D'
```

---

### Post by days_of_ruin on 2008-09-28
> **LaRoza said:**
> Six character hex, 1-9, A-F. ;)

It is just a number.


what if its longer or shorter then 6 characters?

---

### Post by Greyed on 2008-09-28
> **days_of_ruin said:**
> what if its longer or shorter then 6 characters?

.... len?

---

### Post by LaRoza on 2008-09-28
> **days_of_ruin said:**
> what if its longer or shorter then 6 characters?

3 characters are allowed also.

It is just a RGB colour value.

[http://www.w3schools.com/Html/html_colors.asp](http://www.w3schools.com/Html/html_colors.asp)

---


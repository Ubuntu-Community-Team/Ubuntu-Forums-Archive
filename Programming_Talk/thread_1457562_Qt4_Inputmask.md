---
title: "Qt4 Inputmask"
date: 2010-04-18
forum: Programming Talk
---

### Post by Woody1987 on 2010-04-18
I have a QLineEdit and would like to have an input mask. The input mask must allow only numbers and 1 dot(.). The input can be of any length. So for example

35.22 - good
463467347357.745 - good
325.23.32 -bad with two dots
325 - good

Can i do this?

---

### Post by Bachstelze on 2010-04-18
You want a QValidator.

[http://doc.trolltech.com/4.6/qvalidator.html](http://doc.trolltech.com/4.6/qvalidator.html)

---


---
title: "Printing decimal numbers without printf in c++"
date: 2007-01-30
forum: Programming Talk
---

### Post by Greykrrr on 2007-01-30
Hi

I have posted about this before and have seen others have too. I've found a solution to this problem and well, I figured I would post it for others as well.

When wanting to output a floating number to the screen with a fixed number of decimals after the decimal point the iostream header defines setprecision, as described here:
[http://www.cplusplus.com/reference/iostream/manipulators/setprecision.html](http://www.cplusplus.com/reference/iostream/manipulators/setprecision.html)

It will specify the number of decimals used to the right of the decimal point.

Also to specify wether number should be written scientifically or as a normal iostream defines fixed and scientific which sets the output format to be a normal number and scientific output respectively.

I hope this helps someone :)

---

### Post by Tomosaur on 2007-01-30
Thanks for that, could come in useful :)

---

### Post by slavik on 2007-01-30
this is why I sometimes prefer printf() over operator<<()

edit: although when I print debugging info, operator<<() is faster to type :)

---


---
title: "&lt;?= operator"
date: 2008-12-05
forum: Programming Talk
---

### Post by smilitude on 2008-12-05
I recently shifted to ubuntu. And I suddenly found g++ doesnt have <?= operator anymore. It was a very favorite operator of mine. x <?= y means for x = ( y < x ) ? y : x; And i started to miss >? and <?  operator too!

It must sound childish but I am feeling sad for them. 
Is there any way to get them in the g++ of my ubuntu?

---

### Post by nvteighen on 2008-12-05
Write a macro... Anyway, such an operator seems a bit unreadable to me.

---

### Post by geirha on 2008-12-05
Those operators have been deprecated since 4.0 and have now apparently been completely removed. You'll have to use an older version of g++ if you really want to keep using them, but I'd recommend just getting used to using the functions instead. 

[http://gcc.gnu.org/onlinedocs/gcc/Deprecated-Features.html](http://gcc.gnu.org/onlinedocs/gcc/Deprecated-Features.html):
> The G++ minimum and maximum operators (`<?' and `>?') and their compound forms (`<?=') and `>?=') have been deprecated and are now removed from G++. Code using these operators should be modified to use std::min and std::max instead.

---


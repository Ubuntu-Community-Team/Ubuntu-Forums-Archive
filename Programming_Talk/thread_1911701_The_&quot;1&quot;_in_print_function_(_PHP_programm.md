---
title: "The &quot;1&quot; in print function ( PHP programming)"
date: 2012-01-19
forum: Programming Talk
---

### Post by vikkyhacks on 2012-01-19
This is my simple program .....

[I][B]<?php
print print print print "HELLO";
?>
[/B][/I]
The output is 

***HELLO111***

The desired output is HELLO but i am getting those three 111 , **WHY ????**

---

### Post by Zugzwang on 2012-01-19
Here's a suggestion: copy&paste the *complete* php script here. You wrote "print print print print" - It's unlikely that this is accepted by the interpreter, so you are not showing your actual code.

---

### Post by vikkyhacks on 2012-01-19
I am just now learning php. This is a code which I developed to just try out how it would work ... I am using XAMPP under Ubuntu 11.04 and the above code is the complete code ....
Don believe me ?? I am attaching the code as a zip file

---

### Post by v8YKxgHe on 2012-01-19
It's simple. As stated in the docs ([http://php.net/print](http://php.net/print)) the return value of 'print' will always be 1. The "HELLO" appears first, followed by the three ones which are being printed out by the very first "print".

To make this clearer, see the following:

[PHP]print(print(print(print 'HELLO')));[/PHP]

---

### Post by vikkyhacks on 2012-01-20
Thanks A LOT !!! :D:D:D:D

---


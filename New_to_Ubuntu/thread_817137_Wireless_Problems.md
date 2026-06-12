---
title: "Wireless Problems"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-06-03
Hi,

My wireless does not turns on even after presssing the shortcut for it (fn+F3) for my Dell Inspiron Laptop. 
Problem that I think is the following. When I turn on my Laptop the first thing or rather first message that appears is 
> "The AC power adapter type cannot be determined. Your system will operate slower and the battery will not charge". 
Also I have recently shifted from India to Europe and my Laptop is from India, so I have to use the International adapter for the socket. And my wireless was working just one week before I shifted to Europe. Is this really what is preventing me from getting my wireless on? All the other accessories works fine. And I am sure that my wireless is not turning on as I used to see the light when it was working fine but now I dont. Thanx for any kind of help.

---

### Post by spiderbatdad on 2008-06-03
Sounds like this adapter may be better detected with the help of some kernel boot parameters. Read through ```
 dmesg 
``` for some clues.

[http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/) (my lame blog)

or search google and the forums for boot parameters...like pci=routeirq  and how to apply the parameters.

---

### Post by dimitarc on 2008-06-03
[http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/](http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/)

This solved my wireless problem. I hope it will for you too.

---


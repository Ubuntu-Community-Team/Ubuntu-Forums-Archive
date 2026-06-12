---
title: "Php + gd"
date: 2007-04-03
forum: Programming Talk
---

### Post by purefan on 2007-04-03
Hello guys :)

I used synaptic and it worked fine for installing apache and php with support for mysql, so I got a nice server up and running on my local pc, but I need gd and no matter how many times I (re)install it it just wont load along with apache. I dont want to use my server to allow access to anyone else, I just want it to work so I dev my proyects locally and when they are ready I can just upload them to where they belong. But I need gd now and cant get it working... any ideas?

thank you for your time :)

---

### Post by lnostdal on 2007-04-03
hm, shouldn't the package:

```

root@ibmr52:~# aptitude search gd | grep php
p   php5-gd                         - GD module for php5  

```

..work out of the box?

---

### Post by purefan on 2007-04-03
Hello Inostdal,

thank you for your reply.

I ran your code on my Terminal and here is what I got:
> 
id  php4-gd                         - GD module for php4                        
v   php4-gd2                        -                                           
c   php5-gd                         - GD module for php5   


Im running apache2 and php 4.4. And if I do a phpinfo() no gd is found...

---

### Post by sunset_studies on 2007-04-05
is the following line in your php.ini file?

;extension=gd.so

If so, try removing the ';'

---


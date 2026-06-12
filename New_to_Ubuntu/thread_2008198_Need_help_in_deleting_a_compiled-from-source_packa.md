---
title: "Need help in deleting a compiled-from-source package"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by neo1691 on 2012-06-22
Hey guys, I downloaded the source of PHP and APACHE2 and compiled them from source, but i think i did some mistake configuring them and now i cant seem to get them working. So I was wondering how to remove the compilation and start afresh.

Apache seems to have gone to /usr/local/apache2/

I dont know where did PHP go.

Please help me. I wanna get php and apache working on my ubuntu 12.04 64 bit (desktop edition) for learning purpose. Do i need to have Ubuntu Server edition to make Apache work??

---

### Post by sandyd on 2012-06-22
> **neo1691 said:**
> Hey guys, I downloaded the source of PHP and APACHE2 and compiled them from source, but i think i did some mistake configuring them and now i cant seem to get them working. So I was wondering how to remove the compilation and start afresh.

Apache seems to have gone to /usr/local/apache2/

I dont know where did PHP go.

Please help me. I wanna get php and apache working on my ubuntu 12.04 64 bit (desktop edition) for learning purpose. Do i need to have Ubuntu Server edition to make Apache work??
Go to the source dir.
run 
```

sudo make uninstall
```

---

### Post by neo1691 on 2012-06-22
I did that, but unfortunately the author of the make file never wrote an uninstall it seems. 

Anyways i fired up terminal and did sudo apt-get purge apache2 
also sudo apt-get purge php

for both the commands i got there is no such  packages installed.

Yet there were those folders in usr/local/apache2.

so later I installed bot apache2 and php from apt-get and it worked just fine.

So now I have Php and apache both running on my laptop and also those files are there that were resulted from the compilation from source files!!

Bittersweet story!

---

### Post by chamber on 2012-06-22
What happened when you tried

```
sudo make uninstall
```

and from what directory did you run it?

---

### Post by neo1691 on 2012-06-22
> **chamber said:**
> What happened when you tried

```
sudo make uninstall
```

and from what directory did you run it?
I exactly don't remember but there was the error that cannot find uninstall for make target or something.. Exit code was 1

---


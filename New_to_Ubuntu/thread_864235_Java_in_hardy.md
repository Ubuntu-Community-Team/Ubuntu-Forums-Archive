---
title: "Java in hardy"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by littleangelwithwings on 2008-07-19
Hi everyone!! 

This is my first post on here. I am new(well ish) to ubuntu. been using it for over 2 years now and its great. but im a little stuck. my bf introduced me to it and so he's always helped me if i've had problems but he said ive got to start workin it out for myself.

Problem: I cant seem to play games that require Java. 

Tried: ive tried a few methods, had a look on this site and found a really good post, followed the commands but unfortunately didnt work.

Can anyone help me please. i would class myself as a newbie, so try not to use any technicial words. i can use the command line thing tho :)


Look forward to hearing from anyone :)

M:confused:

---

### Post by Vivaldi Gloria on 2008-07-19
Start 

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings. Then click refresh. Then search & install 

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

---

### Post by spiderbatdad on 2008-07-19
check to see that you have packages like:
java-gcj-compat in synaptic.

I think sudo apt-get install ubuntu-restricted-extras will handle your needs...I seem to have java applet games by default...probably through the seamonkey browser packages. In the past, with FF I have had to add packages like gcj to run java applet games. icedtea webplugin might be what your looking for if your using Firefox.

---

### Post by littleangelwithwings on 2008-07-19
yay!!!

thanks guys it worked :) much appreciated:)

---


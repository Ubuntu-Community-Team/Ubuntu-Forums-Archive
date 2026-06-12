---
title: "Help with touchegg"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Chaz46 on 2012-05-25
Evening folks,

I am using ubuntu 12.04 on an asus eee pc, I would like to use some of the features offered by touchegg but having some issues. I have installed it through the software center but when I type touchegg into the terminal all I get is:

```
charlie@charlie-1015PX:~$ touchegg
Reading config from  "/home/charlie/.config/touchegg/touchegg.conf"
```

Am I missing something? It just stays like that permanently?

---

### Post by anewguy on 2012-05-25
I haven't heard of this package before, so even though I can't use it on my desktop I installed it anyway to check it out.  I get the following:

```
dave@dave-desktop:~$ touchegg
"/home/dave/.config/touchegg/touchegg.conf"  not found, copying config from  /usr/share/touchegg/touchegg.conf 
Reading config from  "/home/dave/.config/touchegg/touchegg.conf" 
Segmentation fault (core dumped)
dave@dave-desktop:~$ touchegg
Reading config from  "/home/dave/.config/touchegg/touchegg.conf" 
Segmentation fault (core dumped)
dave@dave-desktop:~$ 


```
I assume the segmentation fault may be due to not having any kind of trackpad device on my desktop.

I'll do some more playing and see if I find anything, but since this is new to me no promises.

Maybe there is someone out there who has made it work.  There is a 2-week old thread on the forums for the same error with no answer.

Dave ;)

---

### Post by Chaz46 on 2012-05-25
Thank you for the reply Dave, that would be great if you could look into it. It would be really useful if I could get it to work, the segmentation fault is discussed as an error on their site, but for some reason mine doesn't register a fault at all. If it is of any use the error that you seem to get is discussed here:

[http://code.google.com/p/touchegg/issues/detail?id=148](http://code.google.com/p/touchegg/issues/detail?id=148)

Thanks again.

---

### Post by Chaz46 on 2012-06-09
Any luck with this in the end? I had another try but still no luck!

Cheers

---

### Post by Hadaka on 2012-06-09
looks like Touchegg doesnt like 12.4 just yet

[http://code.google.com/p/touchegg/issues/detail?id=148](http://code.google.com/p/touchegg/issues/detail?id=148)

---


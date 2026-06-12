---
title: "over 99% CPU while viewing web page"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-31
Hello guys,

Visiting certain websites makes my Ubuntu system very slow. For example, tumblr error messages seem to go accompanied by a very resource-consuming graphic. Like this:  [jeiofuapoi.tumblr.com]("http://jeiofuapoi.tumblr.com")

Viewing a page like that makes my computer slow. When I type the command:

```
$ top
```
I get the following:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1087 root      20   0  386m  87m 9740 R   99  2.2   3:22.12 Xorg               
 2823 owner     20   0  667m 203m  40m S    3  5.0   0:49.31 firefox            
 2876 owner     20   0  461m 122m  23m S    2  3.0   1:03.76 plugin-containe  

```
Over 99% CPU usage. Closing the offending web page brings everything back to normal again. Does anybody know what could be the source of this?


Edit: I have downloaded graphic card drivers for my Nvidia GeForce 9600 GT according to this website: [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)  That didn't solve the problem.

---

### Post by vasa1 on 2013-10-31
> **sha1sum said:**
> .... Like this:  [jeiofuapoi.tumblr.com]("http://jeiofuapoi.tumblr.com")
....
Gives me a "page not found". Do you have another example?

---

### Post by sha1sum on 2013-11-01
That's exactly the page I want you to see. It contains a graphic in the background, that eats away CPU on Ubuntu, while it runs happily with no problem at all on my Windows OS on the same computer.

---


---
title: "xxxterm dependencies"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by Todd42 on 2011-12-09
I downloaded xxxterm from 
[https://opensource.conformal.com/wiki/xxxterm_linux](https://opensource.conformal.com/wiki/xxxterm_linux)
and, I noticed that there were a list of dependencies before the compiling process.  
I looked in Synaptic Package Manager, and I could not find a 1 to 1 match of the 
dependencies listed.  However, I noticed that the dependencies were BSD related.  
So, my first question is how can I verify that I have the correct dependencies before 
compiling?
My second question is, are those dependencies for BSD only?
My third question is, where can I get those dependencies if I do in fact need them?
My fourth question is, I know in FreeBSD when doing a Make Install Clean that FreeBSD 
will go out and try to find, install, and resolve the dependencies during the Make Install, 
so does Xubuntu do the same?
And my last question is, I found a Debian article at 
[http://packages.debian.org/sid/i386/xxxterm](http://packages.debian.org/sid/i386/xxxterm)
so, can I just add a Debian source to my sources list and see if the dependencies are 
resolved by going through a Debian source?
Thanks in advance.

---

### Post by gordintoronto on 2011-12-10
> **Todd42 said:**
> I downloaded xxxterm...


Why?

---

### Post by Todd42 on 2011-12-10
Did you read their website?  
1.  I use vi and vim mostly, so the idea of combining a browser with vi command functionality would 
simply add to the way I already manipulate most files.
2.  If what they are saying is true then there is greater security simply by design.
3.  I support minimalism and elegant design.
4.  What Open Source means to me has nothing to do with licensing or proprietary contracts.  It is the ability for anyone (including me...) to be able to have the source code available so I can learn how things really work inside and what is going on.  For all I know, if I ever get it installed I may want to uninstall it.  But, this project has already given me a priceless gift.  It caused me to ask questions of how Linux works and what are the differences in how it works compared to other Operating Systems.
Lastly, I have always said and believe these words:
If science were a building, then it's cornerstone would be great questions; and it's keystones great observations.
Linux is a learning tool for me.  And, I am grateful for it.  Projects like this whether successful or not teach me what I need to learn and why things are happening in the world around me.
Also, note that I installed Uzbl and Surf as well on similar terms...

---

### Post by Luz77 on 2012-01-14
The dependencies due to xxxterm are:
> Build dependencies:
libbsd-devel
webkitgtk-devel
gtk2-devel
gcc
git
Runtime dependencies:
webkit
libbsd

My compilation problem was:
```
../xxxterm.h:38:24: fatal error: bsd/stdlib.h: No such file or directory
compilation terminated.
```
Thus I installed "libbsd-dev".
Then my problem was:
```
../xxxterm.h:58:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
```
Thanks volinthius! Solution:
```
sudo apt-get install libgnutls-dev
```

---

### Post by volinthius on 2012-03-01
I solved this by running in shell (see linux/Makefile):
```

pkg-config --libs gtk+-2.0 webkit-1.0 libsoup-2.4 gnutls gthread-2.0

```

This complained about missing gnutls which fixed the missing gtk.h as well.

---


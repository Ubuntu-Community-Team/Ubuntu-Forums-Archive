---
title: "[debian eeepc] need super light and small pdf viewer"
date: 2008-11-08
forum: Other OS Talk
---

### Post by hanzj on 2008-11-08
hello,

2G surf eeepc (running debian) needs lightweight and nimble pdfviewer. 
which app fits the bill?

---

### Post by alwayshere on 2008-11-08
------------------------------------
ePDFView
[http://trac.emma-soft.com/epdfview/](http://trac.emma-soft.com/epdfview/)
------------------------------------

-----------------------------
pdfedit
[http://pdfedit.petricek.net/](http://pdfedit.petricek.net/)
-----------------------------

---

### Post by hanzj on 2008-11-08
are the 2 lighter than xpdf?

---

### Post by alwayshere on 2008-11-08
[http://trac.emma-soft.com/epdfview/wiki/Download](http://trac.emma-soft.com/epdfview/wiki/Download)

[http://pdfedit.petricek.net/bdownload_e.html](http://pdfedit.petricek.net/bdownload_e.html)

---

### Post by darrelljon on 2008-11-10
I don't think you can get lighter than Xpdf but Foxit is a good reader.

---

### Post by mikjp on 2008-11-12
I usually use xpdf in my older boxes.

Mikko

---

### Post by regomodo on 2008-11-13
> **hanzj said:**
> are the 2 lighter than xpdf?

Xpdf is light as it'll go but I also reccomend epdfview. It's also used in Puppy Linux.

---

### Post by hanzj on 2008-11-13
I did
 ```
sudo apt-get install epdfview
```and it says 
> 2699 kb of additional disk space will be used.



I did 
```
sudo apt-get install xpdf
```and it says
> 13.7MB of additional disk space will be used. Wow! What a difference. **Why the big difference?_*[COLOR=Green] And why is epdfview smaller than xpdf, if xpdf is what you folks recommend when asked for a super light and small pdf viewer?[/COLOR]*_** 
Is it because I'm using LXDE as my desktop environment?

---

### Post by regomodo on 2008-11-13
> **hanzj said:**
> I did
 ```
sudo apt-get install epdfview
```and it says 
.



I did 
```
sudo apt-get install xpdf
```and it says
Wow! What a difference. **Why the big difference?_*[COLOR=Green] And why is epdfview smaller than xpdf, if xpdf is what you folks recommend when asked for a super light and small pdf viewer?[/COLOR]*_** 
Is it because I'm using LXDE as my desktop environment?

Probably because you have its dependencies already installed.

---

### Post by zmjjmz on 2008-11-13
> **hanzj said:**
> I did
 ```
sudo apt-get install epdfview
```and it says 
.



I did 
```
sudo apt-get install xpdf
```and it says
Wow! What a difference. **Why the big difference?_*[COLOR=Green] And why is epdfview smaller than xpdf, if xpdf is what you folks recommend when asked for a super light and small pdf viewer?[/COLOR]*_** 
Is it because I'm using LXDE as my desktop environment?

As the previous poster pointed out, that's not a fair comparison.

The install sizes for each individual package can be gotten with
```
apt-cache show <package>
```

---


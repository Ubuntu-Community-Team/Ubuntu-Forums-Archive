---
title: "Install Ubuntu 10.04 Classic Desktop"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by dolphin194 on 2011-11-09
Hi. I would like to install the GNOME Desktop from Ubuntu 10.04 in Ubuntu Server 10.04 LTS. 

I know about 
```
sudo apt-get install ubuntu-desktop
```however, I want to install the desktop that was included in Ubuntu 10.04

In other words, I want my Ubuntu desktop to look like this:
[http://www.geek.com/wp-content/uploads/2010/04/Ubuntu_10_04-Beta2.jpg](http://www.geek.com/wp-content/uploads/2010/04/Ubuntu_10_04-Beta2.jpg)

**NOT LIKE THIS **
[http://4.bp.blogspot.com/-1vKwA2IMPKA/Th8x7ZX45TI/AAAAAAAACUo/XNzEa6Xdwiw/s1600/ubuntu11.10alpha2review.png](http://4.bp.blogspot.com/-1vKwA2IMPKA/Th8x7ZX45TI/AAAAAAAACUo/XNzEa6Xdwiw/s1600/ubuntu11.10alpha2review.png)

So I don't want to install the unity interface from Ubuntu 11.10.

I want the Ubuntu desktop from 10.04, not the classic GNOME for 11.10. How would I go about doing this?

---

### Post by fantab on 2011-11-09
> **dolphin194 said:**
> Hi. I would like to install the GNOME Desktop from Ubuntu 10.04 in Ubuntu Server 10.04 LTS. 

I know about 
```
sudo apt-get install ubuntu-desktop
```however, I want to install the desktop that was included in Ubuntu 10.04

In other words, I want my Ubuntu desktop to look like this:
[http://www.geek.com/wp-content/uploads/2010/04/Ubuntu_10_04-Beta2.jpg](http://www.geek.com/wp-content/uploads/2010/04/Ubuntu_10_04-Beta2.jpg)

**NOT LIKE THIS **
[http://4.bp.blogspot.com/-1vKwA2IMPKA/Th8x7ZX45TI/AAAAAAAACUo/XNzEa6Xdwiw/s1600/ubuntu11.10alpha2review.png](http://4.bp.blogspot.com/-1vKwA2IMPKA/Th8x7ZX45TI/AAAAAAAACUo/XNzEa6Xdwiw/s1600/ubuntu11.10alpha2review.png)

So I don't want to install the unity interface from Ubuntu 11.10.

I want the Ubuntu desktop from 10.04, not the classic GNOME for 11.10. How would I go about doing this?

Lets see if I understood you correctly. You want Ubuntu 10.04 desktop  on your Ubuntu 11.10, you want to replace UNITY with PANELS.

If I understood you Okay then the answer is NO, you cant. 10.04 uses Gnome 2 and 11.10 uses Gnome 3. It is not Possible.

You can still use 10.04 it is still supported or try XUBUNTU or KUBUNTU or  LUBUNTU if you need Panels.

---

### Post by cbowman57 on 2011-11-09
If you haven't changed your repositories I would think it would pull in the (gnome) ubuntu-desktop that  came with 10.04.

---

### Post by dolphin194 on 2011-11-10
I have installed Ubuntu Server, and the 10.04 desktop. It was the correct version. I made this thread simply because I wasn't sure if it would install the latest desktop or the 10.04 desktop.

---

### Post by cbowman57 on 2011-11-10
> **dolphin194 said:**
> I have installed Ubuntu Server, and the 10.04 desktop. It was the correct version. I made this thread simply because I wasn't sure if it would install the latest desktop or the 10.04 desktop.

Glad it went well. :)

Don't blame you for using caution when it comes to making a change to your server.

---

### Post by snowpine on 2011-11-10
Curious why you did it this round-about way instead of simply installing Ubuntu Desktop 10.04 in the first place?

---

### Post by dolphin194 on 2011-11-10
> **snowpine said:**
> Curious why you did it this round-about way instead of simply installing Ubuntu Desktop 10.04 in the first place?
I didn't want to have to deal with removing all the other garbage, like OpenOffice and such

---

### Post by snowpine on 2011-11-11
> **dolphin194 said:**
> I didn't want to have to deal with removing all the other garbage, like OpenOffice and such

Then make sure you install ubuntu-desktop with the "--no-recommends" flag, otherwise you're going to end up with OpenOffice anyway. :)

---


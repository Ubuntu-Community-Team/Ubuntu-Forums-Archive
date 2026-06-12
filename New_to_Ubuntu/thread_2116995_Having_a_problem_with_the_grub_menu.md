---
title: "Having a problem with the grub menu"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by IndigoBunting on 2013-02-17
Ok, so I am brand new, and yesterday I installed Ubuntu 12.04.2 by burning it on a cd. 

I have a Dell Inspiron n5050, and yesterday Ubuntu worked fine, but today I booted up to a blank screen. I read that  the problem may be I need to install Nvidia drivers with the grub menu, so I did that. Then I looked up my graphics card, it is actually Intel HD. 

So when I went to install those drivers, my grub menu suddenly won't let me enter nomodeset. I type it in place of quiet splash, then hit enter, and the line goes down, like I'm in a word processor. So I am still in grub menu, unable to edit it. Any help would be greatly appreciated.

---

### Post by sudodus on 2013-02-17
Welcome to the Ubuntu Forums:-)

With intel graphics, you don't need any proprietary driver, opposite to the case with nVidia. But if you have a combination, you may need ***Bumblebee***.

[[COLOR="Red"]https://wiki.ubuntu.com/Bumblebee[/COLOR]]("https://wiki.ubuntu.com/Bumblebee")

Don't hit enter, it only enters a line-feed character. Instead start by

***ctrl + x***

---

### Post by IndigoBunting on 2013-02-17
Ok I figured it out. Sorry for wasting the forum's time.

---

### Post by IndigoBunting on 2013-02-17
Thank you for your help. Installing more Intel drivers didn't fix the blank screen =( I will figure it out though.

---


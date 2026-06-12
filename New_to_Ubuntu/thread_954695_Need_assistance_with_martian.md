---
title: "Need assistance with martian"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by mishivia on 2008-10-21
Good Afternoon All,
I have been trying for 3 weeks now to surf the internet using my cellphones bluetooth connection. However, trial-and-error and lots of documentation reading has proven that Ubuntu does not  support winmodems. :( 
I have been able to sucessfully run scanmodem and I know that I need martian-full-20080625, however, the furthest I have been able to get is "this is a directory". Everything kind of goes haywire after that. 
Make all, sudu make install, make clean, all give me the same message. stop.no target or something like that. (forgive me I am at work:lolflag:.) martian_dev...gives me a fatal module not found message. 
As far as I know, I have all of the necessary dependecies (build-essential) so I have no clue what more could I be doing wrong. 
Thanks again to dstin for helping me out..but I still haven't gotten this thing up and running. Any help will be most appreciated.

---

### Post by mishivia on 2008-10-31
<Bump>

---

### Post by mishivia on 2008-10-31
In the event that this problem is one that anyone else may face here is how I solved my problem. With the help from Marv@linmodems, I was able to realize that I was never in my directory; I was only simply recognizing my directory. 
Apparently when typing in terminal you have to be VERY aware of spaces as well as letter case. In essence I was typing :
cd/home/niesha/Desktop when I should have been typing:
cd /home/niesha/Desktop! 
(note that there should be a space between cd and the /)
Hope this helps others:)
niesha

---


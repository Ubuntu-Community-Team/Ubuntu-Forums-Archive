---
title: "Apple Magic Mouse with Ubuntu 13.04? + reverse scrolling issues"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Olavbs on 2013-07-11
I'm an old mac-user, but when my late 2009 Macbook slowly fainted after  three years of heavy duty, i decided to start using linux. 
I started out with Linux Mint 14 nadia, but I didn't like it too well.  Then I tried Debian, but it was a little too hard to use for a beginner  like me.
Now I'm using Ubuntu 13.04 and it seems like heaven to me! It is fast  and smooth but, since I used to have a mac, i still have my magic mouse,  and I really want to use it with ubuntu.
It was easy to connect an apple wireless keyboard to my Dell Vostro 3350, but with the magic mouse, it was a different story...

The mouse is visible, and when I connect it, it says "Successfully set  up new device "MyMouse", but i get no response on my movements or  mouseclicks.
In the bluetooth settings, I can see that the mouse is not paired and the connection is off. Why is this happening?

Also, when I connect an ordinary USB mouse, and everything worked fine, I missed the reversed scrolling from my mac experience.
I know i can enable "two finger scrolling" and "Content sticks to  fingers" which together will replicate the scrolling with a trackpad on a  mac very well!
What my problem is, is that i can't find a similar  option for a mouse, so if anybody know what I've done wrong when i tried  to connect my magic mouse or how to invert scrolling on a mouse, please  let me know!
Thank you!

- Olavbs

---

### Post by dino99 on 2013-07-11
you might have made nothing wrong yourself; but some hardware are not recognized out of the box. Its time for you to glance at the logs to finf something (warning/error) usefull : .xsession-errors (ctrl+h to unhide it inside /home/youruser) & inside /var/log/dmesg (& other subdirs too)

Some mice need a few settings inside an xorg.conf
[http://www.google.fr/#q=ubuntu+mac+mouse+xorg.conf&source=lnt&tbs=qdr:y&sa=X&ei=ZOXeUf3NENDy7AbJpYHIDQ&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48705608,d.Yms&fp=39f807f1709d30b4&biw=1672&bih=924](http://www.google.fr/#q=ubuntu+mac+mouse+xorg.conf&source=lnt&tbs=qdr:y&sa=X&ei=ZOXeUf3NENDy7AbJpYHIDQ&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48705608,d.Yms&fp=39f807f1709d30b4&biw=1672&bih=924)

---


---
title: "xorg.conf"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by Xinv3rse on 2012-07-14
Hey there. I accidentally modified my /etc/X11/xorg.conf file. Can I just delete it or I am toasted? Is there anything I should be worried about. I'm not having any issue except the twitchy/shaky touchpad. I have a Dell Inspiron n4050. How can I get my default xorg.conf back? and if possible how can I remove the twitchy/shaky touchpad? I saw a lot of threads regarding this issue but I could not get the solution to it. Thanks

---

### Post by Xinv3rse on 2012-07-14
The xorg.conf problem has been resolved. Now I just need to remove this twitchy/shaky touchpad problem. It's so annoying and irritating. When I hold my finger on the touchpad, the touchpad goes SUPER SENSITIVE and the cursor, it's like rotating here and there around where it should have been. Duh :/, does anyone have a solution to it? I have a Dell Touchpad.

---

### Post by DaveDeviant on 2012-07-26
Same problem for me too - [**_Touchpad twitchy_**](http://askubuntu.com/questions/128181/touchpad-twitchy-on-an-hp-g62-with-a-synps-2-synaptics-touchpad)

You can edit your xorg file with by adding this [**_Touchpad bug_**](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/992330) (check my last post from there). The problem will not be resolved 100% as after adding different values you will feel that the touchpad is kinda "slip" and you can't control it as before...

---


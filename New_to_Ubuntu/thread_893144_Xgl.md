---
title: "Xgl"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Shippou on 2008-08-18
Hello guys...

Do you know how to stop Xgl-server from autostarting after a system boot?

It is lagging my system... :(

---

### Post by overdrank on 2008-08-18
> **Shippou said:**
> Hello guys...

Do you know how to stop Xgl-server from autostarting after a system boot?

It is lagging my system... :(

HI and could you give a little more info. What version of Ubuntu are you using, Hardy, Gutsy? What is the model of the graphics card?

---

### Post by Shippou on 2008-08-18
I am currently Linux Mint right now... Found out that it uses Ubuntu Hardy as kernel... :)

I have no video cards or any other cards installed, so it is stupid of me to turn compiz on...

I am enjoying it though, though it lags my system.

---

### Post by Shippou on 2008-08-18
Bump.

---

### Post by overdrank on 2008-08-18
> **Shippou said:**
> I am currently Linux Mint right now... Found out that it uses Ubuntu Hardy as kernel... :)

I have no video cards or any other cards installed, so it is stupid of me to turn compiz on...

I am enjoying it though, though it lags my system.

Hi and you can find your graphics card using the ```
lspci 
``` command in the terminal. Look for VGA
 If you are not sure of your graphics card then why install xgl?

---

### Post by oliviacond on 2008-08-18
[http://ubuntuforums.org/showpost.php?p=3596195&postcount=2](http://ubuntuforums.org/showpost.php?p=3596195&postcount=2)

> To disable Xgl autostart for this user, create a file named ~/.config/xserver-xgl/disable



---

### Post by Shippou on 2008-08-18
II uninstalled  Xgl but not the other libraries it depends upon. This solved my problem.

---


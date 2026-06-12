---
title: "Dash Won't Show Up / Brings up a blank window. Also glitchy screen"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by therampoo on 2013-07-30
[SIZE=5]I have **recently installed Ubuntu Desktop 13.04** on a **5 year old desktop** and **everything works fine, except the dash button.**
[/SIZE]
[SIZE=5]When I click on the dash button it just **blanks out everything behind it** and the **dash doesn’t show up**. I am wondering if there is a fix for this. I want to search for my applications and such but I **cannot get the dash to show up.**[/SIZE]

  [IMG]http://i.stack.imgur.com/4Evbg.jpg[/IMG]

  [SIZE=5]I also have **one more problem.**
[/SIZE]
[SIZE=5]The **top half of my screen is glitchy** and is really annoying. It kind of **flickers**, and I am wondering if this is just a refresh rate problem or what, but I cannot get it to stop.[/SIZE]

---

### Post by mojo706 on 2013-07-31
Hey you can try ```
unity --reset
``` in a Terminal

---

### Post by humpmihk-msn on 2013-07-31
I had something like this on one laptop the dash was patterned and unreadable. I solved it by changing the dash blur from active blur to no blur. This can be done by installing ccsm > sudo apt-get install compiz compizconfig-settings-manager  then going to Ubuntu unity plugin on the general tab you will find Dash blur

---

### Post by Vladlenin5000 on 2013-07-31
What's your graphics card? Are you using proprietary drivers? If ATI or nVIDIA maybe you should...

---

### Post by therampoo on 2013-07-31
> **mojo706 said:**
> Hey you can try ```
unity --reset
``` in a Terminal

[SIZE=4][B]It shows up with this
ERROR: the reset option is now deprecated[/B][/SIZE]

---

### Post by therampoo on 2013-07-31
> **Vladlenin5000 said:**
> What's your graphics card? Are you using proprietary drivers? If ATI or nVIDIA maybe you should...

[SIZE=4][/SIZE]**[SIZE=4]Graphics: Gallium 0.4 on ATI RV370[/SIZE]**

---

### Post by therampoo on 2013-07-31
> **humpmihk-msn said:**
> I had something like this on one laptop the dash was patterned and unreadable. I solved it by changing the dash blur from active blur to no blur. This can be done by installing ccsm  then going to Ubuntu unity plugin on the general tab you will find Dash blur

**[SIZE=4]I know i'm kinda a noob on ubuntu, but where do i find what i just installed from the terminal?[/SIZE]**

---


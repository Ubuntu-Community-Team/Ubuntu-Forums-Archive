---
title: "Mouse not clicking"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by qwiksilver711 on 2013-01-12
I just installed 12.04 on an Alienware m14x, I use a Cyborg MMO7 mouse. When the mouse is plugged in I can click on the launcher bar stuff on the left but once a window is open I can't do anything with it. I cant close it or move to other windows without alt tab.

I have tried editing the xorg file thing, but it didn't work. Right now I think its not so much that its a complicated mouse but a general mouse issue but I dont know enough to know for sure.

---

### Post by 2F4U on 2013-01-12
If you have the R.A.T. 7 then it is an issue with the mouse:

[http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/](http://delightlylinux.wordpress.com/2012/03/07/using-the-cyborg-r-a-t-7-with-ubuntu/)

---

### Post by qwiksilver711 on 2013-01-13
I have tried these steps with an edited config due to the fact that an MMO7 has more buttons than a RAT7. 
 My theory is there is some button that is reading as pressed on the mouse. If there was some way to record button presses I could edit the xorg config and disable the button

---

### Post by qwiksilver711 on 2013-01-16
so this is not ideal, but if i spam the mouse click on login, and then use ctrl alt del to log out, then log back in, it works

---

### Post by d4rk0wl on 2013-01-16
I know you marked the topic as solved but if I may I believe I can shed some light on the situation since I recently went through the same issuse as you with a RAT5 on a Kubuntu install. The reason why you are experiencing these issues is due to the multi-profiles button. The X window system is getting confused.

Editing the xorg file did not work for me either, I have an alternate writeup on my blog if you want to check it out. [http://d4rkb0x.com/wordpress](http://d4rkb0x.com/wordpress)

Regards,
- D4rk0wl

---

### Post by qwiksilver711 on 2013-01-16
Thank you! I will try this tomorrow and if it works I'll update an move on to my next issue.

---

### Post by Narcas on 2013-02-26
I have the same problem as you and I can't find a solution..

---

### Post by dargaud on 2013-02-26
I wrote some instructions for the RAT7 [here]("https://www.gdargaud.net/Hack/LinuxMouse.html")

---

### Post by Narcas on 2013-02-26
> **d4rk0wl said:**
> I know you marked the topic as solved but if I may I believe I can shed some light on the situation since I recently went through the same issuse as you with a RAT5 on a Kubuntu install. The reason why you are experiencing these issues is due to the multi-profiles button. The X window system is getting confused.

Editing the xorg file did not work for me either, I have an alternate writeup on my blog if you want to check it out. [http://d4rkb0x.com/wordpress](http://d4rkb0x.com/wordpress)

Regards,
- D4rk0wl

Do you know how to do that with the M.M.O.7?

---


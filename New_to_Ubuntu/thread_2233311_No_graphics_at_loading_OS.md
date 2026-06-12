---
title: "No graphics at loading OS"
date: 2014-07-07
forum: New to Ubuntu
---

### Post by gongonni on 2014-07-07
Hi, sorry for my poor english. I beg you all would be able to understand me. 

Last day, after months of non-entering into ubuntu (I have Win7 and ubuntu installed on my PC) I choose ubuntu in OSloader. Then, ubuntu loaded as image shows:

[IMG]http://i60.tinypic.com/28hin1s.jpg[/IMG]

No graphics shows. Only DOS lines. I enter my password and DOS lines still appears.

Have anyone know what is happening to my ubuntu?

Thanks!

---

### Post by Vladlenin5000 on 2014-07-07
Has it ever worked, I mean with a graphical interface?
What happens (eventual error messages) when you do *startx* after logging in?

---

### Post by gongonni on 2014-07-07
Yes, It ran well when I installed ubuntu... let's say, year a half ago.
I don't remember if there were any error message, but. I bet it not. Only appears the typical DOS line logged in. "/Albert-Desktop/[..]:" or similar. I repeat: I don't remember well, but I was able to do things. But the only thing I did was type "exit" or "restart"

---

### Post by Vladlenin5000 on 2014-07-07
OK, a clearer picture no doubt (and pun intended) but what about > What happens (eventual error messages) when you do *startx* after logging in?
(I was asking you to do it and post back the error messages)

---

### Post by gongonni on 2014-07-08
Of course! I knew that I was to shoot a picture on the screen, but where I live was 2 AM so, I just reply only a part of the question. Today I make the shot:

[IMG]http://i62.tinypic.com/sw5nhy.jpg[/IMG]

---

### Post by Vladlenin5000 on 2014-07-08
As expected, an API mismatch error. You'll need to reinstall the nvidia drivers and in order to do that you need to remove all traces of the current ones. This should guide you trough: [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by gongonni on 2014-07-08
Thanks! I'll try it!

---


---
title: "lost unity greeter"
date: 2016-05-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2016-05-02
running 16.04. after i removed lubuntu and lxde lost the unity greeter only have the lubuntu one. any idea how to restore/tks

---

### Post by RobGoss on 2016-05-02
Hello and welcome, This post might help you out
[http://askubuntu.com/questions/403477/restore-unity-greeter](http://askubuntu.com/questions/403477/restore-unity-greeter)

---

### Post by rburkartjo on 2016-05-02
rob tks. i did this 
ran this in terminal
gksudo gedit  /etc/lightdm/lightdm.conf

and added

user-session=ubuntu
greeter-session=unity-greeter

saved and restarted puter

---

### Post by RobGoss on 2016-05-02
Were you able to reinstall the [COLOR=#000000]unity-greeter[/COLOR]

---

### Post by rburkartjo on 2016-05-02
yes

---

### Post by RobGoss on 2016-05-02
Great if you're satisfied with the out come of this post can you mark this post as solved

You can use the Thread Tool tab at the top of this post

Thank you

---


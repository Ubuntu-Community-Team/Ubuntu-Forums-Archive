---
title: "how to add process to Services window ?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by mokkai on 2008-06-12
when my system was with ubuntu 7.04 , i installed postgresql .
it was listed in Services window(list). fromthat i can off postgresql,so it didn't rum at booting time (whenever i want postgresql i did start it with manually like sudo /etc/init.d/postgresql start)

now my os ubuntu-8.04, i installed postgresql(through synaptic)
but postgresql is not listed in services

how can i add that process into services window ?
or 
is there any way to stop the process (/etc/init.d/postgresql) at boot time ?

---

### Post by kpkeerthi on 2008-06-12
Here is a good link that talks about tools available to configure startup "services":
[http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html](http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html)

---

### Post by mokkai on 2008-06-13
when i use "update-rc.d application remove" 
it is removing whole file
but i don't want like that.....
because later i want to run my application (if i want)

---

### Post by hyper_ch on 2008-06-13
what filoes will be removed? It removes just the symlinks in the according runlevels...

---


---
title: "Startup questions"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by edison2 on 2014-10-24
Hello.

I'm really confused when it comes to startup applications or services. I see references to /etc/init.d, /etc/rc.local, /etc/rcx.y. I'm not sure what each stands for. As far as I can tell, init.d where start up scripts live. As for the others, I don't know lol.

In my case, I installed memcached from source files manually on 13.04 (because 13.04 and its repositories are no longer up). I copied and pasted some ./configure and make commands for the install. As far as I know and hope, the program installed correctly. I had to run the memcached bin manually. How would I get to start automatically on start up? For sure I don't see a service under init.d.

Hope this makes sense.

---

### Post by nerdtron on 2014-10-24
HHmmm not quite sure about, but I think the init.d folder is the location for installed programs to place their "init scripts" in order to start, stop, reload and restart. While rc.local is more like a "run this command once upon start up"

A fairly good explanation here [http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/](http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/)

---

### Post by Alireza_Zamani on 2014-10-31
hi

in linux operating systems usually you can run services in two different ways :

1) by [COLOR=#ff0000]init[/COLOR]
2) or by [COLOR=#008000]xinetd[/COLOR]

after you have installed [COLOR=#0000cd]memcached[/COLOR] , it automatically running, you can test this bye type this command :

> $ pidof memcached

or in output of this command :

> $ pstree -aef

and by default it is managed by [COLOR=#ff0000]init[/COLOR] , you can see this in that commands,

after installed you can change Configurations in /etc/memcached.conf

> /etc$ vim memcached.conf

for more info you can read man page :

> $ man memcached

---


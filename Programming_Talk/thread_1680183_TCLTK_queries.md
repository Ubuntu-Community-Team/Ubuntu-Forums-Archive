---
title: "TCL/TK queries"
date: 2011-02-02
forum: Programming Talk
---

### Post by sandeep.bangalore09 on 2011-02-02
Hello every one,
 
i am pretty new to toll command language(TCL).i have written a script on tcl which will tellnet to all the systems connected to my network and get some details from them.but for that i need to enable telnet services for each system.is there any way so that i can write a script which will automatically enable the services in each system and then it will start to do the telnet proccess.or shall i use any 3rd party s/w which can enable the services from remotely.
 
any help regarding this will be appreceated.
thank you.
you can send me mail to [EMAIL="sandeep.bangalore09@gmail.com"]sandeep.bangalore09@gmail.com[/EMAIL]

---

### Post by fct on 2011-02-02
Don't use telnet. Use SSH.

Also, you need third party software for remote systems administration if you want to start services. Webmin is a popular choice.

---


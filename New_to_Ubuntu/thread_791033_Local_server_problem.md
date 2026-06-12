---
title: "Local server problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-11
Hi all,
I'm installad apache on my own pc. But there is a problem. I was start it. But I saw problem. Then i start Mongrel server. It runs. After that I show my result of my application. But it have a problem. Somebody help me ? And any idea


Please show my attached files !!!!!!!!!!!!

---

### Post by Monicker on 2008-05-11
Please give details. What kind of problem do you mean exactly?

---

### Post by Zeck on 2008-05-11
Okay attach my errors. Please show my attached files.

---

### Post by Monicker on 2008-05-11
> **Zeck said:**
> Okay attach my errors. Please show my attached files.

Apache could not start up on port 80 because something else was already listening on that port.


What does this command show?

```
sudo netstat -anltp |grep :80
```


Did you start Mongrel server while apache was disabled?  It may have bound to that port also, thus preventing apache from using it later.

---

### Post by Zeck on 2008-05-11
> **Monicker said:**
> Apache could not start up on port 80 because something else was already listening on that port.


What does this command show?

```
sudo netstat -anltp |grep :80
```


Did you start Mongrel server while apache was disabled?  It may have bound to that port also, thus preventing apache from using it later.

Yes, I stop my appache then I start mongrel server. Could you tell me how to solve this problem. I'm just newbie. Could you teach me step by step ?

Best regards
Zeck

---

### Post by Monicker on 2008-05-11
Both servers can't listen on port 80 at the same time.  You can either change the default port for apache, or change it for mongrel.

For apache you would change the default port in /etc/apache2/ports.conf:

```
Listen 80
```

Change the 80 to something else. And then do

```
sudo /etc/init.d/apache2 reload
```

Of course, now you would have to specify the new port when you connect to apache.


[http://localhost:1234](http://localhost:1234) - for example

---

### Post by Zeck on 2008-05-11
> **Monicker said:**
> Both servers can't listen on port 80 at the same time.  You can either change the default port for apache, or change it for mongrel.

For apache you would change the default port in /etc/apache2/ports.conf:

```
Listen 80
```

Change the 80 to something else. And then do

```
sudo /etc/init.d/apache2 reload
```

Of course, now you would have to specify the new port when you connect to apache.


[http://localhost:1234](http://localhost:1234) - for example


Thanks. It helps for me. 



Best Regards 
Zeck

---


---
title: "gksu nautilus gives nautilus:6691 warning"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-11
The following warning is displayed in terminal.  Any ideas on why this warning is displayed?

```
bs@bs-laptop:~$ gksu nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6691): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown
bs@bs-laptop:~$ 
```

---

### Post by bapoumba on 2008-11-11
I get the same, probably because samba is not installed. The forums are slow for me ATM, but I found threads with the same error. Nautilus runs with root priviledge, so I think it is just a warning.
[http://ubuntuforums.com/showthread.php?p=5313622](http://ubuntuforums.com/showthread.php?p=5313622)

---

### Post by shoot2kill on 2008-11-11
nvm, i didnt read all of the error messege.. =[
ignore post

---

### Post by shoot2kill on 2008-11-11
wtf, double post because of slow forums.. =[

sorry

wouldnt have been so bad if the first wasnt a mistake..

---

### Post by bapoumba on 2008-11-11
Graphical apps should not be invoked with sudo but with gksudo or gksu 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I see the link I pasted is wrong, but I cannot retrieve the thread I found..

---

### Post by boof1988 on 2008-11-11
> **bapoumba said:**
> Graphical apps should not be invoked with sudo but with gksudo or gksu 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I see the link I pasted is wrong, but I cannot retrieve the thread I found..

Thanks for the links... will take a look at them.  I have a pretty hard time finding stuff when searching so I really appreciate the links.

I *did* use gksu for running nautilus.  One of my next tasks is understanding the difference between sudo, gksu and gksudo.  Think I have a couple links somewhere (Ubuntu Community Documentation) that talk about these.

Thanks again...

---

### Post by bapoumba on 2008-11-12
I know you used gksu, but the post above has been deleted by the member, so now my comment makes no sense, it was not directed at you ;)
I'll leave it, these links are useful anyway.

---


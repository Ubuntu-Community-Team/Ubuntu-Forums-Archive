---
title: "Can not find the file ca.crt"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by xavi fernandez on 2011-11-08
Hi, I installed open vpn, and doesn't appear when I look for it typing in the dash home, the only way to find it is when I press Alt+F2 and when I typin for openvpn appears there and the files ca.crt too, but I can not access them.
How can I manage this files?

I need this files for import inside the configuration of the vpn and make it work... I hope!!!

Thanks in advance

---

### Post by xavi fernandez on 2011-11-08
I add a screen shot for see better the icons from the files in case this help

---

### Post by llamabr on 2011-11-08
To locate a file, try the 'locate' command:

```
brock@vader:~$ locate ca.crt
/usr/share/ca-certificates/debconf.org/ca.crt
/usr/share/doc/openvpn/examples/sample-keys/ca.crt
brock@vader:~$ 
```

---

### Post by xavi fernandez on 2011-11-08
Thanks llamabr for your fast reply, I did what you said, and come exactly in the terminal what you wrote to me. The think is that after that I went to home/documents/and there was just a folder named linux configuration when I open it just came the files for the vpn, but not the ca.crt ones :(

---

### Post by llamabr on 2011-11-08
Hi.  Well, what that says is that you can get to the file, by doing:

```
nano /usr/share/ca-certificates/debconf.org/ca.crt
```
I'm not quite sure what the file does, but if you're trying to edit it, you'll go to it there.  I'm not sure what you're looking for in your Documents file, etc.

---


---
title: "cant keep connected to networked"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Kedster on 2008-06-12
ok in gutsy and feisty i could connect to network drives right and then it would make a link on my desktop and reconnect every startup but in hardy i can connect to them but then like it makes only a temporary link and it isn't there the next log in. how can i make it do what it did before

---

### Post by Xiong Chiamiov on 2008-06-12
Assuming that they are sharing via nfs, you can add a line something like this to your fstab:
```

192.168.1.101:/media/samba/anime   /files/anime   nfs   rsize=8192,wsize=8192,timeo=14,intr,rw,noatime   0   0

```
This is mine, of course, but adjust the first address to be the remote one, and the second to where you want to mount it.  Make sure that you have a folder to mount it to first.

---

### Post by Kedster on 2008-06-12
umm yes they are samba but what ip dop i use like that the other comps or mine or what 
it on a router so

---

### Post by cariboo on 2008-06-13
You use ip address of the computer that the shared drives are mounted in.

Here is a link that might interest you

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

Jim

---


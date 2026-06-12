---
title: "running no-ip help?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-05-23
I have installed noip2 from the guide here 
[http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

I use no-ip for my linux set top box. (Which is on 24/7) only today my router has been switched off. So i needed to update the no-ip client.

I tried

xxxxx@xxxxx-laptop:~$ noip2
Can't locate configuration file /usr/local/etc/no-ip2.conf. (Try -c). Ending!

xxxxx@xxxxx-laptop:~$ 

Had to do something i did not want to do! Turned on the wife m$! (but made it a point to use vnc from ubuntu hahah)

Just to run the no-ip from windows.

How can i run it from ubuntu please?

Thanks

---

### Post by Cypher on 2008-05-23
Check the directory /usr/local/etc and see what's there. Did you run the "make install" step in those instructions?

---

### Post by Monicker on 2008-05-23
You need to create the config file.


```
sudo noip2 -C
```

---

### Post by H.Callahan on 2008-05-23
I believe you need:```
sudo noip2
```

---

### Post by iwannalearn on 2008-05-23
Thanks guys, got it working now

:)

---


---
title: "how to give linux a name similar to domain names?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-01
Hi
Thank you for reading my post
I remember that in windows we could edit ```
hosts
``` file to add new entries like 127.0.0.1 legolas.com now I am looking for a similar file in linux to ensure that I can type the same thing in my browser instead of 127.0.0.1

Thanks

---

### Post by stuarttaylor on 2008-11-01
You can edit the hosts file by entering the following into the terminal:

```

sudo gedit /etc/hosts

```

The hosts file can also be changed from the network manager under System>Network>Hosts

Hope this helps.

---


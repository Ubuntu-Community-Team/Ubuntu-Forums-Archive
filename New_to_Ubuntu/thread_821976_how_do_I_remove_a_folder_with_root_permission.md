---
title: "how do I remove a folder with root permission?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by shamusl on 2008-06-07
When I go to remove the folder:

```
/home/shamus/VMware-server-e.x.p
```

But it won't let me, it says I don't have proper permissions, can anybody help me with this?

---

### Post by Oldsoldier2003 on 2008-06-07
> **shamusl said:**
> When I go to remove the folder:

```
/home/shamus/VMware-server-e.x.p
```

But it won't let me, it says I don't have proper permissions, can anybody help me with this?

```
sudo rm -r /home/shamus/VMware-server-e.x.p
```

---

### Post by rampageoberon on 2008-06-07
use sudo to gain temporary root privilages

```
sudo rm -r /home/shamus/VMware-server-e.x.p
```

remember rm can not be reversed.

---

### Post by DBrocks on 2008-06-07
in the terminal:

```
sudo rm -rf /home/shams/VMware-server-e.x.p.
```

That will do it for you.

---

### Post by DBrocks on 2008-06-07
lol 3 people posted the same thing at once...

---

### Post by rampageoberon on 2008-06-07
Hehe, still good to know that there is a lot of support for open source software :-)

---

### Post by issih on 2008-06-07
All the above replies are absolutely correct, if you prefer a less command line oriented method (though not by much) you can enter the following:

gksudo nautilus

which will launch the file manager with root privileges.

Obviously, if you are not careful, you can seriously mess things up from in there, and you should close it as soon as you are finished with it, but its a bit less daunting if you are not comfortable with command line stuff

---

### Post by shamusl on 2008-06-07
> **Oldsoldier2003 said:**
> ```
sudo rm -r /home/shamus/VMware-server-e.x.p
```

thank you.

---


---
title: "Transmission (Torrent)"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-08-04
Hi, i downloaded a move few minutes ago but the movies comes in folders which is .rar 

do i need to move it to windows to burn it on a DVD or is there any solution under ubuntu ?

---

### Post by sharks on 2008-08-04
[http://tombuntu.com/index.php/2008/02/15/open-rar-archives-in-ubuntu/](http://tombuntu.com/index.php/2008/02/15/open-rar-archives-in-ubuntu/)

sudo apt-get install unrar

---

### Post by AdamWood on 2008-08-04
.rar files can be "unzipped" using the unrar and unrar-free packages. unrar-free doesn't support the newest version of rar however. Either install unrar through synaptic or from a terminal.
```

sudo apt-get install unrar-free

```

---

### Post by Vivaldi Gloria on 2008-08-04
> **Ginoxy said:**
> Hi, i downloaded a move few minutes ago but the movies comes in folders which is .rar 

do i need to move it to windows to burn it on a DVD or is there any solution under ubuntu ?

Install unrar using synaptic. Then click the file and choose extract.

To burn use brasero or k3b.

---

### Post by Ginoxy on 2008-08-04
Thanks all, but do i need to add all these folders together when burning ? i mean it comes as parts part1 2 3 4 like 20 parts how can i make them as a movie later on?

---

### Post by hyper_ch on 2008-08-04
unrar it first

---

### Post by Vivaldi Gloria on 2008-08-04
> **Ginoxy said:**
> Thanks all, but do i need to add all these folders together when burning ? i mean it comes as parts part1 2 3 4 like 20 parts how can i make them as a movie later on?

If you right click the first one and choose exract it will join all.

---


---
title: "edit NetworkManger.conf"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by sistyN on 2011-11-01
how can i edit NetworkManger.conf in terminal ?

---

### Post by Yayestechlab on 2011-11-01
To edit networkmanager.conf run ```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
``` in the terminal.

---

### Post by wildmanne39 on 2011-11-01
Hi, the better question is why do you want too? most likely if you edit network manager or its settings it may quit working.
Thank you

---

### Post by sistyN on 2011-11-03
> **Yayestechlab said:**
> To edit networkmanager.conf run ```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
``` in the terminal.



ty , but didnt work :

           ```
failed to run gedit'/etc/NetworkManger/NetworkManger.conf'
as user root unable to copy the user's Xauthorization file .
```

---

### Post by sistyN on 2011-11-03
> **wildmanne39 said:**
> Hi, the better question is why do you want too? most likely if you edit network manager or its settings it may quit working.
Thank you


My NetworkManger status changed to unmanaged . I dont know the reason !

---

### Post by Majorix on 2011-11-03
> **sistyN said:**
> ty , but didnt work :

           ```
failed to run gedit'/etc/NetworkManger/NetworkManger.conf'
as user root unable to copy the user's Xauthorization file .
```

Is there a space between gedit and the path of the conf file? The one you got there is an odd error.

---

### Post by Yayestechlab on 2011-11-04
Try running the command again after making sure you have a space after gedit. If that doesn't work try running ```

sudo nano /etc/NetworkManager/NetworkManager.conf

```

---

### Post by cbowman57 on 2011-11-04
> **sistyN said:**
> My NetworkManger status changed to unmanaged . I dont know the reason !

NetworkManager.conf
managed=true

---

### Post by sistyN on 2011-11-06
> **Yayestechlab said:**
> Try running the command again after making sure you have a space after gedit. If that doesn't work try running ```

sudo nano /etc/NetworkManager/NetworkManager.conf

```


ty , its worked !

why network manager status changed to unmanaged ?

---

### Post by vasa1 on 2011-11-06
> **wildmanne39 said:**
> Hi, the better question is why do you want too? most likely if you edit network manager or its settings it may quit working.
Thank you

I've found no functional difference in ```
managed=true
``` and ```
managed=false
```

(Any expert in Network Manager is welcome to help me as well [over here]("http://ubuntuforums.org/showthread.php?t=1873217").)

---

### Post by cbowman57 on 2011-11-06
> **sistyN said:**
> ty , its worked !

why network manager status changed to unmanaged ?

Not certain, it must have been updated recently & modified or replaced that file.

---


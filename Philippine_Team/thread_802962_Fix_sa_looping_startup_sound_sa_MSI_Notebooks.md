---
title: "Fix sa looping startup sound sa MSI Notebooks"
date: 2008-05-21
forum: Philippine Team
---

### Post by Nhatz on 2008-05-21
Tagal ko nang naghahanap ng ng fix nito kagabi ko lang nakita.. hehehe :)
ngayon ok na yung MSI laptop ko installed na ang hardy wala nang problema. 
ang pinaka problem pala nya ay sa Kernel.. 
palitan lang yung stock kernel nya (2.6.24-16-generic) to (2.6.24-16-386) 
then yun tapos ang problem.

System --> Administration --> Synaptic Package Manager
check linux-386 then apply and reboot

or

sa terminal

Applications --> Accessories --> Terminal

```
sudo apt-get install linux-386
```

Astig! :)

---

### Post by rjmdomingo2003 on 2008-05-22
> **Nhatz said:**
> Tagal ko nang naghahanap ng ng fix nito kagabi ko lang nakita.. hehehe :)
ngayon ok na yung MSI laptop ko installed na ang hardy wala nang problema. 
ang pinaka problem pala nya ay sa Kernel.. 
palitan lang yung stock kernel nya (2.6.24-16-generic) to (2.6.24-16-386) 
then yun tapos ang problem.

System --> Administration --> Synaptic Package Manager
check linux-386 then apply and reboot

or

sa terminal

Applications --> Accessories --> Terminal

```
sudo apt-get install linux-386
```

Astig! :)
Nung pagka-upgrade ko, yan din ang ininstall ko para mapagana ko yung sound ng laptop ko. Tip c/o chinwong.com

---


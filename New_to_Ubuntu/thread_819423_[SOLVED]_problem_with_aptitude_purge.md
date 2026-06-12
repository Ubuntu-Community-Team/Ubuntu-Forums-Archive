---
title: "[SOLVED] problem with aptitude purge"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by novatotal on 2008-06-05
been trying to remove pakages installed by me, but synaptic, leaves behind orphaned files even with complete removal choice, found out theres a way of doing it using aptitude and a short howto but I must be doing something wrong because it wont work, heres what I get when trying to purge
eduardo@eduardo-desktop:~$ sudo purge
sudo: purge: command not found
eduardo@eduardo-desktop:~$ sudo purge~'ies4linux'
sudo: purge~ies4linux: command not found
eduardo@eduardo-desktop:~$ purge ~'ies4linux'
bash: purge: orden no encontrada
eduardo@eduardo-desktop:~$ sudo purge ~'ies4linux'
sudo: purge: command not found
eduardo@eduardo-desktop: $ 

also cant find the correct key to this character  ~

and to anybody up to speed with my problem with internet exploiter: I haven't found the solution yet!

check that thread for update to what I have tried!!!
thank you all for your help!!!

---

### Post by bcom on 2008-06-05
I'm not sure you have the correct command.

Try sudo aptitude purge [name of the package you want to purge]

---

### Post by novatotal on 2008-06-05
> **bcom said:**
> I'm not sure you have the correct command.

Try sudo aptitude purge [name of the package you want to purge]
 

hey that almost worked!!! the command structure is correct, but there must be something else wrong!! aptitude did try to purge but...
 heres what I got in terminal!!!

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ies4linux"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "ies4linux"

sorry here it goes in my own translate ok?
readding pakage list... done
creatin dependencis tree
reading state information... done
reading extended state information
initialasing pakage state... done
building tags database... done
unable to find any pakage matching ies4linux
unable to find any pakage matching ies4linux
hope the translations is accurate if not I beg your pardon!!!!

---

### Post by novatotal on 2008-06-05
have to go to work!! sorry read your posts latter dudes!!!

---

### Post by starcannon on 2008-06-05
You could also search for that package in synaptic package manager, then check the "completely remove" button. thats what I do when I forget the exact package name.

---

### Post by philinux on 2008-06-05
This is a useful utility

GtkOrphan from synaptic, it's the frontend to deborphan.

---

### Post by novatotal on 2008-06-05
> **starcannon said:**
> You could also search for that package in synaptic package manager, then check the "completely remove" button. thats what I do when I forget the exact package name.

did that but synaptic is unable to find ies4linux, maybe it is not a package?

any way thank you for your time

---

### Post by novatotal on 2008-06-05
> **philinux said:**
> This is a useful utility

GtkOrphan from synaptic, it's the frontend to deborphan.

thank you very much!! so that removes orphaned files with out the need off aptitude! great!!! shame it wont work with ies4linux, I'm beginning to think it is not a package!!!

---

### Post by novatotal on 2008-06-08
well after all I don't want to remove ies4linux!!! it does work, only that with my poor knowledge off linux I wasn't able to find the icon,(on the desktop folder) not on the desktop-like w$!!!! but now I found it and well continue thinkering with my ubuntu untill it breaks or is in a state where I'm happy with it!!!!:guitar:

---


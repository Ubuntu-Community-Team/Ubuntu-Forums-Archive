---
title: "scary looking red circle"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by shayvasa on 2008-10-13
hey all...
im getting an error when trying to update ubuntu...heres the error and a photo of the red circle.

E:Problem parsing dependency Depends, E:Ocurrió un error mientras se procesaba btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado

---

### Post by acosta68 on 2008-10-13
Hi, change in /etc/apt/sources.list where is "harty" for "hardy"

then:

sudo apt-get update
sudo apt-get upgrade

Bye!

---

### Post by Vadi on 2008-10-13
What the above person said. You got a typo!

---

### Post by shayvasa on 2008-10-13
gracias acosta!

---


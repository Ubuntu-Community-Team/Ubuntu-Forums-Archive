---
title: "Not able to run system as root"
date: 2020-02-26
forum: New to Ubuntu
---

### Post by alfero on 2020-02-26
Hi,

I installed Xubuntu yesterday, i don't see a section here at these forums for this 'flavor', neither for other languages (Spanish, my case).

Well i have realized now that i'm not able to do anything as # what step i'm missing here?:

```
kaos@kaos-pc:~$ su 
Contraseña: 
su: Fallo de autenticación
kaos@kaos-pc:~$ su -
Contraseña: 
su: Fallo de autenticación
kaos@kaos-pc:~$ sudo apt update
[sudo] contraseña para kaos: 
Obj:1 http://us.archive.ubuntu.com/ubuntu eoan InRelease
Des:2 http://us.archive.ubuntu.com/ubuntu eoan-updates InRelease [97.5 kB]
Obj:3 http://security.ubuntu.com/ubuntu eoan-security InRelease
Des:4 http://us.archive.ubuntu.com/ubuntu eoan-backports InRelease [88.8 kB]
Descargados 186 kB en 1s (223 kB/s)  
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se pueden actualizar 3 paquetes. Ejecute «apt list --upgradable» para verlos.
kaos@kaos-pc:~$ 



```

Sorry for my questions and my poor english,

Saludos ):P

---

### Post by deadflowr on 2020-02-26
You used sudo and it worked, so what's the issue?
Ubuntu sets root as locked by default.
See:[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
> I installed Xubuntu yesterday, i don't see a section here at these forums for this 'flavor', 
Official flavors of Ubuntu are just as openly supported in the main forums as main Ubuntu is, so post away.

>  neither for other languages (Spanish, my case).
These forums are officially English, though we do have minor sub forums for loco communities and other languages here:
[https://ubuntuforums.org/forumdisplay.php?f=183]("https://ubuntuforums.org/forumdisplay.php?f=183")

---

### Post by GhX6GZMB on 2020-02-26
Ubuntu does not allow a user to operate as "root" or "su".

Using "sudo" you can elevate the rights of single commands with your password, eg, "sudo apt upgrade".

---

### Post by Impavidus on 2020-02-26
If you really want a root shell (rarely useful), you can use sudo -s. That has the same effect as su, but you have to provide your own password, not root's password.

---

### Post by alfero on 2020-02-26
Thank you very much!. :D

---

### Post by rsteinmetz70112 on 2020-02-26
You can also run sudo -i which sets the home directory Usuallu /root) and shell in accordance with the password file for root.\
This is the same thing that would happen if you logged in as root.
It's useful sometimes if you need to strore scratch files.

---

### Post by TheFu on 2020-02-26
> **rsteinmetz70112 said:**
>  
It's useful sometimes if you need to strore scratch files.

A technique for that is to use tee with sudo.
```
$ egrep -i 'reject' /var/log/mail.log  | sudo tee /root/spammers
```

Assuming I understand the goal.

---

### Post by rsteinmetz70112 on 2020-02-27
When I'm doing a lot of administration or trouble shooting I sudo -i in a terminal window so I don't have to keep typing sudo. The fact I'm in /root (unless I change it) means I know where scratch files I make to store command output I may make go.  Since I started fooling with *nix long before sudo existed I'm comfortable as root when I need to be. I often have several terminal windows open on my desktop doing things on different machines, some as sudo -i and others as my main user on that machine.

---

### Post by hk42 on 2020-02-28
As I am a great fan of Midnight Commander I often use 
sudo mc 
in a text console to avoid entering password too many times.
It works with ssh login too.
PS : On a local machine gpm allows using mouse in text mode.

---


---
title: "How to become root"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by jtmedin on 2008-06-20
Trying to intall the nvidia drivers in 8.04 & it says i must be root. 
nvidia site said 'sh the-drivers-file-name' & that some how led to being root. So how does one become root? TIA

---

### Post by Oldsoldier2003 on 2008-06-20
> **jtmedin said:**
> Trying to intall the nvidia drivers in 8.04 & it says i must be root. 
nvidia site said 'sh the-drivers-file-name' & that some how led to being root. So how does one become root? TIA

```
sudo sh the-drivers-file-name
```

see the wiki for more information regarding root and sudo : [uwiki]RootSudo[/uwiki]

---

### Post by jakupl on 2008-06-20
write

```
sudo
```

before your command - that is if you are using the terminal.

---

### Post by drunkardivan on 2008-06-20
And, when you add "sudo", it will ask you for your password. Just type it in and hit enter. You will not see it, but it's there.

---

### Post by cerealtx on 2008-06-20
but just for informational purpouses, sudo su will put u into root, BE CAREFUL!!! u can compeltely trash your system, never go into root unless ABSOLUTELY necessary or u know what ur doing :)

---

### Post by Duck2006 on 2008-06-20
> **cerealtx said:**
> but just for informational purpouses, sudo su will put u into root, BE CAREFUL!!! u can compeltely trash your system, never go into root unless ABSOLUTELY necessary or u know what ur doing :)

And make sure you exit it after you have done what you needed to do.

exit

---

### Post by sdennie on 2008-06-20
> **cerealtx said:**
> but just for informational purpouses, sudo su will put u into root, BE CAREFUL!!! u can compeltely trash your system, never go into root unless ABSOLUTELY necessary or u know what ur doing :)

Not to sidetrack the thread but, to get a root shell, it's much better to use:

```

sudo -i

```

---


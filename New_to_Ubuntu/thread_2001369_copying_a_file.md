---
title: "copying a file ???"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by squrl on 2012-06-10
I have a network drive I can get to with the file browser. I have some files on my home directory that I want to move to the network drive. I cant get to the network directory from a terminal. When I drag and drop it says I dont have permission. If I cant get there from a terminal  how do I get those files copyed across???

Thanks

---

### Post by HarryTorry on 2012-06-10
You can type this into a terminal, and it will open a folder with root privileges. So you'll be able to copy/paste your files as if it was a normal folder browser. Be careful with it though!

```
sudo nautilus
```

---

### Post by squrl on 2012-06-10
Thanks Harry. Thats exactly what I needed.

---

### Post by Cheesemill on 2012-06-11
> **HarryTorry said:**
> You can type this into a terminal, and it will open a folder with root privileges. So you'll be able to copy/paste your files as if it was a normal folder browser. Be careful with it though!

```
sudo nautilus
```
Don't do this. You should always use gksudo for graphical qpplications:
```
gksudo nautilus
```

---

### Post by emoguitarist06 on 2012-06-11
> **Cheesemill said:**
> Don't do this. You should always use gksudo for graphical qpplications:
```
gksudo nautilus
```

I find sudo works better than gksudo

Example ```
sudo gedit
``` vs ```
gksudo gedit
```
the only difference is ```
gksudo gedit
``` will open the file you're trying to open so let's say ```
gksudo gedit /etc/fstab
``` BUT it will open gedit with two tabs. One for the fstab file that you requested and one empty one. I find this very annoying because when I ctrl+s to save my changes and than alt+4 the close gedit that annoying pop up pops up asking if I want to discard/save changes to gedit. It's referring to the blank open tab

```
sudo gedit /etc/fstab
``` won't do this

---

### Post by lisati on 2012-06-11
Some people swear by sudo, others by gksudo, it largely depends on what you're doing. Some useful information can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cheesemill on 2012-06-11
But using sudo with graphical applications has other problems associated with it. It can cause files in a users home folder to become owned by root with unexpected side effects.

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by timcowchip on 2012-06-11
> **squrl said:**
> I have a network drive I can get to with the file browser. I have some files on my home directory that I want to move to the network drive. I cant get to the network directory from a terminal. When I drag and drop it says I dont have permission. If I cant get there from a terminal  how do I get those files copyed across???

Thanks

Have you tried mounting your network drive with gigolo? Its in Miscellaneous - Graphical (universe)

---

### Post by Jimmyfj on 2012-06-11
Well, I might be a bit different 'cause I always use:

```
gksu nautikus
```

When ever I need to work graphically as root. Haven't had any problems with this way so far (since Ubuntu 7.04).

---

### Post by Cheesemill on 2012-06-11
gksu and gksudo are exactly the same thing:
```
rob@quantal:~$ ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 May 18 21:23 /usr/bin/gksudo -> gksu
```

---


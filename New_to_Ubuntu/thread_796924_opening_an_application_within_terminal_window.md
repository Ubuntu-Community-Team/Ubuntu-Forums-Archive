---
title: "opening an application within terminal window"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by mitchelljj on 2008-05-16
Hi,

How would I open an application within the terminal window?

The reason that I am asking is that after I upgraded to Hardy Heron my VMWare program menu option was no longer within the Applications -> System Tools menu.

Where would the file be that I could either double click on or call it within the terminal window.

I have noticed that the VMWare folder is still within the etc folder.

Thanks,

John

---

### Post by jaytek13 on 2008-05-16
use 
```
./
```
at the beginning of the program name you want to execute

---

### Post by mitchelljj on 2008-05-16
Thanks for the information, but I don't know how to find the program name that I need to execute.

John

---

### Post by starcannon on 2008-05-16
most programs get installed to /usr/bin

if you know the name of the program, or a partial name you can try this:

cd /
sudo find . -name *nameOfProgram*

The *'s are wild cards, so if your unsure of the name you can play around with some wildcard variations and partial program name variations. GL

---

### Post by mister_pink on 2008-05-16
Make copious use of tab completion always. So for example, for gedit, I could type "g" and press tab, and I'd get offered 200 options, so extend it to "ged" and press tab and you get gedit. 

 I don't use vmware so I dont know the file name, but try things starting with v! Its case sensitive, and while most things are lower case I noticed virtual box doesnt stick to this convention so vmware might not either. Also you need to double press tab when its not just one unique answer it wants to give.

---


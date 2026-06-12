---
title: "[SOLVED] transfer data between ubuntu computers"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-07-31
hi
I have 2 laptops running ubuntu and would like to transfer data between them
Is this as simple as purchasing a usb to usb cable plugging it in and off you go
Or is it more complex than this?
I have no idea of the procedure
any help appreciated

---

### Post by pearlythepirate on 2008-07-31
The easiest way to do this is to use a USB drive (either flash-drive or external hard drive) to transfer the data.

---

### Post by tuxxy on 2008-07-31
Maybe samba

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jimrz on 2008-07-31
do you have any sort of network setup? maybe a router you use to connect the boxes to the internet.

if so, samba ssh & ftp are all good. 

personally I like openssh for just moving data between boxes. the client for open ssh is installed by default and the server is easily installed using synaptic.

---

### Post by LTFC2020 on 2008-08-01
hi
if I connect the two machines with a lan cable (therefore off line)
how can I get them to 'talk' to each other - will openssh do this?
there is way too much data for a flash drive

---

### Post by roquefilipe on 2008-08-01
you will have to use a crossover cable: [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by billgoldberg on 2008-08-01
> **LTFC2020 said:**
> hi
I have 2 laptops running ubuntu and would like to transfer data between them
Is this as simple as purchasing a usb to usb cable plugging it in and off you go
Or is it more complex than this?
I have no idea of the procedure
any help appreciated

Do you use a router to connect to the internet? Are both computers connected to it?

Then you have a network and you can use ssh to transfer data.

Openssh is very easy to set up and use. You should be up and running in 2 minutes.

I've written the "how-to" on my blog:

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

Just connecting the computers with an usb cable won't work.

---

### Post by LTFC2020 on 2008-08-01
I have a router but only one cable
is it possible to just connect the two computers and not have them connected to the internet?
if not then i guess I'll get hold of another cable and do as you suggested
thanks

---

### Post by billgoldberg on 2008-08-01
> **LTFC2020 said:**
> I have a router but only one cable
is it possible to just connect the two computers and not have them connected to the internet?
if not then i guess I'll get hold of another cable and do as you suggested
thanks

I never tried it myself, but I don't think it will work.

Ethernet cables are cheap.

---


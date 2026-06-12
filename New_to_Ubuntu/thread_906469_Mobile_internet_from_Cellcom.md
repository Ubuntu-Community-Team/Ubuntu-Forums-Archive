---
title: "Mobile internet from Cellcom"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-08-31
Bs'd

Hi guys,

I'm thinking about getting mobile internet from cellcom.

They'll give me an extern modem for my labtop.  
My question is, how are my chances to get that modem working in Ubuntu? 
Does anybody have experience with that?

Carni.

---

### Post by Sealbhach on 2008-08-31
Hi,
Have you got more details on the modem?

Is it a 3G modem, connecting to the USB?


.

---

### Post by Carnivorum on 2008-08-31
Bs'd

I don't have the modem yet.  Before I get it, I would like to know whether or not I can use it with Ubuntu. 

Carni.

---

### Post by Carnivorum on 2008-08-31
Bs'd

Build in in my labtop is an Atheros 5007EG modem for wifi.

How do I get that working in Ubuntu?

Carni.

---

### Post by Carnivorum on 2008-08-31
Bs'd

Build in in my labtop is an Atheros 5007EG modem for wifi.

How do I get that working in Ubuntu?

Carni.

---

### Post by Carnivorum on 2008-08-31
> **Sealbhach said:**
> Hi,
Have you got more details on the modem?

Is it a 3G modem, connecting to the USB?


.


Bs'd

I know it does connect to the USB.


Carni.

---

### Post by Sealbhach on 2008-09-03
Hi,

Just looking on Google, there's a walkthrough here:

[http://www.seejay.net/2008/03/get-atheros-5007eg-working-under.html](http://www.seejay.net/2008/03/get-atheros-5007eg-working-under.html)

So it can be got to work in Linux, it just takes a little effort.



.

---

### Post by Carnivorum on 2008-10-12
Bs'd

I have to do this: 

Open the Terminal. Go to the folder where you got the windows driver(the .inf file) for your Atheros card and type
ndiswrapper -i xxx.inf (replace xxx with the name of the inf file)

But how do I go to the .inf file in the terminal?

I have the terminal open

---

### Post by Carnivorum on 2008-10-12
Bs'd

Can somebody tell me what this means:  tar xfz madwifi-ng-r3366+ar5007.tar.gz (this comand has to be issue in the same folder where you downloaded the file from point nr. 3)

The folder with the driver is in my desktop.  So what would the command be then?


Carni

---


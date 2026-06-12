---
title: "HOWTO: Install your Canon PIXMA MP130 Printer using the iP1500 Printer Driver"
date: 2008-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Ziggy72 on 2008-04-19
I installed my MP130 printer using the iP1500 driver by modifying the instructions posted by another forum member. I know that some of the instructions here are actually copied from his/her post (because I copied them at the time) but unfortunately I now don't know who the author was, so I can't acknowledge the source. Sorry.

Here goes - I've kept the instructions brief and to the point.

Add the following to the /etc/apt/sources.list:
```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```
	
Then:
```
sudo apt-get update
```
Then:		
```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
```

Cupsys will be automatically restarted and you can select printer in cupsys configuration which is [html]http://localhost:631[/html]

To add the printer through the cups, the first thing you do is click on add a printer. The next screen will ask you for the name of you printer, location and description. The only thing you really have to fill in is the name – anything you want will do. After you have filled in the information click continue. The next page asks you to select your printer which should be 	Gutenprint USB Printer #1 (Canon MP130). Hit continue and then it will ask you for your driver. Select the Canon Pixma iP1500 Ver.2.50 (en) then click on add printer. Printing a test page should work! I've used the method on both Gutsy and Hardy. This resolved a problem I've struggled with for months! I hope it helps you.

---

### Post by Hex on 2008-05-03
Works excellent!

Is there an option to use the scanner as well?

---

### Post by el_mel on 2008-06-16
> **Ziggy72 said:**
> I installed my MP130 printer using the iP1500 driver by modifying the instructions posted by another forum member. I know that some of the instructions here are actually copied from his/her post (because I copied them at the time) but unfortunately I now don't know who the author was, so I can't acknowledge the source. Sorry.

Here goes - I've kept the instructions brief and to the point.

Add the following to the /etc/apt/sources.list:
```
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./
```
	
Then:
```
sudo apt-get update
```
Then:		
```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
```

Cupsys will be automatically restarted and you can select printer in cupsys configuration which is [html]http://localhost:631[/html]

To add the printer through the cups, the first thing you do is click on add a printer. The next screen will ask you for the name of you printer, location and description. The only thing you really have to fill in is the name – anything you want will do. After you have filled in the information click continue. The next page asks you to select your printer which should be 	Gutenprint USB Printer #1 (Canon MP130). Hit continue and then it will ask you for your driver. Select the Canon Pixma iP1500 Ver.2.50 (en) then click on add printer. Printing a test page should work! I've used the method on both Gutsy and Hardy. This resolved a problem I've struggled with for months! I hope it helps you.

Hi boy!
Thank for this post. i have seen in other places.
But i my case, it is the result when installing:
[FONT="Courier New"]mel@laptop-mel:~$ sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete libcnbj-2.5
[/FONT]

My system is a Hardy Heron, and AMD Turion 64
Some idea why for?  Thanks. :)

---

### Post by TAcuMopo on 2008-10-08
It`s work exellent. But how to set up printing for two-sided printing?
How to make scanner avaliable?

---

### Post by pelaopino on 2009-10-06
Works great!, considering that this posthas 1 year old!. all code lines-source codes still on!.

Cheers

---


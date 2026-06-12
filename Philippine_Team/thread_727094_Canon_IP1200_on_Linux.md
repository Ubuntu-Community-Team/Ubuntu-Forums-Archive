---
title: "Canon IP1200 on Linux"
date: 2008-03-17
forum: Philippine Team
---

### Post by dodimar on 2008-03-17
I have a Canon Pixma ip1200. I bought this before I made a decision to use Linux. Bad thing is Linux doesn't support this kind of printer (or should I say, this specific Canon printer doesn't support Linux).

I tried using Turboprint, but I have to purchase it in order to print in quality mode without its logo (can only print in draft).

I tried some instructions to use ip2200's driver, no go.

Is there any solution for my problem. Anyone who also use this kind of printer in their linux box?

Honestly, I'm getting frustrated on this one...

---

### Post by fedex1993 on 2008-03-17
well right now my canon pixma ip6010 has no driver for linux ecept using turboprint. i recommend buying it because it works well. Cannon does not like linux from what i have seen if you buy a new printer in the future i would go with an HP hp seems to love linux

---

### Post by dodimar on 2008-03-17
yeah... I just wish Turboprint is free. But I don't blame them because they have to purchase info from the printer manufacturers.

Well, if I have no other choice, I'd probably buy a new printer.

But if my credit card application will be approved the following weeks, I might buy Turboprint..

But if there's a solution aside from purchasing... it'll be great...:)

---

### Post by loell on 2008-03-17
i don't want to be implicated as violating the forum rules, ;)  but there is turboprint in tar format, from "other" sources if you know what i mean, probably just try it out ;)

---

### Post by wersdaluv on 2008-03-18
I have an MP150 and it works out of the box. I can scan and print. 

Are you on Gutsy? It supports a lot of printers. 

Anyway, here's a useful link [http://mynewbietips.blogspot.com/2007/06/installing-canon-pixma-ip1200-driver.html](http://mynewbietips.blogspot.com/2007/06/installing-canon-pixma-ip1200-driver.html)

---

### Post by dodimar on 2008-03-19
Unfortunately, na-subukan ko na yun. Using ip2200 driver for ip1200.. ang nang yayari, nagflash lang yung ilaw ng printer, tapos wala namang na-iprint.

Using Ubuntu 7.10... It supports lots of printer, canon ip1200 not included... pero nade-detect nya na canon ip1200 yung printer, pero walang driver...  <sighs>

Turboprint na lang ako.. sana ma-approve na ang credit card application ko...

---

### Post by loell on 2008-03-19
*ha..*   subukan mo muna yung nasa p2p na turboprint, bago mo bilhin *ching!!* :mrgreen:

---

### Post by dodimar on 2008-03-19
> **loell said:**
> *ha..*   subukan mo muna yung nasa p2p na turboprint, bago mo bilhin *ching!!* :mrgreen:

oo nga ano...

Bakit ba nakalimutan ko yun... hehehe

---

### Post by dodimar on 2008-06-06
Wala na ba talaga solution ito?

---

### Post by phpmonkey on 2008-12-15
I just got this working on my laptop using the following steps, from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Open up a terminal and 


1. ```
sudo nano /etc/apt/sources.list
```
Add the line > deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./ 

2. ```
sudo apt-get upgrade
```

3. ```
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

4. Open your web browser and go to > [http://127.0.0.1:631/](http://127.0.0.1:631/) which is the cupsys admin. Under the "home" tab" click "add printer" and follow the instructions, choosing > Canon iP2200 Ver.2.60 as your driver

5. Go to the "Printers" tab, and click "Print Test page".


It shoud be possible to do steps 4-5 through System>Administration>Printing but the correct driver wasn't showing up there for me, so I went through the cupsys browser admin instead.

Note: The only available printing option appears to be 600dpi

---

### Post by dodimar on 2008-12-16
> **phpmonkey said:**
> I just got this working on my laptop using the following steps, from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Open up a terminal and 


1. ```
sudo nano /etc/apt/sources.list
```
Add the line 

2. ```
sudo apt-get upgrade
```

3. ```
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
```

4. Open your web browser and go to  which is the cupsys admin. Under the "home" tab" click "add printer" and follow the instructions, choosing  as your driver

5. Go to the "Printers" tab, and click "Print Test page".


It shoud be possible to do steps 4-5 through System>Administration>Printing but the correct driver wasn't showing up there for me, so I went through the cupsys browser admin instead.

Note: The only available printing option appears to be 600dpi

I think I had tried this before, but still not working.. But I'll try it again on my next reinstall just to make sure..

Thanks for the info man..

---

### Post by nenyalorien on 2009-12-03
hi guys. I tried this, however the server already removed the driver. Is there any other solution to this? Thank you.

---


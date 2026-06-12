---
title: "Emergency boot option"
date: 2011-04-28
forum: Philippine Team
---

### Post by eSPiYa on 2011-04-28
Around 1 month na din ang lumipas mula nang nagshift ako sa Ubuntu as primary OS(wala ding MS Windows) ng desktop pc ko.

Kanina ay naka-corrupt 'yung naka-install na Ubuntu 10.10 sa machine ko and sinubukan kong maghanap kung paano i-boot sa terminal(walang Xorg) pero lahat ng options na nakikita ko ay nangangailangang maayos akong makapasok sa loob ng OS at d'un ayusin ang lahat(pero malabo dahil corrupted na). Paano ko ifo-force 'yung Grub na mag-boot sa terminal lang nang hindi ko kailangang mag-boot sa loob ng installed na OS.

Salamat po.

---

### Post by tech-hero on 2011-04-28
pwede nyo po gamitin yung live cd sir para makapagboot. then saka nyo po fix.

---

### Post by eSPiYa on 2011-04-28
> **tech-hero said:**
> pwede nyo po gamitin yung live cd sir para makapagboot. then saka nyo po fix.

Sa LiveCD lang s'ya magbo-boot and mounted lang 'yung HDD ko n'un.

---

### Post by tech-hero on 2011-04-28
"Paano ko ifo-force 'yung Grub na mag-boot sa terminal lang nang hindi ko kailangang mag-boot sa loob ng installed na OS."
 
Hindi ko po maintindihan yung part na ito.. ang gusto nyo po ba is makapasok lang sa ubuntu na walang GUI? as in sa terminal lang katulad ng safe mode?

---

### Post by dsdeiz on 2011-04-28
Edit lang daw ang entry ng grub tas append lang ng '3' sa end ng command para hanggang runlevel 3 lang w/c is wala daw x.. Hehe


> **eSPiYa said:**
> Sa LiveCD lang s'ya magbo-boot and mounted lang 'yung HDD ko n'un.

Pag ganito siguro, after mount ung hard disk, edit na lang ung config ng Grub. I think nasa /boot/grub/menu.lst though sa Grub 2, am not sure kung saan :D

Although if makapagboot naman sya, puede siguro gumamit ng ctrl + alt + f1 to f6 para mag switch sa ibang terminals.. Hehehe

> Kanina ay naka-corrupt 'yung naka-install na Ubuntu 10.10 sa machine ko and sinubukan kong maghanap kung paano i-boot sa terminal(walang Xorg) pero lahat ng options na nakikita ko ay nangangailangang maayos akong makapasok sa loob ng OS at d'un ayusin ang lahat(pero malabo dahil corrupted na). Paano ko ifo-force 'yung Grub na mag-boot sa terminal lang nang hindi ko kailangang mag-boot sa loob ng installed na OS.

Awts, sorry sir, mali ata pagka intindi ko :( Though baka worth the try lang :D Andun pa rin yung OS kahit walang gui.. Hehehe

---

### Post by eSPiYa on 2011-04-29
> **tech-hero said:**
> "Paano ko ifo-force 'yung Grub na mag-boot sa terminal lang nang hindi ko kailangang mag-boot sa loob ng installed na OS."
 
Hindi ko po maintindihan yung part na ito.. ang gusto nyo po ba is makapasok lang sa ubuntu na walang GUI? as in sa terminal lang katulad ng safe mode?

Yes boss, atleast sa terminal ay may power ako if everything failed.


> **dsdeiz said:**
> Edit lang daw ang entry ng grub tas append lang ng '3' sa end ng command para hanggang runlevel 3 lang w/c is wala daw x.. Hehe




Pag ganito siguro, after mount ung hard disk, edit na lang ung config ng Grub. I think nasa /boot/grub/menu.lst though sa Grub 2, am not sure kung saan :D

Although if makapagboot naman sya, puede siguro gumamit ng ctrl + alt + f1 to f6 para mag switch sa ibang terminals.. Hehehe



Awts, sorry sir, mali ata pagka intindi ko :( Though baka worth the try lang :D Andun pa rin yung OS kahit walang gui.. Hehehe
Kasi after i-update 'yung configurations ng Grub ay kailangang i-run 'yung command na grub update yata 'yun. Kung ira-run ko 'yun while under ng LiveCD; it means ang maa-update ay 'yung Grub ng OS na 'yun at hindi 'yung nasa internal HDD ko(dahil mounted lang ito). Correct me if I'm wrong.

Though na-reformat ko na 'yung machine ko, atleast ay alam ko ang gagawin ko next time mangyari ito sa akin. Thanks!

---

### Post by dsdeiz on 2011-04-29
Ah, right. Sorry, maling information :D Though I think if you mount your hdd, puede kang mag navigate sa mounted device and yung boot nia na dir. Not sure though. Anyway, glad you sorted it out. I had no idea about the update-grub thing.. Haha

---

### Post by jepong on 2011-04-29
> **tech-hero said:**
> "Paano ko ifo-force 'yung Grub na mag-boot sa terminal lang nang hindi ko kailangang mag-boot sa loob ng installed na OS."
 
Hindi ko po maintindihan yung part na ito.. ang gusto nyo po ba is makapasok lang sa ubuntu na walang GUI? as in sa terminal lang katulad ng safe mode?

press SHIFT

---

### Post by eSPiYa on 2011-05-01
> **jepong said:**
> press SHIFT

Thanks! Will try once na makauwi ako mamayang gabi. ^_^

---


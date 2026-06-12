---
title: "&quot;System dumped&quot; need some help to fix."
date: 2016-07-05
forum: New to Ubuntu
---

### Post by captainecook on 2016-07-05
Hello, i'm new to ubuntu system (ubuntu 14.04 LTS) and recently i have an issue. 
 

> Feaucon:~$ sudo apt-get update
Erreur de segmentation (core dumped)



Thanks for the help.

---

### Post by oldrocker99 on 2016-07-05
Segmentation faults are usually graphics-driver related. What is your GPU and which drivers are you using?

---

### Post by captainecook on 2016-07-06
Oh! i seach a lot but i didn't think about this. 

GPU: Nvidia GTS 450
Drivers : Nvidia binary-352.63 (tested)

---

### Post by X-RED_Tech on 2016-07-06
361 or 367 should be a better choice for that card (according to geforce.com) but you probably won't have either available in 14.04 without an additional PPA. 
I'm not sure upgrading the driver will solve it but I would test it (in a non production machine).

Please wait for other comments.

---

### Post by captainecook on 2016-07-07
i wait.

---

### Post by mörgæs on 2016-07-09
If you try a live boot of 16.04 what do you see under the 'additional drivers' tab?

---


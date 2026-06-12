---
title: "[SOLVED] Fan Control Question"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by stuart264 on 2008-08-02
I am having problems controlling the fans on my cpu, I have installed LM-Sensors which detects fine and pwmconfig runs but generates an permission denied error pwml1_enable, but starts up the fans but the moment I reboot the fans fail to start and I have to run pwmconfig from the command line again to start them.

Can anyone tell me what I need to do to get this started as I have worked through loads of the instructions for lm_sensors and pwmconfig and none of them seem to work right

---

### Post by collinp on 2008-08-02
> **stuart264 said:**
> I am having problems controlling the fans on my cpu, I have installed LM-Sensors which detects fine and pwmconfig runs but generates an permission denied error pwml1_enable, but starts up the fans but the moment I reboot the fans fail to start and I have to run pwmconfig from the command line again to start them.

Can anyone tell me what I need to do to get this started as I have worked through loads of the instructions for lm_sensors and pwmconfig and none of them seem to work right


The first error is due to you not running the command as root or "sudo". Add sudo to the command when you execute it in terminal again. The last error, sorry, but i have no clue.

---


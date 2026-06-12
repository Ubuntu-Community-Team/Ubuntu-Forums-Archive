---
title: "Headphone sound only since 12.04 upgrade"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Septuagenarian on 2012-05-15
Since upgrading my laptop to Precise 12.04 , I can only get sound on my headphone socket despite the output being set to internal speakers . I have tried all the usual things and can only assume it is a bug in pulse audio . When I boot into Oneric 11.10 the speakers work fine . There is a reference to this problem on launchpad and suggests downloading different sound card drivers , but not sure how to do this . Beginner level replies please .

---

### Post by NikTh on 2012-05-15
Hi , 
try to use alsamixer to see if something is muted.. open terminal and write ```
alsamixer
``` 

next option is to install pavucontrol.. ```
sudo apt-get install pavucontrol
``` and tick your speakers from there .

---

### Post by Septuagenarian on 2012-05-15
Thanks very much , I will give both ideas a try .

---

### Post by Lisiano on 2012-05-15
Also make sure you set Analogue output in the Connector option in the Sound Settings.

---

### Post by Septuagenarian on 2012-05-15
I have tried all these suggestions ,and according to alsamixer and pavucontrol the speakers are working ,but still no sound . So , have bought a mini plug in speaker to connect to the headphone socket , works fine . Problem ( sort of ) solved .

---

### Post by Lisiano on 2012-05-15
Question. Did you upgrade from 11.10 or did you reinstall 12.04 on top of 11.10? If the former, could you try burning a LiveCD/USB and check if sound works there? If it does, then there was an error during the upgrade or something else. If it doesn't then there was a regression and you should file a bug.

---

### Post by sequille on 2012-06-01
i am experiencing the same problem, tried everything that was suggested here. and to answer the latest question, fresh install. everything works except for the built-in speakers. i even installed it again because elsewhere i found that someone had this problem only after upgrading to the 3.2.0-24 kernel so i installed it with 3.2.0-23-generic. Nothing muted, i triple checked (alsamixer) :)
Also i am not satisfied with OP's solution of carrying around laptop speakers. (since he didn't return for an answer i assume it was good enough for him)

---

### Post by Hadaka on 2012-06-01
Are you running a 64bit system and the alsamixer display
shows the chipset of VT1708 ??

---

### Post by inashdeen on 2012-06-02
how bout changing the sound card option on pavu. maybe it point to the wrong card. just a suggestions

---


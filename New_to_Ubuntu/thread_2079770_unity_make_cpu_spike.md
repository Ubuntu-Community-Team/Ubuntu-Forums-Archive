---
title: "unity make cpu spike"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by hnf a on 2012-11-02
hi all i have a question why the cpu spike around 70% when i use clementine,chrome and few light app, is this normal in 12.04 or not if not is there any way to fix it without change to unity 2D? is in 12.10 the unity is more stable than 12.04

---

### Post by daslinkard on 2012-11-09
> **hnf a said:**
> hi all i have a question why the cpu spike around 70% when i use clementine,chrome and few light app, is this normal in 12.04 or not if not is there any way to fix it without change to unity 2D? is in 12.10 the unity is more stable than 12.04


Unity tends to be a bit resource-hungry,  though I am surprised to hear that you experienced similarly poor  performance even under Unity2D. One possible solution would be to play  around with other more lightweight Desktop Environments such as Lubuntu  (LXDE) or Xubuntu (XFCE). I think you will see a substantial difference  in overall responsiveness and performance.


  Additionally, you can try going into the Startup Applications manager  and unchecking applications and processes that you don't need Ubuntu to  automatically start for you at login (e.g. Bluetooth Manager if you  don't have bluetooth, UbuntuOne if you don't use it, programs you simply  don't use, etc.) Before doing this, first make hidden startup  applications visible in the manager:
  ```
sudo sed -i ‘s/NoDisplay=true/NoDisplay=false/g’ /etc/xdg/autostart/*.desktop
```

---

### Post by hnf a on 2012-11-11
actually i don't have any problem with unity 2D what i mean that i should change to unity 2d to make ubuntu run without taking a lot of cpu resource, and i think the problem isn't in the application because when i look at the top command the only app that taking a lot of cpu res is the unity,is there any think that can fix this and is in 12.10 the unity did't take a lot of cpu res?

---

### Post by vasa1 on 2012-11-11
> **hnf a said:**
> ... when i look at the top command **the only app** that taking a lot of cpu res** is the unity**,is there any think that can fix this and is in 12.10 the unity did't take a lot of cpu res?
Could you put up the data here, as well as your computer specs?

(Unity on 12.10 may or may not be a good idea on "older" PCs.)

---

### Post by monkeybrain2012 on 2012-11-11
Could be chrome, seen some bug report that it uses a lot of cpu before. 

It may be due to the Nvidia driver if you have a Nvidia card, in that case unchecke sync to vbank in ccsm and Nvidia settings may help.

---

### Post by jerome1232 on 2012-11-11
It's fairly normal for cpu's to do little spikes here and there, are you actually noticing any slowdowns or are you just glued to a resource monitor and freaking out when the needle moves?

---

### Post by hnf a on 2012-11-19
i have intel e2180 p5ld2x mobo and hd 5570,what i experience is not just litte spike actually its almost constant the cpu taking up to 50 percent everytime i browser the web or typing something in libreof and play small res video all in separate time not all at once and all i can see is compiez in top of the list

---


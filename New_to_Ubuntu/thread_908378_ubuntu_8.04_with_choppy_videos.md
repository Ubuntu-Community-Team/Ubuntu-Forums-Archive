---
title: "ubuntu 8.04 with choppy videos"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by wenhui100 on 2008-09-02
I am having problems with DVDs and video playbacks ... its seems a bit choppy ... can anyone help me .... i am using an ATI 9600 graphic card ... i am guessing there is something to do with the driver... oh .. and its and AMD 64 3200+     1GHZ .....
i have also installed a 2G ram ...

help please ...

---

### Post by nitro_n2o on 2008-09-02
it might be a problem with the driver and the OpenGL installation! 

make sure you have the right driver. I don't knw much about ATI cards, but Envy should be able to do this for you

sudo apt-get install envyng-core envyng-gtk 

Then just run the program and it'll detect your card and install the driver 

it won't hurt to install the opengl stuff as well

---

### Post by wenhui100 on 2008-09-02
Thanks nitro ... i will try it now ..

---

### Post by crispy_420 on 2008-09-02
My guess is video driver as well because DMA is standard now. (tell me if I'm wrong)

---

### Post by kansasnoob on 2008-09-02
Well, I've found VLC plays better.

Open synaptic and search for vlc. Install it and then  open terminal and:

```
sudo apt-get -f install
```

---

### Post by sharat3 on 2008-09-03
> **nitro_n2o said:**
> it might be a problem with the driver and the OpenGL installation! 

make sure you have the right driver. I don't knw much about ATI cards, but Envy should be able to do this for you

sudo apt-get install envyng-core envyng-gtk 

Then just run the program and it'll detect your card and install the driver 

it won't hurt to install the opengl stuff as well

Thanx a lot buddy..envy fixed my problem :)

---


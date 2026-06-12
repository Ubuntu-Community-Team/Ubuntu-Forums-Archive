---
title: "i want to enable ATI crossfire"
date: 2014-11-27
forum: New to Ubuntu
---

### Post by cosy2 on 2014-11-27
hello :)

i am new to linux and i want to enbale CF just because i have the 2 identical GPU installed 

i did google abit about this and i dint find the "sweep spot" for this problem so i decided to cry for help

```
sudo aticonfig --lsch
No Multiple GPU chains defined

```
then i made 
```
ticonfig --adapter=0,1 --cfa
Multiple GPU chain added
Warning: X needs to be restarted before MGPU changes take effect.

```

```
sudo aticonfig --lsch

Multiple GPU chain for adapter 0, status: disabled
  0. 01:00.0 AMD Radeon HD 5800 Series
  1. 05:00.0 AMD Radeon HD 5800 Series

```

now what i need to do ?

thanks in advance


edit: links [http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1)

---

### Post by Mark Phelps on 2014-11-27
I think you have to run Catalyst Control Center using the fglrx driver -- at least, that's what the linked thread indicates: [http://forum.wurmonline.com/index.php?/topic/74128-linux-with-crossfire-ati-cards/]("http://forum.wurmonline.com/index.php?/topic/74128-linux-with-crossfire-ati-cards/")

---

### Post by cosy2 on 2014-11-27
i do run the amd drivers but for some reason when i make ```
sudo amdcccle
``` there is no crossfire option in the menu

---

### Post by cosy2 on 2014-11-27
i managed to enable the crossfire
```
sudo aticonfig --lsch

Multiple GPU chain for adapter 0, status: Crossfire is enabled
  0. 01:00.0 AMD Radeon HD 5800 Series
  1. 05:00.0 AMD Radeon HD 5800 Series

```

i have a question now, the temperature, load and speed for the second GPU is not available because is on CF or because somehow the CF have failed ?

```
aticonfig --adapter=0 --odgt --odgc

Adapter 0 - AMD Radeon HD 5800 Series
            Sensor 0: Temperature - 57.00 C

Adapter 0 - AMD Radeon HD 5800 Series
                            Core (MHz)    Memory (MHz)
           Current Clocks :    725           1000
             Current Peak :    725           1000
  Configurable Peak Range : [550-900]     [900-1250]
                 GPU load :    0%

```
```
aticonfig --adapter=1 --odgt --odgc
ERROR - Get temperature failed for Adapter 1 - AMD Radeon HD 5800 Series
ERROR - Get clocks failed for Adapter 1 - AMD Radeon HD 5800 Series

```

---

### Post by cosy2 on 2014-11-28
```
aticonfig --lscs
    Candidate Combination: 
    Master: 0:0:0 
    Slave: 0:0:0 
    CrossFire is disabled on current device
    CrossFire Diagnostics:
    CrossFire can work with P2P mapping through GART
    Candidate Combination: 
    Master: 0:0:0 
    Slave: 0:0:0 
    CrossFire is disabled on current device
    CrossFire Diagnostics:
    CrossFire can work with P2P mapping through GART

```
i dont know what to make from this

---

### Post by dejan_da_dude on 2015-03-12
Have the same issue... new guy,, any suggestions would help.

I have two Hd 5770's - I hope these are supported to run in crossfire mode ..

 Thank you everyone!

---


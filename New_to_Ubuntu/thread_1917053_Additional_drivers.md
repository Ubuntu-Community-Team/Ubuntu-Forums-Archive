---
title: "Additional drivers"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by pqku on 2012-01-29
Hi , I'am completely new at ubuntu.
I have ubuntu 11.10.
I have found some additional drivers. Should I install them ? 

[http://i41.tinypic.com/mlms5d.png](http://i41.tinypic.com/mlms5d.png)

Thank you

---

### Post by carl4926 on 2012-01-29
Your ATI might work well enough using the Radeon driver, which is what you should have installed by default.
Wait for an ATI user to advise. Most folks do install these though.
If you post the result of
```
lspci -nnk
```
Everyone can see your hardware and drivers

---

### Post by Frogs Hair on 2012-01-29
If you are unable to run Unity 3D and Compiz effects you may want to install them .

---

### Post by nipunshakya on 2012-01-29
> **pqku said:**
> Hi , I'am completely new at ubuntu.
I have ubuntu 11.10.
I have found some additional drivers. Should I install them ? 

[http://i41.tinypic.com/mlms5d.png](http://i41.tinypic.com/mlms5d.png)

Thank you


I have the same stuffs identified by Additional Drivers too...guess no harm for you too...

---

### Post by pqku on 2012-01-29
So, my computer will be slower if i install them ?

---

### Post by nipunshakya on 2012-01-29
its just like installing a driver for your machine when you are using a windows on it.... slower in sense you may get few seconds of boot delay after installation or maybe u won't....(similar to after an update in windows....) ..but you can have full potential to use your machine with maximum hardware being utilized. Goodluck

Regards,WinuxUser

---

### Post by coffeecat on 2012-01-29
> **pqku said:**
> So, my computer will be slower if i install them ?

Not necessarily. For some/most ATI cards the open source driver that you are already using suffices for many users, myself included, but it partly depends on the actual graphics chipset you are using. Do you know which one this is? If you don't, open a terminal and post the output of this:

```
lspci | grep VGA
```

Sorry about asking you to open a terminal. It's simply easier and quicker to get the information needed. :)

---

### Post by pqku on 2012-01-31
> **coffeecat said:**
> Not necessarily. For some/most ATI cards the open source driver that you are already using suffices for many users, myself included, but it partly depends on the actual graphics chipset you are using. Do you know which one this is? If you don't, open a terminal and post the output of this:

```
lspci | grep VGA
```Sorry about asking you to open a terminal. It's simply easier and quicker to get the information needed. :)


Thank you for your answer. There is what you asked , hope it helps :)

VGA compatible controller: ATI Technologies Inc Device 9806

---

### Post by pqku on 2012-02-01
[UP] 

ty

---

### Post by mastablasta on 2012-02-01
wait for 2 days before bumping the thread.
 
anyway i am not sure we can tell about the card from that data. try the lshw command (it should list all hardware).
 
anyway if you do not have dual graphics (switching) it might be better to install proprietary drivers for better performance. some new cards though might have issues. and for those opensource drivers give better performance.
 
if needed the proprietary drivers (fglrx) can later be removed:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by nothingspecial on 2012-02-01
> **mastablasta said:**
> wait for 2 days before bumping the thread.
 


24 hours or so is fine :)

---

### Post by coffeecat on 2012-02-01
> **pqku said:**
> VGA compatible controller: ATI Technologies Inc Device 9806

A few google hits suggest that is the Radeon HD6320 card. I don't have experience of any of the 6*** series, so I'd better not comment on whether you are better with the open source or proprietary driver. Perhaps someone else can. However, I did find this:

[https://answers.launchpad.net/ubuntu/+question/178731](https://answers.launchpad.net/ubuntu/+question/178731)

No answers though, so it's difficult to say whether that is typical experience for that GPU.

---


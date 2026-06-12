---
title: "Driver for ATI Radeon X1400 in Ubuntu 11.10?"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by Flashlight242 on 2012-02-02
Help! Please!

I'm having problems installing a compatible driver for Ati Radeon X1400 graphics card on Ubuntu 11.10. Can someone give me some guidance?

Flashlight

---

### Post by BC59 on 2012-02-02
Try installing the driver from the repository x-swat:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install fglrx

```

---

### Post by mastablasta on 2012-02-02
> **BC59 said:**
> Try installing the driver from the repository x-swat:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install fglrx

```

are u sure about that? i don't think that card is supported by fglrx.

---

### Post by BC59 on 2012-02-02
> **mastablasta said:**
> are u sure about that? i don't think that card is supported by fglrx.

Why not? As I see here is supported.
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X1400](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X1400)
Do you no something in contrary?

---

### Post by Flashlight242 on 2012-02-03
Not working...any other suggestions?

---

### Post by Flashlight242 on 2012-02-03
I read  that "the last driver that supported your hardware was 2 and half years ago,  9.3 which you cannot run with the current versions of xorg and kernel  present in Ubuntu." Is there another option?

---

### Post by Mark Phelps on 2012-02-03
> **Flashlight242 said:**
> I read  that "the last driver that supported your hardware was 2 and half years ago,  9.3 which you cannot run with the current versions of xorg and kernel  present in Ubuntu." 
You're correct.

> Is there another option?
You don't NEED to install a video driver -- because you already have the default open-source driver installed.  That is done when you first setup Ubuntu.

---

### Post by Flashlight242 on 2012-02-03
> **Mark Phelps said:**
> You're correct.


You don't NEED to install a video driver -- because you already have the default open-source driver installed.  That is done when you first setup Ubuntu.


Thanks. I read about that... I guess I'm specifically trying to find out how to I get the same level of control over my monitor settings like in ATI Cat Control Center? I want to adjust the brightness, contrast, and gamma etc...

---

### Post by Mark Phelps on 2012-02-04
> **Flashlight242 said:**
> Thanks. I read about that... I guess I'm specifically trying to find out how to I get the same level of control over my monitor settings like in ATI Cat Control Center? I want to adjust the brightness, contrast, and gamma etc...

Sorry ... you don't. 

CCC features only come with the AMD driver -- and there's no driver that will work with your card and any Ubuntu version newer than 8.10.  AMD dropped driver support for your card when 9.04 came out.

---

### Post by mastablasta on 2012-02-04
maybe you can find something about that here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

droping the support of driver is ATI fault but having no GUI for configuring radeon driver is on the people who made the opensource driver. they could have included at least some basics. i believe some settings are found under other tools, but they are not stickign together,

anyway it can be done but it's messy: [http://ubuntuforums.org/showthread.php?t=1850578](http://ubuntuforums.org/showthread.php?t=1850578)

---

### Post by Taigen on 2012-02-26
Sorry to revive a possible dead forum. I'm using an old alien-ware laptop and trying to play regnum online. Well it doesn't like my gfx card driver. Is this going to be a problem with the driver or just something ill have to code to bypass on the game. Basically I was hoping for a driver for more "gaming" options.

---

### Post by Mark Phelps on 2012-02-26
AMD dropped support YEARS ago for this chipset -- so your reviving and old post is NOT going to change anything.

---

### Post by Taigen on 2012-02-26
k thanks... all I needed to know I guess.

---


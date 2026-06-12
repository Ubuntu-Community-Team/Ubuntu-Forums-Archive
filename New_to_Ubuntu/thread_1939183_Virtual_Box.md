---
title: "Virtual Box"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by harimurugan on 2012-03-11
i have installed ubuntu in windows 7 (dual booting).. now if i install virtual Box in (windows or ubuntu) how can i able to acess the other one(windows or ubuntu) which already installed rather than installing another new one..  is it possible to acess using virtual box..

---

### Post by squenson on 2012-03-11
No, you can't access your other installed OS from VirtualBox. It has to be installed inside VirtualBox first.

---

### Post by harimurugan on 2012-03-11
> **squenson said:**
> No, you can't access your other installed OS from VirtualBox. It has to be installed inside VirtualBox first.

plz see the link below.. 

[http://ubuntuhelpportal.blogspot.in/2011/08/creating-virtual-machine-for-physical.html](http://ubuntuhelpportal.blogspot.in/2011/08/creating-virtual-machine-for-physical.html)

---

### Post by westie457 on 2012-03-11
Hi it is possible. See here for guidance [https://forums.virtualbox.org/viewtopic.php?f=28&t=33356](https://forums.virtualbox.org/viewtopic.php?f=28&t=33356)

Personally have not used this, **so no guarantees**. As stated on the page **Try this at your own risk**.

Also it is advisable _not repeat not_ to boot into the native operating system that will now be accessed via virtualbox. Doing so in all likelyhood will break it big style and you will not be able to access it either way.

---

### Post by harimurugan on 2012-03-11
> **westie457 said:**
> Hi it is possible. See here for guidance [https://forums.virtualbox.org/viewtopic.php?f=28&t=33356](https://forums.virtualbox.org/viewtopic.php?f=28&t=33356)

Personally have not used this, **so no guarantees**. As stated on the page **Try this at your own risk**.

Also it is advisable _not repeat not_ to boot into the native operating system that will now be accessed via virtualbox. Doing so in all likelyhood will break it big style and you will not be able to access it either way.

i hav both ubuntu and windows os (dual booting), i hav installed virtual box in ubuntu.. now i want to access the windows which i already had.. i didnt understand any step from yr link.. can u plz elobrate wat to do..

---

### Post by haqking on 2012-03-11
it can be done but not recommended.

Best to either have a shared resource for data such as shared folders or a USB ext HDD for shared data.

or take a clone (clonezilla) of the installed OS and clone it into a VM for use.

Cheers

---

### Post by haqking on 2012-03-11
> **harimurugan said:**
> i hav both ubuntu and windows os (dual booting), i hav installed virtual box in ubuntu.. now i want to access the windows which i already had.. i didnt understand any step from yr link.. can u plz elobrate wat to do..

what do you need to access from it ?

if it is data then setup a shared resource for use by both

---

### Post by harimurugan on 2012-03-11
> **haqking said:**
> what do you need to access from it ?

if it is data then setup a shared resource for use by both

i would like to use some programs while using ubuntu (eg: NitroPdf).. i already have data on my shared folder only.. so no problem with the data..

---

### Post by haqking on 2012-03-11
> **harimurugan said:**
> i would like to use some programs while using ubuntu (eg: NitroPdf).. i already have data on my shared folder only.. so no problem with the data..

well you cant use installed programs in one OS in another OS especially when one is Windows and the other Linux unless they are standalone executables on similar systems and in a shared resource

Either find a alternative for Linux, or install and use it in Wine or as mentioned using Virtualisation by taking a clone of your existing OS and cloning into a VM.

Easier to find alternatives or Linux versions of your programs etc.

Cheers

---

### Post by harimurugan on 2012-03-14
after all i found out that its better to have dual booting rather using Virtual machine... i uninstalled virtual box.. thanks for yr replies..

---


---
title: "help me to work on ubuntu.."
date: 2012-07-03
forum: New to Ubuntu
---

### Post by royalprakash on 2012-07-03
hi 
i use Ubuntu 10.04 LTS . I've only vodafone modem(k3770)
it is possible to use that modem in Ubuntu???
if it is possible give me the steps...
otherwise
 help me to install wine (because modem software is in .exe format)
how to download wine and In which format?
And also how to install that package?
plz give me a web address and comment for installing wine.....

---

### Post by alphacrucis2 on 2012-07-03
I used to have one of those Huawei modems and Ubuntu recognised it when it was plugged in. Didn't need to install any drivers.

---

### Post by mastablasta on 2012-07-03
> **royalprakash said:**
> hi 
i use Ubuntu 10.04 LTS . I've only vodafone modem(k3770)
it is possible to use that modem in Ubuntu???
if it is possible give me the steps...
otherwise

Firts off the 10.04 LTS is an old Stable. You should use 12.04 instead. 10.04 has old kernel and drivers in linux are often part of kernel. So new edition, new kernel, new/more drivers.
 
Secondly plug it in and try additional hardware drivers applicaiton. see if oyu can install them via that.
 
thirdly plug it in and do the following command in terminal
 
lsusb (if it's a USB modem)
 
so we can see the chip it uses. Copy the result and post it here.
 
> 
help me to install wine (because modem software is in .exe format)
how to download wine and In which format?
And also how to install that package?

using drivers in wine won't help you at all. wine is a compatibility layer that can make some windows programmes run in  linux. It can not install drivers.
 
otherwise to install wine you open ubuntu software center, find wine and click install.
 
to install progammes within wine you type the following command in terminal
 
wine programme.exe
 
or you can also type wine and space and then click drag & drop the .exe file in terminal. or... there are plenty of other ways.
 
back to drivers. if there are now linux drivers for you modem you might be able to get it working with ndsiwrapper which "wraps itself arround" windows drivers. works only with some models. 
 
in short it is hard to help you if you don't post exact chip your modem has.

---

### Post by NikTh on 2012-07-03
> **mastablasta said:**
> Firts off the 10.04 LTS is an old Stable. You should use 12.04 instead. 10.04 has old kernel and drivers in linux are often part of kernel. So new edition, new kernel, new/more drivers.

+1

My opinion exactly. Many devices that needed ext.drivers or compiling or further configuration they play out of the box in 12.04

---


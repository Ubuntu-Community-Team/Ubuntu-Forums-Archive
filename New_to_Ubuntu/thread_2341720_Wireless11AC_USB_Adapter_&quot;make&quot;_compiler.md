---
title: "Wireless11AC USB Adapter &quot;make&quot; compiler error"
date: 2016-10-30
forum: New to Ubuntu
---

### Post by rodrigodelper on 2016-10-30
Hi all,

I'm having problems installing the driver for a wifi adapter (EDUP Wireless 11AC USB Model: EP-DB1607), I tar the file, run the make command and get an error for the modules, and when I try to run bash ./install.sh it says: Makefile:1551: recipe for target 'modules' failed. Pretty much all recipes for target module fail... what can I do?

Thanks!

---

### Post by leunam12 on 2016-10-31
From the readme file: "Please refer to document/Quick_Start_Guide_for_Driver_Compilation_and_Installation.pdf"

Did you read that guide and followed the necessary steps?

---

### Post by haroldw on 2016-12-07
Is this one resolved? I ran into the same problem.

---

### Post by Geoffrey_Arndt on 2016-12-07
Was the PDF leunam12 referred to still available at the EDUP website?

If you prefer not to work thru building the module driver, a very easy solution is here:    [http://www.pandawireless.com/](http://www.pandawireless.com/)

No compilation required . . . just "plug & play" . . .

---

### Post by jeremy31 on 2016-12-08
haroldw please post the result in terminal for ```
lsusb
```

I am thinking you may have a rtl8814au device

---


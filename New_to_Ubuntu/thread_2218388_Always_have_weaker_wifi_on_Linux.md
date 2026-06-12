---
title: "Always have weaker wifi on Linux"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by Ploni_Almoni on 2014-04-20
I want to install the latest LTS but I have always had problems with a much weaker wifi signal on *buntu and Debian linuces than what I experience when using Windows.  What can I do to insure that the signal will be just as strong as when using Windows?

---

### Post by Vladlenin5000 on 2014-04-20
Hi, welcome.

Your issue boils down to drivers and it's possible there are no better drivers yet for your device. BTW, what is is WiFi card?

---

### Post by wildmanne39 on 2014-04-20
Please post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by Ploni_Almoni on 2014-04-20
Realtek RTL8191SE  Is there no way to use a Window's driver if Linux does not yet have a better one?

---

### Post by Ploni_Almoni on 2014-04-20
sorry, I only have windows atm.

---

### Post by Ploni_Almoni on 2014-04-20
> **Wild Man said:**
> Please post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

Sorry, only have Windows at the moment.  Do you know the command for Windows cmd?

---

### Post by wildmanne39 on 2014-04-20
That driver is terrible in ubuntu but it can usually be fixed by compiling a new one. You could use ndiswrapper for a windows driver but it is usually worse then using linux drivers.

---

### Post by wildmanne39 on 2014-04-20
> **Ploni_Almoni said:**
> Sorry, only have Windows at the moment.  Do you know the command for Windows cmd?
No, I do not know a command for windows, I have not used it in years.

---

### Post by Ploni_Almoni on 2014-04-20
> **Wild Man said:**
> That driver is terrible in ubuntu but it can usually be fixed by compiling a new one. You could use ndiswrapper for a windows driver but it is usually worse then using linux drivers.  How exactly would I go about compiling a new one ?  I mean, where would I grab the source code and all of the dependencies?  Would I have to uninstall the original driver before the compile and if so how?

---

### Post by Ploni_Almoni on 2014-04-20
Anyone can explain to me what Wild Man meant by 'compiling a new one' ?

---

### Post by Gnawnsense on 2014-04-20
> **Ploni_Almoni said:**
> Anyone can explain to me what Wild Man meant by 'compiling a new one' ?


You would more than likely need to download and install the RTL819x driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true)


Untar it and then compile it with:
```
sudo su
make
make install
```

Then a reboot.

---


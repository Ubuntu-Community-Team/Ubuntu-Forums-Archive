---
title: "Desktop Environment on Ubuntu"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by chris1216 on 2012-04-01
All,

I am running Ubuntu 10.4 LTS on a netbook with a single core processor and one gigabyte of RAM.  It is very stable but, in my opinion a little sluggish.  As I understand it, I can download the DE Lubuntu uses, LXDE I believe, or something like openbox DE,and log into this and use it as the DE on the netbook without getting rid of Ubuntu 10.4 and reinstalling Lubuntu or Xbuntu.  Is this correct? 

If it is correct will I notice a difference, or will it just be in my head?  If I am totally wrong can someone make a suggestion as I am not opposed to wiping the netbook and starting over with something else.


Chris

---

### Post by idoitprone on 2012-04-01
> **chris1216 said:**
> All,

I am running Ubuntu 10.4 LTS on a netbook with a single core processor and one gigabyte of RAM.  It is very stable but, in my opinion a little sluggish.  As I understand it, I can download the DE Lubuntu uses, LXDE I believe, or something like openbox DE,and log into this and use it as the DE on the netbook without getting rid of Ubuntu 10.4 and reinstalling Lubuntu or Xbuntu.  Is this correct? 

If it is correct will I notice a difference, or will it just be in my head?  If I am totally wrong can someone make a suggestion as I am not opposed to wiping the netbook and starting over with something else.


Chris

yep
for lxde
```
sudo apt-get install lubuntu-desktop
```for xfce
```
sudo apt-get install xubuntu-desktop
```
and you can choose your environment on loggin

btw: seriously, single core? We havnt have single core for almost a decade

dawm it i missed my demon post arrrrrrrgggggggggggg 667

---

### Post by Peripheral Visionary on 2012-04-01
It's the desktop environment a little, but mostly it's *applications* that eat up memory and processor resources. Keep your favorite desktop if you like it (lightweights are Xfce and LXDE - Lubuntu and Xubuntu are designed with and for those environments), but choose lightweight applications - like Abiword and Gnumeric in place of LibreOffice; Midori or Chromium in place of Firefox, that sort of thing.

---

### Post by skatinjj on 2012-04-01
You can definitely install LXDE without wiping your current install by going to the terminal:

```
sudo apt-get install lubuntu-desktop
```

Then selecting the environment before logging in.

---

### Post by idoitprone on 2012-04-01
> **Peripheral Visionary said:**
> It's the desktop environment a little, but mostly it's *applications* that eat up memory and processor resources. Keep your favorite desktop if you like it (lightweights are Xfce and LXDE - Lubuntu and Xubuntu are designed with and for those environments), but choose lightweight applications - like Abiword and Gnumeric in place of LibreOffice; Midori or Chromium in place of Firefox, that sort of thing.

chromium is not a light app
In fact newer versions of firefox is lighter on the ram than chromium

---

### Post by chris1216 on 2012-04-01
Thank you all.  

Idiotprone, thank you for the code and yes it is a single core.  In my defense my employer purchased it on sale several years ago and gave it to me for some work projects.  Thanks to Linux though it is bearable, or as a thread I read here said, "Linux has breathed new life into this old machine."  Or something to that effect.

Chris

---

### Post by Kevin McCready on 2012-04-01
Linux breathes new life into low spec new machines which are sold off cheap because the punters are wedded to microsux and need higher spec to run. Good for me!!!

---

### Post by ajgreeny on 2012-04-01
You don't necessarily need to install the complete operating system alternatives, you can if you prefer just add the DEs with sudo apt-get install lxde or sudo apt-get install xfce4, and then still continue with the applications you want to use, eg libreoffice.

I actually installed Lubuntu 11.04 on my netbook and then added the apps I want, including Libreoffice, Firefox, GIMP, etc etc.  It runs brilliantly!  I shall proably update to Lubuntu 12.04 later this month or in May, once any bugs are sorted.

---


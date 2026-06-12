---
title: "i've installed ubuntu 8.04 LTS  on a generic pc but desktop does not appear"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by mistaboins on 2008-08-28
generic pc but desktop does not appear, what did i do wrong?

---

### Post by Oldsoldier2003 on 2008-08-29
Moved from tutorials and tips moderation queue and a giving a free bump for this support request.

---

### Post by nicedude on 2008-08-29
For starters can you tell me some more info about your situation so I or others that see this can help you.

Here are some questions that would be good to know.

1. Although you said you installed Ubuntu 8.04 LTS already but are sure you didn't install the server version which is not GUI based? If you did use the desktop install CD did you use the one that says live CD and if so did it boot to a desktop with the live CD before you installed it ?

2. Some info about your PC might help but since I am thinking you are talking about a desktop PC it should probably be fine but some info would still help, Like what CPU your PC has, How much RAM & what kind of video card or built in chipset it has ( Like Nvidia or ATI or some other onboard one )

3. When you say it wont boot to the desktop please tell us what exactly happens as in does it do anything when you start it? and assuming it does at what point does it stop loading? As in what is the last thing you see working before it stops and how does it stop ( freeze or constant black screen that does nothing etc ) 

Armed with these answers I can try to help you figure this out but without more info I can't really suggest anything so I will wait for your responses.

---

### Post by xeth_delta on 2008-08-29
> **mistaboins said:**
> generic pc but desktop does not appear, what did i do wrong?

I am not sure I understand what you mean, could you please be more explicit? Do you mean that the graphical interface is missing? What CD did you use to install. If you used the server version, the GUI is not installed implicitely, AFAIK.

If that is what you did, and if you are presented with a command prompt, you can install it rather easily, provided you have an internet connection. I will offer as an example three of the desktop environments.

To intall KDE
```
sudo apt-get install kubuntu-desktop
```
To install Gnome
```
sudo apt-get install ubuntu-desktop
```
To install XFCE
```
sudo apt-get install xubuntu-desktop
```

Let us know if you need further help

---


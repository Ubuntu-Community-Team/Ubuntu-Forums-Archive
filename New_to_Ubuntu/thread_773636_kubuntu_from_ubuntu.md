---
title: "kubuntu from ubuntu"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Errol on 2008-04-29
I asked this question on the kubuntu forum but I would like to hear opinions of Ubuntu users as well. I had problems connecting to the net using a static address when I installed Kubuntu. With ubuntu I don't have those problems . My question isn't about solving that problem. It is about installing KDE4 in Ubuntu. I really prefer KDE to Gnome (no offense to anyone) so I want to know will installing KDE "convert" Ubuntu to Kubuntu ar will there still be differences between the "conversion" to the original Kubuntu installed from scratch.
I hope this question isn't OT.
TIA
Errol

---

### Post by tzulberti on 2008-04-29
It is very easy to install Kubuntu from ubuntu by installing kubuntu-desktop.- To install Ubuntu from Kubuntu, you should only install Ubuntu-desktop. 

The main difference of doing this, is that in the menu, you would have the Gnome and Kde programs.

---

### Post by salazar35 on 2008-04-29
To install kubuntu-desktop you can use this code (as root):
```
apt-get install kubuntu-desktop
```

---

### Post by RyanVanDiemen on 2008-04-29
I`d say if you install KDE in Ubuntu, you will basically get kubuntu desktop (only the boot screen will be ubuntu :) ) As kubuntu is basically not so different to ubuntu as people usually think. It`s the same system with two (even more obviously) different dektop enivronments. So the answer to your question is that if you have this problem with kubuntu, you will most probably have the same problem under KDE in ubuntu as the problem is with the libraries KDE use (doesn`t matter if it`s in ubuntu or kubuntu, the libraries are still the same). Hope, it answers your question.

---

### Post by Errol on 2008-04-29
Thanks to those who replied. I am hoping that by installing Ubuntu I will then setup my static IP and THEN install KDE4 to be able to work as Kubuntu. Hopefully the stup will remain and I wil have ha\d a workaround to my problem.
I'll inform this thread of results.
Errol

---

### Post by PetePete on 2008-04-29
you probably just need to download and install the gnome network config app, using that inside kde might make your network work.

failing that, you can always manually edit /etc/network/interfaces for a static IP
for example change /etc/network/interfaces to something like the following:
```

iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254

```

then restart the computer or just restart networking by
sudo /etc/init.d/networking restart

---

### Post by Errol on 2008-04-29
Petepete Thanks for your ideas. 
I cannot load anything into my Kubuntu as I have NO internet connection. I did try and edit /etc/network/interfaces as you described. The result was that the static IP that came up had very little connection to the number I had typed there. 
To say the least I was very disappointed in the KDE knetworkmanager and it's inaccessibility. I really tried every workaround I (with my limited knowledge) was able to conjour up. So meanwhile I seem to have no option but to try the "Ubuntu first then KDE option". In ubuntu I am able to set up the static address. The whole thing seems to be a problem with knetworkmanager. When I eventually get to Kubuntu I will post a bug.
Errol

---

### Post by Errol on 2008-04-30
I wrote this question on several forums and as I have now "solved" the problem i.e. successfully loaded Kubuntu with internet connection onto my computer. As the problem (from my point of view) is no longer I want to detail the problem and the solution I used for the benefit of others AND to thank the many people on these various forums that gave advice which helped me and set me on the right track. So first of all thank you all!
The problem I came across:
I installed Kubuntu and was unable to set up my static IP address in order to connect to the internet. I tried every possible way that I knew or was advised to try on various forums.
The main problem was with knetworkmanager. I could not get it to allow me to get into manual setup. What happened was that when going to knetworkmanager and trying to operate manual setup I was asked for my password which I typed in. The request closed and then NOTHING happened. No reaction at all from the manager. So I was unable to setup my static IP that way.
I then tried to write my static IP in /etc/network/interfaces. My static IP starts with 10.* etc. but the static IP number I got when restarting my computer was 198.* etc. No connection to what I had tried. All this was on a wired connection. 
In desperation I installed Ubuntu and had NO problems with setting up my static IP. I prefer the Kubuntu interface and programs so I tried this:
I then installed KDE4 using 
sudo apt-get install KDE4
After seeing that KDE4 worked properly I went to the next step an completely installed Kubuntu from within Ubuntu
apt-get install kubuntu-desktop
I am very satisfied with the results although I haven't tried out everything yet. I particular I haven't tried knetworkmanager but when I get home from work I will do just that.
I intend to send this letter as a bug notice to Kubuntu if I can find out how(where) to do this.
I hope this can help others as I was helped here.
Errol

---


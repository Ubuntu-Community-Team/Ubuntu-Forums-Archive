---
title: "I need TeXmacs"
date: 2022-08-19
forum: New to Ubuntu
---

### Post by atomekid on 2022-08-19
New to Ubuntu (KUbuntu), I need TeXmacs but Discover seems unable to install this soft.
How may I do ?
Thanks a lot for help (I apologize for my bad english).
AtomeKid.

---

### Post by Holger_Gehrke on 2022-08-19
TeXmacs has it's own repositories which you need to integrate with the Ubuntu package system. You'll find instructions on texmacs.org. If you're using 22.04 then you're slightly out of luck, there's no package for that yet. But there is a generic binary package (a gzip compressed tar) which might work.

Holger

---

### Post by grahammechanical on 2022-08-19
You need to get the appropriate TeXmacs package from the developers.

[https://www.texmacs.org/tmweb/download/linux-packages.en.html#ubuntu](https://www.texmacs.org/tmweb/download/linux-packages.en.html#ubuntu)

Click on "TeXmacs package for xUbuntu_20.04 with a 64bits Intel/AMD processor" and the package will download. Then you run the commands recommended.

Ubuntu 20.10; 21.04 and 21.10 are now out of date. They should not be used. At present there is not a version for Ubuntu 22.04. So, you will have to use the 20.04 version of TeXmacs.

You do not tell us what version of Kubuntu you are using. Information like that is useful for avoiding inaccurate suggestions.

Regards

---

### Post by atomekid on 2022-08-19
My version is 22.04 (KUbuntu).
Thank you !

---

### Post by atomekid on 2022-08-23
I downloaded TeXmacs-2.1.1.amd64.deb, and stored it in my directory "Downloads".
Then in Konsole, I go to Downloads and type : 
 ```
sudo apt-get install TeXmacs-2.1.1.amd64.deb
```
Konsole answers :
```
[FONT=monospace][COLOR=#000000]Lecture des listes de paquets... Fait [/COLOR]
Construction de l'arbre des dépendances        
Lecture des informations d'état... Fait 
E: Impossible de trouver le paquet TeXmacs-2.1.1.amd64.deb 
E: Impossible de trouver de paquet correspondant à l'expression rationnelle « TeXmacs-2.1.1.amd64.deb » 
E: Impossible de trouver de paquet correspondant à l'expression rationnelle « TeXmacs-2.1.1.amd64.deb »[/FONT]
```[FONT=monospace]
(Translation :
[/FONT]```
Unable to find a packet matching the rational expression "TeXmacs-2.1.1.amd64.deb"
```)
What can I do ?
Thanks a lot !
AK


[FONT=monospace]



[/FONT]

---

### Post by Frogs Hair on 2022-08-23
After navigating to the downloads directory try the following. 
```
sudo dpkg -i texmacs*.deb
```

---

### Post by ActionParsnip on 2022-08-23
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

### Post by Impavidus on 2022-08-23
apt-get doesn't handle .debs that it doesn't know from a repository. You can use dpkg, as explained by Frogs Hair, but only if you don't need more dependencies. You can also (assuming your Ubuntu is recent enough) use the higher-level apt:```
sudo apt install ./TeXmacs-2.1.1.amd64.deb
```

---


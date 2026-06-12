---
title: "yahoo messenger via wine and gyachi"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by k66473 on 2008-04-27
I would like to have webcam support so I tried install yahoo messenger on wine. Everything seem to be OK when installing but I can not log in by yahoo messenger on wine cause YIM can not see the internet connection, it try to find proxy or something else. Do you have any idea to solve this?

After that, I tried download and install Gyachi which has a rumor can support webcam very well. But, when I install deb package, it said that dependency is not satisfiable : xmms. I immediately go to Synaptic and add all package with name xmms and Gyachi package still stuck and can not be install with the error above. Plz help me

---

### Post by Perfect Storm on 2008-04-27
> dependency is not satisfiable : xmms

xmms is no more. That's why (it's obsolite and not maintained anymore). The things you have install must been part of xmms2 which are CLI music player.

---

### Post by barbedsaber on 2008-04-27
if its webcam support your after, then, try running
```
sudo apt-get install kopete
```

it is another IM client, which I find to be a bit slower and buggier than pidgen, never the less, it has webcam support

EDIT: if the webcam doesn't work at first, and you get error messages asking for somthing called jasper, then try

```
sudo apt-get install libjasper1
```

it worked for me

---


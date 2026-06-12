---
title: "installing deb from desktop"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by trucker33377 on 2008-05-31
Its taken me month to get to this point so I dont want to mess up now.

ive got a deb package downloaded to the desktop and i would like to install it. this is kubuntu 8.04 amd. I got the deb from  this link. [http://ubuntu.cafuego.net/dists/hardy-cafuego/secondlife/](http://ubuntu.cafuego.net/dists/hardy-cafuego/secondlife/). 

it works on my desktop by right clicking it with ubuntu 8.04 it installs and shows up in my internet tab

---

### Post by mgranet on 2008-05-31
> **trucker33377 said:**
> Its taken me month to get to this point so I dont want to mess up now.

ive got a deb package downloaded to the desktop and i would like to install it. this is kubuntu 8.04 amd. I got the deb from  this link. [http://ubuntu.cafuego.net/dists/hardy-cafuego/secondlife/](http://ubuntu.cafuego.net/dists/hardy-cafuego/secondlife/). 

it works on my desktop by right clicking it with ubuntu 8.04

Just click on it. GDebi will automatically install, and find and install your dependencies.

EDIT: Well, most of the time. If some red text appears telling you dependencies cannot be met, things can get interesting.

---

### Post by trucker33377 on 2008-05-31
yup maybe most of the time but not this time. ark opens it says no archive loaded

Humm maybe i need to install gdeb first

---

### Post by Maestro23 on 2008-05-31
You need to install gdebi first.

> sudo apt-get install gdebi

---

### Post by ChompTheMan on 2008-05-31
Open up a terminal and type in:

```
sudo dpkg -i Desktop/file_name.deb
```

If it tells you that there are unmet dependancies then it will give you a list of the missing dependancies.  These will have to be installed before you can finish installing your .deb file.  Type in:

```
sudo apt-get install dependancy1 dependancy2 dependancy3
```

to easily copy paste in the command line highlight what you want to copy then middle click your mouse to paste.  Once you have the dependancies installed repeat the above dpkg command.

---

### Post by trucker33377 on 2008-06-01
humm cant do anything now synaptic broke command line wont even work. this looks pretty unstable to me this is the 2nd time ive put kubuntu 8.04 on this. the wireless wont  always connect at start up. So im at a loss here as where to go with  it.

this is a gateway mt3421 amd 2 gis of ram

---

### Post by sayakb on 2008-06-01
```
sudo apt-get install -f
```
To fix broken dependencies.

---

### Post by trucker33377 on 2008-06-01
when i  try to  fix synaptic it  says i need to install SL but when i try to  install it im told there is no package.

ive got gdeb installed but if i try to install with that it says that SL package is 64bit

thought thats what i needed for AMD and kubuntu 64

---

### Post by Xiong Chiamiov on 2008-06-01
You only need 64-bit packages if you're running the 64-bit version of Kubuntu.

---

### Post by trucker33377 on 2008-06-01
> **Xiong Chiamiov said:**
> You only need 64-bit packages if you're running the 64-bit version of Kubuntu.

this is 64 bit kubuntu and amd 64 bit laptop

---


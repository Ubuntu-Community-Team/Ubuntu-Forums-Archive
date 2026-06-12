---
title: "Trying to install WINE on Unbuntu 12.10"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-08
Now that I have my ethernet working, I wanted to install WINE so I could load up a windoze program for my Verizon wireless. It won't go for me and I get this error:

```
 The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

```

Not sure what I need to do in order to satisfy these dependencies.

---

### Post by ppjdee on 2013-04-08
you ran this in the terminal?

```
*sudo add-apt-repository ppa:ubuntu-wine/ppa*
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.4
```

---

### Post by alhefner on 2013-04-08
Tried another method- [http://askubuntu.com/questions/224592/how-to-install-wine-on-ubuntu-12-10]("http://askubuntu.com/questions/224592/how-to-install-wine-on-ubuntu-12-10") -and still no go.

```
The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.27-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: fonts-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by alhefner on 2013-04-08
> **ppjdee said:**
> you ran this in the terminal?

```
*sudo add-apt-repository ppa:ubuntu-wine/ppa*
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.4
```

Other than it being 1.5 instead of 1.4, yep.

---

### Post by ppjdee on 2013-04-08
[http://askubuntu.com/questions/204840/dependency-error-while-installing-wine](http://askubuntu.com/questions/204840/dependency-error-while-installing-wine)

dont know if it will work but could try. maybe someone more knowledgeable about this will see this thread.
goodluck

---

### Post by avsprasad on 2013-04-08
Easy method is to install Playonlinux...and then you can install wine and other stuff quite easily.

---

### Post by alhefner on 2013-04-08
OK, got it done. Here's what I had to do:

```
sudo dpkg --add-architecture i386
```
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.5
```

Thanks ppjdee!

---

### Post by ppjdee on 2013-04-08
No problem, glad I could help.

---

### Post by Mark Phelps on 2013-04-08
Don't know what Verizon app you're talking about, but I've found them NOT to work with Wine.

---

### Post by alhefner on 2013-04-09
> **Mark Phelps said:**
> Don't know what Verizon app you're talking about, but I've found them NOT to work with Wine.

I found the same thing out. Now to see what I need to do to get the mobile broadband working on Ubuntu.... back to the drawing board!

---

### Post by ppjdee on 2013-04-09
It may be best to check [WineHQ/AppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true") for software you are interested in running through wine. Could save you from a headache too :P

---


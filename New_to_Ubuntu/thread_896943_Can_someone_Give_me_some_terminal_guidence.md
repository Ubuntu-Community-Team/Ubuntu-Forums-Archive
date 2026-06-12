---
title: "Can someone Give me some terminal guidence?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by mattcadu on 2008-08-21
Ok, I just downloaded Frostwire to my desktop, the files name is

frostwire-4.17.0.i586.deb

Can somebody walk me thru exactly what i need to type in the terminal to install this?  Im so lost.

Ty

---

### Post by mc4100 on 2008-08-21
```
sudo dpkg -i ~/Desktop/frostwire-4.17.0.i586.deb
```

---

### Post by tijmz on 2008-08-21
A .deb package is perhaps more easily installed using the graphical interface. Just right-click on the file and select "Install with GDebi Package Installer", whichi is likely to be the default action. Follow instructions and you're done :)

But if necessary, the terminal command post above should suffice :)

---

### Post by Elfy on 2008-08-21
You can do this 2 ways - double click the file on the desktop and Gdebi should install it for you or

```
cd Desktop
sudo dpkg -i frostwire-4.17.0.i586.deb
```

you could also do it without changing to the desktop

```
sudo dpkg -i ~/Desktop/frostwire-4.17.0.i586.deb
```

If you only had 1 deb on the desktop you could replace the filename with *.deb, also you don't have to type the whole thing - tab will autocomplete for you

---


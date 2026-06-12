---
title: "how do I install (find) brl-cad? Or any other program"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by mitar on 2008-05-12
I downloaded brl-cad as a .deb file and I install it but can't get to run. I press alt-F2 and type the name of the programs but I get the message saying that it can not be found. So I guess I have to do it using terminal. Can someone help with this?

---

### Post by JoshuaRL on 2008-05-12
> **mitar said:**
> I downloaded brl-cad as a .deb file and I install it but can't get to run. I press alt-F2 and type the name of the programs but I get the message saying that it can not be found. So I guess I have to do it using terminal. Can someone help with this?

Is it in your menus?  If not, try searching APT for it:
```

apt-get search brl-cad

```
When you find the package name, try running it from the terminal.  If it works, you can add it to the menus with Alacarte:
```

alacarte

```
Then make a new entry in the menu where you want it and with the icon you want, and use the name of the package as the command to run with that icon.  That should do it for you.

---

### Post by mitar on 2008-05-12
> **JoshuaRL said:**
> Is it in your menus?  If not, try searching APT for it:
```

apt-get search brl-cad

```
When you find the package name, try running it from the terminal.  If it works, you can add it to the menus with Alacarte:
```

alacarte

```
Then make a new entry in the menu where you want it and with the icon you want, and use the name of the package as the command to run with that icon.  That should do it for you.

it says invalid operation search. Any other possibilities?

---

### Post by JoshuaRL on 2008-05-12
> **mitar said:**
> it says invalid operation search. Any other possibilities?

Try searching for "cad".

---

### Post by zvacet on 2008-05-13
```
apt-cache search package_name
```

or 

```
locate package_name
```

---

### Post by Xiong Chiamiov on 2008-05-13
Did you install the .deb file, or just download it?  You have to double-click it, which will open it in GDebi and install it.  If it's been installed, then you can see a list of the installed files either with zvacet's 2nd command, or somehow in Synaptic (I use adept).

---


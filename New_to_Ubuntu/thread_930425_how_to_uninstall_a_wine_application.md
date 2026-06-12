---
title: "how to uninstall a wine application"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-26
I downloaded and installed utorrent via wine.

How do i remove it?

---

### Post by HittingSmoke on 2008-09-26
> **faraz_k86 said:**
> I downloaded and installed utorrent via wine.

How do i remove it?

Applications > Wine > Uninstall Wine Programs

Some things dont show up in that list for me so you might just have to go to browse C: and delete the program's folder

---

### Post by WWSmith36 on 2008-09-26
Remove the program with

```
sudo apt-get --remove wine
```

Remove configuration files with

```
sudo rm -rf .wine
```

---

### Post by Liviu-Theodor on 2008-09-26
> **WWSmith36 said:**
> Remove the program with

```
sudo apt-get --remove wine
```

Remove configuration files with

```
sudo rm -rf .wine
```

This command does not uninstall wine? It seems **faraz_k86** wants only the *utorrent* uninstalled.

---

### Post by WWSmith36 on 2008-09-26
Sorry, try

sudo apt-get --purge wine

---

### Post by Primefalcon on 2008-09-26
don't try either of those, that'll remove wine

just go to

accessories => uninstall wine software

It'll bring up a windows like add/remove panel

edit: I looked back and yes hittingsmoke was right, my advice though to WWSmith is if you don't know what your saying don't post, those kind of answers just make things worse

---


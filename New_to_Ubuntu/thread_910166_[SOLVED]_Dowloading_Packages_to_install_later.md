---
title: "[SOLVED] Dowloading Packages to install later"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Matuku on 2008-09-04
Is there anyway to download packages and then save them to a memory stick to allow transfer to a computer that doesn't have an internet connection?

---

### Post by forger on 2008-09-04
yes:
```
sudo aptitude download nameofpackage
```

or if it's for a different architecture, search for it at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Matuku on 2008-09-04
Where do they download to using this method? Also will it download the required dependencies?

---

### Post by nothingspecial on 2008-09-04
Wherever you are in the terminal, for example if I wanted this silly game my wife like called monsterz on my desktop -

```
cd ~/Desktop
```

Then -

```
sudo aptitude download monsterz
```

---

### Post by Matuku on 2008-09-04
Will I have to download each of the dependencies individually?

---

### Post by nothingspecial on 2008-09-04
I`m not sure but I would because the machine that you are downloading the package on may have dependencies that the machine you are installing the package on does not, if you see what I mean.

---

### Post by hyper_ch on 2008-09-04
```

sudo apt-get download packagename

```

will download it t where also synaptic and add/remove and aptitute download the .debs to.

If you want to have it then install, just run

```

sudo apt-get install packagename

```

---

### Post by ds[de] on 2008-09-04
The downloaded .deb files should be in 
```
/var/cache/apt/archives
```


Regards,
ds[de]

---


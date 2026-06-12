---
title: "what is a minimal ubuntu os?"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by anonu on 2013-01-23
Hello,
 
I am looking for a bare bone ubuntu OS version. I want nothing else other than my OS, and then i would like to get only the programs i want. the desktop i would like is cinnamon.
 
could you help how i can do this.
 
i downloaded ubuntu mini, but when i do sudo apt-add-repository ppa something something, it says command not found.
 
all help appreciated. also i had another q. is there a prg where in a terminal like window i can see what the scripts are being executed in real time and then can save the entire log to a text file.
 
thank you, thank you and cheers.

---

### Post by howefield on 2013-01-23
> **anonu said:**
> i downloaded ubuntu mini, but when i do sudo apt-add-repository ppa something something, it says command not found.

try...

```
sudo add-apt-repository ppa something something
```of course substituting "ppa something something" with the real ppa you want to add.

---

### Post by omeomi on 2013-01-23
> **anonu said:**
> also i had another q. is there a prg where in a terminal like window i can see what the scripts are being executed in real time and then can save the entire log to a text file.

You mean like top?

```
top -b -n1 > output.txt
```

---

### Post by furything on 2013-01-23
Try just installing ubuntu with xfce desktop (it's quite minimal) or lbuntu (never tried that one though)

Should also add you can install more than one desktop so if you installed xfce you could install the other desktop you want then uninstall xfce. You may find using the gui interface and synaptic package manager much easier than installing things via apt-get.

---

### Post by ibjsb4 on 2013-01-23
You really need a understanding of packages.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=minimal+install&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=minimal+install&as_qdr=all&sa=Google+Search&lang=en)

---


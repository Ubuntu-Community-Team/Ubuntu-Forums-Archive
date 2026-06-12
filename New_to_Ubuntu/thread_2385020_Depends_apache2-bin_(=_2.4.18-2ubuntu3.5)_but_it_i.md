---
title: "Depends: apache2-bin (= 2.4.18-2ubuntu3.5) but it is not installable"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by moridz on 2018-02-15
Hello

I am new to Ubuntu and I just installed a server with OSUbuntu 16.04 x64 in vultr
I am getting this error when I tried installing apache server

```
The following packages have unmet dependencies:
apache2 : Depends: apache2-bin (= 2.4.18-2ubuntu3.5) but it is not installable
```

I have tried all the guides available online but the problem still persist. I am hoping there are experts here who'll be able to assist

---

### Post by QIII on 2018-02-15
Hello!

Please use the default font, size and weight unless you need to emphasize a particular point for clarity or bring attention to an important item.

Also please include all terminal commands and output in code tags in one of the following ways:

1. Highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. Type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by mörgæs on 2018-02-16
Please post the output from ```
sudo apt update
``` and ```
sudo apt dist-upgrade
```

---


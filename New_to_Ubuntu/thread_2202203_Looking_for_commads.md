---
title: "Looking for commads"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by nAHE8Yx on 2014-01-27
i'm looking for easy way to install downloaded programs in a terminal.

somebody  help...

thanks a lot community

---

### Post by QIII on 2014-01-27
Hello!

It depends on what you downloaded.  Could you give us an example -- including the file type?

---

### Post by nAHE8Yx on 2014-01-28
teamviewer

---

### Post by QIII on 2014-01-28
OK.

What did you download, from where, what file type is it, etc?

---

### Post by chili555 on 2014-01-28
Let's assume your download is in the folder Downloads. Then open a terminal Ctrl+Alt+t and change to that directory:```
cd ~/Downloads
```Now use dpkg to install the package. Adding or removing software requires root permission, so we use sudo:```
sudo dpkg -i teamviewer*.deb
```We needn't type the whole name, we use the wildcard *.

In recent Ubuntu versions, you needn't use the command line to do this, you can simply right-click the .deb file and select 'Open with Software Center.'

---

### Post by nAHE8Yx on 2014-01-28
thanks a lot guys

---


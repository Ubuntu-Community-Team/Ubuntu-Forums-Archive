---
title: "Ubuntu Mobile SDK install failing!"
date: 2013-01-02
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2013-01-02
Hi All

Following the announcement of ubuntu going mobile I thought I might install the SDK as per the instructions on the website:

[http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/)

After the first install of Qt 5 going fine the install of QML toolkit preview fails with the following error:

```
W: Failed to fetch http://ppa.launchpad.net/ui-toolkit/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ui-toolkit/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

This is obviously because the PPA is on the blink but is anyone else getting this or is there a known fix?

Thanks in advance

Mike

---

### Post by majhamza on 2013-01-02
Hi , i found the same problem too, but i found an article on the web that helped me.

i don't know the source of the problem or how you can fix it but it seems that you can download the files manualy from the launchpad ppa directory, here: [https://launchpad.net/~ui-toolkit/+archive/ppa/+packages]("https://launchpad.net/~ui-toolkit/+archive/ppa/+packages").

if you don't know how to install the files, put them in a directory, go to that directory in your terminal and do:

chmod 777 *.deb
dpkg -i *.deb

i hope that helped you a little bit

---

### Post by Mickeysofine1972 on 2013-01-03
Awesome! thanks that worked!

Mike

---

### Post by Yolan on 2013-01-03
The issue is they only have packages for Quantal and not Precise.

Replace precise with your version of ubuntu. This will work without installing with dpkg so you will receive updates:

sudo add-apt-repository ppa:ui-toolkit/ppa
sudo sed -i 's/precise/quantal/g' /etc/apt/sources.list.d/ui-toolkit-ppa-precise.list
sudo apt-get update && sudo apt-get install qt-components-ubuntu qt-components-ubuntu-demos qt-components-ubuntu-examples qt-components-ubuntu-doc notepad-qml

---

### Post by Mickeysofine1972 on 2013-01-03
Nice one!

Mike

---

### Post by jimmyco2008 on 2013-01-04
Thanks! I'm surprised they didn't mention this in the instructions.

---


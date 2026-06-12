---
title: "install Opera from terminal?"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-20
how do u install Opera from terminal?
I installed Lubuntu 11.10 recently, 
Chrome is defaut, but it does not launch.

---

### Post by Frogs Hair on 2011-12-20
I think you would have to add the entire line below to the software sources list first. 

Opera Browser (final releases) ([http://deb.opera.com/opera/stable](http://deb.opera.com/opera/stable)) 

```
sudo apt-get update
``````
sudo apt-get install opera
```Opera has an Ubuntu .deb package that can be downloaded from the site and installed also . I think downloading the .deb is the easier option because the source is added during installation . If you download the package and double click it I think the software center will be offered as a  package installer .

---

### Post by Matrix01 on 2011-12-21
terminal got error message; package 'opera' has no installation candidate.


> **Frogs Hair said:**
> I think you would have to add the entire line below to the software sources list first. 

Opera Browser (final releases) ([http://deb.opera.com/opera/stable](http://deb.opera.com/opera/stable)) 

```
sudo apt-get update
``````
sudo apt-get install opera
```Opera has an Ubuntu .deb package that can be downloaded from the site and installed also . I think downloading the .deb is the easier option because the source is added during installation . If you download the package and double click it I think the software center will be offered as a  package installer .

---

### Post by aeiah on 2011-12-21
you can install .deb files from the command line as easily as from the gui

```

sudo dpkg -i packagename.deb

```

---

### Post by Lars Noodén on 2011-12-21
If you want to install it via the repository, which is a good idea, then you have to add it to [font=Courier New]/etc/apt/sources.list[/font] and add the corresponding key.  See this page for details:
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by daemoncycler on 2012-12-13
Thanks - a year later.

---


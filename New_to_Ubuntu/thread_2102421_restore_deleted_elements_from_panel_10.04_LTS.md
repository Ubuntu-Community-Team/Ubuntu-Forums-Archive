---
title: "restore deleted elements from panel 10.04 LTS"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by xptional on 2013-01-07
Hi , 
I want to restore the deleted elements from ubuntu 10.04 LTS panel. 
Sorry that I have deleted as playing with panel properties etc. 
**Deleted elements are "Wifi" and "Volume control". **
I have searched on forum but could not find any pointed help nor by googling :(. 

I checked by right clicking on the panel, selecting 'add to panel' option but could not find anything related to my described problem. 

Thanks in advance for your help and cooperation. 

PS: I have only one panel that is on upper side of the screen.

---

### Post by ibjsb4 on 2013-01-07
I think thats your "Indicator Applet" you need to restore.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+reset+panel+10.04&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=restore+reset+panel+10.04&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by xptional on 2013-01-07
OK
I got it. It means I have to restore the panel to default settings. Firstly I was searching the selected items to restore but it works in other way. 

I did that. 
```

$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
$ reboot

``` 

It works. 

Thanks a lot.

---

### Post by ibjsb4 on 2013-01-07
Welcome  :)

---


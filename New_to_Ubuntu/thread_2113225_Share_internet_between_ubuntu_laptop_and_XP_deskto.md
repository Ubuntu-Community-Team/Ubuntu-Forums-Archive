---
title: "Share internet between ubuntu laptop and XP desktop via ethernet cord"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by JSF16 on 2013-02-06
I have a laptop running Ubuntu 12.10. I also have a desktop running windows XP. I want to connect my wireless laptop to my desktop via ethernet cord so my desktop can use the internet. However when I plug my laptop and desktop together, my desktop says that internet connection is limited and I cannot connect. Any advice on how to overcome this?

---

### Post by ibjsb4 on 2013-02-06
If you had ubuntu on your desktop you could install firestarter and in a few clicks be up and running.  Don't know how its done in windows.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ics+internet+connection+sharing&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ics+internet+connection+sharing&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Thee on 2013-02-06
If I understood correctly, you have:
{wireless internet} --> {ubuntu laptop} --> {XP desktop}
Right?

If so, try what the previous poster suggested (with firestarter). And make sure that in XP all the network settings are set to automatic.

---

### Post by 3rdalbum on 2013-02-06
In Network Manager on Ubuntu, add a new Ethernet connection and set the type to "Shared to other computers". Save your changes and then select the new connection from the Network Manager menu on your top panel. It should work now.

---


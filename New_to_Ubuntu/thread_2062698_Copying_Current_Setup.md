---
title: "Copying Current Setup"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by Galgotha on 2012-09-25
I am sure this may actually be simple, but I can't seem to find tool yet. I have setup Xubuntu with applications and UI adjustments that I want to be able to clone and install the same setup on another PC.
 
Is there a way to create an ISO of your current settings and applications being loaded verses standard ISO I download?
 
Like I removed Abiword and put on LibreOffice. Switched Chromium for Firefox, installed few other apps I want included installed on the next PC right from the install.
 
I also switch UI settings adjusted bars information settings etc...and want that to be installed on next PC in that same way.
 
Thoughts?
 
Thanks

---

### Post by jerrrys on 2012-09-25
You can clone your Hdd if you want with [Clonezilla]("http://clonezilla.org/")

Or you can make a [backup of installed packages]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=copy+backup+installed+packages&as_qdr=all&sa=Google+Search&lang=en")

For keeping your [custom settings]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+configuration+files&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by Cheesemill on 2012-09-25
You can use [Remastersys]("http://www.geekconnection.org/remastersys/index.html") to create an installable iso of your current setup.

---

### Post by Galgotha on 2012-09-25
> **Cheesemill said:**
> You can use [Remastersys]("http://www.geekconnection.org/remastersys/index.html") to create an installable iso of your current setup.
 
Thank You Cheesemill this is exactly what I was looking for.

---

### Post by cmcanulty on 2012-09-25
i believe if you clone the whole hard drive and then put it on another machine you have to change various hosts files or it will be messed up. I don't know exactly.

---

### Post by Galgotha on 2012-09-26
I do a lot of IT support for church friends many of these machines are very old and Win7 would not be supported. I am looking to get a few custom setup ISO that I can show them and then install. A "Win" or "X OS" clones shall we say with LibreOffice and few other audio, video/photo editing apps packages preinstalled.
 
I know program heavy users don't like the simplification of Ubuntu but I think 12.04.1 will see great use from low end users, were mail/net/simple document support is all they need. And due to free cost and ability to run very well on older machines means a lot of my elderly church members can get a nice machine to stay in contact with thier kids/grandkids for little no money as I find retired workstations from business to convert.

---

### Post by rai4shu2 on 2012-09-26
I would suggest testing your result iso in something like VirtualBox first, then try it out on some actual hardware if that works.

---

### Post by Galgotha on 2012-09-26
I have a test laptop just for testing :) old HP dv8000

---

### Post by cmcanulty on 2012-09-26
just be aware if they have dialup it is very hard to get working. I used to recommend Ubuntu for older machines but found out if they use dialup you might get it to connect and might not. I can't even after a lot of studying.

---

### Post by rai4shu2 on 2012-09-26
I don't think using Ubuntu is a good idea if you're on dialup. I think if I were on a slow connection, I would stick with Debian stable.

---


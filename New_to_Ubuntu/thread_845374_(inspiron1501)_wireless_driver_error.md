---
title: "(inspiron1501) wireless driver error"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Corey4666 on 2008-06-30
i installed ubuntu 8.04 on my new laptop and when i did a message came up asking me to install the driver for my wireless internet, when i installed it + firmware or something it mentioned it gave a error and i took a picture. (i could not copy and paste the error)

(i attached the file at the last second, i was having problems with image shack)

---

### Post by dwhitney67 on 2008-06-30
Perhaps you should update your system first, then install the proprietary driver.
[PHP]$ sudo apt-get update[/PHP]
The problem you had seems to be related to ssl-cert.

---

### Post by Corey4666 on 2008-06-30
Thats the first thing i did when i installed Ubuntu before anything else, i will try one more time and wait for you to reply.

UPDATE: i tryed doing the sudo apt-update but after it updated nothing changed the wireless still dont work

---

### Post by Corey4666 on 2008-06-30
bump? should i install a wireless software? instead of using the normal one built into the computer icons on the top right toolbar? i am trying to figure out how to make this work, having no luck. :(

---

### Post by mity on 2008-06-30
I found this to be an excellent blog and a great tool for fellow 
1501 owners. 

[http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html](http://www.ubuntu1501.com/2008/04/overview-of-ubuntu-804-hardy-heron-on.html)

---

### Post by Corey4666 on 2008-06-30
thanks man awesome website i am trying the guide as i type i will tell ya how it works out! :popcorn: by the way are you a 1501 user also? if so we could exchange im so we can chat I'm very noobish with linux. :)








UPDATE:

Thanks so much! it works 100% now perfectly i just wanna let you know i really appreciate your help. :D

---

### Post by saskchi on 2008-11-02
Here is what I did to fix the wireless issue in 1501

First install any updates using the update manager or command line

1. Connect your laptop to the Internet using your Ethernet port
2. Click System-> Administration-> Hardware Drivers
3. Let it search for the Broadcom drivers
4. Activated drivers
5. Once installed, click the network icon and choose connect to hidden network
6. The rest is self explanatory

Hope this helps

---


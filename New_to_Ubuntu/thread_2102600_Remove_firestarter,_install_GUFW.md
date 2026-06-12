---
title: "Remove firestarter, install GUFW"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by toxictex on 2013-01-07
I am new to ubuntu, I have 12.04 installed. I want to know if what I am  about to do is the right way to purge firestarter and install GUFW by  typing this in the terminal: -  
```
sudo apt-get purge firestarter
sudo apt-get install gufw
```and do I need to flush the ip tables before I enable gufw by typing this: -
```
sudo iptables -F
```I know this has cropped up many times, I  have read many conflicting posts on this subject which have left me  totally confused. Please help.

---

### Post by Frogs Hair on 2013-01-07
Enter the first two commands separately and it would be a good idea to flush any rules set up with firestarter prior to removing it and installing GUFW . For further info: ```
man iptables 

```

---

### Post by toxictex on 2013-01-07
Thank you so much, I will do what you suggested. I have looked at dozens of posts on this subject and I ended up totally confused. I hope setting up Gufw is
simple.

---


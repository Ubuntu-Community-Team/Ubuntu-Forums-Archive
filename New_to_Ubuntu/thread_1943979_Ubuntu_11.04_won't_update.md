---
title: "Ubuntu 11.04 won't update"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by vincep123 on 2012-03-20
Hello all, I appreciate your advice as I am nearly a noob when it comes to linux. I cannot update, and I think the problem stems from when I attempted to install TOR last year. I also if I try to search for a new application through the ubuntu software center it loads forever without any result until I close the window. When I type sudo apt-get update into a terminal I simply get:

E: Type '[deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <natty> main]' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Any help is appreciated!

---

### Post by Bucky Ball on 2012-03-20
Open Software Sources (or Software Centre), untick 'deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <natty> main' and try again.

---

### Post by IWantFroyo on 2012-03-20
Open the Software Center, hit Edit->Sources, and untick the source.

---

### Post by vincep123 on 2012-03-20
Thanks, but I still cannot update. I tried restarting also and the problem persists.

E: Type '[deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <natty> main]' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by Bucky Ball on 2012-03-20
Okay, doesn't sound like it was unticked so go the terminal method. Open a terminal and input this:

```
sudo nano /etc/apt/sources.list
```... find this line or the line containing it: 

```
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <natty> main
```Put a hash in front so it looks like this:

```
# deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <natty> main
```Hit control+x then enter to affirm 'Y'. Try an update. DON'T change anything else in that file and if you want to be ultra vigilant, make a copy of it before altering like this:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```If you screw up the file, the original can replace it with:

```
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list
```

---

### Post by vincep123 on 2012-03-24
This worked perfectly! Thanks a lot for your help!

---

### Post by Bucky Ball on 2012-03-24
No probs! Glad it worked. Enjoy the OS, the learning curve, and don't forget to post another thread with any new issues/questions. ;)

---

